# P03: Del modelo E-R al modelo relacional (3FN)

## Objetivo
Transformar el modelo entidad-relacion (E-R) del proyecto a un modelo relacional en 3FN, justificando las decisiones de normalizacion y documentando claves y dependencias.

## Entregables
- Esquema relacional con nombres consistentes.
- Lista de tablas con PK, FK.
- Comprobacion de 1FN, 2FN y 3FN con breve justificacion.
- Diccionario de datos minimo (tabla, campos, tipo, descripcion).

## Material necesario
- Modelo E-R del proyecto (actualizado).
- Herramienta de diagramado o editor de texto.

## Pasos
1. **Revisa el E-R**
   - Verifica cardinalidades, entidades debiles, atributos compuestos y multivaluados.
   - Ajusta nombres si hay inconsistencias.

2. **Transforma entidades a tablas**
   - Cada entidad fuerte pasa a una tabla.
   - Atributos compuestos: descomponer en atributos atomicos.
   - Atributos multivaluados: crear tabla aparte con FK.

3. **Transforma relaciones**
   - 1:1 -> FK en la tabla con participacion total o en la que tenga menos nulos.
   - 1:N -> FK en el lado N.
   - N:M -> tabla intermedia con PK compuesta (o surrogate + UNIQUE).
   - Relaciones con atributos -> incluirlos en la tabla intermedia.

4. **Define claves**
   - Elige PK estables y minimales.
   - Identifica claves candidatas

5. **Normaliza**
   - 1FN: valores atomicos, sin grupos repetidos.
   - 2FN: elimina dependencias parciales en PK compuesta.
   - 3FN: elimina dependencias transitivas.
   - Si se requiere, crea tablas auxiliares y ajusta FK.


## Criterios de evaluacion (10 puntos)
- Transformacion correcta E-R -> relacional (3 puntos).
- Claves primarias y foraneas bien definidas (2 puntos).
- Normalizacion a 3FN justificada (3 puntos).
- Diccionario de datos claro y completo (2 puntos).


