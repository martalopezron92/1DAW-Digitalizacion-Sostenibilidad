# 🧠 Actividad – Carga inicial de datos

## 📝 Título
**Carga y verificación de los primeros datos del proyecto**

---

## 🎯 Objetivo de la actividad
Importar los primeros registros de datos obtenidos del centro o del sector elegido al sistema de gestión de bases de datos (PostgreSQL), asegurando la calidad, coherencia y validez de la información mediante comprobaciones y consultas SQL.

---

## ⚙️ Contexto
Hasta este punto, ya has:
- Diseñado el modelo entidad-relación del proyecto.
- Creado la base de datos con sus tablas.
- Definido los campos y relaciones.

Ahora es el momento de **incorporar los primeros datos reales** (del centro o de fuentes abiertas) para comenzar el análisis posterior.  
Estos datos pueden proceder de:
- Ficheros CSV generados por encuestas digitales.
- Registros descargados desde portales de datos abiertos.
- Estimaciones o mediciones locales del centro.

---

## 🧩 Tareas a realizar

### 1. Preparar el archivo CSV
- Asegúrate de que el archivo esté **codificado en UTF-8**.  
- Verifica que los nombres de las columnas coincidan con los definidos en tu tabla SQL.  
- Revisa el separador (coma o punto y coma) y que no haya campos vacíos innecesarios.  
- Guarda el archivo con un nombre representativo, por ejemplo:  
  `consumo_energia_centro.csv` o `residuos_sector.csv`.

---

### 2. Importar los datos al SGBD
Usa uno de los siguientes métodos según tu entorno:
- Comando `\copy` desde `psql`.
- Comando SQL `COPY` si tienes permisos de superusuario.
- Herramienta gráfica (PgAdmin, DBeaver, etc.).

Ejemplo de importación:
```sql
\copy consumo_energia(mes, consumo_kwh, fuente)
FROM 'C:\datos\consumo_energia_centro.csv'
DELIMITER ','
CSV HEADER;
```

💡 **Consejo:** realiza la carga dentro de una transacción (`BEGIN` / `COMMIT`) por si necesitas revertir los cambios.

---

### 3. Comprobación inicial de la importación
Ejecuta consultas para verificar que los datos se han cargado correctamente:
```sql
SELECT COUNT(*) FROM consumo_energia;
SELECT DISTINCT fuente FROM consumo_energia;
SELECT * FROM consumo_energia LIMIT 5;
```
Registra los resultados en tu documento de evidencias.

---

### 4. Limpieza y validación de los datos
Revisa la calidad de los registros mediante:

#### a) Tipos de datos
```sql
SELECT column_name, data_type 
FROM information_schema.columns
WHERE table_name = 'consumo_energia';
```

#### b) Duplicados
```sql
SELECT mes, COUNT(*) 
FROM consumo_energia
GROUP BY mes
HAVING COUNT(*) > 1;
```

#### c) Valores nulos
```sql
SELECT * FROM consumo_energia WHERE consumo_kwh IS NULL;
```

#### d) Coherencia
Verifica que los valores sean realistas:
```sql
SELECT * FROM consumo_energia WHERE consumo_kwh <= 0;
```
Corrige los errores detectados usando `UPDATE`, `DELETE` o `ALTER TABLE` según el caso.

---

### 5. Validación final
Crea un **checklist técnico** con los siguientes puntos marcados como “Correcto / Incorrecto”:
- [ ] Se ha importado el archivo CSV correctamente.  
- [ ] No hay errores de codificación ni delimitadores.  
- [ ] No existen registros duplicados.  
- [ ] No hay valores nulos en campos clave.  
- [ ] Los tipos de datos son correctos.  
- [ ] Se han verificado los datos con consultas SELECT.  

Entrega este checklist junto con tu script SQL o captura de las consultas realizadas.

---

## 📊 Resultado esperado
Al finalizar la sesión deberás tener:
- Una o varias tablas pobladas con los primeros registros del proyecto.  
- Los datos validados y limpios.  
- Un documento o script con las consultas usadas para verificar la carga.  

---

## 🧭 Evaluación
**Criterio:**  
DIG-RA3 — Organiza y verifica datos para análisis.  

**Instrumento:**  
Checklist técnico de validación de datos (entregado junto con el script SQL).  

**Valoración:**  
- ✅ Correcto: datos importados sin errores, verificación completa, coherencia comprobada.  
- ⚠️ Parcial: importación correcta, pero con errores o sin validación completa.  
- ❌ Incorrecto: errores en la importación o falta de evidencia de validación.
