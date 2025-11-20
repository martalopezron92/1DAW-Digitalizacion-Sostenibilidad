# 📊 P01: Modelado Entidad-Relación
## Digitalización + Sostenibilidad | 1º DAW

### 📋 **Información de la Práctica**

- **Código**: P01-Modelado-ER
- **Nombre**: Diseño del Modelo de Datos del Proyecto
- **Trimestre**: 1º
<!-- - **Semana de entrega**: 8 (15 de octubre)
- **Duración estimada**: 8 horas (4h clase + 4h autónoma)
- **Modalidad**: Trabajo en equipo (3-4 personas)
- **Peso en la evaluación**: 15% del primer trimestre -->

---

## 🎯 **Objetivos de Aprendizaje**

Al finalizar esta práctica, el estudiante será capaz de:

1. **Analizar** los datos recopilados del centro para identificar entidades y relaciones
2. **Diseñar** un diagrama entidad-relación normalizado hasta 3FN
3. **Implementar** la integridad referencial y constraints apropiados
4. **Documentar** el modelo de datos con un diccionario completo
5. **Validar** el diseño con los datos reales disponibles

---

## 📚 **Antes de empezar, lee:**

- 📖 [Apuntes: Modelado de datos](../../apuntes/Sesion4_Modelado_de_datos.md)
<!-- - 📝 [Actividad previa: Modelado](../../actividades/Sesion4_Actividad_Modelado.md) -->
<!-- - 📊 [Rúbrica específica](../../docs/rubrica/R01-Rubrica.md) -->

---

## 🗃️ **Descripción del Problema**

Tu equipo debe crear el **modelo de datos** que servirá como base para todo el proyecto integrador. Este modelo debe:

- Reflejar los **datos reales** que habéis recopilado del centro
- Ser **escalable** para añadir nuevos tipos de datos
- Incluir los **indicadores ASG** que habéis seleccionado

---

## 📋 **Requisitos Técnicos**

### **Entidades Mínimas Requeridas**
Tu modelo debe incluir **al menos**:

1. **Centro/Organización** (entidad principal)
2. **Ubicaciones/Espacios** (edificios, plantas, aulas...)
3. **Temporal** (fechas, períodos, horarios...)
4. **Mediciones/Datos** (valores numéricos de indicadores)
5. **Categorización** (tipos, clasificaciones...)

### **Relaciones Obligatorias**
- Al menos **5 relaciones** entre entidades
- Mínimo **2 relaciones muchos-a-muchos** (con tabla intermedia)
- **1 relación jerárquica** (auto-referencia o herencia)

### **Integridad Referencial**
- **Claves primarias** en todas las tablas
- **Claves foráneas** correctamente definidas
<!-- - **Constraints** apropiados (CHECK, UNIQUE, NOT NULL)
- **Índices** en campos de búsqueda frecuente -->

---

## 🛠️ **Herramientas Recomendadas**

### **Para el Diagrama ER**
- **Draw.io** (gratuito, web): [https://app.diagrams.net/](https://app.diagrams.net/)
- **ERDPlus** (educativo): [https://erdplus.com/](https://erdplus.com/)
- **MySQL Workbench** (profesional)
- **Lucidchart** (con cuenta edu)

---

## 📝 **Entregables**

### **1. Diagrama ER Completo** 📊
- **Formato**: PDF + archivo fuente editable
- **Contenido**:
  - Todas las entidades con atributos
  - Relaciones con cardinalidades
  - Claves primarias y foráneas marcadas
- **Naming**: `P01_DiagramaER_EquipoX.pdf`

### **2. Diccionario de Datos** 📖
- **Formato**: Documento Markdown
- **Contenido**:
  - Descripción de cada entidad
  - Explicación de cada atributo
  - Justificación de las relaciones
  - Reglas de negocio aplicadas
- **Naming**: `P01_Diccionario_EquipoX.md`

### **3. Documento de Justificación** 📋
- **Formato**: PDF (máximo 3 páginas)
- **Contenido**:
  - Decisiones de diseño tomadas
  - Problemas encontrados y soluciones
  - Futuras extensiones posibles
- **Naming**: `P01_Justificacion_EquipoX.pdf`

---

## ✅ **Criterios de Aceptación**

### **Funcionales**
- [ ] Incluye los indicadores ASG seleccionados

### **Técnicos**
- [ ] Todas las tablas tienen clave primaria
- [ ] Las relaciones están correctamente implementadas
- [ ] Los tipos de datos son apropiados
- [ ] Los nombres siguen convenciones

### **Documentación**
- [ ] El diagrama ER es claro y completo
- [ ] El diccionario describe todas las entidades
- [ ] Las justificaciones están bien argumentadas
- [ ] Los archivos están correctamente nombrados

---

## 🎯 **Cómo te evaluaremos**

Esta práctica trabaja los siguientes Resultados de Aprendizaje y Criterios de Evaluación:

### 📱 **Digitalización aplicada al sistema productivo**

**RA1**: Analiza el concepto de digitalización y su repercusión identificando entornos IT y OT.

| Criterio | Indicador de logro |
|:---------|:-------------------|
| **c)** Diferencias y similitudes entre IT y OT | El modelo distingue claramente datos de sistemas IT (gestión) y OT (sensores, medidores físicos) |
| **d)** Identificación de departamentos/entornos IT | Identifica y modela correctamente las fuentes de datos digitales del centro |

**RA2**: Caracteriza las tecnologías habilitadoras digitales necesarias para la transformación digital.

| Criterio | Indicador de logro |
|:---------|:-------------------|
| **e)** Identificación de THD en negocio y planta | El modelo contempla la captura de datos tanto de gestión como operacionales |
| **f)** Mejoras por implantación de THD en IT y OT | Diseña estructuras que permitan integrar datos de diferentes fuentes tecnológicas |

**RA5**: Evalúa la importancia de los datos y su protección.

| Criterio | Indicador de logro |
|:---------|:-------------------|
| **b)** Descripción del ciclo de vida del dato | El modelo refleja correctamente la fase de almacenamiento estructurado de datos |
| **d)** Características que definen Big Data | Diseña para escalabilidad, contemplando volumen, variedad y velocidad |
| **e)** Etapas de ciencia de datos y su relación | Estructura los datos de forma que faciliten su posterior análisis |


### 🌱 **Sostenibilidad aplicada al sistema productivo**

**RA1**: Identifica aspectos ASG relativos a la sostenibilidad.

| Criterio | Indicador de logro |
|:---------|:-------------------|
| **d)** Identificación de aspectos ASG relevantes | El modelo incluye entidades y atributos para medir indicadores ASG seleccionados |
| **e)** Métricas para evaluación del desempeño | Diseña estructuras que permitan calcular métricas de sostenibilidad |

---

## 📊 **Rúbrica de Evaluación**

### **Dimensión 1: Corrección Técnica (40%)**

| Criterio | Excelente (9-10) | Notable (7-8) | Bien (5-6) | Insuficiente (0-4) |
|:---------|:-----------------|:--------------|:-----------|:-------------------|
| **Integridad referencial** | Todas las claves PK/FK correctas | Mayoria de PK/FK correctas | Algunas FK incorrectas | Faltan PK/FK |
| **Tipos de datos** | Tipos óptimos, precisión adecuada, consideraciones de rendimiento | Tipos correctos y apropiados | Algunos tipos mejorables | Tipos inadecuados o incorrectos |
| **Nomenclatura** | Convenciones claras, consistentes y profesionales en todo el modelo | Convenciones correctas con pequeñas inconsistencias | Nomenclatura aceptable pero mejorable | Nombres confusos o sin convención |

### **Dimensión 2: Completitud (25%)**

| Criterio | Excelente (9-10) | Notable (7-8) | Bien (5-6) | Insuficiente (0-4) |
|:---------|:-----------------|:--------------|:-----------|:-------------------|
| **Entidades requeridas** | Todas las mínimas + adicionales relevantes bien justificadas | Todas las entidades mínimas correctamente modeladas | Faltan 1-2 entidades secundarias | Faltan entidades principales |
| **Relaciones** | Más de 5, correctamente modeladas, incluye M:N | 5 relaciones correctas, incluye M:N | 4-5 relaciones, alguna mejorable | Menos de 4 o errores conceptuales |
| **Indicadores ASG** | Modelo completo para todos los indicadores seleccionados, extensible | Modelo para indicadores principales, escalable | Modelo básico para indicadores | No contempla indicadores ASG |
| **Entregables** | Todos completos, profesionales, en formatos correctos | Todos presentes, correctos | Falta algún elemento secundario | Faltan entregables principales |

### **Dimensión 3: Calidad del Diseño (20%)**

| Criterio | Excelente (9-10) | Notable (7-8) | Bien (5-6) | Insuficiente (0-4) |
|:---------|:-----------------|:--------------|:-----------|:-------------------|
| **Escalabilidad** | Diseño muy flexible, fácil añadir nuevos datos/indicadores | Diseño permite extensiones sin grandes cambios | Permite extensiones con modificaciones | Diseño rígido, difícil de extender |
| **Integración IT/OT** | Modelo integra perfectamente datos operacionales y de gestión | Distingue y conecta datos IT/OT correctamente | Contempla ambos tipos pero integración mejorable | No diferencia IT/OT adecuadamente |
| **Elegancia** | Solución simple, clara y profesional, evita redundancia | Diseño claro y bien organizado | Funcional pero algo complejo | Diseño confuso o excesivamente complejo |

### **Dimensión 4: Documentación (15%)**

| Criterio | Excelente (9-10) | Notable (7-8) | Bien (5-6) | Insuficiente (0-4) |
|:---------|:-----------------|:--------------|:-----------|:-------------------|
| **Diagrama ER** | Muy claro, profesional, notación correcta, fácil de entender | Claro y completo, notación correcta | Legible pero mejorable estéticamente | Confuso o incompleto |
| **Diccionario de datos** | Exhaustivo, describe todo, incluye ejemplos y validaciones | Completo, describe entidades y atributos correctamente | Básico, falta detalle en algunos elementos | Incompleto o superficial |
| **Justificaciones** | Argumenta todas las decisiones con criterios técnicos y de negocio | Justifica decisiones principales correctamente | Justificaciones básicas | Faltan justificaciones o son débiles |
| **Presentación** | Formato profesional, sin errores, estructura clara y organizada | Bien presentado, estructura correcta | Presentación aceptable | Desorganizado o con errores de formato |

### **Puntuación Total**

| Dimensión | Peso | Nota |
|:----------|:-----|:-----|
| Corrección técnica | 40% | ___ / 10 |
| Completitud | 25% | ___ / 10 |
| Calidad del diseño | 20% | ___ / 10 |
| Documentación | 15% | ___ / 10 |
| **NOTA FINAL** | **100%** | **___ / 10** |


### **Penalizaciones**

- **-1.0**: Entrega fuera de plazo sin justificación
- **-0.5**: Archivos mal nombrados o estructura incorrecta
- **-0.5**: Modelo no implementable (errores SQL graves)
- **-2.0**: Evidencia de copia o falta de autoría del equipo
---

## 🆘 **¿Necesitas Ayuda?**

### **Recursos Adicionales**
- 📚 [Tutorial de normalización](../../docs/recursos/TUTORIAL-NORMALIZACION.md)
- 🎥 [Vídeo: Diagramas ER paso a paso](enlace-pendiente)
- 🔧 [Herramientas de modelado](../../docs/recursos/HERRAMIENTAS-BD.md)
---

## 👥 **Checklist del Equipo**

Antes de entregar, verificad que:

- [ ] **Todos los miembros** han contribuido equitativamente
- [ ] **Todos entienden** el modelo diseñado
- [ ] **El diseño es consensuado** por todo el equipo
- [ ] **Los archivos están revisados** por al menos 2 personas
- [ ] **La entrega está completa** según la lista de entregables
- [ ] **Las pruebas funcionan** en una BD limpia
- [ ] **La documentación es clara** para alguien externo

---

**🎓 ¡Buena suerte con vuestro primer modelo de datos!**
