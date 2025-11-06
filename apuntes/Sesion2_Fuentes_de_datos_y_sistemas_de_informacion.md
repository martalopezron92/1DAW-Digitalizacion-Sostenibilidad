# 💾 Sesión 2 – Fuentes de datos y sistemas de información

## 🧠 1. Introducción

En la era digital, los datos son un **activo estratégico**. Cada acción —encender una luz, registrar asistencia, enviar un correo, analizar una factura o medir una temperatura— genera información.  
Sin embargo, los datos no tienen valor por sí solos: deben **recogerse, almacenarse, procesarse y analizarse** de forma estructurada.  
Comprender **de dónde provienen** (fuentes de datos) y **cómo circulan** (flujo de información digital) es el primer paso para poder convertirlos en conocimiento útil.

---

## 🔍 2. Tipos de fuentes de datos

Una **fuente de datos** es cualquier origen desde el cual se puede obtener información que posteriormente será tratada en un sistema informático (base de datos, aplicación, dashboard, etc.).  
Pueden clasificarse en **internas** y **externas**, y también según su naturaleza (**estructurada**, **semiestructurada** o **no estructurada**).

### 2.1. Fuentes internas

Proceden de **dentro de la organización o centro educativo**.  

| Tipo de dato | Fuente | Ejemplo concreto |
|---------------|--------|------------------|
| Operacionales | Sistemas internos | Registro de consumo eléctrico del edificio, control de acceso RFID, inventario TIC |
| Humanos | Cuestionarios o formularios | Encuestas al alumnado sobre hábitos de transporte o reciclaje |
| Administrativos | Documentación interna | Facturas de suministros, partes de mantenimiento, uso de recursos de impresión |
| Tecnológicos | Sensores o IoT | Temperatura, luminosidad, CO₂, nivel de ruido, aforo de aulas |

🧩 *Ejemplo práctico:*  
Un sistema IoT instalado en el laboratorio de informática registra el consumo eléctrico de los equipos cada 5 minutos y lo envía en formato JSON a una base de datos PostgreSQL.  
Estos datos internos permiten calcular la huella energética del centro y detectar horarios de mayor consumo.

---

### 2.2. Fuentes externas

Proceden de **organismos públicos, empresas o comunidades científicas** que publican datos abiertos o accesibles mediante APIs.

| Tipo | Descripción | Ejemplo de uso |
|------|--------------|----------------|
| **Open Data (datos abiertos)** | Datos disponibles libremente con licencias públicas. | Consumo energético nacional, emisiones de CO₂, estadísticas de movilidad. |
| **APIs públicas** | Interfaces que permiten acceder a bases de datos o servicios en tiempo real. | API de AEMET (datos meteorológicos), API de REE (demanda eléctrica). |
| **Plataformas de datasets** | Repositorios de datos para investigación o análisis. | Kaggle, Our World in Data, datos.gob.es |
| **Datos institucionales** | Publicaciones de organismos oficiales. | Instituto Nacional de Estadística (INE), Eurostat, Banco Mundial. |

📡 *Ejemplo práctico:*  
Desde la API de AEMET se pueden extraer los registros de temperatura media y radiación solar de una provincia.  
Estos datos externos pueden combinarse con los internos del centro para analizar la **eficiencia energética** y el **impacto de la temperatura ambiental** en el consumo eléctrico.

---

### 2.3. Formato y estructura de los datos

| Tipo | Ejemplo | Características |
|------|----------|-----------------|
| **Estructurados** | Tablas SQL, hojas de cálculo | Datos organizados en filas y columnas. Fácil de procesar con SQL o Power BI. |
| **Semiestructurados** | JSON, XML, CSV | Datos jerárquicos o separados por delimitadores. Requieren limpieza previa. |
| **No estructurados** | Texto libre, imágenes, vídeos | No tienen formato predecible. Necesitan procesamiento avanzado (IA, NLP). |

📂 *Ejemplo:* un archivo CSV de *datos.gob.es* sobre consumo energético puede tener esta estructura:

```
Año;Mes;Consumo_kWh;Tipo_Instalacion
2023;01;13200;Centro educativo
2023;02;11800;Centro educativo
```

---

## ⚙️ 3. Sistemas IT y OT: dos mundos que se conectan

### 3.1. IT (Information Technology)

Engloba toda la **infraestructura digital** que gestiona la información en formato electrónico:
- **Servidores, bases de datos, redes y almacenamiento**.  
- **Software de gestión** (ERP, CRM, LMS, sistemas contables).  
- **Aplicaciones web o móviles** para procesar datos.

💡 *Ejemplo:*  
El sistema IT del centro podría incluir una base de datos MySQL con el consumo mensual de electricidad, accesible desde una aplicación web que muestra gráficos comparativos.

### 3.2. OT (Operational Technology)

Hace referencia a los **sistemas que controlan procesos físicos** o industriales.  
Incluye sensores, actuadores, autómatas y sistemas SCADA que recogen información del entorno físico y ejecutan acciones.

💡 *Ejemplo:*  
Un sensor IoT conectado a una Raspberry Pi mide la temperatura de un aula y regula automáticamente el encendido del aire acondicionado.  
Ese dato se almacena en la red (sistema IT) y se puede visualizar en un dashboard energético.

### 3.3. Convergencia IT/OT

En entornos modernos (industria 4.0 o centros inteligentes), ambos sistemas están interconectados.  

```
[Sensor IoT / OT] → [Red / API REST] → [Servidor / IT] → [Base de datos SQL] → [Dashboard / Usuario]
```

Esto permite pasar de la observación manual a la **automatización basada en datos**, donde las decisiones se apoyan en métricas en tiempo real.

---

## 🔄 4. Flujo de información digital

Comprender el ciclo completo del dato ayuda a diseñar sistemas de análisis sostenibles y eficientes.  
El flujo típico incluye cinco fases:

| Fase | Descripción | Ejemplo |
|------|--------------|----------|
| **1. Captura** | Recolección de datos por sensores, encuestas o importaciones. | Un sensor mide el consumo eléctrico del aula. |
| **2. Transmisión** | Envío de los datos al servidor mediante red local, WiFi o API. | MQTT, HTTP, WebSocket. |
| **3. Almacenamiento** | Registro en una base de datos o en la nube. | MySQL, PostgreSQL, Google Cloud SQL. |
| **4. Procesamiento** | Limpieza, validación y agregación de datos. | Script Python que elimina duplicados y normaliza unidades (kWh → MWh). |
| **5. Visualización y decisión** | Presentación de resultados para la toma de decisiones. | Power BI o Tableau muestra tendencias de consumo. |

💡 *Ejemplo integrado:*  
Un sistema de monitorización energética recoge datos cada minuto (OT), los almacena en una base de datos SQL (IT) y genera un dashboard que muestra el consumo por aula.

---

## 🌐 5. Revisión de portales de datos abiertos

Los **datos abiertos** (*open data*) son conjuntos de información publicados por organismos públicos o privados bajo licencias que permiten su uso, redistribución y análisis libremente.

| Portal | Descripción | Ejemplo de dataset |
|--------|--------------|--------------------|
| **[datos.gob.es](https://datos.gob.es)** | Catálogo nacional de datos abiertos. Integra datos de ayuntamientos, ministerios y CCAA. | Consumo eléctrico de edificios públicos, movilidad urbana, residuos. |
| **[Kaggle](https://www.kaggle.com)** | Comunidad global de ciencia de datos. Ofrece datasets y competiciones. | “Global Energy Consumption”, “CO₂ Emissions by Country”. |
| **[Our World in Data](https://ourworldindata.org)** | Repositorio internacional con visualizaciones basadas en investigación científica. | Energías renovables, igualdad de género, emisiones de gases. |
| **[INE](https://www.ine.es)** | Instituto Nacional de Estadística. | Datos demográficos, transporte, empleo y medio ambiente. |
| **[AEMET OpenData](https://opendata.aemet.es)** | API meteorológica oficial de España. | Precipitaciones, radiación solar, temperaturas medias. |
| **[Eurostat](https://ec.europa.eu/eurostat)** | Oficina estadística de la Unión Europea. | Indicadores de sostenibilidad y energía. |

---

## 🧮 6. Criterios técnicos de evaluación de fuentes de datos

| Criterio | Descripción técnica | Buen ejemplo |
|-----------|--------------------|---------------|
| **Exactitud** | Grado en que los datos reflejan la realidad. | Sensor calibrado con desviación < 1 %. |
| **Integridad** | Ausencia de datos faltantes o inconsistentes. | Dataset completo de todos los meses del año. |
| **Consistencia** | Homogeneidad de formatos y unidades. | Todas las fechas en formato ISO 8601. |
| **Actualización** | Frecuencia con que se renuevan los datos. | API con registros diarios o en tiempo real. |
| **Trazabilidad** | Posibilidad de conocer el origen y el proceso de obtención. | Dataset firmado por el INE o AEMET. |
| **Accesibilidad** | Facilidad para descargar o consultar los datos. | CSV accesible mediante URL o API REST. |

---

## 🧭 7. Ejemplo completo de integración de fuentes

**Escenario:** análisis del consumo energético del instituto.  

1. **Fuente interna (IT):** consumo mensual registrado por el sistema eléctrico del edificio en una hoja CSV.  
2. **Fuente externa (API AEMET):** datos meteorológicos diarios (temperatura y radiación solar).  
3. **Proceso:** un script Python extrae los datos de la API, los transforma (ETL) y los fusiona con los del centro.  
4. **Almacenamiento:** se guarda todo en una base de datos relacional MySQL con tablas `consumo`, `clima` y `aulas`.  
5. **Visualización:** Power BI genera un panel que muestra la correlación entre temperatura exterior y consumo energético.

**Resultado:** el análisis revela que los días con temperaturas > 30 °C aumentan el consumo un 22 %.  
Con esa información se propone ajustar el horario de climatización y mejorar la eficiencia.

---

## 🧩 8. Conclusión

Conocer y evaluar las **fuentes de datos** y los **sistemas IT/OT** permite desarrollar proyectos de digitalización y sostenibilidad basados en evidencia.  
Un dato bien capturado, documentado y analizado se convierte en una **herramienta de decisión**, capaz de optimizar recursos, reducir el impacto ambiental y fomentar una gestión inteligente tanto en empresas como en instituciones educativas.
