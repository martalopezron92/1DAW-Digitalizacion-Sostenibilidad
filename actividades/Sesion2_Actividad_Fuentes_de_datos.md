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
   - Breve descripción de cómo se podrían importar los datos a una base de datos (ej. con `pandas`, `requests`, `LOAD DATA` en SQL…).

---

## 🧩 Parte 4. Entrega y evaluación

- **Formato de entrega:**  
  Archivo digital (`.md`, `.docx` o `.pdf`) subido al aula virtual.  
  Incluid los enlaces a todas las fuentes consultadas.

- **Evaluación (lista de cotejo):**

| Criterio | Nivel alto | Nivel medio | Nivel bajo |
|-----------|-------------|--------------|-------------|
| Pertinencia de las fuentes seleccionadas | Las fuentes se relacionan directamente con el ámbito y el proyecto. | Algunas fuentes son relevantes. | Las fuentes no están relacionadas con el tema. |
| Fiabilidad y actualidad | Todas las fuentes son oficiales o verificadas, actualizadas. | La mayoría son fiables. | Varias fuentes son poco fiables o desactualizadas. |
| Diversidad de fuentes | Incluye internas y externas, de distinto tipo (portal, API, dataset). | Incluye 2 tipos. | Solo un tipo o repetidas. |
| Claridad y estructura del informe | Presentación ordenada y completa con tablas y justificación. | Presentación aceptable pero mejorable. | Desorganización o falta de justificación. |

---

## 💬 Reflexión final

> ¿Qué es más valioso en un proyecto de sostenibilidad: tener muchos datos o tener pocos datos pero bien estructurados y fiables?
