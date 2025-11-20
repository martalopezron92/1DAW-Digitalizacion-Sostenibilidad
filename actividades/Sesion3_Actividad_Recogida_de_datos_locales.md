# 🧩 Actividad – Diseño y planificación de la recogida de datos locales

## 🎯 Objetivo
Definir **cómo se obtendrán los datos del centro educativo** relacionados con el ámbito de sostenibilidad elegido por el grupo (energía, residuos, movilidad, TIC, etc.), aplicando criterios técnicos de calidad, ética y cumplimiento del **RGPD**.

El resultado de esta sesión será un **plan técnico de recogida de datos** o una **encuesta digital funcional** que servirá para alimentar la base de datos del proyecto.

---

## 🧠 Contexto
Hasta ahora, el alumnado ha comprendido:
- Qué son las **fuentes de datos** (internas y externas).
- Qué información se quiere analizar.
- Qué indicadores sostenibles son relevantes para el centro.

En esta sesión toca **pasar a la acción**: diseñar la forma en que se recopilarán los datos **reales o estimados** del entorno.

---

## 🧱 Tareas a realizar

### Fase 1 – Definición del ámbito y variables (30 min)
1. Revisar el ámbito asignado (energía, residuos, movilidad…).  
2. Listar las **variables a medir**, indicando tipo de dato y unidad.

   | Variable | Tipo | Unidad | Método previsto |
   |-----------|------|---------|----------------|
   | Consumo medio de PC | Numérico | kWh/semana | Estimación |
   | Uso de enchufes inteligentes | Booleano | – | Sensor IoT |
   | Horas de uso de aula | Numérico | h/día | Encuesta |

3. Documentar el listado en una hoja compartida o documento del grupo.

---

### Fase 2 – Selección del método de recogida (30 min)
Cada grupo debe decidir **cómo obtendrá los datos** para cada variable:

| Método | Cuándo usarlo | Ejemplo técnico |
|---------|----------------|----------------|
| **Encuesta digital** | Para hábitos, opiniones o datos humanos | Google Forms sobre modos de transporte |
| **Estimación** | Cuando no hay datos medibles directos | Calcular consumo a partir de potencia y horas de uso |
| **Sensor o medición automática** | Para datos continuos o precisos | Sensor DHT22 o smart plug |
| **Observación directa** | Para recuentos o inspecciones simples | Número de bicicletas o residuos generados |

📌 Cada grupo debe usar al menos **dos métodos distintos** para complementar la información.

---

### Fase 3 – Diseño técnico de la recogida (45 min)
1. **Si usan encuestas digitales:**
   - Crear el formulario en **Google Forms, Microsoft Forms o LimeSurvey**.
   - Incluir entre 8 y 12 preguntas con tipos variados.
   - Añadir una introducción explicando propósito y anonimización.
   - Configurar la recogida de respuestas anónimas.
   - Exportar una vista previa en PDF o enlace público.

2. **Si usan estimaciones:**
   - Crear una **tabla de cálculo** con fórmulas (por ejemplo, \(E = P × t × n\)).
   - Justificar el origen de los valores (catálogo, medición, observación…).

3. **Si usan sensores:**
   - Describir hardware, magnitud medida y frecuencia de lectura.
   - Indicar cómo se almacenarán los datos (CSV, BD local, etc.).
   - Dibujar un **diagrama simple** del flujo de datos.

4. **Si usan observación directa:**
   - Diseñar una plantilla de registro con fecha, lugar y variable.
   - Definir responsables y calendario de recogida.

---

### Fase 4 – Control de calidad y cumplimiento RGPD (15 min)
Antes de finalizar:
- Verificar que no se recogen datos personales identificables.
- Comprobar las **reglas de calidad**: completitud, coherencia y precisión.
- Rellenar la **checklist RGPD** proporcionada en clase.

---

## 📦 Producto final
Cada grupo entregará:

1. **Documento resumen (.docx o .pdf)** con:
   - Ámbito y variables definidas.
   - Tabla de métodos elegidos.
   - Explicación técnica del proceso.
   - Captura o enlace del formulario o sensor.
   - Diagrama del flujo de datos.

2. **Enlace o archivo funcional**:
   - Enlace público al formulario.  
   - Hoja de cálculo con estimaciones.  
   - Script o fichero de registro (si usan sensores).

---

## 🧩 Evaluación

| Criterio | Indicador observable | Instrumento |
|-----------|----------------------|--------------|
| **DIG-RA1 / RA2** | Usa herramientas digitales adecuadas para la captura de datos. | Rúbrica de diseño de encuesta o sensor |
| **DIG-RA5** | Aplica buenas prácticas de seguridad y privacidad de datos. | Checklist de cumplimiento RGPD |
| **SOST-RA1** | Selecciona indicadores sostenibles pertinentes y medibles. | Análisis del documento entregado |

---

## 💡 Ejemplo práctico orientativo
Grupo “Energía” decide medir el consumo en laboratorios:
- Variables: consumo eléctrico, horas de uso de equipos, temperatura ambiente.  
- Métodos:
  - Estimación con fórmula \(E = P × n × t\).  
  - Sensor de corriente INA219 conectado a Arduino.  
  - Encuesta sobre hábitos de apagado de equipos.  
- Flujo de datos:  
  **Sensor/Encuesta → CSV → MySQL → Power BI (análisis en trimestre 2)**.
