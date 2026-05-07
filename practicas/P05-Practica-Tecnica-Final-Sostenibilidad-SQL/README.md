# Práctica técnica final evaluable
## Proyecto: Nuestro Instituto frente al Mundo

## 1. Contexto
Vuestro equipo debe consolidar el proyecto en un producto técnico completo basado en Oracle Database XE, SQL y visualización de datos en DBeaver. Esta práctica evalúa vuestra capacidad para transformar un diseño lógico en una solución funcional y argumentada para analizar sostenibilidad en el centro.

## 2. Objetivos de la práctica
1. Implementar un modelo físico coherente en Oracle XE.
2. Cargar y validar datos con criterios de calidad.
3. Diseñar consultas SQL de análisis con propósito real.
4. Construir vistas reutilizables para explotación de datos.
5. Elaborar visualizaciones útiles para toma de decisiones.
6. Interpretar resultados y proponer mejoras sostenibles justificadas.

## 3. Requisitos técnicos obligatorios
### 3.1. Diseño físico
1. Script `01_schema.sql` ejecutable desde esquema vacío.
2. Mínimo 5 tablas relacionadas.
3. PK en todas las tablas.
4. FK en relaciones principales.
5. Restricciones `NOT NULL` y `CHECK` en campos críticos.

### 3.2. Inserción y validación de datos
1. Script `02_datos.sql` o carga desde CSV documentada.
2. Volumen mínimo recomendado: entre 80 y 150 filas totales repartidas en tablas relevantes.
3. Script `02_validaciones.sql` con controles de:
   - nulos críticos,
   - valores fuera de rango,
   - duplicados funcionales,
   - huérfanos por integridad referencial.

### 3.3. Consultas de análisis
1. Script `03_consultas.sql` con mínimo 8 consultas analíticas.
2. Al menos:
   - 3 consultas con `JOIN`,
   - 3 consultas con agregaciones (`SUM`, `AVG`, `COUNT`, `MAX`, `MIN`),
   - 2 consultas con `GROUP BY` y `HAVING`.
3. Cada consulta debe incluir comentario de objetivo y posible uso en decisión.

### 3.4. Vistas SQL
1. Script `04_vistas.sql` con mínimo 2 vistas.
2. Cada vista debe tener una utilidad clara para informes o visualizaciones.

### 3.5. Visualización e interpretación
1. Mínimo 3 visualizaciones en DBeaver.
2. Cada visualización debe incluir título, unidad y periodo.
3. Documento `05_analisis_resultados.md` con:
   - hallazgos principales,
   - límites del análisis,
   - 3 propuestas de mejora sostenible justificadas por datos.

## 4. Requisitos mínimos de calidad
1. Coherencia entre modelo relacional inicial y modelo físico final.
2. Nomenclatura consistente en tablas, columnas y restricciones.
3. Evidencia de validación de datos antes del análisis.
4. Consultas legibles, estructuradas y documentadas.
5. Interpretaciones prudentes: distinguir hechos, hipótesis y propuestas.

## 5. Requisitos no permitidos
1. No se aceptan entregas con SQL exclusivamente generado sin justificación técnica propia.
2. No se aceptan consultas sin relación con preguntas de sostenibilidad del proyecto.
3. No se acepta un conjunto de gráficos sin interpretación escrita.
4. No se acepta una práctica que sea una copia literal de ejemplos de clase.

## 6. Estructura de entrega
Carpeta del equipo:

```text
/equipo-XX_practica-final-tecnica/
  01_schema.sql
  02_datos.sql                (o /datos_csv + notas de carga)
  02_validaciones.sql
  03_consultas.sql
  04_vistas.sql
  05_analisis_resultados.md
  /visualizaciones/           (capturas o exportaciones)
  /evidencias/                (resultados SQL relevantes)
  README.md                   (resumen ejecutivo técnico)
```

## 7. Criterios de evaluación
| Criterio | Qué se valora | Peso |
|---|---|---|
| Diseño físico | coherencia de tablas, tipos, PK/FK, restricciones | 25% |
| Calidad del dato | inserción ordenada, validaciones, gestión de incidencias | 20% |
| Consultas SQL | pertinencia analítica, corrección técnica y legibilidad | 25% |
| Vistas y visualización | reutilización, claridad visual y conexión con objetivos | 15% |
| Interpretación y propuestas | argumentación, pensamiento crítico y viabilidad sostenible | 15% |

## 8. Recomendaciones para rendir al máximo
1. Priorizad profundidad sobre cantidad: mejor 8 consultas sólidas que 20 superficiales.
2. Diseñad primero las preguntas de análisis y luego el SQL.
3. Documentad decisiones durante el proceso, no al final.
4. Verificad siempre integridad y calidad antes de graficar.
5. Reconoced limitaciones: mejora la credibilidad técnica.

## 9. Lista de control antes de entregar
- [ ] Todos los scripts ejecutan correctamente en Oracle XE.
- [ ] Se puede recrear el proyecto desde cero con vuestra entrega.
- [ ] Las consultas responden preguntas reales del proyecto.
- [ ] Las visualizaciones son legibles y coherentes con las consultas.
- [ ] Las propuestas sostenibles están justificadas por evidencia.
