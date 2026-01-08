# 📊 Sesión 9 – Actividad: Diseño de Batería de Indicadores ASG
## Del Dato al Impacto: Interpretando tu modelo de datos

---

## 🎯 Objetivos de la actividad

Al finalizar esta actividad, habrás:
1. ✅ Identificado qué indicadores ASG puedes extraer de tu modelo de datos actual
2. ✅ Diseñado una batería de 5-8 indicadores priorizados y relevantes
3. ✅ Creado fichas técnicas completas para cada indicador
4. ✅ Preparado consultas conceptuales (pseudocódigo) para su futura implementación
5. ✅ Conectado tu proyecto con los ODS de forma práctica y medible

---

## 📋 Contexto

Ya has completado el **modelado de datos** de tu proyecto (diagrama ER + esquema SQL). Ahora es el momento de **dar sentido a esos datos desde la perspectiva de la sostenibilidad**.

Esta actividad es un **puente** entre:
- **LO QUE TIENES:** Tu modelo de datos (tablas, campos, relaciones)
- **LO QUE NECESITAS:** Información relevante para tomar decisiones sostenibles

**No necesitas dominar SQL todavía**, pero sí debes entender **qué preguntas puedes responder** con los datos que has estructurado.

---

## 📦 Entregables

Documento único en formato **Markdown** o **PDF** con el nombre:  
`Equipo-XX_Sesion9_Bateria_Indicadores_ASG.md` (o `.pdf`)

**Estructura del documento:**

```
📄 Equipo-XX_Sesion9_Bateria_Indicadores_ASG.md
│
├── 1. Contexto del Proyecto
├── 2. Análisis del Modelo de Datos
├── 3. Batería de Indicadores (5-8 fichas completas)
├── 4. Priorización y Justificación
├── 5. Consultas Conceptuales
└── 6. Plan de Implementación
```

---

## 🚀 PARTE 1: Contexto del Proyecto (10 minutos)

### Objetivo
Recordar y sintetizar el ámbito de trabajo de tu proyecto.

### Tareas

**1.1. Resumen del proyecto**

Completa esta ficha de forma breve:

```markdown
## 1. CONTEXTO DEL PROYECTO

### Título del proyecto
[Nombre descriptivo de vuestro proyecto]

### Ámbito de análisis
[¿Qué estáis analizando? Ej: consumo energético, residuos, movilidad, igualdad, etc.]

### ODS principales trabajados
- ODS X: [Nombre]
- ODS Y: [Nombre]
- (Listar 2-4 ODS prioritarios)

### Alcance
- **Temporal:** [Ej: curso 2024-2025, últimos 6 meses, etc.]
- **Espacial:** [Ej: todo el instituto, edificio principal, aulas de FP, etc.]
- **Poblacional:** [Ej: 450 estudiantes, 35 docentes, comunidad educativa completa]

### Pregunta de investigación principal
[¿Qué queréis saber? Ej: "¿Es eficiente el consumo energético de nuestro instituto?"]
```

**Ejemplo cumplimentado:**

```markdown
## 1. CONTEXTO DEL PROYECTO

### Título del proyecto
Análisis de eficiencia energética del IES Tecnológico

### Ámbito de análisis
Consumo eléctrico y de climatización en las instalaciones del centro

### ODS principales trabajados
- ODS 7: Energía asequible y no contaminante
- ODS 11: Ciudades y comunidades sostenibles
- ODS 13: Acción por el clima

### Alcance
- **Temporal:** Curso completo 2024-2025 (octubre-junio)
- **Espacial:** 3 edificios principales (A, B, C) del instituto
- **Poblacional:** 420 estudiantes + 38 docentes + personal no docente

### Pregunta de investigación principal
¿Cuál es el consumo energético por metro cuadrado de nuestro instituto 
y cómo se compara con centros similares?
```

---

## 🔍 PARTE 2: Análisis del Modelo de Datos (25 minutos)

### Objetivo
Identificar **qué información sostenible** puedes extraer de tus tablas y campos.

### Tareas

**2.1. Inventario de tablas y campos relevantes**

Crea una tabla que liste **solo las entidades y atributos relevantes para indicadores ASG**:

```markdown
## 2. ANÁLISIS DEL MODELO DE DATOS

### 2.1. Inventario de datos disponibles

| Tabla | Campos clave | Tipo de dato | Dimensión ASG |
|-------|--------------|--------------|---------------|
| [Nombre tabla 1] | [campo1, campo2, campo3] | [numérico/fecha/texto] | [A/S/G] |
| [Nombre tabla 2] | [campo1, campo2] | [numérico/fecha] | [A/S/G] |
| ... | ... | ... | ... |
```

**Ejemplo cumplimentado:**

```markdown
### 2.1. Inventario de datos disponibles

| Tabla | Campos clave | Tipo de dato | Dimensión ASG |
|-------|--------------|--------------|---------------|
| Edificios | m2_totales, año_construccion | numérico | A (Ambiental) |
| Aulas | nombre, m2, capacidad_personas, edificio_id | numérico | A |
| Mediciones_Energia | consumo_kwh, tipo_energia, fecha, hora | numérico, fecha | A |
| Ocupacion | num_ocupantes, hora_inicio, hora_fin | numérico | A |
| Sensores | ubicacion, modelo, estado_activo | texto, booleano | G (Gobernanza) |
```

**2.2. Mapa conceptual: Datos → Indicadores potenciales**

Identifica **qué puedes calcular** con esos datos. No hace falta fórmulas complejas todavía, solo ideas:

```markdown
### 2.2. Qué puedo calcular con mis datos

**Indicadores absolutos (básicos):**
- [ ] [Ejemplo: Consumo total mensual de energía]
- [ ] [Ejemplo: Número total de mediciones realizadas]
- [ ] ...

**Indicadores relativos (eficiencia):**
- [ ] [Ejemplo: Consumo energético por m²]
- [ ] [Ejemplo: Consumo por persona]
- [ ] ...

**Indicadores de tendencia:**
- [ ] [Ejemplo: Variación mensual de consumo]
- [ ] [Ejemplo: Comparación entre edificios]
- [ ] ...

**Indicadores de impacto:**
- [ ] [Ejemplo: Huella de carbono estimada]
- [ ] ...
```

**2.3. Identificación de datos faltantes**

¿Qué indicadores te gustaría calcular pero **no tienes datos suficientes**?

```markdown
### 2.3. Datos faltantes identificados

| Indicador deseado | Datos que me faltan | Posible solución |
|-------------------|---------------------|------------------|
| [Ej: % energía renovable] | [Origen de la energía] | [Consultar factura eléctrica] |
| [Ej: Confort térmico] | [Temperatura interior] | [Instalar sensores de temperatura] |
| ... | ... | ... |
```

---

## 📊 PARTE 3: Batería de Indicadores (45 minutos) ⭐

### Objetivo
Diseñar **5-8 indicadores ASG completos y priorizados** que darán sentido a tu proyecto.

### Tareas

**3.1. Selección de indicadores**

Elige **entre 5 y 8 indicadores** que cumplan:
- ✅ Puedes calcularlos con tus datos actuales (o con datos fácilmente obtenibles)
- ✅ Están relacionados con al menos un ODS
- ✅ Son relevantes para tomar decisiones en el instituto
- ✅ Cubren diferentes tipos: al menos 1 absoluto, 2-3 relativos, 1 de tendencia

**Distribución recomendada:**
```
📊 Tu batería de indicadores debe incluir:
   • 1-2 indicadores absolutos (para contexto)
   • 3-4 indicadores relativos/eficiencia (núcleo del análisis)
   • 1-2 indicadores de tendencia (evolución temporal)
   • (Opcional) 1 indicador compuesto/índice
```

**3.2. Fichas técnicas de indicadores**

Para **cada uno** de tus 5-8 indicadores, completa esta ficha:

---

### 📊 **INDICADOR [número]: [Nombre descriptivo]**

#### **Información básica**

| Campo | Contenido |
|-------|-----------|
| **Nombre del indicador** | [Nombre corto y descriptivo] |
| **Tipo** | [Absoluto / Relativo / Eficiencia / Impacto / Tendencia / Compuesto] |
| **Dimensión ASG** | [🌍 Ambiental / 👥 Social / ⚖️ Gobernanza] |
| **ODS relacionados** | ODS X - [Nombre completo] |
| **Prioridad** | [🔴 Alta / 🟡 Media / 🟢 Baja] |

#### **Definición y propósito**

**¿Qué mide este indicador?**  
[Explica en 2-3 líneas qué informa este indicador y por qué es importante]

**¿Por qué es relevante para el proyecto?**  
[Conexión con los objetivos de sostenibilidad del centro]

#### **Cálculo**

**Fórmula:**
```
[Escribe la fórmula matemática o descripción del cálculo]
Ejemplo: 
  Consumo_por_m2 = SUM(consumo_kwh) / SUM(m2_edificios)
```

**Datos necesarios:**
- **Tabla:** [Nombre_Tabla_1]
  - Campo: `[campo_1]` → [descripción]
  - Campo: `[campo_2]` → [descripción]
- **Tabla:** [Nombre_Tabla_2]
  - Campo: `[campo_3]` → [descripción]

**Unidad de medida:**  
[kWh, %, kg, litros, personas, etc.]

**Frecuencia de cálculo:**  
[Diaria / Semanal / Mensual / Anual]

#### **Consulta conceptual (pseudocódigo)**

```sql
-- Descripción en lenguaje natural de la consulta SQL futura
-- No tiene que ser sintaxis perfecta, pero debe mostrar la lógica

EJEMPLO:
  SELECCIONAR la suma de consumo_kwh de la tabla Mediciones_Energia
  DIVIDIR entre la suma de m2 de la tabla Edificios
  AGRUPAR por mes (del campo fecha)
  ORDENAR por mes
```

#### **Interpretación**

**¿Qué significa el valor obtenido?**
- **Valor alto** (> [umbral]): [interpretación y qué hacer]
- **Valor medio** ([rango]): [interpretación]
- **Valor bajo** (< [umbral]): [interpretación y qué hacer]

**Meta u objetivo:**
- **Valor actual (estimado):** [si lo sabéis, poner una estimación]
- **Valor objetivo:** [meta cuantificada a alcanzar]
- **Plazo:** [fecha o periodo]

**Benchmark de referencia:**
- **Media del sector:** [valor] - Fuente: [origen]
- **Mejor práctica:** [valor] - Fuente: [ejemplo real o estándar]

#### **Visualización sugerida**

**Tipo de gráfico recomendado:**  
[Gráfico de línea / barras / gauge / semáforo / tarjeta con número / mapa de calor]

**Justificación:**  
[Por qué este tipo de visualización es el más adecuado]

**Ejemplo de visualización (boceto):**
```
[Aquí podéis hacer un dibujo simple, captura o descripción]
Ejemplo:
  📊 Gráfico de barras con consumo kWh/m² por edificio
     Edificio A: ████████░░ 8.2 kWh/m²
     Edificio B: ███████░░░ 7.1 kWh/m²
     Edificio C: ██████████ 9.8 kWh/m²
     MEDIA:      ████████░░ 8.4 kWh/m²
```

#### **Limitaciones y advertencias**

**¿Qué problemas pueden afectar la calidad de este indicador?**
- [ ] [Ejemplo: Datos incompletos en horario nocturno]
- [ ] [Ejemplo: Falta de datos de temperatura exterior para contextualizar]
- [ ] ...

**¿Qué precauciones hay que tener al interpretarlo?**
[Ejemplo: El consumo varía mucho en invierno por calefacción, hay que comparar meses equivalentes]

---

**Repite esta ficha para cada uno de tus 5-8 indicadores seleccionados.**

---

### 📌 Ejemplo de indicador completo

Para que veas cómo quedaría una ficha bien cumplimentada:

---

### 📊 **INDICADOR 1: Intensidad energética del centro**

#### **Información básica**

| Campo | Contenido |
|-------|-----------|
| **Nombre del indicador** | Consumo energético por metro cuadrado |
| **Tipo** | Relativo / Eficiencia |
| **Dimensión ASG** | 🌍 Ambiental |
| **ODS relacionados** | ODS 7 - Energía asequible y no contaminante |
| **Prioridad** | 🔴 Alta |

#### **Definición y propósito**

**¿Qué mide este indicador?**  
Mide la cantidad de energía eléctrica consumida por cada metro cuadrado de superficie construida del centro. Es un indicador estándar de eficiencia energética en edificios.

**¿Por qué es relevante para el proyecto?**  
Permite comparar la eficiencia energética del instituto con otros centros educativos similares y con estándares del sector. Ayuda a identificar si estamos consumiendo más energía de la necesaria y dónde enfocar mejoras.

#### **Cálculo**

**Fórmula:**
```
Intensidad_Energetica = SUM(consumo_kwh) / SUM(m2_edificios)

Para un periodo mensual:
  Intensidad_Energetica_mensual = SUM(consumo_kwh WHERE mes=X) / SUM(m2)
```

**Datos necesarios:**
- **Tabla:** Mediciones_Energia
  - Campo: `consumo_kwh` → Consumo registrado por los contadores
  - Campo: `fecha` → Para filtrar por periodo (mes/año)
- **Tabla:** Edificios
  - Campo: `m2_totales` → Superficie construida de cada edificio

**Unidad de medida:**  
kWh/m²/mes (kilovatios-hora por metro cuadrado al mes)

**Frecuencia de cálculo:**  
Mensual (con cierre al último día del mes)

#### **Consulta conceptual (pseudocódigo)**

```sql
-- Cálculo de intensidad energética mensual por edificio

SELECCIONAR 
  nombre_edificio,
  mes_año,
  SUMA(consumo_kwh) como consumo_total,
  m2_totales,
  SUMA(consumo_kwh) / m2_totales como intensidad_energetica

DE 
  tabla Mediciones_Energia 
  UNIDA CON tabla Aulas (por aula_id)
  UNIDA CON tabla Edificios (por edificio_id)

AGRUPAR POR 
  nombre_edificio, 
  mes_año

ORDENAR POR 
  mes_año, 
  intensidad_energetica (de mayor a menor)
```

#### **Interpretación**

**¿Qué significa el valor obtenido?**
- **Valor alto** (> 10 kWh/m²/mes): Consumo ineficiente. Posibles causas: equipos obsoletos, mala climatización, pérdidas térmicas. **Acción:** Auditoría energética urgente.
- **Valor medio** (6-10 kWh/m²/mes): Consumo dentro de rango habitual para centros educativos. **Acción:** Identificar áreas de mejora incremental.
- **Valor bajo** (< 6 kWh/m²/mes): Consumo muy eficiente. **Acción:** Mantener buenas prácticas y compartir como ejemplo.

**Meta u objetivo:**
- **Valor actual (estimado):** 8.5 kWh/m²/mes (basado en facturas eléctricas)
- **Valor objetivo:** 7.0 kWh/m²/mes (reducción del 18%)
- **Plazo:** Final del curso 2025-2026

**Benchmark de referencia:**
- **Media del sector:** 8.5 kWh/m²/mes - Fuente: IDAE (Instituto para la Diversificación y Ahorro de la Energía)
- **Mejor práctica:** 5.2 kWh/m²/mes - Fuente: IES Ítaca (Barcelona), certificado Passivhaus

#### **Visualización sugerida**

**Tipo de gráfico recomendado:**  
Gráfico de barras horizontales con línea de referencia (benchmark)

**Justificación:**  
Las barras permiten comparar fácilmente entre edificios o entre meses. La línea de referencia muestra la meta u objetivo de forma visual.

**Ejemplo de visualización (boceto):**
```
📊 Intensidad Energética por Edificio (kWh/m²/mes - Diciembre 2025)

Edificio A    ████████████░░ 9.2   [Por encima de objetivo]
Edificio B    ███████░░░░░░░ 6.8   [Dentro de objetivo ✓]
Edificio C    ██████████████ 10.5  [Muy por encima]
────────────────────────────────────────────────
MEDIA Centro  ████████████░░ 8.8
OBJETIVO      ███████░░░░░░░ 7.0   ← Meta
SECTOR        ████████████░░ 8.5   ← Benchmark
```

#### **Limitaciones y advertencias**

**¿Qué problemas pueden afectar la calidad de este indicador?**
- [x] Variación estacional: El consumo es mayor en invierno (calefacción) y verano (refrigeración). Hay que comparar siempre meses equivalentes.
- [x] Mediciones parciales: Si faltan lecturas de algún contador, el cálculo será incompleto.
- [x] Superficie no considerada: No diferenciamos entre m² climatizados y no climatizados (almacenes, pasillos).

**¿Qué precauciones hay que tener al interpretarlo?**
Al comparar con benchmarks externos, hay que tener en cuenta el clima de la zona (grados-día de calefacción/refrigeración), la antigüedad del edificio y la intensidad de uso (horas lectivas). Un valor alto no siempre indica mala gestión; puede deberse a un edificio muy antiguo sin aislamiento.

---

**[FIN DEL EJEMPLO - Ahora crea tus propios 5-8 indicadores siguiendo esta estructura]**

---

## 🎯 PARTE 4: Priorización y Justificación (15 minutos)

### Objetivo
Explicar **por qué has elegido esos indicadores** y **en qué orden** los implementarás.

### Tareas

**4.1. Matriz de priorización**

Evalúa cada indicador según **factibilidad** (datos disponibles + complejidad) e **impacto ASG**:

```markdown
## 4. PRIORIZACIÓN Y JUSTIFICACIÓN

### 4.1. Matriz de priorización

| Indicador | Factibilidad (1-5) | Impacto ASG (1-5) | Puntuación total | Cuadrante |
|-----------|--------------------|-------------------|------------------|-----------|
| [Indicador 1] | 5 | 5 | 10 | 🟩 Quick Win |
| [Indicador 2] | 4 | 5 | 9 | 🟩 Quick Win |
| [Indicador 3] | 3 | 5 | 8 | 🟨 Proyecto Mayor |
| [Indicador 4] | 5 | 3 | 8 | 🟦 Posterior |
| [Indicador 5] | 2 | 4 | 6 | 🟨 Proyecto Mayor |
| ... | ... | ... | ... | ... |

**Escala:**
- Factibilidad: 5=Datos completos y cálculo simple, 1=Requiere datos externos y cálculo complejo
- Impacto ASG: 5=Muy relevante para decisiones clave, 1=Interesante pero secundario

**Cuadrantes:**
- 🟩 Quick Win (factibilidad ≥4, impacto ≥4): Implementar primero
- 🟨 Proyecto Mayor (impacto ≥4, factibilidad <4): Planificar cómo obtener datos
- 🟦 Posterior (factibilidad ≥4, impacto <4): Implementar si queda tiempo
- 🟥 Descartar (factibilidad <4, impacto <4): No priorizar
```

**4.2. Justificación de la selección**

```markdown
### 4.2. Justificación de la batería elegida

**¿Por qué estos indicadores y no otros?**

[Explica en un párrafo los criterios que habéis seguido para seleccionar esta batería concreta. Ejemplos de criterios: disponibilidad de datos, alineación con ODS prioritarios, demanda de la dirección del centro, viabilidad técnica, etc.]

**¿Qué indicadores hemos descartado y por qué?**

- **[Nombre indicador descartado 1]:** [Razón: no tenemos datos, demasiado complejo, etc.]
- **[Nombre indicador descartado 2]:** [Razón]
- ...

**¿Cómo se complementan entre sí los indicadores elegidos?**

[Explica cómo tu batería ofrece una visión completa del problema. Por ejemplo: un indicador absoluto da contexto, varios relativos permiten comparar, y uno de tendencia muestra evolución]
```

---

## 💻 PARTE 5: Consultas Conceptuales (20 minutos)

### Objetivo
Preparar la **lógica de las consultas SQL** que implementarás en el futuro (cuando domines SQL).

### Tareas

**5.1. Pseudocódigo de consultas**

Para **los 3 indicadores prioritarios** (los de la matriz con mayor puntuación), escribe la consulta en **pseudocódigo detallado**:

```markdown
## 5. CONSULTAS CONCEPTUALES

### 5.1. Consulta para Indicador [Nombre Indicador 1]

**Objetivo de la consulta:**  
[Qué información debe devolver]

**Pseudocódigo:**
```
PASO 1: Obtener datos de consumo
  - De la tabla [Tabla1]
  - Seleccionar campos: [campo1, campo2, campo3]
  - Filtrar por: [condiciones, ej: fecha entre X e Y]

PASO 2: Obtener datos de contexto
  - De la tabla [Tabla2]
  - Seleccionar campos: [campo4, campo5]

PASO 3: Unir las tablas
  - Relacionar Tabla1 con Tabla2 mediante [clave_foranea]

PASO 4: Calcular agregaciones
  - Sumar [campo_numerico]
  - Agrupar por [campo_categoria]

PASO 5: Calcular indicador final
  - Dividir [resultado1] entre [resultado2]

PASO 6: Ordenar y presentar
  - Ordenar por [criterio]
  - Mostrar solo [top X resultados o todos]
```

**Resultado esperado (ejemplo):**
```
| edificio | mes | consumo_total | m2 | intensidad_energetica |
|----------|-----|---------------|----|-----------------------|
| A | 2025-01 | 12450 | 1500 | 8.3 |
| B | 2025-01 | 9800 | 1200 | 8.2 |
| ...
```

---

**[Repetir para los otros 2 indicadores prioritarios]**

---

## 📅 PARTE 6: Plan de Implementación (10 minutos)

### Objetivo
Establecer **cuándo y cómo** calcularéis estos indicadores en las próximas sesiones.

### Tareas

**6.1. Cronograma de implementación**

```markdown
## 6. PLAN DE IMPLEMENTACIÓN

### 6.1. Cronograma

| Fase | Indicadores a implementar | Sesión prevista | Estado |
|------|---------------------------|-----------------|--------|
| **Fase 1** (próximas 2 semanas) | [Indicador 1, Indicador 2] | Sesión 10-11 | ⏳ Pendiente |
| **Fase 2** (semanas 3-4) | [Indicador 3, Indicador 4] | Sesión 12-13 | ⏳ Pendiente |
| **Fase 3** (semanas 5-6) | [Indicador 5, Indicador 6] | Sesión 14-15 | ⏳ Pendiente |
| **Revisión y ajuste** | Todos los indicadores | Sesión 16 | ⏳ Pendiente |
```

**6.2. Necesidades identificadas**

```markdown
### 6.2. ¿Qué necesitamos para implementar estos indicadores?

**Datos adicionales a recopilar:**
- [ ] [Ejemplo: Obtener facturas eléctricas del último año]
- [ ] [Ejemplo: Solicitar planos del edificio para confirmar m²]
- [ ] ...

**Conocimientos técnicos a adquirir:**
- [ ] [Ejemplo: Consultas SQL con JOIN entre múltiples tablas]
- [ ] [Ejemplo: Funciones de agregación GROUP BY]
- [ ] [Ejemplo: Cálculo de porcentajes en SQL]
- [ ] ...

**Herramientas a utilizar:**
- [ ] [Ejemplo: PostgreSQL para ejecutar consultas]
- [ ] [Ejemplo: Excel/Python para validar cálculos]
- [ ] [Ejemplo: Power BI para visualizaciones]
- [ ] ...

**Validaciones externas:**
- [ ] [Ejemplo: Contrastar cálculos con facturas reales]
- [ ] [Ejemplo: Consultar con responsable de mantenimiento del centro]
- [ ] ...
```

---

## ✅ Checklist de autoevaluación

Antes de entregar, verifica que tu documento cumple:

### Contenido completo
- [ ] He incluido el contexto del proyecto con ODS y alcance
- [ ] He analizado mi modelo de datos e identificado tablas/campos relevantes
- [ ] He diseñado entre 5 y 8 indicadores (ni menos ni más)
- [ ] Cada indicador tiene su ficha técnica completa
- [ ] He priorizado los indicadores con la matriz factibilidad/impacto
- [ ] He escrito pseudocódigo para los 3 indicadores prioritarios
- [ ] He planificado el cronograma de implementación

### Calidad técnica
- [ ] Todos los indicadores son **medibles** con mis datos actuales (o con datos fácilmente obtenibles)
- [ ] Al menos 2-3 indicadores son **relativos/de eficiencia** (no solo absolutos)
- [ ] Todos los indicadores están relacionados con **al menos 1 ODS**
- [ ] Las fórmulas de cálculo son claras y replicables
- [ ] He identificado **limitaciones** de cada indicador

### Relevancia sostenibilidad
- [ ] Los indicadores cubren **al menos 1 dimensión ASG** (idealmente varias)
- [ ] Cada indicador tiene **meta u objetivo cuantificado**
- [ ] He incluido **benchmarks o referencias** cuando existen
- [ ] Los indicadores orientan **decisiones concretas** del centro

### Presentación
- [ ] Documento bien estructurado y legible
- [ ] Tablas y listas con formato correcto
- [ ] Pseudocódigo con comentarios explicativos
- [ ] Sin faltas de ortografía ni errores de formato

---

## 📊 Rúbrica de evaluación

| Criterio | Excelente (9-10) | Notable (7-8) | Aprobado (5-6) | Insuficiente (<5) | Peso |
|----------|-----------------|---------------|----------------|-------------------|------|
| **Análisis del modelo de datos** | Inventario completo, identifica datos relevantes y faltantes | Inventario completo, identifica algunos faltantes | Inventario básico, no identifica faltantes | Inventario incompleto o ausente | 15% |
| **Calidad de indicadores** | 5-8 indicadores SMART, bien justificados, diversos | 5-8 indicadores, mayoría SMART, algo repetitivos | 4-5 indicadores, no todos cumplen criterios SMART | <4 indicadores o no cumplen criterios | 35% |
| **Fichas técnicas** | Todas completas, fórmulas claras, benchmarks incluidos | Mayoría completas, fórmulas claras | Fichas básicas, falta información | Fichas incompletas o ausentes | 25% |
| **Consultas conceptuales** | Pseudocódigo claro, detallado y viable | Pseudocódigo comprensible | Pseudocódigo básico o poco detallado | Ausente o incomprensible | 15% |
| **Relevancia ASG/ODS** | Fuerte conexión con ODS, metas cuantificadas | Buena conexión con ODS | Conexión débil con ODS | Sin conexión clara con ODS | 10% |

**Puntuación total: 100 puntos**

### Instrumentos de evaluación:
- ✅ Rúbrica analítica (esta tabla)
- ✅ Checklist de completitud
- ✅ Revisión por pares (opcional): Intercambio de documentos entre equipos para feedback

---

## 💡 Consejos y recomendaciones

### Para elegir buenos indicadores:
1. **Empieza por lo simple**: Un indicador sencillo pero útil es mejor que uno complejo que nadie entiende.
2. **Piensa en el destinatario**: ¿Lo entenderá la dirección del centro? ¿El equipo de mantenimiento? ¿Los estudiantes?
3. **Conecta con problemas reales**: ¿Hay quejas sobre el frío/calor? → Indicador de confort térmico. ¿Preocupa el coste energético? → Intensidad energética.
4. **No te obsesiones con la perfección**: Es mejor tener indicadores "buenos" implementados que indicadores "perfectos" en papel.

### Para escribir pseudocódigo:
1. **Usa lenguaje natural**: No intentes escribir SQL perfecto todavía.
2. **Divide en pasos**: Es más fácil de entender y luego traducir a SQL.
3. **Comenta todo**: Explica cada paso, asume que lo leerá alguien que no conoce tu proyecto.
4. **Usa nombres reales**: Escribe los nombres exactos de tus tablas y campos.

### Para priorizar:
1. **Quick Wins primero**: Los indicadores fáciles de calcular y de alto impacto te dan resultados rápidos.
2. **No descartes lo complejo**: Los "Proyectos Mayores" pueden ser tus mejores indicadores; planifica cómo obtener los datos necesarios.
3. **Equilibrio**: No elijas solo indicadores de eficiencia; incluye al menos uno de tendencia para ver evolución.

### Errores comunes a evitar:
- ❌ **Indicadores imposibles**: "Huella hídrica global del centro" → Requiere datos de agua virtual que no tendrás.
- ❌ **Vanity metrics**: "Número total de registros en la BD" → No aporta valor para sostenibilidad.
- ❌ **Fórmulas sin contexto**: "Indicador 1 = A/B" → Explica qué son A y B y por qué los divides.
- ❌ **Sin meta**: "Consumimos 8.5 kWh/m²" → ¿Es bueno o malo? Sin objetivo o benchmark, no es accionable.

---

## 🎓 Resultados de Aprendizaje trabajados

Esta actividad evalúa:

### **Sostenibilidad aplicada al sistema productivo**

| RA | Criterio de evaluación | Evidencia en esta actividad |
|:---|:-----------------------|:----------------------------|
| **SOST-RA1** | CE1.1: Identifica indicadores ambientales | Selección y diseño de indicadores dimensión A |
| **SOST-RA1** | CE1.2: Selecciona métricas sociales | Selección y diseño de indicadores dimensión S |
| **SOST-RA1** | CE1.3: Evalúa aspectos de gobernanza | Selección y diseño de indicadores dimensión G |
| **SOST-RA2** | CE2.2: Compara con estándares del sector | Inclusión de benchmarks y referencias |

### **Digitalización aplicada al sistema productivo**

| RA | Criterio de evaluación | Evidencia en esta actividad |
|:---|:-----------------------|:----------------------------|
| **DIG-RA3** | CE3.1: Diseña modelos relacionales correctos | Conexión del modelo ER con indicadores |
| **DIG-RA3** | CE3.2: Realiza consultas SQL complejas | Pseudocódigo de consultas (preparación) |

---

## 📅 Fecha de entrega y formato

**Fecha límite:** [A definir por el profesor - sugerencia: 1 semana desde la sesión]

**Formato de entrega:**
- **Archivo:** `Equipo-XX_Sesion9_Bateria_Indicadores_ASG.md` o `.pdf`
- **Tamaño:** No hay límite, pero se estima entre 10-20 páginas
- **Plataforma:** [Moodle / Google Classroom / según indique el profesor]

**Miembros del equipo:**
- Incluir nombre completo de todos los miembros al inicio del documento
- Indicar el rol de cada miembro en la actividad (si se han repartido tareas)

---

## 🌟 Ejemplo de buena práctica

Si quieres ver un ejemplo de cómo podría quedar un documento completo (con 3 indicadores en lugar de 5-8 por motivos de espacio), consulta el **Anexo: Ejemplo de batería de indicadores** al final de este enunciado.

---

## ❓ FAQs - Preguntas frecuentes

**P: ¿Puedo cambiar indicadores después de entregar esta actividad?**  
R: Sí, esta batería es un punto de partida. Cuando empieces a implementar, puede que descubras problemas con los datos o encuentres indicadores mejores. La iteración es parte del proceso.

**P: ¿Qué hago si mis datos no permiten calcular ningún indicador relevante?**  
R: Es poco probable. Incluso con datos básicos (fechas + valores numéricos) puedes calcular tendencias, promedios, totales. Si realmente falta algo crítico, identifícalo en la sección "datos faltantes" y propón cómo obtenerlo.

**P: ¿Puedo usar indicadores de otros equipos si trabajamos temas similares?**  
R: Los indicadores pueden repetirse (ej: todos los grupos de energía calcularán kWh/m²), pero la ficha técnica debe adaptarse a **tu modelo de datos específico**. No copies literalmente.

**P: ¿Necesito programar o ejecutar SQL en esta actividad?**  
R: No. Esta actividad es de diseño conceptual. El SQL lo implementarás en sesiones futuras.

**P: ¿Cuánto detalle se espera en el pseudocódigo?**  
R: Suficiente para que otra persona (o tú dentro de 2 semanas) pueda implementarlo en SQL. Ejemplo: "Sumar consumo de tabla X agrupado por mes" es aceptable; solo "calcular consumo" es insuficiente.

**P: ¿Puedo incluir más de 8 indicadores?**  
R: Puedes mencionar indicadores adicionales en una sección "Indicadores futuros", pero solo desarrolla fichas completas para 5-8. Más de eso es inmanejable para el alcance del curso.

---

## 📚 Recursos de apoyo

### Documentos de consulta:
- **Apuntes Sesión 9**: Del Dato al Impacto - Interpretación de Indicadores ASG
- **Apuntes Sesión 1**: ODS y criterios ASG
- **Apuntes Sesión 4**: Modelado de datos (para repasar tu ER)

### Fuentes de benchmarks:
- **IDAE** (eficiencia energética): https://www.idae.es
- **MITECO** (datos ambientales España): https://www.miteco.gob.es
- **INE** (datos sociales y demográficos): https://www.ine.es
- **Indicadores ODS oficiales**: https://unstats.un.org/sdgs/indicators/indicators-list/

### Herramientas útiles:
- **Calculadora de emisiones CO₂**: https://www.miteco.gob.es (apartado "Calculadoras")
- **Conversor de unidades**: https://www.unitconverters.net/

---

## 🎤 Preparación para la puesta en común

En la próxima sesión (Sesión 10), cada equipo hará una **presentación de 5 minutos** de su batería de indicadores:

**Qué preparar:**
1. **2-3 diapositivas** (o 1 página visual si no usáis PPT)
2. **Contenido:**
   - Slide 1: Contexto y ODS trabajados
   - Slide 2: Los 3 indicadores prioritarios (quick wins) con sus fórmulas
   - Slide 3: Cómo los usaréis para mejorar la sostenibilidad del centro

**Objetivo de la puesta en común:**
- Recibir feedback de otros equipos y el profesor
- Identificar sinergias (equipos trabajando temas similares)
- Aprender de enfoques diferentes

**No es una defensa formal**, es un espacio de aprendizaje colectivo.

---

## 🏆 Criterios de excelencia

Si quieres aspirar a la máxima nota, tu batería debería:

✨ **Ser diversa**: Combinar indicadores absolutos, relativos y de tendencia  
✨ **Ser completa**: Cubrir las 3 dimensiones ASG (aunque con diferente peso según tu proyecto)  
✨ **Ser viable**: Todos los indicadores calculables con datos disponibles o fácilmente obtenibles  
✨ **Ser relevante**: Cada indicador relacionado con ODS y con meta cuantificada  
✨ **Ser clara**: Fichas completas, pseudocódigo comprensible, limitaciones identificadas  
✨ **Ser útil**: Los indicadores orientan decisiones reales del centro

---

**¡Manos a la obra!** 🚀  
Esta batería de indicadores será la **hoja de ruta** para las próximas semanas del proyecto. Cuanto mejor la diseñes ahora, más fácil será implementarla después.

---

**Actividad elaborada para:**  
1º DAW - Digitalización + Sostenibilidad aplicadas al sistema productivo  
IES [Nombre del Centro] - Curso 2025/2026  

**Tiempo estimado:** 2 horas (sesión presencial) + trabajo autónomo si es necesario  
**Última actualización:** Enero 2026
