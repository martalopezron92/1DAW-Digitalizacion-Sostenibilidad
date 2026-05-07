# 📘 Sesión 6 – Carga inicial de datos
**Proyecto:** Digitalización + Sostenibilidad – “Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible”  
**Objetivo de la sesión:** Aprender a importar datos desde fuentes externas (CSV), verificar su calidad y realizar una limpieza básica antes del análisis.

---

## 🧩 1. Importación de datos desde archivos CSV

### 1.1. ¿Qué es un archivo CSV?
Un **CSV (Comma Separated Values)** es un formato de texto plano donde los datos se almacenan en filas y columnas separadas por un delimitador (coma, punto y coma o tabulador).  
Se utiliza ampliamente por su **compatibilidad** con hojas de cálculo, bases de datos y herramientas de análisis.

Ejemplo de archivo `consumo_energia.csv`:
```csv
id,mes,consumo_kwh,fuente
1,Enero,1250,Red eléctrica
2,Febrero,1180,Red eléctrica
3,Marzo,980,Paneles solares
```

### 1.2. Preparación previa de la base de datos
Antes de importar, debemos tener creada la tabla correspondiente en PostgreSQL.  
Ejemplo:
```sql
CREATE TABLE consumo_energia (
    id SERIAL PRIMARY KEY,
    mes VARCHAR(20),
    consumo_kwh NUMERIC(10,2),
    fuente VARCHAR(50)
);
```

### 1.3. Métodos de importación en PostgreSQL

#### a) Comando `\copy` desde la consola `psql`
Permite importar archivos CSV desde el cliente:
```sql
\copy consumo_energia(mes, consumo_kwh, fuente)
FROM 'C:\datos\consumo_energia.csv'
DELIMITER ','
CSV HEADER;
```
- `DELIMITER` define el separador.  
- `CSV HEADER` indica que la primera fila contiene los nombres de las columnas.  
- No requiere permisos de superusuario (a diferencia de `COPY`).  

#### b) Comando SQL `COPY` (requiere permisos de superusuario)
```sql
COPY consumo_energia(mes, consumo_kwh, fuente)
FROM '/var/lib/postgresql/datos/consumo_energia.csv'
DELIMITER ','
CSV HEADER;
```

#### c) Importación mediante herramienta gráfica (PgAdmin / DBeaver)
1. Clic derecho sobre la tabla → *Import/Export Data*.  
2. Seleccionar el archivo CSV.  
3. Configurar delimitador y cabecera.  
4. Ejecutar y revisar el resumen de importación.  

---

## 🔎 2. Control de calidad de los datos

Una vez importados los datos, se debe garantizar su **fiabilidad** antes de analizarlos.  
El control de calidad incluye:

| Verificación | Descripción | Ejemplo de comprobación |
|---------------|-------------|--------------------------|
| **Estructura** | Coincidencia entre columnas del CSV y la tabla | Comprobar número y nombre de columnas |
| **Codificación** | Evitar errores de acentos o símbolos | `SHOW client_encoding;` |
| **Delimitador** | Confirmar separador (`,` o `;`) | Abrir CSV en un editor de texto |
| **Cabecera** | Verificar nombres coherentes | Evitar espacios o caracteres especiales |
| **Tipos de datos** | Ajustar tipos según contenido | `edad` → INTEGER, `fecha` → DATE |

Ejemplo en Python para previsualizar:
```python
import pandas as pd

df = pd.read_csv("consumo_energia.csv")
print(df.info())
print(df.head())
```
Esto ayuda a detectar errores de formato o celdas vacías antes de la carga en PostgreSQL.

---

## 🧽 3. Limpieza básica de datos

Una vez los datos están en la base de datos, se aplican tareas de limpieza para asegurar su coherencia y consistencia.

### 3.1. Revisión y corrección de tipos de datos
A veces los datos importados como texto (`TEXT`) deben convertirse a su tipo real:
```sql
ALTER TABLE consumo_energia
ALTER COLUMN consumo_kwh TYPE NUMERIC
USING consumo_kwh::NUMERIC;
```

### 3.2. Detección y eliminación de duplicados
```sql
SELECT mes, COUNT(*) 
FROM consumo_energia
GROUP BY mes
HAVING COUNT(*) > 1;
```
Eliminación de registros duplicados:
```sql
DELETE FROM consumo_energia a
USING consumo_energia b
WHERE a.ctid < b.ctid
AND a.mes = b.mes
AND a.consumo_kwh = b.consumo_kwh;
```

### 3.3. Gestión de valores nulos
Verificar columnas con valores nulos:
```sql
SELECT * FROM consumo_energia WHERE consumo_kwh IS NULL;
```
Asignar valores por defecto o calcular promedios:
```sql
UPDATE consumo_energia
SET consumo_kwh = (SELECT AVG(consumo_kwh) FROM consumo_energia)
WHERE consumo_kwh IS NULL;
```

### 3.4. Normalización de texto
Estandarizar el formato de campos como nombres o fuentes de energía:
```sql
UPDATE consumo_energia
SET fuente = INITCAP(TRIM(fuente));
```
👉 `INITCAP` pone en mayúscula la primera letra, `TRIM` elimina espacios innecesarios.

---

## 🧮 4. Verificación mediante consultas SELECT

Para confirmar que la carga de datos fue exitosa:

- **Contar registros:**
  ```sql
  SELECT COUNT(*) FROM consumo_energia;
  ```

- **Verificar rangos de valores:**
  ```sql
  SELECT MIN(consumo_kwh), MAX(consumo_kwh) FROM consumo_energia;
  ```

- **Validar coherencia de categorías:**
  ```sql
  SELECT DISTINCT fuente FROM consumo_energia;
  ```

- **Revisar posibles errores:**
  ```sql
  SELECT * FROM consumo_energia WHERE consumo_kwh <= 0;
  ```

- **Comprobación global:**
  ```sql
  SELECT fuente, AVG(consumo_kwh) AS promedio
  FROM consumo_energia
  GROUP BY fuente;
  ```

Estas verificaciones permiten confirmar que la información importada es coherente, útil y lista para su análisis.

---

## ⚙️ 5. Buenas prácticas de carga y validación

1. **Usar transacciones**:
   ```sql
   BEGIN;
   COPY consumo_energia FROM 'ruta.csv' DELIMITER ',' CSV HEADER;
   COMMIT;
   ```
   Si ocurre un error, se puede revertir con `ROLLBACK`.

2. **Documentar cada carga**: origen del dataset, fecha, número de registros.

3. **Mantener una copia del CSV original** para auditoría o replicación.

4. **Automatizar validaciones** con scripts SQL o Python.

5. **Revisar logs** en PgAdmin o terminal para detectar advertencias durante la importación.

6. **Controlar permisos de escritura**: solo usuarios con rol adecuado deberían poder hacer inserciones masivas.

---

## ✅ Conclusión

La carga inicial de datos es un paso crítico en cualquier proyecto de digitalización.  
Garantizar la **calidad, integridad y coherencia** desde el principio evita errores en fases posteriores de análisis y visualización.  
En el contexto del proyecto “Nuestro Instituto frente al Mundo”, estos datos serán la base para los **indicadores sostenibles** del centro o del sector analizado (energía, residuos, movilidad, etc.).
