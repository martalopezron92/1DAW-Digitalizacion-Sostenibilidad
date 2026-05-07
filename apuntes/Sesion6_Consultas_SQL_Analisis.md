# Sesión 6 – Consultas SQL de análisis

**Proyecto:** Digitalización + Sostenibilidad – "Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible"
**Objetivo de la sesión:** Diseñar consultas SQL con propósito analítico real, dominar `JOIN`, agregaciones, `GROUP BY`, `HAVING` y vistas para extraer información útil en la toma de decisiones sostenibles.

---

## 1. De la consulta técnica a la pregunta de negocio

Una consulta SQL analítica no empieza por el código: empieza por una pregunta que alguien necesita responder para tomar una decisión.

Proceso recomendado:

1. Formular la pregunta en lenguaje natural.
2. Identificar qué tablas y columnas contienen la información.
3. Determinar si es necesario cruzar tablas, filtrar, agrupar o calcular.
4. Escribir y ejecutar la consulta.
5. Interpretar el resultado con cautela.

Ejemplos de preguntas analíticas del proyecto:

- ¿Qué zona del centro consume más energía eléctrica de media cada mes?
- ¿Ha crecido la generación de residuos orgánicos en el último trimestre?
- ¿Qué tipo de transporte usan mayoritariamente los alumnos para llegar al centro?
- ¿Existen zonas con consumo excepcionalmente alto que justifiquen intervención inmediata?

---

## 2. Funciones de agregación en Oracle

Las funciones de agregación calculan un único valor a partir de un conjunto de filas.

| Función | Qué calcula | Nota importante |
|---|---|---|
| `COUNT(*)` | Número total de filas | Incluye nulos |
| `COUNT(columna)` | Número de filas con valor no nulo | Útil para detectar nulos |
| `SUM(columna)` | Suma de todos los valores | Ignora nulos |
| `AVG(columna)` | Media aritmética | Ignora nulos (ojo: puede ser engañoso) |
| `MAX(columna)` | Valor máximo | |
| `MIN(columna)` | Valor mínimo | |
| `ROUND(valor, n)` | Redondeo a n decimales | No es función de agregación, pero se usa junto a ellas |

Ejemplo: consumo medio mensual redondeado a dos decimales.

```sql
SELECT ROUND(AVG(consumo_kwh), 2) AS media_kwh
FROM medicion_energia;
```

Precaución con `AVG` y nulos: si una zona tiene cinco mediciones, tres con valor y dos con `NULL`, `AVG` calcula sobre tres filas, no sobre cinco. El resultado puede sobreestimar o subestimar el consumo real.

---

## 3. GROUP BY: agregaciones por categoría

`GROUP BY` divide el conjunto de resultados en grupos y aplica la función de agregación a cada grupo por separado.

Regla fundamental: toda columna del `SELECT` que no esté dentro de una función de agregación debe aparecer en el `GROUP BY`.

```sql
-- Consumo total por zona
SELECT
    id_zona,
    SUM(consumo_kwh) AS consumo_total
FROM medicion_energia
GROUP BY id_zona
ORDER BY consumo_total DESC;
```

Para obtener el nombre de la zona en lugar del identificador, es necesario un `JOIN`.

---

## 4. JOIN: cruzar información de varias tablas

### 4.1. INNER JOIN

Devuelve solo las filas que tienen correspondencia en ambas tablas.

```sql
SELECT
    z.nombre_zona,
    SUM(m.consumo_kwh) AS consumo_total
FROM medicion_energia m
INNER JOIN zona_centro z ON m.id_zona = z.id_zona
GROUP BY z.nombre_zona
ORDER BY consumo_total DESC;
```

### 4.2. LEFT JOIN

Devuelve todas las filas de la tabla izquierda aunque no tengan correspondencia en la derecha. Útil para detectar zonas sin mediciones.

```sql
SELECT
    z.nombre_zona,
    COUNT(m.id_medicion) AS num_mediciones
FROM zona_centro z
LEFT JOIN medicion_energia m ON z.id_zona = m.id_zona
GROUP BY z.nombre_zona
ORDER BY num_mediciones;
```

Las zonas con `num_mediciones = 0` son zonas registradas pero sin datos de consumo: una señal de posible omisión en la recogida de datos.

### 4.3. Múltiples JOIN

Se pueden encadenar varios `JOIN` para cruzar más de dos tablas:

```sql
SELECT
    z.nombre_zona,
    t.nombre AS tipo_zona,
    ROUND(AVG(m.consumo_kwh), 2) AS media_kwh
FROM medicion_energia m
JOIN zona_centro z ON m.id_zona = z.id_zona
JOIN tipo_zona t   ON z.id_tipo = t.id_tipo
GROUP BY z.nombre_zona, t.nombre
ORDER BY media_kwh DESC;
```

---

## 5. Filtrado temporal con TRUNC

En Oracle, `TRUNC(fecha, 'MM')` trunca una fecha al primer día del mes, lo que permite agrupar mediciones por periodo sin importar el día exacto.

```sql
SELECT
    TRUNC(fecha_medicion, 'MM') AS mes,
    SUM(consumo_kwh)             AS consumo_mensual
FROM medicion_energia
GROUP BY TRUNC(fecha_medicion, 'MM')
ORDER BY mes;
```

Otras opciones de truncado:

| Patrón | Resultado |
|---|---|
| `TRUNC(fecha, 'MM')` | Primer día del mes |
| `TRUNC(fecha, 'YYYY')` | Primer día del año |
| `TRUNC(fecha, 'IW')` | Primer día de la semana ISO |

---

## 6. HAVING: filtrar grupos después de agregar

`WHERE` filtra filas antes de agrupar. `HAVING` filtra grupos después de aplicar la función de agregación.

```sql
-- Zonas cuyo consumo total supera 300 kWh en el periodo analizado
SELECT
    z.nombre_zona,
    SUM(m.consumo_kwh) AS consumo_total
FROM medicion_energia m
JOIN zona_centro z ON m.id_zona = z.id_zona
GROUP BY z.nombre_zona
HAVING SUM(m.consumo_kwh) > 300
ORDER BY consumo_total DESC;
```

Error frecuente: usar `WHERE SUM(...)` en lugar de `HAVING SUM(...)`. Oracle rechaza funciones de agregación en la cláusula `WHERE`.

Combinar `WHERE` y `HAVING` en una misma consulta:

```sql
SELECT
    z.nombre_zona,
    TRUNC(m.fecha_medicion, 'MM') AS mes,
    SUM(m.consumo_kwh) AS consumo_mes
FROM medicion_energia m
JOIN zona_centro z ON m.id_zona = z.id_zona
WHERE m.fuente_energia = 'RED'                  -- filtro previo a la agregación
GROUP BY z.nombre_zona, TRUNC(m.fecha_medicion, 'MM')
HAVING SUM(m.consumo_kwh) > 150                 -- filtro sobre el resultado agregado
ORDER BY mes, consumo_mes DESC;
```

---

## 7. Patrones de consulta analítica habituales en el proyecto

### Patrón 1: Ranking por indicador

```sql
-- Las 3 zonas con mayor consumo medio por medición
SELECT
    z.nombre_zona,
    ROUND(AVG(m.consumo_kwh), 2) AS media_kwh,
    COUNT(m.id_medicion)         AS num_mediciones
FROM medicion_energia m
JOIN zona_centro z ON m.id_zona = z.id_zona
GROUP BY z.nombre_zona
ORDER BY media_kwh DESC
FETCH FIRST 3 ROWS ONLY;
```

### Patrón 2: Evolución temporal de un indicador

```sql
SELECT
    TRUNC(fecha_medicion, 'MM') AS mes,
    SUM(consumo_kwh)             AS consumo_total,
    ROUND(AVG(consumo_kwh), 2)   AS consumo_medio
FROM medicion_energia
GROUP BY TRUNC(fecha_medicion, 'MM')
ORDER BY mes;
```

### Patrón 3: Comparación entre categorías

```sql
SELECT
    fuente_energia,
    COUNT(*)             AS num_registros,
    SUM(consumo_kwh)     AS total_kwh,
    ROUND(AVG(consumo_kwh), 2) AS media_kwh
FROM medicion_energia
GROUP BY fuente_energia
ORDER BY total_kwh DESC;
```

### Patrón 4: Detección de zonas sin datos

```sql
SELECT z.nombre_zona
FROM zona_centro z
LEFT JOIN medicion_energia m ON z.id_zona = m.id_zona
WHERE m.id_medicion IS NULL;
```

---

## 8. Vistas SQL

Una **vista** es una consulta almacenada en la base de datos a la que se puede acceder como si fuera una tabla. No almacena datos; los recupera dinámicamente al consultarla.

Ventajas en este proyecto:

- Reutilizar consultas complejas en visualizaciones.
- Simplificar el código de análisis posterior.
- Ocultar la complejidad de los `JOIN` a quien solo necesita el resultado.

### 8.1. Creación de una vista en Oracle

```sql
CREATE OR REPLACE VIEW vw_consumo_mensual_zona AS
SELECT
    z.nombre_zona,
    TRUNC(m.fecha_medicion, 'MM') AS mes,
    SUM(m.consumo_kwh)            AS consumo_mensual_kwh,
    COUNT(m.id_medicion)          AS num_registros
FROM medicion_energia m
JOIN zona_centro z ON z.id_zona = m.id_zona
GROUP BY z.nombre_zona, TRUNC(m.fecha_medicion, 'MM');
```

### 8.2. Consulta sobre la vista

```sql
SELECT * FROM vw_consumo_mensual_zona
ORDER BY mes, consumo_mensual_kwh DESC;
```

### 8.3. Cuándo crear una vista

Convertid en vista una consulta cuando:

- Se reutiliza en más de una visualización o análisis.
- Es lo suficientemente compleja para que reescribirla sea un riesgo.
- Sirve como indicador estable del proyecto.

---

## 9. Errores frecuentes en consultas de análisis

| Error | Descripción | Corrección |
|---|---|---|
| Columna fuera de GROUP BY | Columna no agregada en SELECT pero no en GROUP BY | Añadirla al GROUP BY o envolverla en función de agregación |
| WHERE sobre agregado | `WHERE SUM(...) > valor` | Usar `HAVING SUM(...) > valor` |
| JOIN sin condición | Producto cartesiano (todas las combinaciones posibles) | Incluir siempre la condición `ON` |
| Alias en WHERE | `WHERE alias > valor` con alias definido en SELECT | Repetir la expresión o usar subconsulta |
| Interpretar AVG sin revisar COUNT | Media calculada sobre pocas filas | Siempre incluir `COUNT(*)` junto a `AVG` |

---

## 10. Buenas prácticas en consultas de análisis

1. Documentar cada consulta con un comentario que indique su objetivo y la decisión que apoya.
2. Usar alias descriptivos con `AS`: `consumo_total` es mejor que `c`.
3. Incluir siempre `ORDER BY` en consultas de ranking o temporal.
4. Revisar el número de filas del resultado antes de interpretarlo.
5. Comparar resultados con valores de referencia (otro periodo, otra zona, objetivo interno).

Plantilla de documentación de consulta:

```sql
-- Objetivo: identificar zonas prioritarias para medidas de eficiencia energética.
-- Decisión asociada: enfocar la propuesta de mejora en las 3 zonas de mayor consumo medio.
SELECT
    z.nombre_zona,
    ROUND(AVG(m.consumo_kwh), 2) AS media_kwh
FROM medicion_energia m
JOIN zona_centro z ON m.id_zona = z.id_zona
GROUP BY z.nombre_zona
ORDER BY media_kwh DESC
FETCH FIRST 3 ROWS ONLY;
```

---

## 11. Mini retos de reflexión

1. Una consulta devuelve que la zona "Taller Web" tiene el mayor consumo total del trimestre. ¿Podría tener el mayor consumo total pero no el mayor consumo medio? ¿Qué implica cada uno en términos de actuación?

2. Si utilizáis `AVG(consumo_kwh)` sobre una tabla donde el 15% de las filas tienen `NULL`, ¿es el resultado representativo? ¿Qué alternativa tenéis para ser más honestos en el informe?

3. ¿Por qué una vista es más adecuada que copiar y pegar la misma consulta en tres visualizaciones diferentes?
