# 🧠 Sesión 7 – Consultas y verificación

## 1. Introducción a las consultas SQL
El lenguaje **SQL (Structured Query Language)** es el estándar utilizado por sistemas como **PostgreSQL, MySQL o SQLite**.  
Permite **consultar, insertar, modificar y eliminar información** almacenada en bases de datos relacionales.  
En esta sesión aprenderás a realizar **consultas SELECT**, combinar tablas con **JOIN** y verificar la **integridad y coherencia** de los datos importados en tu proyecto.

---

## 2. La instrucción SELECT

La instrucción `SELECT` permite **extraer información** de una o varias tablas.

**Sintaxis general:**
```sql
SELECT columnas
FROM tabla
[WHERE condición]
[GROUP BY columna]
[HAVING condición]
[ORDER BY columna [ASC|DESC]];
```

**Ejemplo básico:**
```sql
SELECT nombre, consumo_kwh FROM consumo_energia;
```

**Ejemplo con alias:**
```sql
SELECT nombre AS "Departamento", consumo_kwh AS "Consumo (kWh)"
FROM consumo_energia;
```

---

## 3. Filtrado de datos con WHERE
Permite seleccionar registros que cumplan condiciones específicas.

**Ejemplo 1:**  
```sql
SELECT nombre, consumo_kwh
FROM consumo_energia
WHERE consumo_kwh > 500;
```

**Ejemplo 2:** Combinando condiciones  
```sql
SELECT nombre, consumo_kwh
FROM consumo_energia
WHERE consumo_kwh > 500 AND tipo_energia = 'Eléctrica';
```

**Operadores más usados:**
- `=`, `!=`, `>`, `<`, `>=`, `<=`
- `AND`, `OR`, `NOT`
- `BETWEEN`, `IN`, `LIKE`

**Ejemplo con LIKE:**
```sql
SELECT nombre FROM departamentos WHERE nombre LIKE 'A%';
```

---

## 4. Ordenación de resultados con ORDER BY
Permite ordenar los registros obtenidos.

**Ejemplo ascendente:**
```sql
SELECT nombre, consumo_kwh
FROM consumo_energia
ORDER BY consumo_kwh ASC;
```

**Ejemplo descendente:**
```sql
SELECT nombre, consumo_kwh
FROM consumo_energia
ORDER BY consumo_kwh DESC;
```

**Múltiples criterios:**
```sql
SELECT nombre, tipo_energia, consumo_kwh
FROM consumo_energia
ORDER BY tipo_energia ASC, consumo_kwh DESC;
```

---

## 5. Funciones de agregación
Permiten realizar **cálculos sobre grupos de datos**.

| Función | Descripción | Ejemplo |
|----------|--------------|----------|
| `COUNT()` | Cuenta registros | `COUNT(*)` |
| `SUM()` | Suma valores | `SUM(consumo_kwh)` |
| `AVG()` | Calcula el promedio | `AVG(consumo_kwh)` |
| `MAX()` | Devuelve el valor máximo | `MAX(consumo_kwh)` |
| `MIN()` | Devuelve el valor mínimo | `MIN(consumo_kwh)` |

**Ejemplo práctico:**
```sql
SELECT tipo_energia, SUM(consumo_kwh) AS consumo_total
FROM consumo_energia
GROUP BY tipo_energia;
```

**Ejemplo con condición HAVING:**
```sql
SELECT d.nombre, AVG(c.consumo_kwh) AS media
FROM consumo_energia c
JOIN departamentos d ON c.id_departamento = d.id
GROUP BY d.nombre
HAVING AVG(c.consumo_kwh) > 600;
```

---

## 6. Combinación de tablas con JOIN
Permite unir datos de diferentes tablas relacionadas mediante claves.

**Tipos más comunes:**
- `INNER JOIN`: solo los registros coincidentes.
- `LEFT JOIN`: todos los registros de la izquierda más coincidencias.
- `RIGHT JOIN`: todos los registros de la derecha más coincidencias.

**Ejemplo INNER JOIN:**
```sql
SELECT d.nombre, c.consumo_kwh
FROM departamentos d
INNER JOIN consumo_energia c ON d.id = c.id_departamento;
```

**Ejemplo LEFT JOIN:**
```sql
SELECT d.nombre, c.consumo_kwh
FROM departamentos d
LEFT JOIN consumo_energia c ON d.id = c.id_departamento
WHERE c.id IS NULL;
```

---

## 7. Subconsultas y vistas

**Subconsulta:**
```sql
SELECT nombre
FROM departamentos
WHERE id IN (
  SELECT id_departamento
  FROM consumo_energia
  WHERE consumo_kwh > 700
);
```

**Creación de una vista:**
```sql
CREATE VIEW consumo_total_departamento AS
SELECT d.nombre, SUM(c.consumo_kwh) AS total
FROM consumo_energia c
JOIN departamentos d ON c.id_departamento = d.id
GROUP BY d.nombre;
```

---

## 8. Verificación de integridad y coherencia de los datos

**Buscar duplicados:**
```sql
SELECT nombre, COUNT(*) AS repeticiones
FROM consumo_energia
GROUP BY nombre
HAVING COUNT(*) > 1;
```

**Buscar valores nulos:**
```sql
SELECT *
FROM consumo_energia
WHERE consumo_kwh IS NULL OR fecha IS NULL;
```

**Detectar registros sin relación:**
```sql
SELECT c.id_departamento
FROM consumo_energia c
LEFT JOIN departamentos d ON c.id_departamento = d.id
WHERE d.id IS NULL;
```

**Comprobar rangos de valores:**
```sql
SELECT * FROM consumo_energia
WHERE consumo_kwh < 0 OR consumo_kwh > 100000;
```

**Validar fechas:**
```sql
SELECT * FROM consumo_energia
WHERE fecha > NOW();
```

---

## 9. Buenas prácticas en consultas SQL
- Evita usar `SELECT *` en consultas finales.  
- Usa **alias** (`AS`) claros para mejorar la legibilidad.  
- Documenta las consultas con comentarios (`--`).  
- Comprueba la integridad antes de generar informes o visualizaciones.  
- Guarda las consultas frecuentes en scripts o vistas reutilizables.  

---
