# Sesión 1 (2h)
## Diseño físico en Oracle Database XE

## Contexto
Vuestro equipo ya dispone de modelo entidad-relación y modelo relacional. En esta sesión debéis convertir ese diseño lógico en un esquema físico ejecutable en Oracle XE, tomando decisiones de tipos de datos, restricciones e integridad.

El objetivo no es producir muchas tablas, sino un núcleo sólido que soporte el análisis de sostenibilidad del proyecto.

## Objetivos de aprendizaje
1. Traducir el modelo relacional a DDL en Oracle de forma coherente.
2. Elegir tipos de datos y restricciones justificadas técnicamente.
3. Detectar riesgos de calidad antes de insertar datos.
4. Documentar decisiones de diseño con criterio profesional.

## Trabajo a realizar
### 1) Definición del alcance físico mínimo viable
Seleccionad qué tablas son imprescindibles para responder vuestras preguntas analíticas principales de energía, residuos, movilidad o consumo.

Pregunta clave: ¿qué tablas son obligatorias para que vuestro primer análisis tenga sentido?

### 2) Diseño de columnas y tipos Oracle
Para cada columna crítica, justificad tipo y longitud/precisión.

Ejemplo orientativo:

```sql
consumo_kwh NUMBER(10,2) NOT NULL
fecha_medicion DATE NOT NULL
nombre_zona VARCHAR2(80) NOT NULL
```

No copiéis ciegamente formatos: ajustadlos al significado real del dato.

### 3) Definición de restricciones
Incluid como mínimo:

1. PK en todas las tablas.
2. FK en relaciones principales.
3. `NOT NULL` en métricas clave.
4. `CHECK` donde tenga sentido (rangos, categorías).

Ejemplo orientativo:

```sql
CONSTRAINT ck_residuos_kg CHECK (kg_residuo >= 0)
```

### 4) Revisión entre iguales
Intercambiad vuestro diseño con otro equipo y revisad:

1. Coherencia entre nombres y significado.
2. Riesgos de nulos no controlados.
3. Relaciones que podrían romperse.
4. Impacto de decisiones sobre futuras consultas.

## Preguntas guía
1. ¿Qué diferencia hay entre una decisión cómoda hoy y una decisión robusta para el análisis posterior?
2. ¿Qué dato puede comprometer más la validez de vuestros indicadores si se registra mal?
3. ¿Qué restricción evita ese riesgo sin bloquear operaciones normales?
4. ¿Dónde hay que permitir flexibilidad y dónde no?

## Decisiones obligatorias del equipo
1. Convención de nombres de tablas y columnas.
2. Política de claves primarias (numéricas, naturales o combinación).
3. Criterio de fechas (qué representa cada fecha y con qué granularidad).
4. Reglas de negocio que deban pasar a `CHECK`.

## Entregables parciales
1. `01_schema.sql` (versión inicial ejecutable).
2. `01_decisiones_diseno.md` con tabla de decisiones:

| Decisión | Alternativas consideradas | Opción elegida | Justificación técnica |
|---|---|---|---|
| Tipo de dato para consumo | NUMBER / VARCHAR2 | NUMBER(10,2) | Permite agregación y control de precisión |

3. Evidencia breve de revisión cruzada con otro equipo (3 hallazgos y 2 mejoras propuestas).

## Checklist de validación
- [ ] El script crea tablas sin errores en Oracle XE.
- [ ] PK y FK están definidas donde corresponde.
- [ ] No hay métricas clave sin `NOT NULL`.
- [ ] Existen controles mínimos de rangos/categorías.
- [ ] Las decisiones están justificadas y no solo descritas.
- [ ] El diseño permite al menos tres consultas analíticas futuras.
