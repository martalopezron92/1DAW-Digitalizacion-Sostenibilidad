# 🧠 Sesión 3 – Recogida de datos locales

## 1️⃣ Fase de adquisición de datos en un sistema digital

En cualquier proyecto de **analítica de datos o sostenibilidad digital**, la primera etapa es la **adquisición de datos**.  
El objetivo es transformar observaciones del mundo real (energía, residuos, movilidad, etc.) en **valores digitales estructurados**, almacenables en una base de datos.

El proceso general sigue este flujo:

```
FUENTE DE DATOS → CAPTURA → VALIDACIÓN → NORMALIZACIÓN → ALMACENAMIENTO (BD)
```

---

## 2️⃣ Métodos de recogida de datos

Según el tipo de variable (cuantitativa, cualitativa, continua o discreta) y el grado de automatización, se utilizan distintos métodos. En el proyecto se recomiendan cuatro técnicas principales:

### 🔹 1. Encuestas digitales

Método orientado a recopilar **datos cualitativos o de comportamiento humano** mediante formularios online.

#### Tecnologías recomendadas
- **Google Forms / Microsoft Forms:** interfaz visual y exportación directa a CSV o Google Sheets.  
- **LimeSurvey o Nextcloud Forms:** opción libre y autohospedada para cumplir RGPD.  

#### Ejemplo de aplicación
Encuesta sobre movilidad del alumnado:
| Pregunta | Tipo de dato | Variable almacenada |
|-----------|---------------|---------------------|
| ¿Cómo vienes al centro? (a pie, bici, bus, coche) | Texto corto | `modo_transporte` |
| Distancia aproximada (km) | Numérico (float) | `distancia_km` |
| ¿Compartes vehículo? (sí/no) | Booleano | `carpool` |

Los resultados pueden exportarse en formato **CSV** y cargarse con Python o SQL:

```sql
LOAD DATA INFILE 'movilidad.csv'
INTO TABLE movilidad
FIELDS TERMINATED BY ','
IGNORE 1 LINES
(modo_transporte, distancia_km, carpool);
```

#### Buenas prácticas técnicas
- Usar **nombres de campos cortos y sin espacios**.  
- Homogeneizar las unidades (km, litros, kWh…).  
- Evitar preguntas abiertas que dificulten el análisis.

---

### 🔹 2. Estimaciones y cálculos indirectos

Útil cuando los datos reales no están disponibles o los sensores no existen.  
Consiste en **modelar o inferir** un valor mediante fórmulas físicas o lógicas.

#### Ejemplo técnico
Cálculo del consumo eléctrico medio de un aula de informática:

| Equipo | Potencia (W) | Nº unidades | Horas/día | Días/semana |
|---------|----------------|-------------|------------|--------------|
| PC sobremesa | 250 | 15 | 4 | 5 |
| Monitor LED | 50 | 15 | 4 | 5 |
| Router | 20 | 1 | 24 | 7 |

**Fórmula general:**
\[
E = \frac{P \times n \times t \times d}{1000}
\]

Ejemplo para PCs:
\[
E = \frac{250 \times 15 \times 4 \times 5}{1000} = 75\text{ kWh/semana}
\]

Estos valores se registran en una tabla SQL:

```sql
CREATE TABLE consumo_estimado (
  id INT AUTO_INCREMENT PRIMARY KEY,
  equipo VARCHAR(50),
  potencia_w INT,
  unidades INT,
  horas_dia FLOAT,
  dias_semana INT,
  kwh_semana FLOAT
);
```

---

### 🔹 3. Sensores e IoT (Internet of Things)

Método avanzado basado en **lecturas automáticas de dispositivos físicos** conectados a la red.

#### Hardware típico
| Sensor | Magnitud | Interfaz | Ejemplo de uso |
|---------|-----------|-----------|----------------|
| DHT22 | Temperatura / Humedad | GPIO / I2C | Control ambiental de aulas |
| BH1750 | Luminosidad | I2C | Verificación de eficiencia lumínica |
| INA219 | Corriente y tensión | I2C | Medir consumo en tiempo real |
| Smart Plug TP-Link | Energía | API HTTP | Monitorizar enchufes de laboratorio |

#### Ejemplo técnico (Python + Arduino)
```python
import serial, time
arduino = serial.Serial('COM3', 9600)
while True:
    lectura = arduino.readline().decode().strip()
    temperatura, humedad = lectura.split(',')
    print(f"T={temperatura}°C H={humedad}%")
    time.sleep(5)
```

Los datos pueden enviarse a un servidor con **HTTP POST** o almacenarse en **MySQL** mediante una API REST.

#### Ventajas
- Datos **continuos y precisos**.  
- Integración directa con sistemas IT/OT (Operational Technology).  

#### Precauciones
- Calibrar sensores periódicamente.  
- Gestionar correctamente la alimentación y la red (seguridad).  
- No transmitir información personal ni direcciones IP sin cifrado (usar HTTPS o VPN).

---

### 🔹 4. Observación directa y conteo manual

Método analógico que se digitaliza mediante hojas de cálculo o aplicaciones móviles.

#### Ejemplo técnico
Registro diario de residuos reciclados:

| Fecha | Tipo | Peso (kg) | Responsable |
|--------|------|-----------|-------------|
| 2025-10-21 | Papel | 4.2 | “Grupo A” |

Al finalizar la semana, se importa el CSV a la base de datos:

```sql
CREATE TABLE residuos (
  fecha DATE,
  tipo VARCHAR(20),
  peso_kg FLOAT,
  grupo VARCHAR(20)
);
```

Consulta de verificación:
```sql
SELECT tipo, SUM(peso_kg)
FROM residuos
GROUP BY tipo;
```

---

## 3️⃣ Control de calidad de los datos

Un dataset de baja calidad genera **errores de análisis y conclusiones falsas**.  
Se aplican reglas de **Data Quality Assurance (DQA)**:

| Criterio | Descripción | Control SQL / Python |
|-----------|-------------|----------------------|
| **Integridad** | No hay valores nulos | `SELECT * FROM tabla WHERE campo IS NULL;` |
| **Coherencia** | Rango y formato correctos | `CHECK (distancia_km BETWEEN 0 AND 50)` |
| **Duplicidad** | Sin registros repetidos | `SELECT campo, COUNT(*) FROM tabla GROUP BY campo HAVING COUNT(*)>1;` |
| **Actualización** | Datos recientes | `WHERE fecha > '2025-01-01'` |
| **Trazabilidad** | Registro de quién y cuándo | Campos `usuario`, `timestamp` |

Todo dataset debe incluir **metadatos**: fuente, método, fecha, unidades y responsable.

---

## 4️⃣ Privacidad y cumplimiento del RGPD

El Reglamento (UE) 2016/679 (RGPD) y la Ley Orgánica 3/2018 regulan el tratamiento de datos personales.  

### Principios técnicos
1. **Anonimización:** usar identificadores numéricos o hash.  
   ```sql
   UPDATE encuestas SET id_alumno = SHA2(email,256);
   ```
2. **Minimización:** no registrar datos sensibles.  
3. **Seguridad:** usuarios y contraseñas seguros.  
   ```sql
   CREATE USER 'recogida'@'localhost' IDENTIFIED BY 'ClaveFuerte#2025';
   GRANT INSERT, SELECT ON proyecto_datos.* TO 'recogida'@'localhost';
   ```
4. **Consentimiento:** informar del propósito de los datos.  
5. **Almacenamiento ético:** uso educativo, destrucción o anonimización al finalizar.

---

## 5️⃣ Ejemplo global integrado

**Caso: Análisis del consumo energético del centro**

1. **Datos internos:** estimaciones, sensores, encuestas.  
2. **Datos externos:** dataset del IDAE (consumo medio en centros educativos).  
3. **Base de datos:**

```sql
CREATE TABLE aulas (
  id_aula INT PRIMARY KEY,
  nombre VARCHAR(30),
  superficie INT
);

CREATE TABLE consumo (
  id INT AUTO_INCREMENT PRIMARY KEY,
  id_aula INT,
  kwh FLOAT,
  fecha DATE,
  FOREIGN KEY (id_aula) REFERENCES aulas(id_aula)
);
```

4. **Comprobaciones:** validación de rangos, permisos mínimos, cifrado de ficheros.

---

## 6️⃣ Conclusiones técnicas

- La recogida de datos es un proceso **técnico y regulado**.  
- La elección del método depende del tipo de variable y recursos.  
- Combinar encuestas, sensores y estimaciones mejora la fiabilidad.  
- Sin calidad ni privacidad, el análisis pierde valor técnico y ético.
