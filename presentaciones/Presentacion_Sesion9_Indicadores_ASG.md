# Del Dato al Impacto: Interpretación de Indicadores ASG

## Sesión 9
### Digitalización + Sostenibilidad | 1º DAW

---

## Pregunta inicial

### ¿Por qué medimos?

> "Lo que no se mide, no se puede mejorar."  
> — Peter Drucker

**Reflexión:**  
¿Cómo sabemos si nuestro instituto es sostenible?  
¿Cómo demostramos el impacto de nuestras acciones?

---

## Agenda de la sesión

1. Introducción: La importancia de los criterios ASG
2. De datos a información: el camino hacia los indicadores
3. Tipos de indicadores de sostenibilidad
4. Diseño de indicadores desde el modelo de datos
5. Casos reales: ODS y métricas aplicadas
6. Criterios para seleccionar buenos indicadores

**Duración:** 2 horas (45 min teoría + 75 min práctica)

---

# PARTE 1
## La importancia de los criterios ASG

---

## ¿Qué son los criterios ASG?

**ASG = Ambiental + Social + Gobernanza**  
(ESG en inglés: Environmental, Social, Governance)

Marco de evaluación que mide el impacto de una organización **más allá de resultados económicos**

### Origen y evolución

- **2004:** Informe "Who Cares Wins" (ONU + instituciones financieras)
- **2015:** Agenda 2030 y Objetivos de Desarrollo Sostenible
- **2021:** Normativa europea de reporting de sostenibilidad
- **Actualidad:** Estándar global para inversión y gestión responsable

---

## Los tres pilares de ASG

### Ambiental
Cambio climático | Energía | Residuos | Agua | Biodiversidad

### Social
Igualdad | Salud y bienestar | Condiciones laborales | Inclusión | Participación

### Gobernanza
Transparencia | Ética | Protección de datos | Participación | Estrategias documentadas

---

## ¿Por qué ASG en educación?

### Pregunta clave: ¿Qué tiene que ver la sostenibilidad con un instituto?

**Cuatro razones fundamentales:**

1. **Responsabilidad institucional**  
   Los centros educativos consumen recursos y generan impacto

2. **Función educativa**  
   Se educa con el ejemplo: coherencia entre lo que enseñamos y hacemos

3. **Obligación normativa**  
   Creciente legislación sobre sostenibilidad y reporting

4. **Mejora continua**  
   Datos para tomar decisiones informadas y eficaces

---

## ASG y ODS: una relación directa

### ¿Cómo se conectan ASG con los Objetivos de Desarrollo Sostenible?

Los **17 ODS** son las metas globales  
Los **criterios ASG** son el marco de medición y gestión

| Dimensión ASG | ODS relacionados (ejemplos) |
|---------------|---------------------------|
| **Ambiental** | ODS 6 (Agua), ODS 7 (Energía), ODS 12 (Consumo), ODS 13 (Clima) |
| **Social** | ODS 3 (Salud), ODS 4 (Educación), ODS 5 (Igualdad), ODS 10 (Reducción desigualdades) |
| **Gobernanza** | ODS 16 (Instituciones), ODS 17 (Alianzas) |

---

## Ejemplo: ODS 7 y criterios ASG

**ODS 7:** Energía asequible y no contaminante

### Meta 7.3
"Para 2030, duplicar la tasa mundial de mejora de la eficiencia energética"

**¿Cómo lo medimos con ASG?**

- **Ambiental:** kWh consumidos, % energía renovable, emisiones CO₂
- **Social:** Acceso equitativo a instalaciones climatizadas, confort térmico
- **Gobernanza:** Políticas energéticas documentadas, transparencia en consumos

**Indicador oficial ONU:** Intensidad energética (energía/PIB)  
**Adaptación educativa:** kWh/m²/año del centro

---

## La urgencia de medir

### Datos recientes (España, sector educativo):

- **Consumo energético:** 8-12 kWh/m²/mes en centros públicos
- **Brecha de género en FP STEM:** < 20% mujeres en ciclos tecnológicos
- **Residuos:** 15-25 kg/estudiante/año, solo 30-40% reciclado
- **Huella de carbono:** 200-400 kg CO₂/estudiante/año

**Pregunta:** ¿Dónde está nuestro instituto en estas estadísticas?

**Respuesta:** Solo lo sabremos si medimos

---

# PARTE 2
## De datos a información

---

## La pirámide de la información

```
           DECISIÓN
              ↑
        CONOCIMIENTO
              ↑
        INFORMACIÓN
              ↑
            DATOS
              ↑
        DATOS BRUTOS
```

### ¿En qué nivel estamos?

**Datos brutos:** 125.3, 142.7, 98.5...  
**Datos:** consumo_kwh en tabla mediciones_energia  
**Información:** "El edificio A consumió 12.450 kWh en enero"  
**Conocimiento:** "15% superior a la media anual"  
**Decisión:** "Instalar temporizadores en iluminación"

---

## ¿Qué es un indicador?

### Definición técnica

**Indicador:** Métrica cuantificable que permite medir desempeño, comparar situaciones y evaluar progreso hacia un objetivo

### Pregunta: ¿Qué diferencia hay entre un dato y un indicador?

| Aspecto | Dato | Indicador |
|---------|------|-----------|
| Naturaleza | Observación individual | Métrica procesada |
| Contexto | Aislado | Con referencia/meta |
| Utilidad | Descriptivo | Accionable |
| Ejemplo | "12.450 kWh" | "8.3 kWh/m² (objetivo: 7.0)" |

---

## Características de un buen indicador

### Framework: Criterios clave

**Relevante:** Relacionado con objetivos estratégicos y ODS

**Medible:** Cuantificable con datos disponibles

**Comprensible:** Interpretable por no expertos

**Comparable:** Permite benchmarking

**Accionable:** Orienta decisiones concretas

**Verificable:** Auditable y trazable

---

## Del modelo de datos a los indicadores

### Proceso sistemático

```
MODELO DE DATOS (ER)
         ↓
   DATOS DISPONIBLES
         ↓
INDICADORES BÁSICOS (agregaciones)
         ↓
INDICADORES DERIVADOS (cálculos)
         ↓
INDICADORES COMPUESTOS (índices)
```

### Pregunta clave
¿Qué puedo calcular con las tablas y campos de mi modelo ER?

---

## Ejemplo práctico

**Mi modelo de datos:**
- Tabla: Aulas (id, nombre, m2, edificio_id)
- Tabla: Mediciones_Energia (id, aula_id, consumo_kwh, fecha)
- Tabla: Edificios (id, nombre, m2_totales)

**¿Qué indicadores puedo calcular?**

| Indicador | Cálculo | Complejidad |
|-----------|---------|-------------|
| Consumo total | SUM(consumo_kwh) | Baja |
| Consumo por m² | SUM(consumo_kwh) / SUM(m2) | Media |
| Consumo por edificio | SUM(...) GROUP BY edificio | Media |
| Variación mensual | (mes_actual - mes_anterior) / mes_anterior | Alta |

---

# PARTE 3
## Tipos de indicadores

---

## Indicadores absolutos vs relativos

### ¿Cuál es más útil?

**Absolutos:** Valores brutos sin normalización
- Ejemplo: 12.450 kWh/mes
- Utilidad: Seguimiento histórico del mismo lugar
- Limitación: Difícil comparación entre centros

**Relativos:** Valores normalizados (ratios, per cápita)
- Ejemplo: 8.3 kWh/m²/mes
- Utilidad: Comparación justa entre centros de diferente tamaño
- Ventaja: Reflejan eficiencia real

**Conclusión:** Necesitamos ambos tipos, pero los relativos son más estratégicos

---

## Indicadores de eficiencia

### Fórmula general

```
Eficiencia = Salida útil / Entrada de recursos
```

### Ejemplos en contexto educativo

| Indicador | Fórmula | Interpretación |
|-----------|---------|----------------|
| Eficiencia energética | m² climatizados / kWh | Más alto = mejor |
| Tasa de reciclaje | kg reciclados / kg totales × 100 | Objetivo: 100% |
| Eficiencia académica | Aprobados / Matriculados × 100 | Más alto = mejor |
| Uso de espacios | Horas ocupación / Horas disponibles | Óptimo: 70-85% |

---

## Indicadores de impacto

### ¿Qué consecuencias estamos generando?

**Miden efectos ambientales o sociales**

| Indicador | Unidad | ODS |
|-----------|--------|-----|
| Huella de carbono | kg CO₂ equivalente | ODS 13 |
| Huella hídrica | m³ | ODS 6 |
| Residuos a vertedero | kg no reciclados | ODS 12 |
| Brecha de género | % diferencia | ODS 5 |

### Pregunta clave
¿Estamos midiendo actividades o resultados?

---

## Indicadores de tendencia

### ¿Estamos mejorando o empeorando?

**Miden cambios en el tiempo**

**Variación absoluta**
```
Cambio = Valor_final - Valor_inicial
```

**Variación relativa (%)**
```
Variación_% = ((Valor_final - Valor_inicial) / Valor_inicial) × 100
```

### Aplicación práctica

- Reducción de consumo año a año: Meta -5% anual
- Incremento de % reciclaje: Tendencia alcista sostenida
- Evolución satisfacción: Identificar patrones

---

## Indicadores compuestos

### ¿Un único número que lo resuma todo?

**Índices:** Combinan varios indicadores simples en una métrica

**Ejemplo: Índice de Sostenibilidad del Centro (ISC)**

```
ISC = (0.4 × Eficiencia_Energética) + 
      (0.3 × Tasa_Reciclaje) + 
      (0.2 × Transporte_Sostenible) +
      (0.1 × Satisfacción_Comunidad)

Escala: 0-100 (bajo/medio/alto)
```

**Ventajas:** Visión holística, útil para ranking  
**Desventajas:** Puede ocultar problemas específicos

---

# PARTE 4
## Diseño desde el modelo de datos

---

## Metodología de diseño

### Proceso paso a paso

**1. Revisar el modelo ER**  
¿Qué tablas, campos y relaciones tengo?

**2. Identificar datos clave**  
Numéricos → agregaciones | Fechas → series | Categóricos → agrupaciones

**3. Mapear datos → ODS**  
¿Qué ODS trabaja mi proyecto? ¿Qué indicadores se asocian?

**4. Definir denominadores**  
Para indicadores relativos: m², estudiantes, días lectivos...

**5. Formular consultas conceptuales**  
Pseudocódigo o lenguaje natural (SQL vendrá después)

---

## Caso completo: Consumo energético

### Modelo de datos disponible

- Edificios (id, nombre, m2_totales, año_construccion)
- Aulas (id, nombre, edificio_id, m2, capacidad)
- Mediciones_Energia (id, aula_id, fecha, hora, consumo_kwh, tipo)
- Ocupacion (id, aula_id, fecha, hora_inicio, hora_fin, num_ocupantes)

### Pregunta
¿Qué indicadores ASG podemos diseñar con estos datos?

---

## Indicador 1: Consumo total mensual

**Tipo:** Absoluto, básico

**Fórmula:**
```
SUM(consumo_kwh) WHERE MONTH(fecha) = X
```

**ODS:** 7 (Energía asequible y no contaminante)

**Meta:** Reducir 10% respecto al año anterior

**Limitación:** No permite comparar con otros centros (depende del tamaño)

---

## Indicador 2: Intensidad energética

**Tipo:** Relativo, eficiencia

**Fórmula:**
```
SUM(consumo_kwh) / SUM(m2_totales)
```

**Unidad:** kWh/m²/mes

**ODS:** 7 + 11 (Ciudades sostenibles)

**Benchmark:** Media sector = 8.5 kWh/m²/mes

**Meta:** < 7 kWh/m²/mes

**Ventaja:** Comparable con cualquier centro educativo

---

## Indicador 3: Consumo per cápita

**Tipo:** Relativo, impacto

**Fórmula:**
```
SUM(consumo_kwh) / AVG(num_ocupantes)
```

**Unidad:** kWh/persona/mes

**ODS:** 7 + 12 (Producción y consumo responsables)

**Meta:** < 25 kWh/persona/mes

**Interpretación:** Refleja el impacto individual

---

## Indicador 4: Derroche energético

**Tipo:** Eficiencia operativa

**Fórmula:**
```
SUM(consumo_kwh fuera de horario) / SUM(consumo_kwh total) × 100
```

**Unidad:** %

**ODS:** 12 (Producción y consumo responsables)

**Meta:** < 15% (solo sistemas de seguridad/emergencia)

**Acción:** Identifica consumos evitables

---

## Indicador 5: Tasa de reducción

**Tipo:** Tendencia

**Fórmula:**
```
((consumo_mes_actual - consumo_mes_anterior) / consumo_mes_anterior) × 100
```

**Unidad:** % de cambio

**ODS:** 7 + 13 (Acción por el clima)

**Meta:** Tendencia negativa (-3% mensual tras mejoras)

**Interpretación:** Mide efectividad de acciones implementadas

---

## Indicador 6: Ranking de eficiencia

**Tipo:** Compuesto, índice

**Fórmula:**
```
Puntuación = 100 - ((consumo_real / consumo_referencia) × 100)
```

**Escala:** 0-100 puntos

**Interpretación:**
- 80-100: Muy eficiente (verde)
- 60-79: Eficiente (amarillo)
- 0-59: Ineficiente (rojo)

**ODS:** 7 + 9 (Industria e infraestructura)

---

## Plantilla de ficha de indicador

### Información que debe incluir cada indicador

1. **Identificación:** Nombre, tipo, dimensión ASG, ODS
2. **Definición:** Qué mide y por qué es importante
3. **Cálculo:** Fórmula + datos necesarios + unidad
4. **Interpretación:** Valores alto/medio/bajo y qué hacer
5. **Meta y benchmark:** Objetivo cuantificado y referencia
6. **Visualización:** Tipo de gráfico sugerido
7. **Limitaciones:** Qué puede afectar la calidad del dato

---

# PARTE 5
## Casos reales

---

## ODS 7: Energía - IES Ítaca (Barcelona)

### Situación inicial
- Consumo: 145 kWh/m²/año
- Sin monitorización en tiempo real
- Iluminación obsoleta

### Acciones implementadas
- Instalación de paneles solares (30% autoconsumo)
- Sustitución luminarias por LED (-40% consumo iluminación)
- Sistema de monitorización y sensibilización

### Resultado
- Consumo actual: 82 kWh/m²/año
- **Reducción: 43%**
- Ahorro anual: 18.000€

---

## ODS 12: Consumo - CEIP Amara Berri (San Sebastián)

### Situación inicial
- Residuos: 45 kg/estudiante/año
- Tasa de reciclaje: 28%
- Todo a vertedero

### Acciones implementadas
- Separación en origen (5 fracciones)
- Compostadora escolar (eliminó 100% orgánicos)
- Monitorización semanal por clase (gamificación)

### Resultado
- Residuos: 18 kg/estudiante/año
- **Tasa de reciclaje: 65%**
- **Reducción: 60%**

---

## ODS 5: Igualdad - IES Vicent Andrés Estellés (Valencia)

### Situación inicial
- Alumnas en DAM/DAW: 12%
- Sin programas de mentorización
- Estereotipos no abordados

### Acciones implementadas
- Programa de mentorización (alumnas senior → junior)
- Visibilización de referentes femeninas en tecnología
- Talleres de sensibilización sobre sesgos
- Medición anual y publicación de datos

### Resultado
- **Alumnas en DAM/DAW: 38%**
- Incremento: 217% en 4 años

---

## ODS 6: Agua - CIFP Los Viveros (Sevilla)

### Situación inicial
- Consumo: 22 litros/persona/día
- Cisternas antiguas (9 litros)
- Pérdidas por fugas

### Acciones implementadas
- Sustitución de cisternas por eficientes (3/4.5L)
- Grifos con temporizador
- Recogida agua lluvia para riego (1.200L)
- Alerta automática de fugas

### Resultado
- **Consumo: 11 litros/persona/día**
- Reducción: 50%

---

## ODS 13: Clima - IES Mar de Aragón (Zaragoza)

### Situación inicial
- Huella: 285 kg CO₂/estudiante/año
- Calefacción de gas
- Movilidad: 68% en coche

### Acciones implementadas
- Sustitución caldera gas por aerotermia (-60% emisiones)
- Autoconsumo solar 40%
- Promoción movilidad sostenible
- Plantación de árboles (absorción 1.2 Tn CO₂/año)

### Resultado
- **Huella: 142 kg CO₂/estudiante/año**
- Reducción: 50%

---

## Lección de los casos reales

### ¿Qué tienen en común estos ejemplos?

1. **Miden primero:** Todos partieron de un diagnóstico cuantitativo
2. **Metas claras:** Objetivos numéricos y plazos definidos
3. **Acción múltiple:** Combinan varias estrategias
4. **Monitorización continua:** Verifican resultados periódicamente
5. **Comunicación:** Publican datos para rendir cuentas

### Conclusión
**Sin medición, no hay mejora demostrable**

---

# PARTE 6
## Selección de buenos indicadores

---

## Framework SMART

### Criterios de validación

**S - Specific (Específico)**  
¿Qué mide exactamente?

**M - Measurable (Medible)**  
¿Puedo cuantificarlo con datos disponibles?

**A - Achievable (Alcanzable)**  
¿Puedo influir en este indicador?

**R - Relevant (Relevante)**  
¿Está alineado con objetivos estratégicos y ODS?

**T - Time-bound (Temporal)**  
¿Puedo medir evolución en el tiempo?

---

## Ejemplo: Aplicando SMART

### Indicador mal definido
"Sostenibilidad del centro"

**Problemas:** No específico, no medible, no temporal

### Indicador SMART
"kWh consumidos por m² mensual"

- **S:** Consumo energético normalizado por superficie
- **M:** kWh (contador) / m² (planos)
- **A:** Podemos actuar (apagar equipos, mejorar aislamiento)
- **R:** ODS 7, objetivo estratégico del centro
- **T:** Mensual, permite ver evolución

---

## Matriz de priorización

### ¿Por dónde empezar?

```
           Alta
            │
            │  QUICK WINS          PROYECTOS MAYORES
            │  (implementar YA)    (planificar)
   IMPACTO  │  
    ASG     │  Prioridad 1         Prioridad 2
            │
            │  POSTERIORES         DESCARTAR
            │  (si queda tiempo)   (no prioritario)
            │  
           Baja  Prioridad 3         Prioridad 4
            └─────────────────────────────────────
                  Baja    FACTIBILIDAD    Alta
```

**Factibilidad:** Datos disponibles + complejidad cálculo  
**Impacto ASG:** Relevancia para decisiones clave

---

## Ejercicio de priorización

### Clasificar estos indicadores

| Indicador | Datos | Complejidad | Impacto | Cuadrante |
|-----------|-------|-------------|---------|-----------|
| kWh/m²/mes | Sí (contador) | Baja | Alto | Quick Win |
| Huella carbono total | Parcial | Media | Alto | Proyecto Mayor |
| % mujeres STEM | Sí (matrícula) | Baja | Alto | Quick Win |
| Índice biodiversidad | No | Alta | Medio | Descartar |
| % residuos reciclados | Sí (pesaje) | Baja | Alto | Quick Win |

**Estrategia:** Implementar los 3 Quick Wins primero, planificar los Proyectos Mayores

---

## Checklist de validación

### Antes de incluir un indicador, verificar:

- ¿Tengo los datos o puedo obtenerlos fácilmente?
- ¿Puedo actualizarlo periódicamente sin esfuerzo excesivo?
- ¿Existe un benchmark o valor de referencia?
- ¿Puedo establecer una meta cuantificada realista?
- ¿Está relacionado con al menos un ODS?
- ¿Puedo explicarlo a alguien sin conocimientos técnicos?
- ¿Las acciones del centro pueden influir en él?
- ¿Puedo representarlo visualmente de forma clara?
- ¿Es auditable y verificable por terceros?
- ¿Aporta información nueva o complementa otros?

**Mínimo: 7 respuestas afirmativas**

---

## Errores comunes a evitar

### Vanity metrics
Indicadores que "quedan bien" pero no orientan decisiones

**Ejemplo:** "Número total de registros en BD"

### Sobrecarga
Medir demasiadas cosas sin capacidad de análisis

**Recomendación:** Máximo 8-10 indicadores por trimestre

### Falta de contexto
Indicadores sin benchmark ni meta

**Solución:** Siempre incluir referencia y objetivo

---

## Errores comunes (continuación)

### Datos no disponibles
Diseñar indicadores sin datos reales

**Solución:** Validar disponibilidad antes de definir

### Complejidad excesiva
Fórmulas incomprensibles para el equipo

**Solución:** Preferir indicadores simples y claros

### Falta de responsable
Nadie asignado para medir y reportar

**Solución:** Asignar responsable y frecuencia

---

# Síntesis y conclusiones

---

## Lo que hemos aprendido hoy

### Conceptos clave

1. **Criterios ASG** son el marco para evaluar impacto más allá de lo económico
2. **Los datos se convierten en información** mediante indicadores bien diseñados
3. **Existen diferentes tipos:** absolutos, relativos, de eficiencia, impacto, tendencia
4. **Metodología de diseño:** Del modelo ER a indicadores medibles
5. **Casos reales demuestran** que medir es el primer paso para mejorar
6. **Framework SMART y matriz de priorización** para seleccionar indicadores

---

## Conexión con vuestro proyecto

### De la teoría a la práctica

**Ya tenéis:**
- Modelo ER diseñado y documentado
- Tablas y campos definidos
- ODS seleccionados

**Ahora vais a:**
- Identificar qué indicadores ASG podéis extraer
- Diseñar 5-8 indicadores priorizados
- Crear fichas técnicas completas
- Preparar consultas conceptuales

**Resultado:** Batería de indicadores lista para implementar (cuando dominéis SQL)

---

## Pregunta final

### ¿Cuál es el mejor indicador?

**Respuesta:** No existe el "mejor" indicador universal

**Depende de:**
- Contexto específico del centro
- Datos disponibles
- Objetivos estratégicos
- Capacidad de actuación

**Clave:** Una batería equilibrada que combine:
- Contexto (absolutos)
- Eficiencia (relativos)
- Evolución (tendencia)
- Visión global (compuesto)

---

## Próximos pasos

### Actividad práctica (75 minutos)

**Parte 1:** Análisis del modelo de datos (25 min)  
Inventario de tablas y campos relevantes para ASG

**Parte 2:** Batería de indicadores (45 min)  
Diseño de fichas técnicas completas (5-8 indicadores)

**Parte 3:** Priorización (15 min)  
Matriz factibilidad/impacto y justificación

**Entregable:** Documento "Batería de Indicadores ASG"  
Formato: Markdown o PDF

---

## Sesión 10: Puesta en común

### Preparar para la próxima sesión

**Presentación breve (5 minutos):**
- Contexto del proyecto y ODS
- 3 indicadores prioritarios (quick wins)
- Cómo los usaréis para mejorar la sostenibilidad

**Objetivo:**
- Recibir feedback
- Identificar sinergias entre equipos
- Aprender de enfoques diferentes

**No es una defensa formal, es aprendizaje colaborativo**

---

## Recursos de consulta

### Documentación oficial

- Indicadores ODS oficiales: unstats.un.org/sdgs/indicators
- IDAE (eficiencia energética): www.idae.es
- MITECO (datos ambientales): www.miteco.gob.es
- INE (datos sociales): www.ine.es

### Herramientas

- Calculadora huella carbono: MITECO
- Certificación energética edificios: energia.gob.es
- Global Reporting Initiative (GRI): www.globalreporting.org

---

## Reflexión final

> "Los mejores indicadores no son los más complejos,  
> sino los que orientan decisiones concretas  
> para hacer del instituto (y del mundo)  
> un lugar más sostenible."

### Recordad

- **Medir es el primer paso**, no el final
- **La sostenibilidad se demuestra con datos**, no con intenciones
- **Vuestro modelo de datos** es la base para comprender y transformar la realidad

---

## ¿Preguntas?

### Antes de empezar la actividad práctica

**Tiempo para aclarar dudas sobre:**
- Criterios ASG y su aplicación
- Tipos de indicadores
- Metodología de diseño
- Casos reales
- Criterios de selección

---

# ¡A trabajar!

## Diseñad vuestra batería de indicadores ASG

**Objetivo:** Dar sentido sostenible a vuestro modelo de datos

**Recordad:** Esta batería será la hoja de ruta para las próximas semanas

**Clave del éxito:** Indicadores medibles, relevantes y accionables

---

**Presentación elaborada para:**  
1º DAW - Digitalización + Sostenibilidad  
Sesión 9 - Enero 2026
