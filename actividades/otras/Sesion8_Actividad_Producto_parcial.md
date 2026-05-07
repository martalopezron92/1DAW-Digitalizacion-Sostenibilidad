# Sesión 8 – Consolidación y presentación parcial
## Enunciado detallado de la actividad (mostrar antes de guardar)

### Objetivo
Entregar un **producto parcial** que demuestre la correcta **estructuración de los datos** (DIG-RA3) y la **interpretación inicial de indicadores sostenibles** (SOST-RA1), y realizar una **presentación breve (5 min)** por equipos.

---

## 1) Entregables (carpeta por equipo)
Estructura de carpetas sugerida (zip final):
```
/equipo-XX_sesion8/
  ├─ 01_ER/               (diagrama ER en .png o .pdf)
  ├─ 02_sql/              (script SQL completo y legible)
  ├─ 03_datos_muestra/    (CSV/SQL con ≥50 filas reales o de ejemplo)
  ├─ 04_evidencias/       (consultas SELECT y capturas de verificación)
  ├─ 05_fuentes/          (resumen de fuentes y metadatos)
  └─ 06_1pager/           (1-pager en .pdf o .md)
```

**Contenido mínimo de cada subcarpeta:**
- **01_ER/**: diagrama ER actualizado (cardinalidades, claves y notas).
- **02_sql/**: `schema.sql` con `CREATE TABLE`, PK, FK, UNIQUE, CHECK, índices (si procede) y comentarios `--` explicativos.
- **03_datos_muestra/**: `muestra.csv` (o `insert.sql`) con registros representativos y limpios.
- **04_evidencias/**: archivo `verificacion.md/pdf` con salidas de consultas (copias de pantalla o resultados pegados).
- **05_fuentes/**: `fuentes.md` con tabla de metadatos (origen, URL, fecha de descarga, licencia, campos clave, calidad).
- **06_1pager/**: documento único que resuma el proyecto (ver plantilla al final).

---

## 2) Requisitos técnicos
1. **Coherencia modelo–esquema–datos**: el ER y el `schema.sql` deben corresponder 1:1 (nombres, tipos y relaciones).
2. **Integridad y calidad**:
   - Sin valores obligatorios nulos.
   - Claves externas válidas.
   - Tipos correctos (fechas, numéricos, categorías).
3. **Verificación con SQL** (incluir evidencias en 04_evidencias/):
   ```sql
   -- Registros totales por tabla (ejemplo)
   SELECT 'energia' AS tabla, COUNT(*) FROM energia
   UNION ALL
   SELECT 'aulas', COUNT(*) FROM aulas;

   -- Nulos en campos críticos
   SELECT COUNT(*) AS nulos_consumo FROM energia WHERE consumo_kwh IS NULL;

   -- Integridad referencial (filas huérfanas)
   SELECT e.id
   FROM energia e
   LEFT JOIN aulas a ON e.aula_id = a.id
   WHERE a.id IS NULL;
   ```
4. **Resumen de fuentes**: justificar **pertinencia** y **fiabilidad** (licencia, actualización, cobertura, precisión).
5. **Indicadores sostenibles (avance)**: al menos **2 indicadores** definidos (fórmula y unidades). *Ejemplos*:
   - **kWh/m²/mes** en edificio A.
   - **% residuos reciclados** sobre el total.
   - **Ratio uso PC fuera de horario lectivo**.

---

## 3) Presentación (5 minutos por equipo)
Guion sugerido (no sobrepasar el tiempo):
1. **Contexto y objetivo** (30s)
2. **ER + esquema** (90s)
3. **Carga de datos y evidencias** (90s)
4. **Indicadores iniciales y hallazgos** (60s)
5. **Próximos pasos** (30s)

**Consejos**:
- 1–2 diapositivas máximo por bloque.
- Mostrar una consulta real y su salida.
- Evitar jerga innecesaria; claridad ante todo.

---

## 4) Rúbrica de evaluación (100 puntos)
| Criterio                         | Descripción                                                                 | Puntos |
|----------------------------------|-----------------------------------------------------------------------------|--------|
| **Claridad técnica**             | Coherencia ER–SQL–datos, nomenclatura, tipos correctos, uso de PK/FK        | 40     |
| **Documentación**                | Estructura de carpetas, `schema.sql` comentado, fuentes y evidencias claras | 30     |
| **Relevancia sostenible**        | Selección y justificación de indicadores ASG apropiados                      | 20     |
| **Presentación oral**            | Claridad, tiempo, reparto de roles                                          | 10     |

**Instrumentos**: rúbrica del producto parcial + lista de cotejo de integridad y documentación.

---

## 5) Lista de cotejo (para autoevaluación del equipo)
- [ ] ER actualizado y legible con cardinalidades y claves.
- [ ] `schema.sql` ejecuta sin errores en un nuevo esquema vacío.
- [ ] Datos de muestra ≥50 filas, sin nulos críticos, tipos correctos.
- [ ] Evidencias de integridad (consultas y resultados) incluidas.
- [ ] `fuentes.md` con metadatos y licencias.
- [ ] 1-pager entregado y presentación preparada (≤5 min).

---

## 6) Convenciones de entrega
- **Nombre del zip**: `equipo-XX_sesion8.zip`
- **Formato**: subir a la plataforma en plazo (según indique el profesor).
- **Compatibilidad**: PostgreSQL o MySQL (indicar versión usada).

---

## 7) Plantilla de 1-Pager (copiar en 06_1pager/1pager.md)
```md
# 1-Pager – Equipo <Nombre>
**Ámbito**: <Energía | Residuos | Movilidad | TIC ...>

## Objetivo
<Resumen en 2–3 frases del problema que resolvéis y el valor sostenible>

## Arquitectura de datos (resumen)
- Tablas clave: <tabla1, tabla2, ...>
- Relaciones: <principal-FK, ...>
- Tecnologías: <SGBD, scripts, herramientas>

## Fuentes de datos
| Origen | URL | Fecha | Licencia | Campos clave | Riesgos/calidad |
|-------|-----|-------|----------|--------------|------------------|
| ...   | ... | ...   | ...      | ...          | ...              |

## Indicadores iniciales
- Indicador 1: <definición, unidades, fórmula>
- Indicador 2: <definición, unidades, fórmula>

## Hallazgos parciales
<Puntos clave, anomalías, decisiones técnicas>

## Próximos pasos
<Tareas inmediatas y riesgos>
```
