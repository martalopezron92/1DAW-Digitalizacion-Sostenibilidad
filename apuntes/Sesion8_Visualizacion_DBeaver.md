# Sesión 7 – Visualización e interpretación de datos en DBeaver

**Proyecto:** Digitalización + Sostenibilidad – "Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible"
**Objetivo de la sesión:** Construir visualizaciones útiles a partir de consultas y vistas propias en DBeaver, interpretarlas con rigor técnico y formular propuestas de mejora sostenible apoyadas en evidencia.

---

## 1. Visualización de datos: objetivo y límites

Visualizar datos no es decorar resultados. El objetivo es facilitar la lectura de información compleja para que una persona pueda tomar decisiones mejor informadas.

Una buena visualización cumple tres condiciones:

1. Responde una pregunta concreta.
2. Es comprensible para quien toma la decisión.
3. No distorsiona la magnitud ni el mensaje del dato.

Una visualización deficiente puede ser peor que no tener ninguna: puede inducir conclusiones falsas a partir de datos correctos.

---

## 2. DBeaver: herramienta de consulta y visualización

DBeaver es un cliente de bases de datos que permite conectarse a Oracle XE, ejecutar SQL y generar visualizaciones básicas a partir de los resultados de una consulta.

### 2.1. Conexión a Oracle XE en DBeaver

Pasos generales:

1. Nueva conexión: seleccionar Oracle en el asistente de conexión.
2. Configurar host (`localhost`), puerto (`1521`), SID o Service Name (`XE`).
3. Introducir usuario y contraseña del esquema de trabajo.
4. Verificar la conexión antes de cerrar el asistente.

### 2.2. Editor SQL

Para abrir el editor SQL sobre la conexión activa:

- Menú "SQL Editor" > "New SQL Script".
- O clic derecho sobre la base de datos > "SQL Editor".

Buenas prácticas en el editor:

- Guardar los scripts en ficheros `.sql` con nombres descriptivos.
- Usar comentarios `--` para documentar cada consulta.
- Ejecutar con F5 o el botón de ejecución del editor.

### 2.3. Panel de visualización

Una vez ejecutada una consulta, los resultados aparecen en la pestaña "Data". Para crear una gráfica:

1. Hacer clic en el icono de gráfico (Chart) en la barra inferior de resultados.
2. Seleccionar el tipo de gráfico.
3. Configurar ejes: columna para el eje X y columna para el eje Y.
4. Exportar la imagen si es necesario (clic derecho sobre el gráfico).

---

## 3. Tipos de gráfico y cuándo usarlos

Elegir el tipo de gráfico incorrecto puede hacer que los datos sean difíciles de leer o que el mensaje quede distorsionado.

| Tipo de gráfico | Mejor para | Evitar cuando |
|---|---|---|
| Gráfico de líneas | Evolución de un indicador en el tiempo | El eje X no es temporal o continuo |
| Gráfico de barras verticales | Comparar valores entre categorías discretas | Hay más de 10-12 categorías |
| Gráfico de barras horizontales | Comparar categorías con nombres largos | Se quiere mostrar tendencia temporal |
| Barras apiladas | Ver composición de un total por categorías | Las categorías son demasiado similares en valor |
| Gráfico de tarta | Mostrar proporciones de un total (pocas categorías) | Más de 5-6 categorías o valores muy parecidos |
| Diagrama de dispersión | Explorar relación entre dos variables numéricas | Las variables no son comparables o tienen unidades muy distintas |

Ejemplo de asignación en el proyecto:

| Pregunta analítica | Tipo recomendado | Justificación |
|---|---|---|
| Evolución del consumo energético mensual | Línea | El eje X es tiempo continuo |
| Consumo total por zona en el trimestre | Barras horizontales | Permite leer bien los nombres de zona |
| Proporción de residuos por tipo | Tarta o barras apiladas | Composición de un total en pocas categorías |
| Relación entre superficie de zona y consumo | Dispersión | Dos variables numéricas continuas |

---

## 4. Criterios de calidad visual

Una visualización bien construida incluye:

1. **Título informativo**: debe incluir qué se mide, en qué unidades y qué periodo cubre.
2. **Ejes con etiquetas y unidades**: sin unidades, los valores carecen de contexto.
3. **Orden lógico de categorías**: ordenar por valor descendente facilita la lectura.
4. **Escalas honestas**: el eje Y debe empezar en 0 en gráficos de barras; truncarlo puede exagerar diferencias pequeñas.
5. **Leyenda clara**: si hay más de una serie de datos, indicar qué representa cada color.
6. **Sin sobrecargar**: menos es más; cada elemento visual que añadís debe aportar información.

Errores visuales frecuentes:

| Error | Efecto | Solución |
|---|---|---|
| Eje Y que no empieza en 0 en barras | Diferencias pequeñas parecen enormes | Ajustar el origen del eje |
| Demasiadas categorías en una tarta | Ilegible, porciones indiferenciables | Agrupar categorías menores en "Otros" |
| Colores sin coherencia | El lector no puede comparar entre gráficos | Usar la misma paleta en todo el panel |
| Título genérico ("Gráfico 1") | El lector no sabe qué está viendo | Título específico y descriptivo |
| Gráfica sin fuente ni periodo | Resultado no verificable | Indicar fuente SQL y rango temporal |

---

## 5. De la visualización a la interpretación

Ver una gráfica no equivale a interpretarla. Una interpretación técnica rigurosa distingue tres niveles:

### Nivel 1: Hechos observados

Descripción objetiva de lo que muestran los datos, sin hipótesis ni valoraciones.

Ejemplo: "El laboratorio de informática registra el mayor consumo mensual acumulado, con 318 kWh en el primer trimestre, frente a una media de 187 kWh en el resto de zonas."

### Nivel 2: Hipótesis explicativas

Posibles causas del patrón observado, formuladas como hipótesis, no como certezas.

Ejemplo: "El mayor consumo del laboratorio podría estar relacionado con la presencia de equipos informáticos de alta potencia, mayor ocupación horaria o ausencia de configuraciones de ahorro energético."

### Nivel 3: Propuestas de mejora

Acciones concretas y viables, con impacto esperable y forma de medir el resultado.

Ejemplo: "Propuesta: activar perfiles de ahorro energético en los equipos del laboratorio fuera del horario lectivo. Impacto esperado: reducción del 10-15% en consumo mensual. Indicador de seguimiento: consumo mensual del laboratorio en el siguiente trimestre."

---

## 6. Límites de la interpretación: qué no se puede afirmar

Es tan importante saber qué se puede concluir como reconocer qué no se puede afirmar con los datos disponibles.

| Situación | Afirmación incorrecta | Afirmación correcta |
|---|---|---|
| Solo tres meses de datos | "El consumo siempre sube en invierno" | "En los tres meses disponibles, el consumo fue mayor en enero que en octubre" |
| Un solo curso académico | "El centro consume más que la media nacional" | "No disponemos de datos comparativos externos para establecer este contraste" |
| Correlación entre dos variables | "El consumo alto se debe al número de alumnos" | "Existe una relación aparente entre ocupación y consumo que requeriría datos adicionales para confirmar" |

---

## 7. Construcción de un panel mínimo viable

Para el proyecto, el panel de visualización debe responder entre tres y cinco preguntas de análisis. Una estructura recomendada:

| Posición en el panel | Pregunta que responde | Tipo de gráfico |
|---|---|---|
| V1 (primera, central) | Evolución temporal del indicador principal | Línea |
| V2 | Comparación entre zonas o categorías clave | Barras horizontales |
| V3 | Composición por tipo en el periodo analizado | Barras apiladas o tarta |
| V4 (opcional) | Detección de focos de actuación prioritaria | Barras con línea de umbral |

Cada visualización debe estar apoyada por una consulta o vista propia del equipo. Nunca generar gráficos directamente sobre consultas sin revisar ni documentar.

---

## 8. Ejemplo completo: de consulta a visualización

Consulta (sesión SQL en DBeaver):

```sql
-- Objetivo: ver la evolución mensual del consumo energético total por tipo de fuente.
-- Decisión: identificar si la energía solar gana peso relativo a lo largo del trimestre.
SELECT
    TRUNC(m.fecha_medicion, 'MM') AS mes,
    m.fuente_energia,
    SUM(m.consumo_kwh)            AS consumo_total
FROM medicion_energia m
GROUP BY TRUNC(m.fecha_medicion, 'MM'), m.fuente_energia
ORDER BY mes, fuente_energia;
```

Tipo de gráfico: barras apiladas por mes, con una barra por fuente de energía.

Título: "Consumo energético mensual por fuente (kWh) – Primer trimestre 2026"

Interpretación:

- Hecho: la energía de red representa el 78% del total en enero, porcentaje que baja al 65% en marzo.
- Hipótesis: el aumento de la energía solar en primavera podría estar relacionado con mayor irradiación.
- Propuesta: revisar el rendimiento de los paneles en meses de menor producción y valorar ampliación.

---

## 9. Mini retos de reflexión

1. Tenéis una gráfica de barras que muestra cinco zonas con consumos entre 180 y 210 kWh. El eje Y empieza en 170. ¿Qué problema visual se produce? ¿Cómo lo corregís?

2. Una visualización muestra que los residuos orgánicos representan el 62% del total. ¿Qué información adicional necesitáis para saber si ese porcentaje es alto, normal o bajo para un centro educativo?

3. ¿Por qué es más útil para una dirección de centro una gráfica con tres meses de tendencia y una propuesta concreta que un dashboard con diez gráficos sin interpretación?
