# 🧩 Actividad práctica: Consultas y verificación de datos

## 🧠 Contexto
En las sesiones anteriores has creado la base de datos del proyecto “Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible”. En esta sesión vas a realizar **consultas SQL** para analizar y verificar la coherencia de los datos, comprobando que las relaciones, tipos y valores son correctos.

## 🎯 Objetivos
- Aplicar consultas SQL básicas y combinadas (`SELECT`, `WHERE`, `ORDER BY`, `JOIN`).
- Detectar posibles errores de integridad o incoherencias en los datos.
- Extraer información significativa que sirva para el análisis sostenible.

## 🧾 Desarrollo paso a paso

### 🥇 Paso 1 – Consultas básicas de exploración
1. Muestra todos los registros de la tabla principal.
2. Visualiza solo columnas relevantes.
3. Usa alias para mejorar la presentación.
```sql
SELECT nombre_departamento AS "Departamento", tipo_energia, consumo_kwh, fecha
FROM consumo_energia;
```

### 🥈 Paso 2 – Filtrado de información
1. Muestra registros con consumo > 500 kWh.
2. Filtra por tipo de energía.
3. Extrae registros por rango de fechas.
```sql
SELECT * FROM consumo_energia
WHERE consumo_kwh > 500 AND tipo_energia = 'Eléctrica';

SELECT * FROM consumo_energia
WHERE fecha BETWEEN '2025-07-01' AND '2025-09-30';
```

### 🥉 Paso 3 – Ordenación y resumen
1. Ordena por consumo descendente (`ORDER BY`).
2. Calcula consumo medio y total por tipo de energía.
```sql
SELECT tipo_energia, ROUND(AVG(consumo_kwh),2) AS promedio, SUM(consumo_kwh) AS total
FROM consumo_energia
GROUP BY tipo_energia
ORDER BY total DESC;
```

### 🏅 Paso 4 – Combinación de tablas
Relaciona tablas para obtener información integrada.
```sql
SELECT d.nombre AS Departamento, c.tipo_energia, c.consumo_kwh
FROM departamentos d
JOIN consumo_energia c ON d.id = c.id_departamento;
```
Interpreta resultados: ¿qué departamento consume más? ¿qué tipo de energía predomina?

### 🧩 Paso 5 – Verificación de integridad
1. **Duplicados**
```sql
SELECT nombre_departamento, COUNT(*)
FROM consumo_energia
GROUP BY nombre_departamento
HAVING COUNT(*) > 1;
```
2. **Valores nulos**
```sql
SELECT *
FROM consumo_energia
WHERE consumo_kwh IS NULL OR fecha IS NULL;
```
3. **Registros sin relación**
```sql
SELECT c.id_departamento
FROM consumo_energia c
LEFT JOIN departamentos d ON c.id_departamento = d.id
WHERE d.id IS NULL;
```
4. **Rangos incoherentes**
```sql
SELECT *
FROM consumo_energia
WHERE consumo_kwh < 0 OR consumo_kwh > 100000;
```

### 🧮 Paso 6 – Interpretación y documentación
- Anota las consultas realizadas y su propósito.
- Describe brevemente las conclusiones: anomalías, departamentos de mayor consumo, propuestas de mejora.

## 🧰 Entregables
1. Script `consultas_sesion7.sql` con todas las consultas comentadas.
2. Documento `verificacion_datos.md` o `.pdf` con capturas y conclusiones.

## 📏 Evaluación
| Criterio | Descripción | Instrumento |
|-----------|--------------|--------------|
| **DIG-RA3** | Extrae e interpreta información mediante consultas SQL. | Entrega práctica con consultas y resultados. |
| **Calidad técnica** | Consultas correctas, bien comentadas y sin errores. | Revisión del script SQL. |
| **Interpretación** | Capacidad para explicar resultados e incoherencias. | Informe de verificación. |
| **Rigor y orden** | Estructura clara del trabajo y buenas prácticas. | Checklist técnico. |
