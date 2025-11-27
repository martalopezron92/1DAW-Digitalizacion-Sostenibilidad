# 📘 Sesión 4 – Introducción al modelado de datos

## 1. ¿Qué es una base de datos relacional?
Una **base de datos relacional (BDR)** es un sistema que permite **almacenar, organizar y consultar información estructurada** de forma eficiente.  
Su principio básico es que **los datos se guardan en tablas** (también llamadas **relaciones**) que pueden conectarse entre sí mediante **claves**.

Cada **tabla** representa una **entidad** del mundo real (por ejemplo, *Alumno*, *Encuesta*, *Consumo energético*), y cada **fila (tupla)** de la tabla representa una instancia concreta de esa entidad.

📊 **Ejemplo básico:**

**Tabla: Alumnos**
| id_alumno (PK) | nombre | curso | edad |
|----------------|--------|--------|------|
| 1 | Ana López | 1ºDAW | 18 |
| 2 | Luis Martín | 1ºDAW | 19 |

**Tabla: Encuestas**
| id_encuesta (PK) | fecha | id_alumno (FK) | puntuación |
|------------------|--------|----------------|-------------|
| 1 | 2025-10-24 | 1 | 4.5 |
| 2 | 2025-10-24 | 2 | 3.8 |

👉 Aquí, `id_alumno` en la tabla **Encuestas** es una **clave foránea (FK)** que hace referencia a la clave primaria (PK) de **Alumnos**.  
Esto permite establecer la relación:  
> “Cada encuesta pertenece a un alumno.”

---

## 2. Conceptos fundamentales del modelado relacional

El **modelado de datos** es la fase de diseño en la que definimos **qué información se guardará** y **cómo se relaciona**.  
Se suele representar mediante un **Diagrama Entidad–Relación (ER)**.

### 🔹 Entidades
Una **entidad** es un conjunto de objetos del mundo real sobre los que se desea almacenar información.

📌 Ejemplos:
- *Alumno*, *Profesor*, *Medición*, *Sensor*, *Contenedor de residuos*.
- En un proyecto sobre sostenibilidad: *Fuente de energía*, *Registro de consumo*, *Ubicación*, *Tipo de residuo*.

Cada entidad se convertirá en una **tabla** en la base de datos.

---

### 🔹 Atributos
Los **atributos** son las propiedades o características de una entidad.

Ejemplo:
- Entidad *Alumno*: `nombre`, `curso`, `edad`.
- Entidad *Sensor*: `modelo`, `ubicacion`, `fecha_instalacion`.

Cada atributo tiene un **tipo de dato** específico en SQL:

| Tipo de dato | Ejemplo de uso | Descripción |
|---------------|----------------|--------------|
| `INT` | `id_sensor` | Número entero |
| `VARCHAR(50)` | `nombre`, `curso` | Texto corto |
| `DATE` | `fecha` | Fecha |
| `DECIMAL(10,2)` | `consumo_kwh` | Número con decimales |
| `BOOLEAN` | `activo` | Verdadero o falso |

🔍 Ejemplo aplicado:  
Si diseñamos una tabla *Mediciones*, el campo `consumo_kwh` debería ser `DECIMAL(8,2)` para admitir valores como `125.73`.

---

### 🔹 Relaciones
Una **relación** describe cómo se vinculan las entidades.  
Se representan con **rombos** en los diagramas ER.

Tipos más comunes:

| Tipo | Descripción | Ejemplo |
|------|--------------|----------|
| 1:1 | Una instancia de A se asocia con una sola de B | Un *centro* tiene **un solo** *director* |
| 1:N | Una instancia de A se asocia con varias de B | Un *sensor* genera **muchas** *mediciones* |
| N:M | Varias instancias de A se asocian con varias de B | Un *alumno* participa en **muchos proyectos**, y cada *proyecto* tiene **muchos alumnos** |

En el caso N:M, se crea una **tabla intermedia** (también llamada tabla puente o de unión).

📘 **Ejemplo técnico:**

Tablas:
- `alumno(id_alumno, nombre)`
- `proyecto(id_proyecto, titulo)`
- `alumno_proyecto(id_alumno, id_proyecto, rol)`

La tabla `alumno_proyecto` define la relación **muchos a muchos** entre alumnos y proyectos.

---

### 🔹 Claves (Keys)
Las **claves** garantizan la integridad de los datos y definen cómo se relacionan las tablas.

| Tipo | Descripción | Ejemplo |
|------|--------------|----------|
| **Clave primaria (PK)** | Identifica de forma única una fila | `id_sensor` |
| **Clave foránea (FK)** | Conecta con la PK de otra tabla | `id_sensor` en *Mediciones* |
| **Clave candidata** | Atributo que podría ser PK | `dni` en *Alumnos* |
| **Clave compuesta** | Compuesta por varios campos | `(id_sensor, fecha)` |

🧩 **Ejemplo SQL:**
```sql
CREATE TABLE Mediciones (
    id_sensor INT,
    fecha DATE,
    consumo_kwh DECIMAL(8,2),
    PRIMARY KEY (id_sensor, fecha),
    FOREIGN KEY (id_sensor) REFERENCES Sensores(id_sensor)
);
```
Esta estructura impide duplicar mediciones del mismo sensor en la misma fecha.

---

## 3. Diagramas Entidad–Relación (ER)

Un **diagrama ER** es una representación gráfica del modelo de datos antes de crear la base de datos real.  
Permite verificar si el diseño tiene sentido y si todas las relaciones son correctas.

### 🔸 Símbolos principales

| Elemento | Representación | Ejemplo |
|-----------|----------------|----------|
| Entidad | ▭ (rectángulo) | `Alumno` |
| Atributo | ⃝ (óvalo) | `nombre`, `edad` |
| Relación | ◆ (rombo) | `realiza`, `posee` |
| Cardinalidad | 1, N, M | 1:N entre *Sensor* y *Medición* |

---

### 🔸 Cardinalidades en detalle

1️⃣ **Uno a uno (1:1)**  
Cada registro de A se asocia a un solo registro de B.  
📍 Ejemplo: un *centro* tiene un *director*.  

2️⃣ **Uno a muchos (1:N)**  
Un registro de A puede relacionarse con varios de B.  
📍 Ejemplo: un *sensor* puede registrar muchas *mediciones*.

3️⃣ **Muchos a muchos (N:M)**  
Varios registros de A pueden estar vinculados con varios de B.  
📍 Ejemplo: un *alumno* puede responder muchas *encuestas* y cada *encuesta* puede tener respuestas de varios *alumnos*.

<!-- --- -->

<!-- ## 4. Normalización de datos

La **normalización** es el proceso de **organizar los datos para reducir redundancia** y mejorar la coherencia.

### Formas normales más utilizadas:

| Forma normal | Objetivo | Ejemplo |
|---------------|-----------|----------|
| **1FN** | Cada campo contiene un solo valor | ❌ `colores = 'rojo, azul'` → ✅ crear tabla `colores_producto` |
| **2FN** | Todos los atributos dependen de la PK completa | Evita dependencias parciales en claves compuestas |
| **3FN** | No hay dependencias transitivas | Si `id_profesor → nombre` y `nombre → email`, elimina `email` de la tabla principal |

📘 **Ejemplo aplicado:**
En lugar de guardar `nombre_profesor` dentro de *Asignaturas*, se crea una tabla *Profesores* y se usa una FK (`id_profesor`). -->

---

## 4. Ejemplo aplicado al proyecto sostenible

Supongamos que el grupo analiza el **consumo energético del centro**.

**Entidades identificadas:**
- `Edificio(id_edificio, nombre, superficie_m2)`
- `Medicion(id_medicion, fecha, consumo_kwh, id_edificio, id_fuente)`
- `Fuente_energetica(id_fuente, tipo, renovable)`

**Relaciones:**
- Un *Edificio* **tiene** muchas *Mediciones* (1:N)  
- Una *Medición* **usa** una *Fuente_energetica* (N:1)

**Diagrama simplificado:**
```
[Edificio]───<realiza>───[Medicion]───<usa>───[Fuente_energetica]
   1               N                  1
```

<!-- **Ejemplo de creación SQL:**
```sql
CREATE TABLE Edificio (
    id_edificio SERIAL PRIMARY KEY,
    nombre VARCHAR(100),
    superficie_m2 DECIMAL(10,2)
);

CREATE TABLE Fuente_energetica (
    id_fuente SERIAL PRIMARY KEY,
    tipo VARCHAR(50),
    renovable BOOLEAN
);

CREATE TABLE Medicion (
    id_medicion SERIAL PRIMARY KEY,
    fecha DATE,
    consumo_kwh DECIMAL(8,2),
    id_edificio INT REFERENCES Edificio(id_edificio),
    id_fuente INT REFERENCES Fuente_energetica(id_fuente)
);
``` -->

---

## 5. Buenas prácticas profesionales

✅ **Consistencia en los nombres**  
Usa minúsculas y guiones bajos (`snake_case`): `consumo_kwh`, `id_sensor`.

✅ **Evita la redundancia**  
Guarda los datos una sola vez y relaciónalos con claves.

✅ **Documenta el modelo**  
Cada grupo debe entregar su **diagrama ER**, las **tablas definidas con atributos y tipos de datos**, y las **relaciones entre ellas**.

✅ **Integridad referencial**  
Define siempre las claves foráneas para asegurar la coherencia entre tablas.

✅ **Usa herramientas de diseño**  
- **draw.io** → gratuito y visual.  
- **Lucidchart** o **DBDesigner** → ideal para diagramas profesionales.
