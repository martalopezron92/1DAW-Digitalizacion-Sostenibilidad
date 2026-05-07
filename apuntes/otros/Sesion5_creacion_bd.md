# 💾 Sesión 5 – Creación de la base de datos

---

## 🧩 1. Introducción: del modelo lógico al físico

En la sesión anterior habéis diseñado el **modelo entidad-relación (ER)**, donde se definían **entidades**, **atributos**, **relaciones** y **cardinalidades**.  
Ese modelo representa la estructura **lógica** de los datos.

El objetivo de esta sesión es **convertir ese modelo lógico en una base de datos real**, almacenada en un **Sistema Gestor de Bases de Datos (SGBD)** como **MySQL** o **PostgreSQL**.  

> 🔍 *En esta fase pasamos del “diseño conceptual” (modelo ER) al “modelo físico” (tablas, tipos de datos y relaciones reales).*  

---

## ⚙️ 2. ¿Qué es un Sistema Gestor de Bases de Datos (SGBD)?

Un **SGBD** es un software que permite **crear, administrar y mantener** bases de datos relacionales.  
Su objetivo es almacenar información de forma **segura, consistente y accesible**.

### Ejemplos de SGBD
- **MySQL** → muy usado en aplicaciones web y sistemas LAMP (Linux, Apache, MySQL, PHP).
- **PostgreSQL** → destaca por su potencia, seguridad y soporte de tipos avanzados (JSON, arrays, geodatos).
- **SQLite** → ligero, sin servidor, ideal para pruebas locales.
- **Oracle / SQL Server** → comerciales, utilizados en grandes empresas.

### Ventajas frente a ficheros tradicionales
- Integridad de los datos (sin duplicados ni incoherencias).
- Control de acceso por usuarios y permisos.
- Mecanismos de copia de seguridad y recuperación.
- Optimización de consultas mediante índices.

---

## 🧱 3. Instalación y configuración básica

### 🔹 MySQL

#### Instalación
- **Windows:** descargar desde https://dev.mysql.com/downloads/  
  Seleccionar *MySQL Server* y *MySQL Workbench*.
- **Linux (Debian/Ubuntu):**
  ```bash
  sudo apt update
  sudo apt install mysql-server
  ```

#### Comandos esenciales
Iniciar y comprobar el servicio:
```bash
sudo systemctl start mysql
sudo systemctl status mysql
```

Acceso al cliente:
```bash
mysql -u root -p
```

Crear una base de datos y usuario:
```sql
CREATE DATABASE sostenibilidad;
CREATE USER 'alumno'@'localhost' IDENTIFIED BY '1234';
GRANT ALL PRIVILEGES ON sostenibilidad.* TO 'alumno'@'localhost';
FLUSH PRIVILEGES;
```

---

### 🔹 PostgreSQL

#### Instalación
```bash
sudo apt install postgresql postgresql-contrib
```

Acceso:
```bash
sudo -u postgres psql
```

Crear base de datos y usuario:
```sql
CREATE DATABASE sostenibilidad;
CREATE USER alumno WITH ENCRYPTED PASSWORD '1234';
GRANT ALL PRIVILEGES ON DATABASE sostenibilidad TO alumno;
```

Para acceder:
```bash
psql -U alumno -d sostenibilidad
```

> 💡 PostgreSQL utiliza el comando `\l` para listar bases de datos y `\dt` para listar tablas.

---

## 📐 4. Tipos de datos en SQL

La elección correcta del tipo de dato es clave para la eficiencia y la integridad de la base.

| Tipo de dato | Descripción | Ejemplo |
|---------------|--------------|----------|
| `INT` | Números enteros | `edad INT` |
| `DECIMAL(p,s)` | Números con decimales (p: total dígitos, s: decimales) | `precio DECIMAL(6,2)` |
| `FLOAT / DOUBLE` | Números reales de precisión variable | `temperatura FLOAT` |
| `VARCHAR(n)` | Texto de longitud variable | `nombre VARCHAR(50)` |
| `CHAR(n)` | Texto de longitud fija | `codigo CHAR(3)` |
| `TEXT` | Texto largo | `observaciones TEXT` |
| `DATE` | Fecha (AAAA-MM-DD) | `fecha_nac DATE` |
| `TIME` | Hora | `hora TIME` |
| `BOOLEAN` | Verdadero o falso | `activo BOOLEAN` |

### 🧮 Ejemplo práctico
```sql
CREATE TABLE alumno (
  id INT PRIMARY KEY,
  nombre VARCHAR(50) NOT NULL,
  edad INT CHECK (edad >= 0),
  fecha_alta DATE DEFAULT (CURRENT_DATE)
);
```

> ⚠️ **Error común:** usar `VARCHAR(255)` para todo. Esto desperdicia espacio y afecta al rendimiento.

---

## 🔒 5. Restricciones (Constraints)

Las **restricciones** definen reglas para mantener la coherencia e integridad de los datos.

| Restricción | Función | Ejemplo |
|--------------|----------|----------|
| `PRIMARY KEY` | Identifica de forma única cada fila | `id INT PRIMARY KEY` |
| `FOREIGN KEY` | Enlaza con otra tabla | `FOREIGN KEY (id_aula) REFERENCES aula(id)` |
| `NOT NULL` | Evita valores vacíos | `nombre VARCHAR(50) NOT NULL` |
| `UNIQUE` | Impide duplicados | `email VARCHAR(100) UNIQUE` |
| `CHECK` | Impone condiciones | `CHECK (consumo >= 0)` |
| `DEFAULT` | Valor asignado automáticamente | `activo BOOLEAN DEFAULT TRUE` |

### 🔧 Ejemplo real:
```sql
CREATE TABLE aula (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nombre VARCHAR(50) NOT NULL,
  superficie DECIMAL(5,2) CHECK (superficie > 0)
);

CREATE TABLE consumo (
  id INT PRIMARY KEY AUTO_INCREMENT,
  id_aula INT,
  energia DECIMAL(8,2) CHECK (energia >= 0),
  fecha DATE DEFAULT (CURRENT_DATE),
  FOREIGN KEY (id_aula) REFERENCES aula(id)
);
```

> 🧠 Las **claves foráneas** aseguran la integridad referencial: no puede haber un consumo asociado a un aula que no exista.

---

## 🗂️ 6. Creación de tablas desde el modelo ER

Una **tabla** representa una **entidad**.  
Cada **fila (row)** representa un registro y cada **columna (column)** representa un **atributo**.

### 🔹 Pasos de transformación ER → SQL
1. Identifica las entidades del modelo (p. ej. *Aula*, *Consumo*, *Sensor*).  
2. Asigna una clave primaria a cada entidad.  
3. Crea relaciones mediante claves foráneas.  
4. Define los tipos de datos y restricciones.  
5. Ejecuta el script SQL y verifica.

### 🔹 Ejemplo de modelo ER: consumo energético del centro
```
AULA (1) -------- (N) CONSUMO -------- (1) SENSOR
```

Script SQL:
```sql
CREATE TABLE aula (
  id_aula SERIAL PRIMARY KEY,
  nombre VARCHAR(50) NOT NULL,
  planta INT,
  superficie DECIMAL(6,2)
);

CREATE TABLE sensor (
  id_sensor SERIAL PRIMARY KEY,
  tipo VARCHAR(20),
  ubicacion VARCHAR(50)
);

CREATE TABLE consumo (
  id_consumo SERIAL PRIMARY KEY,
  id_aula INT REFERENCES aula(id_aula),
  id_sensor INT REFERENCES sensor(id_sensor),
  fecha DATE NOT NULL,
  energia_kwh DECIMAL(8,2) CHECK (energia_kwh >= 0),
  fuente VARCHAR(20) CHECK (fuente IN ('solar','eléctrica','mixta'))
);
```

### 🔹 Inserción de datos de ejemplo
```sql
INSERT INTO aula (nombre, planta, superficie) VALUES ('Aula 101', 1, 42.5);
INSERT INTO sensor (tipo, ubicacion) VALUES ('Medidor eléctrico', 'Aula 101');
INSERT INTO consumo (id_aula, id_sensor, fecha, energia_kwh, fuente)
VALUES (1, 1, '2025-10-24', 125.5, 'eléctrica');
```

---

## 🧰 7. Gestión básica de datos

Una vez creadas las tablas, podemos manipular la información mediante **sentencias SQL DML (Data Manipulation Language)**.

### 🔹 Insertar registros
```sql
INSERT INTO aula (nombre, planta, superficie)
VALUES ('Laboratorio TIC', 2, 60.2);
```

### 🔹 Consultar datos
```sql
SELECT * FROM consumo WHERE energia_kwh > 100;
```

### 🔹 Actualizar datos
```sql
UPDATE aula SET superficie = 45.5 WHERE id_aula = 1;
```

### 🔹 Eliminar datos
```sql
DELETE FROM consumo WHERE id_consumo = 3;
```

> ⚠️ Usa `DELETE` con cuidado. Siempre comprueba antes con un `SELECT`.

---

## 🧾 8. Buenas prácticas de diseño

1. **Usa nombres coherentes y descriptivos** (en minúsculas y con guiones bajos).  
   Ejemplo: `consumo_agua`, `id_aula`, `fecha_registro`.
2. **Normaliza la base de datos**: evita repetir información en varias tablas.  
   (1ª, 2ª y 3ª forma normal → sin duplicados, dependencias completas y no transitivas).
3. **Usa claves primarias simples** siempre que sea posible (numéricas y autoincrementales).
4. **Incluye comentarios** en el código:
   ```sql
   COMMENT ON TABLE consumo IS 'Registra el consumo energético por aula y fecha';
   ```
5. **Planifica copias de seguridad periódicas:**
   - MySQL:
     ```bash
     mysqldump -u root -p sostenibilidad > backup.sql
     ```
   - PostgreSQL:
     ```bash
     pg_dump sostenibilidad > backup.sql
     ```
6. **Usa el principio de mínimos privilegios:**  
   Crea un usuario con permisos limitados para las operaciones de lectura o inserción.

---

## 🧪 9. Errores frecuentes y cómo evitarlos

| Error | Causa | Solución |
|--------|--------|-----------|
| “Error 1452: Cannot add or update a child row” | Inserción con clave foránea inexistente | Asegúrate de insertar primero la tabla padre |
| “Duplicate entry for key PRIMARY” | Duplicas un valor único | Usa `AUTO_INCREMENT` o `SERIAL` |
| “Unknown column” | Error en el nombre del campo | Verifica el esquema con `DESCRIBE tabla;` |
| “Access denied” | Usuario sin permisos suficientes | Concede privilegios con `GRANT` |
| Tipos incompatibles | Intentas unir `VARCHAR` con `INT` | Revisa los tipos de datos y haz *casts* si es necesario |

---

## 🧩 10. Resumen del flujo de trabajo

1. Diseña el **modelo ER** (entidades, atributos, relaciones).  
2. Crea la **base de datos** en MySQL o PostgreSQL.  
3. Define **tablas**, **claves** y **restricciones**.  
4. Inserta datos de prueba.  
5. Verifica mediante consultas `SELECT`.  
6. Documenta la estructura y guarda el script SQL.
