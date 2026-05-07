# Sesión 2 (2h)
## Inserción y validación de datos

## Contexto
El esquema físico ya existe. Ahora toca poblarlo con datos útiles para el análisis. Insertar no es volcar información sin control: es construir evidencia fiable.

Trabajaréis con un conjunto inicial de datos (reales, simulados o mixtos) y aplicaréis verificaciones de calidad.

## Objetivos de aprendizaje
1. Insertar datos en orden coherente con dependencias entre tablas.
2. Verificar integridad referencial, completitud y validez.
3. Detectar errores de calidad y decidir cómo tratarlos.
4. Documentar criterios de limpieza y exclusión de datos.

## Trabajo a realizar
### 1) Plan de carga
Definid el orden de inserción (catálogos, tablas maestras, tablas de hechos).

Pregunta clave: ¿qué falla si invertís ese orden?

### 2) Inserción por lotes y control
Insertad datos por bloques para poder detectar errores pronto.

Ejemplo orientativo:

```sql
INSERT INTO zona_centro (id_zona, nombre_zona, tipo_zona)
VALUES (201, 'Taller Web', 'LABORATORIO');

INSERT INTO medicion_energia (id_medicion, id_zona, fecha_medicion, consumo_kwh, fuente_energia)
VALUES (9001, 201, DATE '2026-03-01', 152.40, 'RED');
```

### 3) Verificaciones mínimas
Diseñad y ejecutad consultas de comprobación para:

1. Conteo de filas por tabla.
2. Nulos en campos críticos.
3. Valores fuera de rango.
4. Registros huérfanos.
5. Duplicados funcionales.

Ejemplo orientativo:

```sql
SELECT COUNT(*) AS huerfanos
FROM medicion_energia m
LEFT JOIN zona_centro z ON m.id_zona = z.id_zona
WHERE z.id_zona IS NULL;
```

### 4) Gestión de incidencias
Cuando detectéis problemas, no basta con corregir: hay que justificar el criterio.

Opciones habituales:

1. Corregir en origen.
2. Excluir registro con justificación.
3. Mantener registro etiquetado como pendiente de revisión.

## Preguntas guía
1. ¿Qué errores invalidan un análisis y cuáles solo lo limitan?
2. ¿Qué impacto tendría eliminar datos incompletos frente a conservarlos?
3. ¿Cómo justificaríais ante dirección del centro una limpieza de datos concreta?
4. ¿Qué validación debería repetirse siempre antes de crear gráficos?

## Decisiones obligatorias del equipo
1. Criterio para tratar nulos en métricas críticas.
2. Criterio para duplicados funcionales.
3. Umbrales de valores aceptables en cada indicador.
4. Política de trazabilidad (fuente, fecha de carga, responsable del lote).

## Entregables parciales
1. `02_datos.sql` o conjunto de CSV con importación documentada.
2. `02_validaciones.sql` con consultas de control.
3. `02_calidad_dato.md` con tabla de incidencias:

| Incidencia | Evidencia SQL | Decisión | Justificación |
|---|---|---|---|
| Consumo negativo | consulta X | excluir | error de captura no verificable |

## Checklist de validación
- [ ] El orden de carga respeta dependencias entre tablas.
- [ ] Se han ejecutado validaciones mínimas con evidencia.
- [ ] Las incidencias tienen decisión y justificación.
- [ ] Existen datos suficientes para análisis por periodo y categoría.
- [ ] El equipo puede explicar la fiabilidad y límites del dataset.
