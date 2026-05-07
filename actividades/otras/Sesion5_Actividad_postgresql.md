# 🧪 Sesión 5 – Actividad práctica: Creación de la base de datos en PostgreSQL

---

## 🎯 Objetivos de la sesión

- Implementar el modelo entidad–relación diseñado en la sesión anterior dentro de un **SGBD PostgreSQL**.  
- Comprender la correspondencia entre **entidades y tablas**, y entre **relaciones y claves foráneas**.  
- Aplicar tipos de datos, restricciones y buenas prácticas de integridad.  
- Verificar la correcta creación, inserción y consulta de datos.  
- Preparar el entorno de trabajo para el análisis de datos del siguiente módulo.

---

## 📋 Descripción general de la actividad

Cada grupo creará una **base de datos PostgreSQL** a partir de su **modelo ER** del proyecto “Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible”.  
La base deberá contener todas las entidades, atributos y relaciones identificadas (mínimo tres entidades y una relación N:M o 1:N).

El objetivo final es tener una base funcional que permita almacenar los datos reales o abiertos que se analizarán en el segundo trimestre.

---

## 🧭 Pasos guiados

### 🔹 Paso 1. Crear la base de datos y el usuario
1. Accede al terminal y entra en PostgreSQL:
   ```bash
   sudo -u postgres psql
   ```
2. Crea la base de datos y el usuario de trabajo:
   ```sql
   CREATE DATABASE sostenibilidad;
   CREATE USER alumno WITH ENCRYPTED PASSWORD '1234';
   GRANT ALL PRIVILEGES ON DATABASE sostenibilidad TO alumno;
   ```
3. Conéctate a la base de datos:
   ```bash
   psql -U alumno -d sostenibilidad
   ```

---

### 🔹 Paso 2. Crear las tablas del modelo ER

1. Analiza tu modelo ER y tradúcelo a SQL.  
2. Usa tipos de datos adecuados (`INT`, `DECIMAL`, `VARCHAR`, `DATE`, `BOOLEAN`, etc.).  
3. Define claves primarias y foráneas, restricciones y valores por defecto.  

#### 🧱 Ejemplo de estructura base
```sql
CREATE TABLE aula (
  id_aula SERIAL PRIMARY KEY,
  nombre VARCHAR(50) NOT NULL,
  planta INT,
  superficie DECIMAL(6,2) CHECK (superficie > 0)
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

> 💡 **Consejo:** empieza por las tablas independientes (sin relaciones) y continúa con las que dependen de otras.

---

### 🔹 Paso 3. Insertar datos de prueba

Crea un conjunto de datos pequeño (mínimo 3 registros por tabla) para comprobar la integridad.

```sql
INSERT INTO aula (nombre, planta, superficie) VALUES
('Aula 101', 1, 42.5),
('Laboratorio TIC', 2, 60.2),
('Biblioteca', 0, 85.7);

INSERT INTO sensor (tipo, ubicacion) VALUES
('Medidor eléctrico', 'Aula 101'),
('Sensor térmico', 'Laboratorio TIC');

INSERT INTO consumo (id_aula, id_sensor, fecha, energia_kwh, fuente) VALUES
(1, 1, '2025-10-24', 125.5, 'eléctrica'),
(2, 2, '2025-10-24', 80.3, 'mixta');
```

> ✅ Comprueba que las inserciones no devuelvan errores y que las claves foráneas funcionen correctamente.

---

### 🔹 Paso 4. Consultas de verificación

Ejecuta las siguientes consultas para validar tu base:

```sql
-- Ver todos los consumos con nombre del aula
SELECT c.id_consumo, a.nombre, c.energia_kwh, c.fuente, c.fecha
FROM consumo c
JOIN aula a ON c.id_aula = a.id_aula;

-- Contar registros en cada tabla
SELECT COUNT(*) FROM aula;
SELECT COUNT(*) FROM consumo;
```

> 🔍 Si las consultas devuelven resultados correctos, tu estructura y relaciones están bien definidas.

---

### 🔹 Paso 5. Documentar y guardar

1. Usa el comando `\dt` para listar las tablas y confirmar su existencia.  
2. Exporta tu script SQL a un archivo de entrega:
   ```bash
   \i script_creacion.sql
   ```
3. Añade un comentario al inicio del archivo con:
   - Nombre del grupo  
   - Fecha  
   - Breve descripción del modelo

---

## 🧩 Entrega y comprobaciones

Cada grupo entregará:

1. Archivo `script_creacion.sql` con las sentencias completas de creación e inserción.  
2. Captura o exportación del resultado de las consultas de verificación.  
3. Archivo `.pdf` o `.md` con un esquema visual del modelo ER (opcional).

---

## 🧠 Criterios e instrumentos de evaluación

### 🔹 Criterios de evaluación (DIG-RA3)

| Indicador | Descripción | Nivel alto | Nivel medio | Nivel básico |
|------------|--------------|-------------|--------------|--------------|
| Diseño estructurado | Las tablas y relaciones reflejan fielmente el modelo ER |  |  |  |
| Tipos y restricciones | Uso correcto de tipos de datos y constraints |  |  |  |
| Integridad referencial | Relaciones correctamente implementadas con claves foráneas |  |  |  |
| Funcionamiento del script | El script se ejecuta sin errores y crea la base completa |  |  |  |
| Presentación y documentación | Código limpio, comentado y entregado correctamente |  |  |  |

### 🔹 Instrumentos de evaluación

- **Rúbrica práctica:** revisión técnica del script SQL.  
- **Checklist de validación:** ejecución de pruebas en PostgreSQL (`SELECT`, `JOIN`, `\dt`).  
- **Autoevaluación del grupo:** breve reflexión final sobre dificultades y soluciones.

---

## 🧾 Resultado esperado

Al finalizar la sesión, cada grupo dispondrá de una base de datos PostgreSQL totalmente operativa y coherente con su modelo entidad–relación, lista para importar datos reales o abiertos en la siguiente fase del proyecto.
