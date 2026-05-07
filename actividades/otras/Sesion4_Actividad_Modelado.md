# 🧩 Actividad Sesión 4 – Modelado inicial del ámbito de análisis

## 🎯 Objetivo de la actividad
Diseñar el **modelo entidad-relación (ER)** que represente la información necesaria para analizar los datos del ámbito elegido por el grupo (energía, residuos, movilidad, uso de TIC, igualdad, etc.), de forma que sirva como **base estructural** para la creación posterior de la base de datos relacional.

El objetivo es **identificar las entidades, atributos, relaciones y claves** que permitirán almacenar y analizar los datos de manera lógica, coherente y sin redundancias.

---

## 📘 Contexto
En las sesiones anteriores habéis definido el ámbito del proyecto, identificado fuentes de datos (internas o abiertas) y aprendido los fundamentos del RGPD.  
Ahora vais a **modelar la información**, es decir, representar cómo se organiza la realidad en forma de tablas relacionadas. Este paso es esencial antes de implementar cualquier base de datos.

El trabajo de esta sesión se centrará en **crear el primer diseño técnico del modelo de datos** mediante un **Diagrama Entidad–Relación (ER)** y un **listado de tablas**.

---

## 🧠 Tareas a realizar

### **1. Análisis del ámbito elegido**
Cada grupo debe:
- Revisar los indicadores que va a analizar (por ejemplo, consumo eléctrico mensual, peso de residuos, número de desplazamientos, etc.).
- Determinar **qué información se necesita guardar** para esos indicadores.
- Identificar **qué actores o elementos intervienen** (por ejemplo: aulas, sensores, encuestas, contenedores, personas, vehículos, etc.).

📌 *Ejemplo:*  
Si el ámbito es **energía**, podrías necesitar registrar los edificios, las fuentes de energía, las fechas de medición y los consumos en kWh.

---

### **2. Identificación de entidades y atributos**
- Definir entre **3 y 6 entidades principales** (cada una representará una tabla).  
- Para cada entidad, listar sus **atributos** y definir su **tipo de dato** (texto, número, fecha, booleano, etc.).  
- Indicar cuál será la **clave primaria (PK)** de cada tabla.

📘 *Ejemplo parcial:*

| Entidad | Atributo | Tipo de dato | Descripción | PK |
|----------|-----------|---------------|--------------|----|
| Edificio | id_edificio | INT | Identificador único | ✅ |
| Edificio | nombre | VARCHAR(100) | Nombre del edificio | |
| Medición | id_medición | INT | Identificador único | ✅ |
| Medición | fecha | DATE | Fecha de la medición | |
| Medición | consumo_kwh | DECIMAL(8,2) | Consumo en kWh | |

---

### **3. Definición de relaciones**
- Analizar cómo se conectan las entidades entre sí.  
- Establecer la **cardinalidad** de cada relación:  
  - 1:1 → Uno a uno  
  - 1:N → Uno a muchos  
  - N:M → Muchos a muchos  
- Si hay relaciones N:M, crear una **tabla intermedia** que las resuelva.

📘 *Ejemplo:*  
Un *Edificio* tiene **muchas** *Mediciones* (1:N).  
Cada *Medición* pertenece a una sola *Fuente_energética* (N:1).

---

### **4. Creación del diagrama ER**
- Usar **draw.io**, **Lucidchart**, **DBDesigner**, o una herramienta similar.  
- Representar las entidades como rectángulos, los atributos dentro de ellas y las relaciones mediante rombos o conectores.  
- Añadir las cardinalidades en cada extremo (1, N, M).  
- El diagrama debe incluir al menos:
  - Todas las entidades identificadas.  
  - Sus atributos principales.  
  - Todas las relaciones y cardinalidades.  
  - Las claves primarias y foráneas.

📌 *Consejo:* nombra las relaciones con verbos (ej.: “tiene”, “registra”, “usa”, “responde”, “transporta”).

---

### **5. Documentación del modelo**
Cada grupo debe entregar:
1. 🗂️ **Diagrama ER final** exportado en formato `.png` o `.pdf`.  
2. 📄 **Documento descriptivo (.md o .docx)** que incluya:
   - Listado de entidades, atributos y tipos de dato.  
   - Descripción de cada relación y su cardinalidad.  
   - Justificación de las decisiones tomadas (por qué se eligieron esas entidades y relaciones).  
   - Posibles mejoras o ampliaciones futuras del modelo.

---

## 🧰 Herramientas recomendadas
- [draw.io (diagrams.net)](https://app.diagrams.net/)  
- [Lucidchart](https://www.lucidchart.com)  
- [DBDesigner.net](https://www.dbdesigner.net/)  
- [ERDPlus](https://erdplus.com/)  

---

## 📊 Ejemplo de resultado esperado

**Caso: Análisis del consumo energético**

**Entidades:**
- *Edificio(id_edificio, nombre, superficie_m2)*
- *Medición(id_medicion, fecha, consumo_kwh, id_edificio, id_fuente)*
- *Fuente_energética(id_fuente, tipo, renovable)*

**Relaciones:**
- Un *Edificio* **tiene muchas** *Mediciones* (1:N).  
- Cada *Medición* **usa una** *Fuente_energética* (N:1).

**Diagrama simplificado:**
```
[Edificio]───<realiza>───[Medicion]───<usa>───[Fuente_energetica]
   1               N                  1
```

---

## 🧾 Criterios de evaluación (DIG-RA3)
| Criterio | Descripción | Instrumento |
|-----------|--------------|--------------|
| **Precisión técnica** | El modelo refleja correctamente las entidades y relaciones del ámbito. | Rúbrica de diagrama ER |
| **Normalización** | No hay redundancia de datos ni errores de dependencia. | Revisión técnica |
| **Claridad visual** | El diagrama es legible, correctamente etiquetado y con cardinalidades visibles. | Rúbrica |
| **Coherencia del diseño** | El modelo permite analizar los indicadores definidos. | Observación y retroalimentación |
| **Justificación del modelo** | El grupo explica de forma razonada las decisiones de diseño. | Informe escrito |

---

## 📅 Entrega
- Fecha: **al final de la sesión o al inicio de la siguiente**.  
- Formato:  
  - Diagrama `.png` o `.pdf`  
  - Documento técnico `.md` o `.docx`  
  - Entrega en el aula virtual o carpeta compartida del grupo.  
