# 🧩 Actividad – Búsqueda y análisis de fuentes de datos sostenibles

## 🎯 Objetivo de la actividad
Identificar, seleccionar y comparar **fuentes de datos internas y externas** relacionadas con el ámbito de estudio elegido (energía, residuos, movilidad, TIC, etc.), evaluando su **fiabilidad, formato, actualización y aplicabilidad** al proyecto integrador.

---

## 🧠 Contexto

En esta sesión vais a comenzar a construir la **base de conocimiento de vuestro proyecto**.  
Antes de poder crear una base de datos o analizar nada, necesitáis saber **de dónde provendrán los datos**.  

Cada grupo deberá localizar y analizar **fuentes de datos internas** (del centro educativo o generadas por vosotros) y **fuentes externas** (portales abiertos, APIs, datasets públicos) que puedan ser útiles para vuestro estudio de sostenibilidad.

---

## 🧭 Parte 1. Análisis de fuentes internas

1. **Identificad qué información puede recogerse dentro del centro educativo** relacionada con vuestro ámbito.  
   Ejemplos:
   - Energía: consumo eléctrico mensual, número de equipos encendidos, horas de iluminación.  
   - Movilidad: medios de transporte utilizados por alumnado y profesorado.  
   - Residuos: papel reciclado, cantidad de envases o residuos generados por semana.  
   - TIC: uso de ordenadores, tiempo medio de conexión, consumo de datos.

2. **Describid cada posible fuente interna** en una tabla con los siguientes campos:

| Fuente interna | Tipo de dato | Formato posible | Frecuencia de registro | Acceso disponible (sí/no) |
|----------------|---------------|------------------|--------------------------|----------------------------|
| Medidor eléctrico del aula 1 | Energía (kWh) | CSV/Excel exportado del contador | Diario | Sí |
| Encuesta a alumnado sobre transporte | Movilidad | Formularios de Google (CSV) | Única vez | Sí |

3. **Analizad la viabilidad técnica** de obtener esos datos:
   - ¿Necesitaríais sensores, encuestas, hojas de cálculo, etc.?  
   - ¿Podéis automatizar la recogida o es manual?  
   - ¿Requiere permiso del centro o profesorado?

---

## 🌐 Parte 2. Búsqueda de fuentes externas

1. **Acceded a los principales portales de datos abiertos y buscad datasets relacionados** con vuestro ámbito:
   - [datos.gob.es](https://datos.gob.es)  
   - [Kaggle](https://www.kaggle.com)  
   - [Our World in Data](https://ourworldindata.org)  
   - [INE](https://www.ine.es)  
   - [AEMET Open Data](https://opendata.aemet.es)  
   - [Eurostat](https://ec.europa.eu/eurostat)

2. **Seleccionad al menos 3 datasets externos** y rellenad la siguiente tabla comparativa:

| Portal / Fuente | Título del dataset | Variables principales | Formato (CSV, JSON, etc.) | Última actualización | Licencia | Relevancia para el proyecto |
|-----------------|--------------------|------------------------|---------------------------|----------------------|-----------|-----------------------------|
| datos.gob.es | Consumo energético edificios públicos | Energía (kWh), fecha, tipo de edificio | CSV | 2023 | CC BY 4.0 | Muy alta |
| Our World in Data | CO₂ Emissions by Country | País, emisiones, año | CSV | 2024 | CC BY 4.0 | Media |
| AEMET OpenData | Radiación solar diaria | Fecha, radiación, provincia | JSON | 2025 | Uso libre | Alta |

3. **Comprobación de fiabilidad y pertinencia:**
   - ¿Proviene de un organismo oficial o de una fuente reconocida?  
   - ¿Los datos están actualizados y son accesibles?  
   - ¿Se pueden descargar sin registro o pago?  
   - ¿Están en un formato adecuado para importarlos a una base de datos (CSV, JSON, XLSX)?  

💡 *Consejo:* Guarda los enlaces exactos a los datasets y haz capturas de pantalla del portal y la licencia.

---

## 🧮 Parte 3. Elaboración del informe comparativo

1. **Cread un documento (Word, Markdown o PDF)** titulado:  
   👉 `Fuentes_de_datos_[nombre_del_grupo].md`  
2. En el documento, incluid:
   - Breve **descripción del ámbito de estudio** elegido.  
   - Tabla de **fuentes internas** con viabilidad técnica.  
   - Tabla de **fuentes externas** con su comparativa.  
   - Un **comentario final justificando** qué fuentes vais a utilizar finalmente en vuestro proyecto y por qué.  
3. Si alguna fuente se obtiene mediante API, añadid:
   - URL del endpoint.  
   - Ejemplo de respuesta JSON o CSV.  

---

## 🧩 Parte 4. Entrega y evaluación

- **Formato de entrega:**  
  Archivo digital (`.md`, `.docx` o `.pdf`) subido al aula virtual.  
  Incluid los enlaces a todas las fuentes consultadas.

---

## 🧾 **Criterios de evaluación**

Esta actividad trabaja los siguientes Resultados de Aprendizaje y Criterios de Evaluación:

### 📱 **Digitalización aplicada al sistema productivo**

**RA1**: Analiza el concepto de digitalización y su repercusión identificando entornos IT y OT.

| Criterio | Indicador de logro | Instrumento |
|:---------|:-------------------|:------------|
| **c)** Se han establecido diferencias y similitudes entre IT y OT | Identifica correctamente fuentes de datos de sistemas IT (bases de datos, aplicaciones) y OT (sensores, medidores físicos) | Tabla de fuentes internas |
| **d)** Se han identificado departamentos típicos que constituyen entornos IT | Reconoce sistemas de gestión del centro como fuentes de información digital | Análisis de viabilidad técnica |

**RA2**: Caracteriza las tecnologías habilitadoras digitales necesarias para la transformación digital.

| Criterio | Indicador de logro | Instrumento |
|:---------|:-------------------|:------------|
| **a)** Se han identificado las principales tecnologías habilitadoras digitales | Identifica tecnologías como APIs, IoT, portales de datos abiertos y su aplicación en la recogida de datos | Tabla de fuentes externas |
| **b)** Se han relacionado las THD con el desarrollo de productos y servicios | Comprende cómo las THD permiten acceder y procesar datos para generar conocimiento | Justificación final del informe |

**RA5**: Evalúa la importancia de los datos y su protección.

| Criterio | Indicador de logro | Instrumento |
|:---------|:-------------------|:------------|
| **a)** Se ha establecido la diferencia entre dato e información | Distingue entre datos brutos y la información procesada que pueden generar | Informe comparativo |
| **b)** Se ha descrito el ciclo de vida del dato | Identifica la fase de captura y origen de los datos en el ciclo completo | Análisis de fuentes internas |
| **i)** Se ha valorado la importancia de la seguridad y regulación en relación con los datos | Verifica licencias, permisos de acceso y normativa de uso de los datos seleccionados | Tabla comparativa (columna licencia) |

### 🌱 **Sostenibilidad aplicada al sistema productivo**

**RA2**: Caracteriza los retos ambientales y sociales y propone acciones para minimizarlos.

| Criterio | Indicador de logro | Instrumento |
|:---------|:-------------------|:------------|
| **b)** Se han relacionado los retos ambientales y sociales con el desarrollo de la actividad económica | Busca datos específicos relacionados con aspectos ASG del ámbito elegido | Selección y relevancia de fuentes |

**RA3**: Establece la aplicación de criterios de sostenibilidad en el desempeño profesional.

| Criterio | Indicador de logro | Instrumento |
|:---------|:-------------------|:------------|
| **c)** Se han identificado acciones necesarias para atender retos desde la actividad profesional | Selecciona fuentes de datos pertinentes que permitirán medir y actuar sobre problemas de sostenibilidad | Justificación de selección de fuentes |

### 📊 **Rúbrica de evaluación por niveles**

| Criterio | Nivel alto (9-10) | Nivel medio (6-8) | Nivel bajo (0-5) |
|-----------|-------------------|-------------------|------------------|
| **Pertinencia de las fuentes** | Las fuentes se relacionan directamente con el ámbito, aspectos ASG y los retos identificados | Algunas fuentes son relevantes pero faltan conexiones claras con ASG | Las fuentes no están relacionadas con el tema o aspectos sostenibles |
| **Fiabilidad y actualidad** | Todas las fuentes son oficiales/verificadas, actualizadas y con licencia clara | La mayoría son fiables pero algunas carecen de verificación o actualización | Varias fuentes son poco fiables, desactualizadas o sin licencia identificada |
| **Diversidad tecnológica** | Incluye fuentes IT y OT, internas y externas, de distinto tipo (portal, API, dataset, sensores) | Incluye 2-3 tipos diferentes de fuentes | Solo un tipo de fuente o todas similares |
| **Viabilidad técnica** | Analiza en detalle la viabilidad de acceso, formato, automatización y permisos necesarios | Analiza parcialmente la viabilidad técnica | No analiza la viabilidad o lo hace de forma superficial |
| **Claridad y estructura** | Presentación ordenada y completa con tablas detalladas, enlaces verificados y justificación sólida | Presentación aceptable pero mejorable en estructura o justificación | Desorganización, falta de justificación o documentación incompleta |

---

## 💬 Reflexión final

> ¿Qué es más valioso en un proyecto de sostenibilidad: tener muchos datos o tener pocos datos pero bien estructurados y fiables?
