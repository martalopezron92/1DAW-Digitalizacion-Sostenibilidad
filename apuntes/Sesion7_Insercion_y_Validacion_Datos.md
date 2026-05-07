# Sesión 5 – Inserción y validación de datos en Oracle XE

**Proyecto:** Digitalización + Sostenibilidad – "Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible"
**Objetivo de la sesión:** Cargar datos en el esquema físico de forma ordenada, coherente con las restricciones definidas, y verificar su calidad antes de pasar al análisis.

---

## 1. La carga de datos como fase técnica

Insertar datos no es simplemente rellenar tablas. Es construir la evidencia sobre la que se apoyarán todas las consultas, gráficos y propuestas de mejora sostenible del proyecto.

Una carga de datos deficiente puede producir:

- Resultados de análisis incorrectos, aunque el SQL sea perfecto.
- Conclusiones engañosas sobre consumo, residuos o movilidad.
- Propuestas sostenibles basadas en información no fiable.

Por eso, la inserción y la validación son inseparables.

---

## 2. Orden de inserción: respetar dependencias

Cuando existen claves foráneas, el orden de inserción importa. Se deben cargar primero las tablas referenciadas (padres) y después las que las referencian (hijos).

Esquema de dependencias habitual en este proyecto:

```
tipo_zona
    |
    v
zona_centro
    |
    v
medicion_energia / medicion_residuos / registro_movilidad
```

Si se intenta insertar en `medicion_energia` antes de que exista el `id_zona` correspondiente en `zona_centro`, Oracle devuelve error de violación de integridad referencial.

Orden recomendado de carga:

1. Tablas de catálogo (sin FK): `tipo_zona`, `tipo_residuo`, `tipo_transporte`.
2. Tablas maestras: `zona_centro`, `proveedor_energia`.
3. Tablas de hechos: `medicion_energia`, `medicion_residuos`, `registro_movilidad`.

---

## 3. Instrucción INSERT en Oracle

### 3.1. Sintaxis básica

```sql
INSERT INTO nombre_tabla (columna1, columna2, columna3)
VALUES (valor1, valor2, valor3);
```

Especificar siempre las columnas explícitamente. Si el orden de columnas cambia en el futuro, una inserción sin lista de columnas fallará o insertará datos incorrectos.

### 3.2. Inserción de fechas

En Oracle, el tipo `DATE` almacena fecha y hora. Para insertar solo fecha se recomienda el literal `DATE`:

```sql
INSERT INTO medicion_energia (id_medicion, id_zona, fecha_medicion, consumo_kwh, fuente_energia)
VALUES (5001, 101, DATE '2026-02-01', 128.75, 'RED');
```

Evitar el formato `'01/02/2026'` sin función de conversión: Oracle puede interpretarlo de forma diferente según la configuración regional del sistema.

Si se necesita convertir texto a fecha de forma controlada:

```sql
TO_DATE('01/02/2026', 'DD/MM/YYYY')
```

### 3.3. Inserción de catálogos (referencia orientativa)

```sql
INSERT INTO tipo_zona VALUES (1, 'AUL', 'Aula estándar');
INSERT INTO tipo_zona VALUES (2, 'LAB', 'Laboratorio');
INSERT INTO tipo_zona VALUES (3, 'OFI', 'Oficina administrativa');
INSERT INTO tipo_zona VALUES (4, 'COM', 'Zona común');
```

### 3.4. Inserción de tablas maestras (referencia orientativa)

```sql
INSERT INTO zona_centro (id_zona, nombre_zona, id_tipo, superficie)
VALUES (101, 'Aula A1', 1, 48.5);

INSERT INTO zona_centro (id_zona, nombre_zona, id_tipo, superficie)
VALUES (102, 'Taller Web', 2, 72.0);
```

### 3.5. Confirmar o deshacer cambios: COMMIT y ROLLBACK

Oracle trabaja con transacciones. Las inserciones no son permanentes hasta ejecutar `COMMIT`.

```sql
-- Confirmar los cambios
COMMIT;

-- Deshacer cambios no confirmados
ROLLBACK;
```

Buena práctica: hacer `COMMIT` al final de cada lote validado, no tras cada INSERT individual.

---

## 4. Calidad del dato: cinco dimensiones clave

| Dimensión | Pregunta de control | Señal de alerta |
|---|---|---|
| Completitud | ¿Faltan valores en campos críticos? | Alto porcentaje de `NULL` en métricas |
| Validez | ¿Los valores cumplen las reglas del dominio? | Consumos negativos, porcentajes > 100 |
| Consistencia | ¿El mismo concepto usa el mismo formato? | 'kg', 'KG', 'Kg' mezclados en la misma columna |
| Unicidad | ¿Hay registros duplicados funcionalmente? | Misma medición del mismo sensor en la misma fecha dos veces |
| Trazabilidad | ¿Se conoce origen, fecha y responsable de los datos? | Filas sin indicación de fuente |

Un dataset puede ser técnicamente válido (no viola restricciones) y al mismo tiempo tener problemas de calidad que afecten al análisis. Las restricciones del DDL capturan errores graves; las validaciones SQL detectan problemas más sutiles.

---

## 5. Consultas de validación esenciales

Ejecutar estas consultas tras cada lote de inserción.

### 5.1. Conteo de filas por tabla

```sql
SELECT 'tipo_zona'        AS tabla, COUNT(*) AS total FROM tipo_zona        UNION ALL
SELECT 'zona_centro',              COUNT(*)           FROM zona_centro       UNION ALL
SELECT 'medicion_energia',         COUNT(*)           FROM medicion_energia;
```

### 5.2. Nulos en campos críticos

```sql
SELECT
    COUNT(*) AS registros_totales,
    COUNT(consumo_kwh) AS con_consumo,
    COUNT(*) - COUNT(consumo_kwh) AS nulos_consumo,
    COUNT(*) - COUNT(fecha_medicion) AS nulos_fecha
FROM medicion_energia;
```

### 5.3. Valores fuera de rango

```sql
-- Consumos negativos o anómalos
SELECT id_medicion, consumo_kwh
FROM medicion_energia
WHERE consumo_kwh < 0 OR consumo_kwh > 50000;

-- Fechas futuras (imposibles en mediciones históricas)
SELECT id_medicion, fecha_medicion
FROM medicion_energia
WHERE fecha_medicion > SYSDATE;
```

### 5.4. Registros huérfanos (FK no satisfecha)

```sql
SELECT m.id_medicion, m.id_zona
FROM medicion_energia m
LEFT JOIN zona_centro z ON m.id_zona = z.id_zona
WHERE z.id_zona IS NULL;
```

Un resultado vacío en esta consulta confirma que la integridad referencial es correcta.

### 5.5. Duplicados funcionales

```sql
SELECT id_zona, fecha_medicion, fuente_energia, COUNT(*) AS repeticiones
FROM medicion_energia
GROUP BY id_zona, fecha_medicion, fuente_energia
HAVING COUNT(*) > 1;
```

---

## 6. Gestión de incidencias de calidad

Cuando se detecta un problema, existen tres decisiones posibles. Ninguna es universalmente correcta: depende del impacto sobre el análisis.

| Decisión | Cuándo aplicarla | Riesgo |
|---|---|---|
| Corregir en origen | El error es verificable y corregible | Requiere acceso a la fuente original |
| Excluir el registro | El error es irreparable y el registro es minoritario | Pérdida de información real |
| Conservar y documentar | El error es importante y no corregible, pero afectar al análisis | Riesgo de conclusiones basadas en datos marcados |

Documentar siempre la decisión tomada en el informe de calidad del dato, con evidencia SQL.

Ejemplo de tabla de incidencias:

| Incidencia | Consulta que la detecta | Volumen | Decisión | Justificación |
|---|---|---|---|---|
| 3 registros con consumo negativo | `WHERE consumo_kwh < 0` | 3 filas | excluir | Probable error de captura, no recuperable |
| 2 duplicados por zona y fecha | consulta de duplicados | 2 grupos | conservar el más reciente | Se asume que el segundo registro corrige al primero |

---

## 7. Carga desde CSV en Oracle XE

Si los datos provienen de un fichero CSV, Oracle no dispone de `\copy` como PostgreSQL. Las opciones habituales en el contexto de este proyecto son:

### 7.1. Importación desde DBeaver

DBeaver permite importar datos CSV directamente:

1. Clic derecho sobre la tabla de destino en el árbol de objetos.
2. Opción "Import Data".
3. Seleccionar fuente CSV, configurar delimitador y mapeo de columnas.
4. Revisar vista previa antes de confirmar.

### 7.2. Conversión a sentencias INSERT

Para volúmenes pequeños (menos de 500 filas), generar el script `INSERT` desde Excel o cualquier hoja de cálculo es un método sencillo.

Ejemplo en una hoja de cálculo con los datos en columnas A, B, C:

```
="INSERT INTO medicion_energia VALUES ("&A1&", "& B1 &", DATE '"& TEXT(C1,"YYYY-MM-DD") &"', ...);"
```

---

## 8. Errores frecuentes en la fase de carga

| Error | Causa | Solución |
|---|---|---|
| Error de FK al insertar | Tabla padre no cargada o id inexistente | Respetar el orden de carga |
| Fechas rechazadas | Formato incompatible con NLS_DATE_FORMAT | Usar `DATE 'YYYY-MM-DD'` o `TO_DATE` |
| Categoría rechazada por CHECK | Valor no incluido en el dominio definido | Revisar valores del CSV contra el CHECK del DDL |
| Truncado de texto | Campo VARCHAR2 demasiado corto | Ajustar longitud en DDL antes de cargar |
| Datos cargados sin COMMIT | Al cerrar sesión, los datos desaparecen | Confirmar con `COMMIT` tras validar cada lote |

---

## 9. Mini retos de reflexión

1. Detectáis que el 8% de los registros de consumo de agua tienen valor `NULL`. ¿Qué impacto tiene esto en una consulta que calcula la media mensual de consumo con `AVG`? ¿Y si se calcula la suma?

2. Tenéis dos filas para la misma zona y el mismo mes con consumos distintos. ¿Cómo decidís cuál es el correcto sin poder consultar la fuente original?

3. ¿Por qué es preferible detectar errores de calidad con consultas SQL antes que corregirlos directamente sobre el CSV?
