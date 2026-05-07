# Sesión 3 (2h)
## Consultas SQL de análisis

## Contexto
Disponéis de un esquema y de datos validados. La tarea ahora es transformar esos datos en información útil para decidir mejoras sostenibles.

Esta sesión se centra en consultas SQL de análisis con `JOIN`, agregaciones, `GROUP BY`, `HAVING` y vistas.

## Objetivos de aprendizaje
1. Formular preguntas analíticas relevantes para el proyecto.
2. Diseñar consultas SQL que respondan esas preguntas.
3. Interpretar resultados y detectar sesgos o limitaciones.
4. Construir al menos una vista reutilizable para visualización.

## Trabajo a realizar
### 1) Definición de preguntas analíticas
Cada equipo debe redactar entre 4 y 6 preguntas de análisis priorizadas.

Ejemplos:

1. ¿Qué zonas concentran mayor consumo energético medio mensual?
2. ¿Cómo varía la generación de residuos por tipo a lo largo del trimestre?
3. ¿Existe relación entre ocupación de espacios y consumo eléctrico?

### 2) Traducción de preguntas a SQL
Para cada pregunta, construid consulta con estructura clara.

Ejemplo orientativo:

```sql
SELECT
    z.nombre_zona,
    TRUNC(m.fecha_medicion, 'MM') AS mes,
    SUM(m.consumo_kwh) AS consumo_mes
FROM medicion_energia m
JOIN zona_centro z ON z.id_zona = m.id_zona
GROUP BY z.nombre_zona, TRUNC(m.fecha_medicion, 'MM')
ORDER BY mes, consumo_mes DESC;
```

### 3) Uso de `HAVING` para detectar focos de acción
Identificad categorías o zonas que superen umbrales definidos por el equipo.

### 4) Creación de vistas
Convertid una consulta clave en vista para facilitar reutilización en sesión 4.

Ejemplo orientativo:

```sql
CREATE OR REPLACE VIEW vw_resumen_consumo_zona AS
SELECT z.nombre_zona, SUM(m.consumo_kwh) AS total_kwh
FROM medicion_energia m
JOIN zona_centro z ON z.id_zona = m.id_zona
GROUP BY z.nombre_zona;
```

## Preguntas guía
1. ¿Qué diferencia hay entre una consulta técnicamente correcta y una consulta útil para decidir?
2. ¿Qué resultado puede ser matemáticamente correcto pero engañoso en contexto?
3. ¿Qué agregación (suma, media, mediana) describe mejor vuestro caso?
4. ¿Qué conclusión nunca deberíais afirmar con los datos actuales?

## Decisiones obligatorias del equipo
1. Selección de indicadores principales y secundarios.
2. Definición de umbrales para detectar prioridades.
3. Criterios de ordenación y comparación (por mes, por zona, por tipo).
4. Consulta que se convertirá en vista estable para el panel.

## Entregables parciales
1. `03_consultas.sql` con al menos 6 consultas analíticas comentadas.
2. `04_vistas.sql` con mínimo 1 vista justificada.
3. `03_interpretacion_preliminar.md` con lectura crítica por consulta:

| Consulta | Qué mide | Resultado clave | Riesgo de interpretación |
|---|---|---|---|
| Q1 | consumo mensual por zona | Taller Web lidera 3 meses | posible sesgo por mayor horario |

## Checklist de validación
- [ ] Cada consulta responde una pregunta explícita.
- [ ] Hay uso correcto de `JOIN`, `GROUP BY` y agregaciones.
- [ ] Se ha utilizado `HAVING` al menos en una consulta.
- [ ] Existe al menos una vista reutilizable.
- [ ] Se incluyen limitaciones y cautelas de interpretación.
