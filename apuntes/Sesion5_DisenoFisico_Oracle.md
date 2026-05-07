# Sesión 4 – Diseño físico en Oracle Database XE

**Proyecto:** Digitalización + Sostenibilidad – "Nuestro Instituto frente al Mundo: Datos para un Futuro Sostenible"
**Objetivo de la sesión:** Transformar el modelo relacional en un esquema físico real y ejecutable en Oracle XE, tomando decisiones técnicas justificadas.

---

## 1. Del modelo relacional al modelo físico

El **modelo relacional** describe qué tablas existen, qué atributos tienen y cómo se relacionan, pero de forma abstracta. El **modelo físico** es la concreción de ese diseño en el lenguaje DDL (Data Definition Language) de un sistema gestor específico, en este caso Oracle Database XE.

La transición exige tres decisiones para cada elemento del modelo:

| Elemento del modelo relacional | Decisión en el modelo físico |
|---|---|
| Entidad / tabla | Nombre, esquema y restricciones |
| Atributo | Tipo de dato, precisión y obligatoriedad |
| Clave primaria | Tipo de valor y estrategia de generación |
| Clave foránea | Tablas referenciadas y comportamiento |
| Regla de negocio | Restricción `CHECK`, `UNIQUE` o `NOT NULL` |

Una buena práctica antes de escribir DDL es rellenar una tabla de decisiones por atributo crítico. Ahorra correcciones posteriores que pueden ser costosas si ya hay datos cargados.

---

## 2. Tipos de datos en Oracle

Oracle XE tiene sus propios tipos de datos, que difieren en sintaxis de PostgreSQL o MySQL. Elegir el tipo correcto mejora la integridad y la eficiencia de las consultas.

### 2.1. Tipos numéricos

| Tipo | Descripción | Ejemplo de uso |
|---|---|---|
| `NUMBER(p)` | Entero de hasta p dígitos | `id_zona NUMBER(6)` |
| `NUMBER(p,s)` | Número con p dígitos totales, s decimales | `consumo_kwh NUMBER(10,2)` |
| `INTEGER` | Alias de `NUMBER(38)` | Válido pero menos preciso para PK |

El parámetro de escala `s` es clave en métricas de sostenibilidad. Un consumo energético en kWh necesita dos decimales; un porcentaje puede necesitar cuatro.

Ejemplo razonado:

```sql
consumo_kwh    NUMBER(10,2)   -- hasta 99.999.999,99 kWh
porcentaje_rec NUMBER(5,2)    -- hasta 999,99 %
temperatura    NUMBER(5,1)    -- hasta 9999,9 ºC
```

### 2.2. Tipos de texto

| Tipo | Descripción | Cuándo usarlo |
|---|---|---|
| `VARCHAR2(n)` | Texto variable hasta n caracteres | Nombres, categorías, descripciones |
| `CHAR(n)` | Texto de longitud fija n | Códigos normalizados (ej. 'EST', 'LAB') |
| `CLOB` | Texto largo sin límite práctico | Observaciones extensas (rara vez en análisis) |

En Oracle, `VARCHAR2` es el tipo de texto estándar recomendado. No usar `VARCHAR` sin el `2`: en Oracle son equivalentes, pero `VARCHAR2` es el oficial y garantiza compatibilidad futura.

```sql
nombre_zona    VARCHAR2(80)
tipo_zona      CHAR(3)         -- 'AUL', 'LAB', 'OFI', 'COM'
descripcion    VARCHAR2(255)
```

### 2.3. Fechas y tiempo

| Tipo | Descripción | Ejemplo |
|---|---|---|
| `DATE` | Fecha y hora (sin zona horaria) | `fecha_medicion DATE` |
| `TIMESTAMP` | Fecha y hora con fracciones de segundo | Para registros de alta precisión |

En este proyecto, `DATE` es suficiente para la mayoría de mediciones periódicas. Usar siempre el formato explícito `DATE 'YYYY-MM-DD'` en inserciones para evitar ambigüedades regionales.

---

## 3. Restricciones de integridad

Las restricciones son reglas que Oracle aplica automáticamente a cada operación de escritura. Son la primera línea de defensa contra datos erróneos.

### 3.1. Clave primaria (PRIMARY KEY)

Identifica cada fila de forma única. Oracle crea automáticamente un índice único sobre la PK.

```sql
CREATE TABLE zona_centro (
    id_zona     NUMBER(6)    PRIMARY KEY,
    nombre_zona VARCHAR2(80) NOT NULL,
    tipo_zona   CHAR(3)      NOT NULL
);
```

También se puede definir como restricción nombrada, lo que facilita el mantenimiento:

```sql
CREATE TABLE zona_centro (
    id_zona     NUMBER(6),
    nombre_zona VARCHAR2(80) NOT NULL,
    tipo_zona   CHAR(3)      NOT NULL,
    CONSTRAINT pk_zona_centro PRIMARY KEY (id_zona)
);
```

Nombrar las restricciones es una buena práctica: los mensajes de error Oracle incluyen el nombre de la restricción violada, lo que agiliza el diagnóstico.

### 3.2. Clave foránea (FOREIGN KEY)

Garantiza que el valor referenciado existe en la tabla padre.

```sql
CREATE TABLE medicion_energia (
    id_medicion    NUMBER(10),
    id_zona        NUMBER(6)     NOT NULL,
    fecha_medicion DATE          NOT NULL,
    consumo_kwh    NUMBER(10,2)  NOT NULL,
    fuente_energia VARCHAR2(20)  NOT NULL,
    CONSTRAINT pk_med_energia    PRIMARY KEY (id_medicion),
    CONSTRAINT fk_med_zona       FOREIGN KEY (id_zona)
                                 REFERENCES zona_centro (id_zona)
);
```

Si se intenta insertar un `id_zona` que no existe en `zona_centro`, Oracle rechaza la inserción con error de violación de integridad referencial.

### 3.3. NOT NULL

Obliga a que el campo tenga valor en toda inserción. Aplicar siempre en:

- Identificadores.
- Métricas que se van a agregar.
- Fechas de referencia.
- Categorías necesarias para clasificar registros.

### 3.4. CHECK

Valida que el valor cumpla una condición específica definida por el diseñador.

```sql
CONSTRAINT ck_consumo_positivo  CHECK (consumo_kwh >= 0),
CONSTRAINT ck_fuente_energia    CHECK (fuente_energia IN ('RED', 'SOLAR', 'MIXTA')),
CONSTRAINT ck_porcentaje        CHECK (porcentaje_rec BETWEEN 0 AND 100)
```

### 3.5. UNIQUE

Impide valores repetidos en la columna sin ser clave primaria.

```sql
CONSTRAINT uq_codigo_sensor UNIQUE (codigo_sensor)
```

### 3.6. Resumen comparativo

| Restricción | Propósito | Cuándo es obligatoria |
|---|---|---|
| `PRIMARY KEY` | Identificación única de fila | Siempre, en todas las tablas |
| `FOREIGN KEY` | Integridad referencial | Siempre que exista relación real |
| `NOT NULL` | Evitar vacíos en campos críticos | En métricas, fechas y categorías clave |
| `CHECK` | Validar rangos y dominios | Cuando el dominio tiene reglas claras |
| `UNIQUE` | Irrepetibilidad funcional | En códigos, identificadores alternativos |

---

## 4. Nomenclatura y convenciones

Adoptar un criterio de nombres claro desde el inicio evita confusión y facilita el mantenimiento del esquema.

Convenciones recomendadas para este proyecto:

| Objeto | Patrón | Ejemplo |
|---|---|---|
| Tabla | sustantivo_en_singular | `zona_centro`, `medicion_energia` |
| Columna | sustantivo_descriptivo | `consumo_kwh`, `fecha_medicion` |
| PK | `pk_<tabla>` | `pk_zona_centro` |
| FK | `fk_<tabla_hijo>_<tabla_padre>` | `fk_med_zona` |
| CHECK | `ck_<tabla>_<descripcion>` | `ck_consumo_positivo` |
| UNIQUE | `uq_<tabla>_<campo>` | `uq_sensor_codigo` |

Evitar nombres con mayúsculas inconsistentes, espacios, tildes o palabras reservadas de SQL.

---

## 5. Estructura de un script DDL completo

Un script DDL bien organizado debe poder ejecutarse desde cero (en un esquema vacío) y reproducir el modelo físico exacto. Estructura recomendada:

```sql
-- =============================================================
-- PROYECTO: Instituto frente al Mundo
-- Esquema: sostenibilidad
-- Versión: 1.0   Fecha: 2026-05-07
-- =============================================================

-- 1. Tablas de catálogo (sin dependencias externas)
CREATE TABLE tipo_zona (
    id_tipo   NUMBER(3)    PRIMARY KEY,
    nombre    VARCHAR2(30) NOT NULL,
    CONSTRAINT uq_tipo_zona_nombre UNIQUE (nombre)
);

-- 2. Tablas maestras
CREATE TABLE zona_centro (
    id_zona     NUMBER(6),
    nombre_zona VARCHAR2(80) NOT NULL,
    id_tipo     NUMBER(3)    NOT NULL,
    superficie  NUMBER(8,2),
    CONSTRAINT pk_zona_centro PRIMARY KEY (id_zona),
    CONSTRAINT fk_zona_tipo   FOREIGN KEY (id_tipo)
                              REFERENCES tipo_zona (id_tipo)
);

-- 3. Tablas de hechos
CREATE TABLE medicion_energia (
    id_medicion    NUMBER(10),
    id_zona        NUMBER(6)    NOT NULL,
    fecha_medicion DATE         NOT NULL,
    consumo_kwh    NUMBER(10,2) NOT NULL,
    fuente_energia VARCHAR2(20) NOT NULL,
    CONSTRAINT pk_med_energia   PRIMARY KEY (id_medicion),
    CONSTRAINT fk_med_zona      FOREIGN KEY (id_zona)
                                REFERENCES zona_centro (id_zona),
    CONSTRAINT ck_consumo_pos   CHECK (consumo_kwh >= 0),
    CONSTRAINT ck_fuente        CHECK (fuente_energia IN ('RED', 'SOLAR', 'MIXTA'))
);
```

---

## 6. Errores frecuentes en diseño físico

| Error | Consecuencia | Solución |
|---|---|---|
| Guardar números como `VARCHAR2` | No se puede agregar, filtrar ni ordenar numéricamente | Usar `NUMBER` con precisión adecuada |
| Guardar fechas como texto | Imposible calcular diferencias o truncar por mes | Usar `DATE` y formato explícito |
| No nombrar restricciones | Mensajes de error crípticos | Nombrar siempre PK, FK, CHECK |
| Permitir nulos en métricas | Resultados parciales o engañosos en `SUM`/`AVG` | `NOT NULL` + valor por defecto si aplica |
| Crear tablas sin orden | Errores al crear FK si la tabla padre no existe | Crear primero catálogos, luego maestras, luego hechos |
| Inconsistencia de nombres | Código ilegible y propenso a errores | Definir convención al inicio y respetarla |

---

## 7. Mini retos de reflexión

1. Si la columna `tipo_zona` se define como `VARCHAR2(30)` sin restricción `CHECK`, ¿qué valores inválidos podrían entrar y cómo afectaría al análisis?

2. Tenéis una tabla de residuos donde `kg_residuo` puede ser 0 (contenedor vacío en esa fecha). ¿Es válido permitir 0? ¿Y nulo? ¿Son la misma situación?

3. ¿Por qué es importante que el script DDL ejecute sin errores en un esquema vacío antes de empezar a insertar datos?

---

## 8. Verificación básica del esquema en Oracle

Consultas útiles para comprobar que el esquema se ha creado correctamente:

```sql
-- Tablas creadas en el esquema actual
SELECT table_name FROM user_tables ORDER BY table_name;

-- Columnas y tipos de una tabla concreta
SELECT column_name, data_type, data_length, nullable
FROM user_tab_columns
WHERE table_name = 'MEDICION_ENERGIA'
ORDER BY column_id;

-- Restricciones definidas en una tabla
SELECT constraint_name, constraint_type, search_condition
FROM user_constraints
WHERE table_name = 'MEDICION_ENERGIA';
```
