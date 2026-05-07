# Sesión 4 (2h)
## Visualización e interpretación de datos en DBeaver

## Contexto
Ya disponéis de consultas y vistas de análisis. En esta sesión debéis convertir resultados SQL en visualizaciones claras y defender su interpretación técnica.

El objetivo no es crear muchas gráficas, sino seleccionar visualizaciones que ayuden a tomar decisiones sostenibles.

## Objetivos de aprendizaje
1. Elegir visualizaciones adecuadas al tipo de información.
2. Construir un panel básico en DBeaver basado en consultas/vistas propias.
3. Interpretar resultados con rigor y cautela.
4. Formular propuestas de mejora sostenibles apoyadas en evidencia.

## Trabajo a realizar
### 1) Selección de mensajes clave
Definid 3 mensajes que queréis comunicar a partir de datos.

Ejemplo:

1. Evolución mensual de consumo energético.
2. Comparación de residuos por tipo y zona.
3. Identificación de áreas prioritarias de actuación.

### 2) Relación consulta-grafica
Para cada mensaje, asociad consulta o vista y tipo de visualización justificado.

Tabla de decisión sugerida:

| Mensaje | Consulta/Vista | Tipo de gráfico | Por qué es adecuado |
|---|---|---|---|
| Evolución mensual | vw_consumo_mensual_zona | línea | permite ver tendencia temporal |

### 3) Diseño del panel
Configurad un panel simple y legible, con coherencia de títulos, unidades y ejes.

Recomendaciones:

1. Evitad sobrecargar con demasiadas categorías.
2. Indicad unidades y periodo en cada visual.
3. Mantened criterios homogéneos de color y orden.

### 4) Interpretación crítica
Redactad conclusiones separando:

1. Hechos observados (lo que muestran los datos).
2. Hipótesis explicativas (posibles causas).
3. Propuestas viables (acciones sostenibles con impacto esperable).

## Preguntas guía
1. ¿Qué visualización ayuda mejor a decidir una acción concreta?
2. ¿Qué gráfico podría inducir una lectura incorrecta en vuestro caso?
3. ¿Qué dato faltante limita vuestra interpretación?
4. ¿Cómo evitar afirmaciones causales cuando solo tenéis correlaciones?

## Decisiones obligatorias del equipo
1. Número final de visualizaciones (mínimo 3, máximo 5).
2. Convención visual (colores, etiquetas, unidades, orden).
3. Criterio para priorizar propuestas de mejora.
4. Nivel de confianza de cada conclusión (alto, medio, bajo).

## Entregables parciales
1. `05_panel_dbeaver` (capturas o exportaciones de visualizaciones).
2. `05_diccionario_visual.md`:

| Visualización | Fuente SQL | Indicador | Interpretación principal | Riesgo de lectura |
|---|---|---|---|---|
| V1 | vw_consumo_mensual_zona | kWh/mes | tendencia ascendente en invierno | faltan datos de fines de semana |

3. `05_propuestas_mejora.md` con 3 propuestas priorizadas y justificadas por datos.

## Checklist de validación
- [ ] Cada gráfico responde a una pregunta explícita.
- [ ] Todas las visualizaciones tienen título, unidad y periodo.
- [ ] El panel está alimentado por consultas o vistas propias.
- [ ] Se distinguen hechos, hipótesis y propuestas.
- [ ] Las propuestas están priorizadas y justificadas con evidencia.
