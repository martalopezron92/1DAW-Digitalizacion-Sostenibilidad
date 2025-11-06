# 💾 **Presentación: Fuentes de Datos y Sistemas de Información**
## *Sesión 2 - Digitalización y Sostenibilidad*

---

## 📋 **Índice**

1. [🎯 Objetivos](#-objetivos)
2. [🧠 ¿Por qué son importantes los datos?](#-por-qué-son-importantes-los-datos)
3. [🔍 Tipos de fuentes de datos](#-tipos-de-fuentes-de-datos)
4. [⚙️ Sistemas IT vs OT](#️-sistemas-it-vs-ot)
5. [🔄 Flujo de información digital](#-flujo-de-información-digital)
6. [🌐 Portales de datos abiertos](#-portales-de-datos-abiertos)
7. [✅ Criterios de calidad](#-criterios-de-calidad)
8. [🎯 Ejemplo práctico](#-ejemplo-práctico)

---

## 🎯 **Objetivos**

### Al final de esta sesión sabrás:

✅ **Identificar** diferentes tipos de fuentes de datos  
✅ **Distinguir** entre sistemas IT y OT  
✅ **Comprender** el flujo de información digital  
✅ **Evaluar** la calidad de las fuentes de datos  
✅ **Localizar** portales de datos abiertos útiles

### 💭 **Pregunta inicial:**
> *"¿Qué datos genera tu móvil cada día sin que te des cuenta?"*

---

## 🧠 **¿Por qué son importantes los datos?**

### 🌟 **Los datos son el nuevo petróleo**

En la era digital, **cada acción genera información**:
- 💡 Encender una luz → consumo energético
- 📱 Usar el móvil → ubicación, batería, apps
- 🚗 Viajar → emisiones, tiempo, distancia
- 📚 Estudiar → rendimiento, participación

### 🔄 **El proceso de valor**

```
DATOS → INFORMACIÓN → CONOCIMIENTO → DECISIONES
```

**Ejemplo:** 
- **Dato:** "25°C en el aula"
- **Información:** "La temperatura ha subido 3°C en una hora"
- **Conocimiento:** "Cuando sube la temperatura, baja la concentración"
- **Decisión:** "Activar ventilación a partir de 24°C"

### 🤔 **Pregunta reflexiva:**
> *"¿Crees que recopilamos demasiados datos o aún necesitamos más para tomar buenas decisiones?"*

---

## 🔍 **Tipos de fuentes de datos**

### 🏠 **1. Fuentes INTERNAS**
*Datos que genera nuestra propia organización*

| 🔧 **Tipo** | 📊 **Ejemplo** | 💻 **Tecnología** |
|:------------|:---------------|:------------------|
| **Operacionales** | Consumo eléctrico del centro | Contador inteligente |
| **Humanos** | Encuestas sobre transporte | Google Forms |
| **Administrativos** | Facturas de suministros | Sistema contable |
| **Tecnológicos** | Temperatura de aulas | Sensores IoT |

### 🌍 **2. Fuentes EXTERNAS**
*Datos públicos o de terceros*

| 🔧 **Tipo** | 📊 **Ejemplo** | 🌐 **Fuente** |
|:------------|:---------------|:--------------|
| **Datos abiertos** | Emisiones de CO₂ nacional | datos.gob.es |
| **APIs públicas** | Datos meteorológicos | AEMET |
| **Datasets** | Energías renovables | Kaggle |
| **Institucionales** | Estadísticas demográficas | INE |

### 📁 **3. Según su ESTRUCTURA**

#### 📊 **Estructurados**
- **Qué son:** Datos organizados en tablas
- **Ejemplo:** Base de datos SQL, Excel
- **Ventaja:** Fácil de analizar

#### 🗂️ **Semiestructurados**
- **Qué son:** Datos con cierta organización
- **Ejemplo:** JSON, XML, CSV
- **Ventaja:** Flexible pero procesable

#### 📝 **No estructurados**
- **Qué son:** Datos sin formato fijo
- **Ejemplo:** Texto libre, imágenes, videos
- **Desafío:** Requiere IA para procesar

### 💡 **Actividad práctica:**
*Identifica qué tipo de datos generarías para medir la sostenibilidad de tu clase*

---

## ⚙️ **Sistemas IT vs OT**

### 💻 **IT (Information Technology)**
*El mundo digital*

#### ¿Qué incluye?
- 🖥️ Servidores y bases de datos
- 🌐 Aplicaciones web y móviles
- 📊 Software de análisis (Excel, Power BI)

#### Ejemplo:
Una aplicación web que muestra gráficos del consumo energético del instituto

### 🔧 **OT (Operational Technology)**
*El mundo físico*

#### ¿Qué incluye?
- 🌡️ Sensores de temperatura
- 💡 Sistemas de control de iluminación
- 🚪 Control de acceso RFID

#### Ejemplo:
Un sensor que mide automáticamente la temperatura del aula cada 5 minutos

### 🔗 **Convergencia IT/OT**

```
🌡️ Sensor (OT) → 📡 WiFi → 💾 Base de datos (IT) → 📊 Dashboard
```

**Resultado:** Gestión inteligente basada en datos reales

### 🤔 **Pregunta:**
> *"¿Qué ventajas y riesgos tiene conectar el mundo físico (OT) con el digital (IT)?"*

---

## 🔄 **Flujo de información digital**

### 📈 **Las 5 fases del dato**

#### 1️⃣ **CAPTURA**
- **Qué:** Recoger datos del entorno
- **Ejemplo:** Sensor mide consumo eléctrico
- **Herramientas:** Sensores, encuestas, APIs

#### 2️⃣ **TRANSMISIÓN**
- **Qué:** Enviar datos al servidor
- **Ejemplo:** WiFi, cable de red, 4G
- **Protocolos:** HTTP, MQTT, WebSocket

#### 3️⃣ **ALMACENAMIENTO**
- **Qué:** Guardar datos de forma organizada
- **Ejemplo:** Base de datos MySQL
- **Opciones:** Local, nube, híbrido

#### 4️⃣ **PROCESAMIENTO**
- **Qué:** Limpiar y transformar datos
- **Ejemplo:** Eliminar duplicados, convertir unidades
- **Herramientas:** Python, R, SQL

#### 5️⃣ **VISUALIZACIÓN**
- **Qué:** Mostrar resultados de forma clara
- **Ejemplo:** Gráficos, dashboards, reportes
- **Herramientas:** Power BI, Tableau, Excel

### 📊 **Ejemplo completo:**

```
Sensor IoT → WiFi → Raspberry Pi → MySQL → Power BI → Usuario
```

---

## 🌐 **Portales de datos abiertos**

### 🇪🇸 **Nacionales**

#### **[datos.gob.es](https://datos.gob.es)**
- **Qué es:** Catálogo oficial de datos abiertos de España
- **Contiene:** Energía, transporte, medio ambiente
- **Ejemplo:** Consumo eléctrico de edificios públicos

#### **[INE](https://www.ine.es)**
- **Qué es:** Instituto Nacional de Estadística
- **Contiene:** Demografía, empleo, sostenibilidad
- **Ejemplo:** Datos de movilidad urbana

### 🌍 **Internacionales**

#### **[Kaggle](https://www.kaggle.com)**
- **Qué es:** Comunidad de ciencia de datos
- **Contiene:** Datasets y competiciones
- **Ejemplo:** "Global Energy Consumption"

#### **[Our World in Data](https://ourworldindata.org)**
- **Qué es:** Investigación con visualizaciones
- **Contiene:** Energías renovables, emisiones CO₂
- **Ejemplo:** Evolución de energías limpias por país

### 🌤️ **Especializados**

#### **[AEMET OpenData](https://opendata.aemet.es)**
- **Qué es:** API meteorológica oficial
- **Contiene:** Temperatura, precipitaciones, radiación solar
- **Uso:** Correlacionar clima con consumo energético

### 💡 **Actividad:**
*Busca en datos.gob.es un dataset relacionado con sostenibilidad de tu ciudad*

---

## ✅ **Criterios de calidad**

### 🎯 **¿Cómo evaluar si una fuente es buena?**

| ✅ **Criterio** | 🔍 **Qué evaluar** | 👍 **Ejemplo bueno** |
|:----------------|:-------------------|:---------------------|
| **Exactitud** | ¿Los datos son correctos? | Sensor calibrado con error < 1% |
| **Integridad** | ¿Faltan datos? | Dataset completo sin huecos |
| **Consistencia** | ¿Mismo formato siempre? | Fechas en formato ISO (2025-11-06) |
| **Actualización** | ¿Qué tan reciente es? | Datos diarios o en tiempo real |
| **Trazabilidad** | ¿Conoces el origen? | Fuente oficial (AEMET, INE) |
| **Accesibilidad** | ¿Fácil de obtener? | Descarga directa o API |

### 🚨 **Señales de alerta:**

❌ **Datos de hace más de 2 años**  
❌ **Fuente desconocida o no oficial**  
❌ **Muchos valores vacíos o inconsistentes**  
❌ **Difícil de descargar o procesar**

### 🤔 **Pregunta crítica:**
> *"¿Prefieres muchos datos de calidad media o pocos datos de alta calidad?"*

---

## 🎯 **Ejemplo práctico**

### 🏫 **Caso: Análisis energético del instituto**

#### 🎯 **Objetivo**
Reducir el consumo eléctrico del centro identificando patrones

#### 📊 **Fuentes de datos**

**🏠 Internas:**
- Facturas eléctricas mensuales (kWh)
- Horarios de ocupación de aulas
- Inventario de equipos (ordenadores, proyectores)

**🌍 Externas:**
- Temperatura exterior (API AEMET)
- Datos de otros centros educativos (datos.gob.es)
- Precios de la electricidad (REE)

#### 🔄 **Flujo del proyecto**

1. **Captura:** Recopilar facturas + API meteorológica
2. **Transmisión:** CSV + peticiones HTTP
3. **Almacenamiento:** Base de datos MySQL
4. **Procesamiento:** Script Python para análisis
5. **Visualización:** Dashboard con gráficos de tendencias

#### 📈 **Resultados esperados**
- Identificar horarios de mayor consumo
- Correlacionar temperatura con gasto energético
- Proponer medidas de ahorro específicas

#### 💡 **Aplicación práctica**
*"Si la temperatura sube 1°C, el consumo aumenta un 15%"*  
→ **Acción:** Mejorar aislamiento térmico

---

## 💭 **Reflexiones finales**

### 🔮 **El futuro de los datos**

#### 🌟 **Tendencias emergentes:**
- **IoT masivo:** Millones de sensores conectados
- **IA integrada:** Análisis automático de patrones
- **Tiempo real:** Decisiones instantáneas basadas en datos
- **Privacidad por diseño:** Datos útiles pero protegidos

#### 🚀 **Nuevas profesiones:**
- **Data Scientists** especializados en sostenibilidad
- **Ingenieros de IoT** para ciudades inteligentes
- **Analistas de huella digital** ambiental

### 🎯 **Tu papel como futuro profesional**

#### 💪 **Habilidades clave:**
- **Pensamiento analítico:** Ver patrones en los datos
- **Curiosidad técnica:** Entender cómo funcionan las APIs
- **Ética digital:** Usar datos de forma responsable
- **Comunicación:** Explicar insights de forma clara

### 🌍 **Preguntas para reflexionar:**

1. **Técnica:** 
   > *"¿Qué datos de tu vida diaria te gustaría analizar para ser más sostenible?"*

2. **Ética:** 
   > *"¿Dónde está el límite entre datos útiles e invasión de privacidad?"*

3. **Práctica:** 
   > *"¿Cómo convencerías a tu instituto para instalar sensores de monitorización?"*

---

## 🎯 **Actividades de cierre**

### 📝 **Autoevaluación rápida**

**Evalúa tu comprensión (1-5):**

- [ ] Distingo entre fuentes internas y externas: ⭐⭐⭐⭐⭐
- [ ] Entiendo la diferencia entre IT y OT: ⭐⭐⭐⭐⭐  
- [ ] Conozco el flujo de información digital: ⭐⭐⭐⭐⭐
- [ ] Puedo evaluar calidad de datos: ⭐⭐⭐⭐⭐

### 🔍 **Mini-investigación**

**Elige una opción:**

**A) Portal explorer:** Encuentra 3 datasets en datos.gob.es relacionados con tu ciudad  
**B) API tester:** Prueba a acceder a la API de AEMET para obtener datos de tu provincia  
**C) Quality checker:** Evalúa un dataset de Kaggle usando los criterios de calidad

### 📊 **Para la próxima sesión**

#### 🎯 **Misión**
Identifica una fuente de datos (interna o externa) que podrías usar para medir algún aspecto de sostenibilidad en tu entorno (casa, instituto, barrio)

#### ✍️ **Entrega** (150 palabras)
- **Fuente elegida:** ¿Cuál y por qué?
- **Tipo de datos:** ¿Estructurados, semi o no estructurados?
- **Calidad:** Evalúa según los 6 criterios
- **Aplicación:** ¿Qué podrías descubrir?

---

## 📚 **Recursos útiles**

### 🌐 **Enlaces directos**
- [datos.gob.es](https://datos.gob.es) - Datos abiertos España
- [AEMET OpenData](https://opendata.aemet.es) - Meteorología
- [Kaggle](https://www.kaggle.com) - Datasets y competiciones
- [Our World in Data](https://ourworldindata.org) - Investigación global

### 📖 **Lecturas recomendadas**
- "Data Science for Business" - Foster Provost
- "The Data Revolution" - Rob Kitchin
- "Big Data: A Revolution" - Viktor Mayer-Schönberger

### 🎥 **Videos complementarios**
- "What is Big Data?" (IBM)
- "IoT Explained" (Cisco)
- "Open Data Movement" (TED Talk)

---

## 🎊 **¡Gracias!**

### 💫 **Recuerda**
> *"Los datos sin análisis son solo ruido.  
> El análisis sin acción es solo entretenimiento."*

### 🚀 **Próximo paso**
**Sesión 3:** Recogida de datos locales  
*Aprenderemos a capturar datos reales de nuestro entorno*

---

*Presentación Sesión 2 - Digitalización y Sostenibilidad*