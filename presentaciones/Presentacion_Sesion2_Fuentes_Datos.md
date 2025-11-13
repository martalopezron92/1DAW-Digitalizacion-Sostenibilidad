# 💾 **Presentación: Fuentes de Datos y Sistemas de Información**
## *Sesión 2 - Digitalización y Sostenibilidad*

---

## 📋 **Índice**

1. [🎯 Objetivos](#-objetivos)
2. [🧠 ¿Por qué son importantes los datos?](#-por-qué-son-importantes-los-datos)
3. [🔍 ¿De dónde vienen los datos?](#-de-dónde-vienen-los-datos)
4. [¿Cómo se organizan los datos?](#-cómo-se-organizan-los-datos)
4. [⚙️ ¿Qué sistemas gestionan los datos?](#️-qué-sistemas-gestionan-los-datos)
5. [🔄 ¿Cómo se recogen y procesan?](#-cómo-se-recogen-y-procesan)
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

---

## 🧠 **¿Por qué son importantes los datos?**
### *El valor de la información*

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

---

## 🔍 **¿De dónde vienen los datos?**
### *Tipos de fuentes de datos*

#### 🏠 **1.Fuentes INTERNAS**
*Datos que genera nuestra propia organización*

| 🔧 **Tipo** | 📊 **Ejemplo** | 💻 **Tecnología** |
|:------------|:---------------|:------------------|
| **Operacionales** | Consumo eléctrico del centro | Contador inteligente |
| **Humanos** | Encuestas sobre transporte | Google Forms |
| **Administrativos** | Facturas de suministros | Sistema contable |
| **Tecnológicos** | Temperatura de aulas | Sensores IoT |

#### 🌍 **2.Fuentes EXTERNAS**
*Datos públicos o de terceros*

| Concepto | Qué es | Ejemplo |
|:---------|:-------|:--------|
| **Datos Abiertos** | 📜 **Licencia** - Datos de libre uso y redistribución | Datos del INE, datos.gob.es |
| **APIs Públicas** | 🔌 **Método de acceso** - Interfaz para obtener datos en tiempo real | API de AEMET, Google Maps API |
| **Datasets públicos** | 📦 **Formato de entrega** - Archivo descargable estático | CSV de Kaggle, archivo Excel |


## 🔍 **¿Cómo se organizan los datos?**
### *Tipos de datos segun su estructura*

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
---

## ⚙️ **¿Qué sistemas gestionan los datos?**
### *IT vs OT: Mundo digital y mundo físico*

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

## 🔄 **¿Cómo se recogen y procesan los datos?**
### *El flujo de información digital completo*

### 📈 **Las 5 fases del dato**

#### 1️⃣ **CAPTURA** (¿Cómo se recogen?)
- **Qué:** Recoger datos del entorno
- **Ejemplo:** Sensor mide consumo eléctrico
- **Métodos:** Sensores IoT, formularios web, APIs, importación de archivos, scraping web

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
- **Comunicación:** Explicar insights de forma clar

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