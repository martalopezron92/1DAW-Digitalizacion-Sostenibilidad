# 📊 P01: Modelado Entidad-Relación
## Digitalización + Sostenibilidad | 1º DAW

### 📋 **Información de la Práctica**

- **Código**: P01-Modelado-ER
- **Nombre**: Diseño del Modelo de Datos del Proyecto
- **Trimestre**: 1º
- **Semana de entrega**: 8 (15 de octubre)
- **Duración estimada**: 8 horas (4h clase + 4h autónoma)
- **Modalidad**: Trabajo en equipo (3-4 personas)
- **Peso en la evaluación**: 15% del primer trimestre

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
- 📝 [Actividad previa: Modelado](../../actividades/Sesion4_Actividad_Modelado.md)
- 📊 [Rúbrica específica](../../docs/rubrica/R01-Rubrica.md)

---

## 🗃️ **Descripción del Problema**

Tu equipo debe crear el **modelo de datos** que servirá como base para todo el proyecto integrador. Este modelo debe:

- Reflejar los **datos reales** que habéis recopilado del centro
- Ser **escalable** para añadir nuevos tipos de datos
- Cumplir con **estándares de normalización** (mínimo 3FN)
- Incluir los **indicadores ASG** que habéis seleccionado

### **Ámbitos de Trabajo Disponibles**

Elegid **uno** de los siguientes ámbitos para vuestro modelo:

| Ámbito | Entidades Principales | Indicadores ASG Típicos |
|:-------|:---------------------|:-------------------------|
| **🔋 Energía** | Edificios, Equipos, Consumos, Medidores | kWh/m², emisiones CO₂, % renovables |
| **♻️ Residuos** | Contenedores, Tipos de residuo, Recogidas | kg/persona, % reciclado, rutas optimizadas |
| **🚗 Movilidad** | Vehículos, Rutas, Transportes, Usuarios | km/día, % transporte público, emisiones |
| **💻 TIC** | Dispositivos, Software, Usuarios, Proyectos | Antigüedad equipos, % actualizado, eficiencia |
| **👥 Bienestar** | Personas, Espacios, Actividades, Satisfacción | Calidad aire, temperatura, índice bienestar |

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

### **Normalización**
- **1FN**: Sin grupos repetidos, claves primarias definidas
- **2FN**: Sin dependencias funcionales parciales
- **3FN**: Sin dependencias transitivas
- **Opcional**: BCNF para nota excelente

### **Integridad Referencial**
- **Claves primarias** en todas las tablas
- **Claves foráneas** correctamente definidas
- **Constraints** apropiados (CHECK, UNIQUE, NOT NULL)
- **Índices** en campos de búsqueda frecuente

---

## 🛠️ **Herramientas Recomendadas**

### **Para el Diagrama ER**
- **Draw.io** (gratuito, web): [https://app.diagrams.net/](https://app.diagrams.net/)
- **ERDPlus** (educativo): [https://erdplus.com/](https://erdplus.com/)
- **MySQL Workbench** (profesional)
- **Lucidchart** (con cuenta edu)

### **Para Validación**
- **PostgreSQL** o **MySQL** para implementar el esquema
- **DBDesigner** para verificar normalización
- **SQLiteStudio** para pruebas rápidas

---

## 📝 **Entregables**

### **1. Diagrama ER Completo** 📊
- **Formato**: PDF + archivo fuente editable
- **Contenido**:
  - Todas las entidades con atributos
  - Relaciones con cardinalidades
  - Claves primarias y foráneas marcadas
  - Constraints visibles
- **Naming**: `P01_DiagramaER_EquipoX.pdf`

### **2. Esquema SQL Implementado** 💾
- **Formato**: Archivo .sql
- **Contenido**:
  - Sentencias CREATE TABLE completas
  - Definición de todas las claves
  - Constraints e índices
  - Comentarios explicativos
- **Naming**: `P01_EsquemaBD_EquipoX.sql`

### **3. Diccionario de Datos** 📖
- **Formato**: Documento Markdown
- **Contenido**:
  - Descripción de cada entidad
  - Explicación de cada atributo
  - Justificación de las relaciones
  - Reglas de negocio aplicadas
- **Naming**: `P01_Diccionario_EquipoX.md`

### **4. Datos de Prueba** 🧪
- **Formato**: Archivo .sql con INSERTs
- **Contenido**:
  - Mínimo 10 registros por entidad principal
  - Datos realistas del ámbito elegido
  - Cobertura de todos los casos de uso
- **Naming**: `P01_DatosPrueba_EquipoX.sql`

### **5. Documento de Justificación** 📋
- **Formato**: PDF (máximo 3 páginas)
- **Contenido**:
  - Decisiones de diseño tomadas
  - Proceso de normalización seguido
  - Problemas encontrados y soluciones
  - Futuras extensiones posibles
- **Naming**: `P01_Justificacion_EquipoX.pdf`

---

## ✅ **Criterios de Aceptación**

### **Funcionales**
- [ ] El modelo refleja los datos reales recopilados
- [ ] Está normalizado hasta 3FN mínimo
- [ ] Incluye los indicadores ASG seleccionados
- [ ] El esquema SQL es ejecutable sin errores
- [ ] Los datos de prueba cargan correctamente

### **Técnicos**
- [ ] Todas las tablas tienen clave primaria
- [ ] Las relaciones están correctamente implementadas
- [ ] Los constraints previenen datos inconsistentes
- [ ] Los tipos de datos son apropiados
- [ ] Los nombres siguen convenciones (snake_case)

### **Documentación**
- [ ] El diagrama ER es claro y completo
- [ ] El diccionario describe todas las entidades
- [ ] Las justificaciones están bien argumentadas
- [ ] Los archivos están correctamente nombrados
- [ ] El código SQL está comentado

---

## 🎯 **Cómo te evaluaremos**

Consulta la **[Rúbrica específica P01](../../docs/rubrica/R01-Rubrica.md)** para conocer los criterios detallados.

### **Resumen de Dimensiones**

| Dimensión | Peso | Qué evaluamos |
|:----------|:-----|:--------------|
| **Corrección técnica** | 40% | Normalización, SQL válido, integridad |
| **Completitud** | 25% | Todos los entregables, requisitos cumplidos |
| **Calidad del diseño** | 20% | Elegancia, escalabilidad, buenas prácticas |
| **Documentación** | 15% | Claridad, justificaciones, presentación |

### **Para alcanzar la Excelencia (9-10)**
- Normalización BCNF o superior
- Diseño especialmente elegante y escalable
- Documentación profesional y exhaustiva
- Innovación en el modelado (patrones avanzados)
- Validación con datos reales excepcional

---

## 📅 **Planificación Sugerida**

### **Semana 7: Análisis y Diseño**
- **Lunes**: Análisis de los datos recopilados
- **Miércoles**: Identificación de entidades y atributos
- **Viernes**: Primer borrador del diagrama ER

### **Semana 8: Implementación y Documentación**
- **Lunes**: Normalización y refinamiento
- **Miércoles**: Implementación del esquema SQL
- **Viernes**: Documentación y entrega

---

## 🆘 **¿Necesitas Ayuda?**

### **Recursos Adicionales**
- 📚 [Tutorial de normalización](../../docs/recursos/TUTORIAL-NORMALIZACION.md)
- 🎥 [Vídeo: Diagramas ER paso a paso](enlace-pendiente)
- 🔧 [Herramientas de modelado](../../docs/recursos/HERRAMIENTAS-BD.md)

### **Soporte**
- **Dudas técnicas**: Abre un [issue en GitHub](../../issues/new?template=duda-practica.md)
- **Problemas de equipo**: Habla con el profesor en tutoría
- **Consultas rápidas**: Canal Discord del módulo

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

## 📤 **Instrucciones de Entrega**

### **Dónde entregar**
- **Repositorio GitHub** del equipo
- **Carpeta**: `/practicas/P01-Modelado-ER/`
- **Branch**: `main` (tras revisión en `develop`)

### **Estructura de archivos**
```
P01-Modelado-ER/
├── README.md (este archivo)
├── diagramas/
│   ├── P01_DiagramaER_EquipoX.pdf
│   └── P01_DiagramaER_EquipoX.drawio
├── sql/
│   ├── P01_EsquemaBD_EquipoX.sql
│   └── P01_DatosPrueba_EquipoX.sql
├── docs/
│   ├── P01_Diccionario_EquipoX.md
│   └── P01_Justificacion_EquipoX.pdf
└── evidencias/
    └── capturas_funcionamiento/
```

### **Fecha límite**
**📅 Viernes 15 de octubre a las 23:59**

⚠️ **Importante**: Entregas tardías tienen penalización del 10% por día.

---

## 🔄 **Actividad de origen**

Esta práctica deriva de: [Actividad Sesión 4: Modelado](../../actividades/Sesion4_Actividad_Modelado.md)

---

**🎓 ¡Buena suerte con vuestro primer modelo de datos!**

**📅 Creado**: 26 octubre 2025  
**👨‍🏫 Responsable**: Equipo docente Digitalización + Sostenibilidad