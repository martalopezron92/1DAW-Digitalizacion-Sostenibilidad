# 📘 Sesión 5 – Del Dato al Impacto: Interpretación de Indicadores ASG

---

## 📚 Índice

1. [Repaso: Criterios ASG en contexto educativo](#1-repaso-criterios-asg-en-contexto-educativo)
2. [De datos a información: El camino hacia los indicadores](#2-de-datos-a-información-el-camino-hacia-los-indicadores)
3. [Tipos de indicadores de sostenibilidad](#3-tipos-de-indicadores-de-sostenibilidad)
4. [Diseño de indicadores desde el modelo de datos](#4-diseño-de-indicadores-desde-el-modelo-de-datos)
5. [ODS y métricas aplicadas: Casos reales](#5-ods-y-métricas-aplicadas-casos-reales)
6. [Criterios para seleccionar buenos indicadores](#6-criterios-para-seleccionar-buenos-indicadores)

---

## 1. Repaso: Criterios ASG en contexto educativo

### 1.1 ¿Qué son los criterios ASG?

Los criterios **ASG (Ambientales, Sociales y de Gobernanza)** o **ESG** en inglés (Environmental, Social, Governance) son un marco de evaluación que mide el impacto de una organización más allá de sus resultados económicos.

```
┌─────────────────────────────────────────────────┐
│         CRITERIOS ASG (ESG)                     │
├─────────────────────────────────────────────────┤
│  🌍 A - AMBIENTALES (Environmental)             │
│     • Cambio climático y emisiones CO₂          │
│     • Consumo de energía y eficiencia           │
│     • Gestión de residuos y economía circular   │
│     • Consumo de agua                           │
│     • Biodiversidad y uso del suelo             │
│                                                  │
│  👥 S - SOCIALES (Social)                       │
│     • Igualdad y diversidad                     │
│     • Salud y bienestar                         │
│     • Condiciones laborales/estudiantiles       │
│     • Participación comunitaria                 │
│     • Accesibilidad e inclusión                 │
│                                                  │
│  ⚖️ G - GOBERNANZA (Governance)                 │
│     • Transparencia y rendición de cuentas      │
│     • Ética y cumplimiento normativo            │
│     • Gestión de datos y privacidad             │
│     • Participación de grupos de interés        │
│     • Políticas y estrategias documentadas      │
└─────────────────────────────────────────────────┘
```

### 1.2 ASG aplicado a centros educativos

En un **instituto o centro de formación**, los criterios ASG se traducen en aspectos concretos y medibles:

#### 🌍 **Dimensión AMBIENTAL**

| Aspecto | Ejemplos de datos medibles | Relación con ODS |
|---------|----------------------------|------------------|
| **Energía** | kWh consumidos, origen renovable, horarios de uso | ODS 7 (Energía asequible y no contaminante) |
| **Residuos** | kg generados, % reciclado, reducción de plásticos | ODS 12 (Producción y consumo responsables) |
| **Agua** | m³ consumidos, detección de fugas, reutilización | ODS 6 (Agua limpia y saneamiento) |
| **Movilidad** | Medios de transporte, km recorridos, huella de carbono | ODS 11 (Ciudades y comunidades sostenibles) |
| **Infraestructura** | m² construidos, eficiencia térmica, materiales sostenibles | ODS 9 (Industria, innovación e infraestructura) |

#### 👥 **Dimensión SOCIAL**

| Aspecto | Ejemplos de datos medibles | Relación con ODS |
|---------|----------------------------|------------------|
| **Igualdad de género** | % mujeres/hombres en ciclos STEM, brecha salarial docente | ODS 5 (Igualdad de género) |
| **Inclusión** | Estudiantes con necesidades especiales, recursos de apoyo | ODS 10 (Reducción de desigualdades) |
| **Bienestar** | Encuestas de satisfacción, índice de estrés, absentismo | ODS 3 (Salud y bienestar) |
| **Calidad educativa** | Tasa de aprobados, abandono, inserción laboral | ODS 4 (Educación de calidad) |
| **Participación** | Asistencia a actividades, implicación en proyectos | ODS 16 (Paz, justicia e instituciones) |

#### ⚖️ **Dimensión GOBERNANZA**

| Aspecto | Ejemplos de datos medibles | Relación con ODS |
|---------|----------------------------|------------------|
| **Transparencia** | Publicación de memorias, acceso a información | ODS 16 (Paz, justicia e instituciones) |
| **Privacidad** | Incidentes de seguridad, cumplimiento RGPD | Transversal |
| **Participación** | Consejos escolares, encuestas, canales de comunicación | ODS 17 (Alianzas para lograr objetivos) |
| **Ética digital** | Uso responsable de TIC, políticas de uso aceptable | ODS 9 (Industria, innovación e infraestructura) |

### 1.3 ¿Por qué medir criterios ASG en educación?

1. **Tomar decisiones basadas en evidencias**: Los datos permiten identificar problemas reales y priorizar acciones.
2. **Rendir cuentas**: Demostrar a la comunidad educativa el compromiso con la sostenibilidad.
3. **Mejorar continuamente**: Establecer metas, medir progreso y ajustar estrategias.
4. **Formar ciudadanía responsable**: Los estudiantes aprenden con el ejemplo.
5. **Cumplir normativas**: Cada vez más legislación exige reportes de sostenibilidad.

> 💡 **Ejemplo real**: El IES XXX redujo un 30% su consumo eléctrico tras medir y visualizar datos de consumo por aula y horario, identificando derroches en iluminación nocturna.

---

## 2. De datos a información: El camino hacia los indicadores

### 2.1 La pirámide de la información

```
           🎯 DECISIÓN
              ↑
        💡 CONOCIMIENTO
              ↑
        📊 INFORMACIÓN
              ↑
        📝 DATOS
              ↑
        🔢 DATOS BRUTOS
```

| Nivel | Descripción | Ejemplo |
|-------|-------------|---------|
| **Datos brutos** | Observaciones sin procesar | `[125.3, 142.7, 98.5, ...]` |
| **Datos** | Organizados y clasificados | `consumo_kwh` en tabla `mediciones_energia` |
| **Información** | Datos procesados con contexto | "El edificio A consumió 12.450 kWh en enero" |
| **Conocimiento** | Información interpretada | "El consumo de enero es 15% superior a la media anual" |
| **Decisión** | Acción basada en conocimiento | "Instalar temporizadores en iluminación del edificio A" |

### 2.2 ¿Qué es un indicador?

Un **indicador** es una **métrica cuantificable** que permite:
- Medir el desempeño de una actividad
- Comparar situaciones en el tiempo o con referencias externas
- Evaluar el progreso hacia un objetivo

#### Características de un buen indicador:

| Característica | Descripción | Ejemplo |
|----------------|-------------|---------|
| **Relevante** | Relacionado con objetivos estratégicos | Consumo energético (relacionado con ODS 7) |
| **Medible** | Cuantificable con datos disponibles | kWh/mes (medido por contador) |
| **Comprensible** | Fácil de interpretar por no expertos | "kWh por metro cuadrado" es claro |
| **Comparable** | Permite benchmarking | kWh/m²/mes (estándar internacional) |
| **Accionable** | Orienta decisiones concretas | Si aumenta → revisar equipos |
| **Verificable** | Auditable y trazable | Datos de contador oficial |

### 2.3 Del modelo de datos a los indicadores

**Proceso de diseño:**

```
1. MODELO DE DATOS (ER)
   ↓ ¿Qué tablas y campos tengo?
   
2. DATOS DISPONIBLES
   ↓ ¿Qué información puedo extraer?
   
3. INDICADORES BÁSICOS (datos directos)
   ↓ Agregaciones, sumas, promedios
   
4. INDICADORES DERIVADOS (cálculos)
   ↓ Ratios, porcentajes, tendencias
   
5. INDICADORES COMPUESTOS (complejos)
   ↓ Índices, rankings, scoring
```

#### Ejemplo práctico:

**Modelo de datos:**
```
Tablas: [Aulas] [Mediciones_Energia] [Edificios]
Campos: id_aula, nombre, m2, edificio_id, consumo_kwh, fecha
```

**Indicadores que puedo calcular:**

| Tipo | Indicador | Cálculo | Complejidad |
|------|-----------|---------|-------------|
| Básico | Consumo total mensual | `SUM(consumo_kwh)` | Baja |
| Derivado | Consumo por m² | `SUM(consumo_kwh) / SUM(m2)` | Media |
| Derivado | Consumo por edificio | `SUM(consumo_kwh) GROUP BY edificio_id` | Media |
| Compuesto | Eficiencia energética | `(consumo_real / consumo_teórico) * 100` | Alta |
| Tendencia | Variación intermensual | `(mes_actual - mes_anterior) / mes_anterior * 100` | Alta |

---

## 3. Tipos de indicadores de sostenibilidad

### 3.1 Indicadores absolutos vs. relativos

#### **ABSOLUTOS**: Valores brutos sin normalización

**Ventajas:**
- Simples de calcular
- Útiles para seguimiento histórico del mismo lugar

**Desventajas:**
- Difícil comparación entre centros de diferente tamaño
- No reflejan eficiencia

**Ejemplos:**
- `12.450 kWh/mes` → ¿Es mucho o poco? Depende del tamaño del centro
- `850 kg de residuos/mes` → Sin contexto, no es interpretable
- `120 estudiantes` → Solo describe tamaño

#### **RELATIVOS**: Valores normalizados (ratios, porcentajes, per cápita)

**Ventajas:**
- Permiten comparaciones justas
- Reflejan eficiencia y rendimiento
- Estándares internacionales

**Desventajas:**
- Requieren más datos (denominadores)
- Cálculo más complejo

**Ejemplos:**
```
kWh/m²/mes          → Consumo por superficie (comparable con otros centros)
kg CO₂/estudiante   → Huella per cápita (normalizado por ocupación)
% residuos reciclados → Proporción sobre total (independiente del tamaño)
litros/persona/día  → Consumo de agua normalizado
```

### 3.2 Indicadores de eficiencia

Miden **qué tan bien se utilizan los recursos**.

**Fórmula general:**
```
Eficiencia = Salida útil / Entrada de recursos
```

**Ejemplos educativos:**

| Indicador | Fórmula | Interpretación |
|-----------|---------|----------------|
| **Eficiencia energética** | `m² climatizados / kWh consumidos` | Más alto = mejor |
| **Eficiencia de reciclaje** | `kg reciclados / kg totales × 100` | Objetivo: 100% |
| **Tasa de aprobados** | `Aprobados / Matriculados × 100` | Más alto = mejor |
| **Uso de espacios** | `Horas de ocupación / Horas disponibles × 100` | Óptimo: 70-85% |

### 3.3 Indicadores de impacto

Miden **consecuencias ambientales o sociales**.

**Ejemplos:**

| Indicador | Cálculo | Unidad | ODS relacionado |
|-----------|---------|--------|-----------------|
| **Huella de carbono** | `Emisiones directas + indirectas` | kg CO₂ equiv. | ODS 13 |
| **Huella hídrica** | `Consumo directo + agua virtual` | m³ | ODS 6 |
| **Residuos a vertedero** | `Residuos totales - Reciclados` | kg | ODS 12 |
| **Brecha de género** | `|% mujeres - % hombres|` | % | ODS 5 |

### 3.4 Indicadores de tendencia

Miden **cambios en el tiempo**.

**Fórmulas comunes:**

```python
# Variación absoluta
Cambio = Valor_final - Valor_inicial

# Variación relativa (%)
Variación_% = ((Valor_final - Valor_inicial) / Valor_inicial) × 100

# Tasa de crecimiento anual compuesta (TCAC)
TCAC = ((Valor_final / Valor_inicial)^(1/años)) - 1
```

**Ejemplos:**

| Indicador | Interpretación |
|-----------|----------------|
| **Reducción de consumo año a año** | Meta: -5% anual |
| **Incremento de % reciclaje** | Mejora sostenida |
| **Evolución de satisfacción** | Tendencia alcista o bajista |

### 3.5 Indicadores compuestos (índices)

Combinan **varios indicadores simples** en una única métrica.

**Ejemplo: Índice de Sostenibilidad del Centro (ISC)**

```
ISC = (0.4 × Eficiencia_Energética) + 
      (0.3 × Tasa_Reciclaje) + 
      (0.2 × Uso_Transporte_Sostenible) +
      (0.1 × Satisfacción_Comunidad)

Escala: 0-100
- 0-40: Bajo
- 41-70: Medio
- 71-100: Alto
```

**Ventajas:** Visión holística, útil para ranking
**Desventajas:** Puede ocultar problemas específicos

---

## 4. Diseño de indicadores desde el modelo de datos

### 4.1 Metodología de diseño

**Paso 1: Revisar el modelo ER**
- ¿Qué entidades tengo? (tablas)
- ¿Qué atributos tiene cada entidad? (campos)
- ¿Qué relaciones existen? (claves foráneas)

**Paso 2: Identificar datos clave**
- Campos numéricos → candidatos para agregaciones (SUM, AVG, COUNT)
- Campos de fecha → candidatos para series temporales
- Campos categóricos → candidatos para agrupaciones (GROUP BY)

**Paso 3: Mapear datos → ODS**
- ¿Qué ODS trabaja mi proyecto?
- ¿Qué indicadores están asociados a cada ODS?
- ¿Puedo calcular esos indicadores con mis datos?

**Paso 4: Definir denominadores**
- Para indicadores relativos, ¿tengo datos de contexto?
- Ejemplos: m², número de estudiantes, días lectivos

**Paso 5: Formular consultas conceptuales**
- Escribir en pseudocódigo o lenguaje natural
- No es necesario dominar SQL todavía

### 4.2 Ejemplo completo de diseño

**Contexto:** Un grupo está analizando el **consumo energético** del instituto.

#### **Su modelo de datos (simplificado):**

```
[Edificios]
- id_edificio (PK)
- nombre
- m2_totales
- año_construccion

[Aulas]
- id_aula (PK)
- nombre
- edificio_id (FK)
- m2
- capacidad_personas

[Mediciones_Energia]
- id_medicion (PK)
- aula_id (FK)
- fecha
- hora
- consumo_kwh
- tipo_energia (electrica/climatizacion)

[Ocupacion]
- id_ocupacion (PK)
- aula_id (FK)
- fecha
- hora_inicio
- hora_fin
- num_ocupantes
```

#### **Indicadores que pueden diseñar:**

##### **1. Consumo energético total mensual** (Absoluto, básico)

```
INDICADOR: Consumo total mensual
FÓRMULA: SUM(consumo_kwh) WHERE MONTH(fecha) = X
DATOS NECESARIOS: Mediciones_Energia.consumo_kwh, Mediciones_Energia.fecha
UNIDAD: kWh/mes
ODS: 7 (Energía asequible y no contaminante)
META: Reducir 10% respecto al año anterior
```

##### **2. Consumo energético por m²** (Relativo, eficiencia)

```
INDICADOR: Intensidad energética
FÓRMULA: SUM(consumo_kwh) / SUM(m2) POR cada edificio
DATOS NECESARIOS: 
  - Mediciones_Energia.consumo_kwh
  - Aulas.edificio_id
  - Edificios.m2_totales
UNIDAD: kWh/m²/mes
ODS: 7 + 11 (Ciudades sostenibles)
BENCHMARK: Media sectorial = 8.5 kWh/m²/mes
META: Alcanzar < 7 kWh/m²/mes
```

##### **3. Consumo energético por ocupante** (Relativo, impacto)

```
INDICADOR: Consumo per cápita
FÓRMULA: SUM(consumo_kwh) / AVG(num_ocupantes)
DATOS NECESARIOS:
  - Mediciones_Energia.consumo_kwh
  - Ocupacion.num_ocupantes (promedio ponderado)
UNIDAD: kWh/persona/mes
ODS: 7 + 12 (Producción y consumo responsables)
META: < 25 kWh/persona/mes
```

##### **4. Porcentaje de consumo fuera de horario lectivo** (Eficiencia operativa)

```
INDICADOR: Derroche energético
FÓRMULA: 
  SUM(consumo_kwh WHERE hora NOT IN horario_lectivo) / 
  SUM(consumo_kwh) × 100
DATOS NECESARIOS:
  - Mediciones_Energia.consumo_kwh
  - Mediciones_Energia.hora
  - Definición de horario_lectivo (8:00-20:00)
UNIDAD: %
ODS: 12 (Producción y consumo responsables)
META: < 15% (solo sistemas de seguridad y emergencia)
```

##### **5. Variación mensual de consumo** (Tendencia)

```
INDICADOR: Tasa de reducción intermensual
FÓRMULA: ((consumo_mes_actual - consumo_mes_anterior) / consumo_mes_anterior) × 100
DATOS NECESARIOS:
  - Mediciones_Energia.consumo_kwh agrupado por mes
UNIDAD: % de cambio
ODS: 7 + 13 (Acción por el clima)
META: Tendencia negativa (-3% mensual en invierno tras mejoras)
```

##### **6. Índice de eficiencia energética por aula** (Compuesto)

```
INDICADOR: Ranking de eficiencia
FÓRMULA: 
  Puntuación = 100 - (
    (consumo_real_kwh/m2 / consumo_referencia_kwh/m2) × 100
  )
DATOS NECESARIOS:
  - Mediciones_Energia.consumo_kwh
  - Aulas.m2
  - Consumo de referencia (estándar)
UNIDAD: Puntos (0-100)
ODS: 7 + 9 (Industria e infraestructura)
INTERPRETACIÓN: 
  - 80-100: Muy eficiente (verde)
  - 60-79: Eficiente (amarillo)
  - 0-59: Ineficiente (rojo)
```

### 4.3 Plantilla de ficha de indicador

Para cada indicador diseñado, completa esta ficha:

```markdown
## 📊 FICHA DE INDICADOR

**Nombre del indicador:** [Nombre descriptivo]

**Tipo:** [Absoluto/Relativo/Eficiencia/Impacto/Tendencia/Compuesto]

**Definición:** [Qué mide y por qué es importante]

**Fórmula de cálculo:**
[Expresión matemática o pseudocódigo]

**Datos necesarios:**
- Tabla: [nombre_tabla]
  - Campo: [campo1]
  - Campo: [campo2]
- Tabla: [otra_tabla]
  - Campo: [campo3]

**Unidad de medida:** [kWh, %, kg, etc.]

**Frecuencia de cálculo:** [Diaria/Semanal/Mensual/Anual]

**Responsable de medición:** [Quién recoge los datos]

**ODS relacionados:** [Número y nombre del ODS]

**Meta u objetivo:**
- Valor actual: [si se conoce]
- Valor objetivo: [cuantificado]
- Plazo: [fecha límite]

**Benchmark o referencia:**
- Media del sector: [valor]
- Mejor práctica: [valor]
- Fuente: [origen de la referencia]

**Consulta SQL conceptual:**
```sql
-- [Pseudocódigo o descripción de la consulta necesaria]
-- Ejemplo: "Sumar consumo_kwh de Mediciones_Energia,
--           agrupar por mes, dividir entre suma de m2 de Aulas"
```

**Interpretación:**
- ↗️ Si aumenta: [qué significa y qué hacer]
- ↘️ Si disminuye: [qué significa y qué hacer]

**Visualización sugerida:**
[Gráfico de barras / línea temporal / gauge / semáforo / tabla]

**Limitaciones o advertencias:**
[Posibles problemas de calidad de datos, excepciones, etc.]

---

## 5. ODS y métricas aplicadas: Casos reales

### 5.1 ODS 7: Energía asequible y no contaminante

#### **Meta 7.3:** Para 2030, duplicar la tasa mundial de mejora de la eficiencia energética

**Indicadores globales oficiales:**
- 7.3.1: Intensidad energética (energía primaria / PIB)

**Adaptación a centros educativos:**

| Indicador adaptado | Cálculo | Benchmark |
|-------------------|---------|-----------|
| Intensidad energética del centro | kWh / m² / año | < 100 kWh/m²/año (clima templado) |
| Consumo per cápita | kWh / estudiante / año | < 300 kWh/estudiante/año |
| % energía renovable | kWh renovable / kWh total × 100 | Meta: 100% |

**Caso real:**
> **IES Ítaca (Barcelona)** redujo su consumo de 145 kWh/m²/año a 82 kWh/m²/año mediante:
> - Instalación de paneles solares (30% autoconsumo)
> - Sustitución de luminarias por LED (-40% consumo iluminación)
> - Monitorización en tiempo real y sensibilización

### 5.2 ODS 12: Producción y consumo responsables

#### **Meta 12.5:** Para 2030, reducir considerablemente la generación de desechos mediante prevención, reducción, reciclado y reutilización

**Indicadores globales oficiales:**
- 12.5.1: Tasa de reciclaje nacional

**Adaptación a centros educativos:**

| Indicador adaptado | Cálculo | Benchmark |
|-------------------|---------|-----------|
| Tasa de reciclaje | kg reciclados / kg totales × 100 | Meta: > 50% |
| Generación de residuos per cápita | kg / estudiante / año | < 15 kg/estudiante/año |
| Reducción de plásticos de un solo uso | Unidades año actual / año anterior | Meta: -80% en 2025 |
| % compostaje de residuos orgánicos | kg compostados / kg orgánicos × 100 | Meta: 100% |

**Caso real:**
> **CEIP Amara Berri (San Sebastián)** alcanzó 65% de tasa de reciclaje mediante:
> - Separación en origen (5 fracciones: papel, envases, orgánico, resto, vidrio)
> - Compostadora escolar (eliminó 100% residuos orgánicos)
> - Monitorización semanal por clase (gamificación)
> - Reducción de 45 kg/estudiante/año a 18 kg/estudiante/año

### 5.3 ODS 5: Igualdad de género

#### **Meta 5.5:** Asegurar la participación plena de las mujeres en todos los niveles de toma de decisiones

**Indicadores globales oficiales:**
- 5.5.2: Proporción de mujeres en cargos directivos

**Adaptación a centros educativos:**

| Indicador adaptado | Cálculo | Benchmark |
|-------------------|---------|-----------|
| Brecha de género en ciclos STEM | |% mujeres - % hombres| en FP STEM | Meta: < 10% |
| Participación en órganos de gobierno | % mujeres en consejo escolar | Meta: 50% |
| Brecha salarial docente | (Salario medio hombres - mujeres) / hombres × 100 | Meta: 0% |
| Representación en materiales didácticos | % figuras femeninas en ejemplos | Meta: 50% |

**Caso real:**
> **IES Vicent Andrés Estellés (Valencia)** pasó de 12% a 38% de alumnas en DAM/DAW mediante:
> - Programa de mentorización (alumnas senior → junior)
> - Visibilización de referentes femeninas en tecnología
> - Talleres de sensibilización sobre sesgos de género
> - Medición anual y publicación de datos

### 5.4 ODS 6: Agua limpia y saneamiento

#### **Meta 6.4:** Para 2030, aumentar sustancialmente la eficiencia en el uso del agua

**Indicadores globales oficiales:**
- 6.4.1: Cambio en la eficiencia del uso del agua con el tiempo

**Adaptación a centros educativos:**

| Indicador adaptado | Cálculo | Benchmark |
|-------------------|---------|-----------|
| Consumo de agua per cápita | litros / persona / día | < 15 litros/persona/día |
| Eficiencia de grifos y cisternas | litros/minuto o litros/descarga | Grifos: < 6 L/min, WC: < 4.5 L |
| % agua reciclada | litros reutilizados / litros consumidos × 100 | Meta: > 20% (riego) |
| Detección de fugas | Consumo nocturno / consumo diario × 100 | Aceptable: < 10% |

**Caso real:**
> **CIFP Los Viveros (Sevilla)** redujo consumo de 22 L/persona/día a 11 L/persona/día:
> - Sustitución de cisternas antiguas (9L) por eficientes (3/4.5L)
> - Instalación de grifos con temporizador
> - Sistema de recogida de agua de lluvia para riego (1.200 L)
> - Alerta automática de fugas (consumo nocturno > umbral)

### 5.5 ODS 13: Acción por el clima

#### **Meta 13.2:** Incorporar medidas relativas al cambio climático en las políticas

**Indicadores globales oficiales:**
- 13.2.1: Número de países con estrategias de mitigación

**Adaptación a centros educativos:**

| Indicador adaptado | Cálculo | Benchmark |
|-------------------|---------|-----------|
| Huella de carbono total | kg CO₂ equiv. / año | Reducir 50% en 2030 |
| Huella de carbono per cápita | kg CO₂ / estudiante / año | < 200 kg CO₂/est/año |
| Emisiones por movilidad | kg CO₂ transporte / año | Reducir 30% |
| Compensación de emisiones | kg CO₂ compensados / emitidos × 100 | Meta: 100% |

**Cálculo simplificado de huella de carbono:**

```
Huella CO₂ = Emisiones_Directas + Emisiones_Indirectas

Emisiones Directas (Alcance 1):
- Calefacción de gas: m³ gas × 2.03 kg CO₂/m³
- Vehículos propios: litros combustible × 2.31 kg CO₂/L

Emisiones Indirectas (Alcance 2):
- Electricidad: kWh × Factor de emisión red (España: 0.25 kg CO₂/kWh)

Emisiones Indirectas (Alcance 3):
- Movilidad: km recorridos × factor transporte
  · Coche: 0.18 kg CO₂/km
  · Autobús: 0.08 kg CO₂/km
  · Tren: 0.04 kg CO₂/km
  · Bicicleta/andando: 0 kg CO₂/km
```

**Caso real:**
> **IES Mar de Aragón (Zaragoza)** redujo su huella de 285 kg CO₂/estudiante/año a 142 kg CO₂/estudiante/año:
> - Sustitución de caldera de gas por aerotermia (-60% emisiones calefacción)
> - Autoconsumo solar 40% (-40% emisiones electricidad)
> - Promoción de movilidad sostenible: de 68% coche a 35% coche
> - Compensación con plantación de árboles en el patio (absorción 1.2 Tn CO₂/año)

---

## 6. Criterios para seleccionar buenos indicadores

### 6.1 Framework SMART

Un indicador debe ser:

```
S - Specific (Específico)
    ¿Qué mide exactamente?
    
M - Measurable (Medible)
    ¿Puedo cuantificarlo con datos disponibles?
    
A - Achievable (Alcanzable)
    ¿Puedo influir en este indicador con acciones del centro?
    
R - Relevant (Relevante)
    ¿Está alineado con objetivos estratégicos y ODS?
    
T - Time-bound (Temporal)
    ¿Puedo medir evolución en el tiempo?
```

**Ejemplo aplicado:**

| Criterio | ❌ Indicador mal definido | ✅ Indicador SMART |
|----------|--------------------------|-------------------|
| Specific | "Sostenibilidad del centro" | "kWh consumidos por m² mensual" |
| Measurable | "Nivel de reciclaje" | "% residuos reciclados sobre total generado" |
| Achievable | "Huella de carbono global del sector educativo" | "kg CO₂ del instituto derivado de electricidad" |
| Relevant | "Temperatura exterior media" | "Temperatura interior vs setpoint (confort)" |
| Time-bound | "Consumo histórico" | "Variación % consumo respecto al mismo mes año anterior" |

### 6.2 Matriz de priorización de indicadores

Para elegir qué indicadores trabajar primero:

```
           Alta
            │
            │  🟩 QUICK WINS          🟨 PROYECTOS MAYORES
            │  (fácil + alto impacto) (difícil + alto impacto)
   IMPACTO  │  
    ASG     │  Prioridad 1            Prioridad 2
            │
            │  🟦 POSTERIORES         🟥 DESCARTAR
            │  (fácil + bajo impacto) (difícil + bajo impacto)
            │  
            │  Prioridad 3            Prioridad 4
           Baja
            └─────────────────────────────────────────
                  Baja        FACTIBILIDAD          Alta
                        (datos disponibles + capacidad)
```

**Ejercicio de priorización:**

| Indicador | Datos disponibles | Complejidad cálculo | Impacto ASG | Prioridad |
|-----------|-------------------|---------------------|-------------|-----------|
| kWh/m²/mes | ✅ Sí (contador) | 🟢 Baja (división) | 🟢 Alto | 🟩 QUICK WIN |
| Huella de carbono total | ⚠️ Parcial | 🟡 Media (múltiples fuentes) | 🟢 Alto | 🟨 PROYECTO MAYOR |
| % mujeres en STEM | ✅ Sí (matrícula) | 🟢 Baja (ratio) | 🟢 Alto | 🟩 QUICK WIN |
| Índice biodiversidad patio | ❌ No | 🔴 Alta (requiere experto) | 🟡 Medio | 🟥 DESCARTAR |
| % residuos reciclados | ✅ Sí (pesaje) | 🟢 Baja (porcentaje) | 🟢 Alto | 🟩 QUICK WIN |

### 6.3 Checklist de validación

Antes de incluir un indicador en tu proyecto, verifica:

- [ ] **¿Tengo los datos necesarios** o puedo obtenerlos fácilmente?
- [ ] **¿Puedo actualizarlo periódicamente** sin esfuerzo excesivo?
- [ ] **¿Existe un benchmark** o valor de referencia para comparar?
- [ ] **¿Puedo establecer una meta cuantificada** realista?
- [ ] **¿Está relacionado con al menos un ODS**?
- [ ] **¿Puedo explicar su significado** a alguien sin conocimientos técnicos?
- [ ] **¿Las acciones del centro pueden influir** en este indicador?
- [ ] **¿Puedo representarlo visualmente** de forma clara?
- [ ] **¿Es auditable y verificable** por terceros?
- [ ] **¿Aporta información nueva** o complementa otros indicadores?

**Si respondes SÍ a 7 o más preguntas → Indicador válido ✅**

### 6.4 Errores comunes al diseñar indicadores

| ❌ Error | 📝 Descripción | ✅ Solución |
|---------|---------------|-----------|
| **Vanity metrics** | Indicadores que "quedan bien" pero no orientan decisiones | Priorizar indicadores accionables |
| **Sobrecarga de indicadores** | Medir demasiadas cosas sin capacidad de análisis | Máximo 8-10 indicadores por trimestre |
| **Falta de contexto** | Indicadores sin benchmark ni meta | Siempre incluir referencia y objetivo |
| **Datos no disponibles** | Diseñar indicadores sin datos reales | Validar disponibilidad antes de definir |
| **Complejidad excesiva** | Fórmulas incomprensibles para el equipo | Preferir indicadores simples y claros |
| **Indicadores estáticos** | No actualizar ni revisar su relevancia | Revisión semestral de batería de indicadores |
| **Falta de responsable** | Nadie asignado para medir y reportar | Asignar responsable y frecuencia |


---

## 🔗 Recursos adicionales

### Documentación oficial ODS:
- **Indicadores ODS oficiales**: https://unstats.un.org/sdgs/indicators/indicators-list/
- **Metadata ODS**: https://unstats.un.org/sdgs/metadata/

### Bases de datos de referencia:
- **INE España**: https://www.ine.es (datos demográficos y sociales)
- **MITECO**: https://www.miteco.gob.es (datos ambientales)
- **Red Eléctrica**: https://www.ree.es (factor de emisión electricidad)
- **IDAE**: https://www.idae.es (eficiencia energética en edificios)

### Calculadoras y herramientas:
- **Calculadora huella de carbono**: https://www.miteco.gob.es/es/cambio-climatico/temas/mitigacion-politicas-y-medidas/calculadoras.aspx
- **Certificación energética edificios**: https://energia.gob.es/desarrollo/EficienciaEnergetica/CertificacionEnergetica/Paginas/Index.aspx

### Informes y estudios:
- **Memoria de Sostenibilidad GRI** (Global Reporting Initiative): https://www.globalreporting.org
- **Agenda 2030 educación**: UNESCO - https://es.unesco.org/gem-report/

---

## 💡 Reflexión final

> "Lo que no se mide, no se puede mejorar."  
> — Peter Drucker

Y recuerda: **los mejores indicadores no son los más complejos, sino los que orientan decisiones concretas** para hacer del instituto (y del mundo) un lugar más sostenible. 🌍💚

---


