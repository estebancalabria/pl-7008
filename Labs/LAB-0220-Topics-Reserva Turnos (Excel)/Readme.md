# 🧪 Laboratorio - Manage Topics en un Agente de Reserva de Turnos (Copilot Studio + Excel Online)

En este laboratorio vas a aprender a trabajar con **Topics en Microsoft Copilot Studio** creando un agente de reserva de turnos médicos.

Vas a ver cómo los topics permiten estructurar conversaciones, controlar el flujo de preguntas y, además, cómo persistir datos en **Excel Online (Business)** como base de datos simple.

Este laboratorio se enfoca en:

* Diseño de Topics
* Control de conversación
* Variables
* Integración directa con Excel Online (Business)

---

# 🎯 Objetivos del laboratorio

Al finalizar este laboratorio vas a poder:

* Entender qué es un Topic y cuándo se dispara
* Crear topics usando Copilot (lenguaje natural)
* Crear topics manuales con trigger phrases
* Editar conversaciones con variables
* Forzar flujos estructurados paso a paso
* Persistir datos en Excel Online (Business)
* Controlar conversaciones con confirmaciones
* Probar cómo los topics compiten con la IA generativa

---

# 📌 Requisitos

Antes de comenzar necesitás:

* Una cuenta Microsoft
* Acceso a [Microsoft Copilot Studio](https://copilotstudio.microsoft.com)
* Acceso a **Excel Online (Business)** (OneDrive o SharePoint)

---

# 📊 Paso 0 - Preparar Excel (Base de datos de turnos)

Antes de ir a Copilot Studio:

1. Crear un archivo en OneDrive o SharePoint:

   ```text
   turnos.xlsx
   ```

2. Crear una tabla con estos campos:

| Nombre | Especialidad | Doctor | Fecha | Estado |
| ------ | ------------ | ------ | ----- | ------ |

3. Convertirlo en tabla:

* Insertar → Tabla
* Nombre de la tabla:

```text
Turnos
```

💡 Esto será la “base de datos” del agente.

---

# 🚀 Paso 1 - Ingresar a Copilot Studio

Abrí el navegador e ingresá a:

👉 [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)

---

# 🤖 Paso 2 - Crear un nuevo agente

1. Ir a **Agents**
2. Seleccionar **New agent**
3. En la descripción del agente escribir:

```text
Create an assistant to help users book medical appointments.
```

💡 El agente se generará automáticamente con IA generativa habilitada.

---

# 🧠 Paso 3 - Entender el comportamiento inicial

Probá en el panel de test:

```text
I need a doctor
```

💡 El agente responde con IA generativa porque todavía no definiste topics.

---

# 🧹 Paso 4 - Revisar topics existentes

Ir a:

```text
Topics
```

Revisar los system topics disponibles.

💡 Podés deshabilitar “Start Over” si querés reducir interferencias.

---

# 🧠 Paso 5 - Crear Topic con Copilot (Reserva de turno)

1. Seleccionar **Add a topic**
2. Elegir **Add from description with Copilot**

## Nombre del topic

```text
Book Appointment
```

## Descripción

```text
Help the user book a medical appointment by collecting specialty, doctor, date, and saving the appointment.
```

3. Seleccionar **Create**

---

# ✏️ Paso 6 - Revisar el topic generado

Verificá que incluya:

* Especialidad médica
* Doctor
* Fecha del turno

💡 Cada respuesta se guarda en variables del tipo:

* Topic.Specialty
* Topic.Doctor
* Topic.Date

---

# 🧩 Paso 7 - Personalizar la conversación

Editar una pregunta usando Copilot:

```text
Thank the user and then ask for the preferred doctor.
```

---

# 💾 Paso 8 - Agregar acción: guardar en Excel Online (Business)

Este es el paso clave del laboratorio.

Dentro del Topic:

1. Agregar nodo:
   👉 **Add node → Action**

2. Seleccionar:

👉 **Excel Online (Business)**

3. Elegir acción:

```text
Add a row into a table
```

4. Configurar:

* File: `turnos.xlsx`
* Table: `Turnos`

5. Mapear campos:

* Nombre → Topic.Name
* Especialidad → Topic.Specialty
* Doctor → Topic.Doctor
* Fecha → Topic.Date
* Estado → "Confirmed"

💡 Esto guarda el turno directamente en Excel.

---

# 🔁 Paso 9 - Agregar confirmación

Agregar un nodo de pregunta:

```text
Do you confirm the appointment details?
```

Opciones:

* Yes → guardar en Excel
* No → finalizar flujo

---

# 🎯 Paso 10 - Crear Topic manual (Cancelar turno)

1. Ir a **Add topic**
2. Seleccionar **From blank**

## Nombre

```text
Cancel Appointment
```

## Trigger phrases

```text
cancel appointment
I want to cancel my appointment
delete my booking
```

---

# 🧠 Paso 11 - Flujo de cancelación

Preguntar:

```text
What is your name or appointment date?
```

Luego:

```text
Do you confirm cancellation?
```

💡 (Opcional avanzado: podrías luego agregar eliminación en Excel)

---

# 🧪 Paso 12 - Probar el agente

Probar:

```text
I want to book a doctor
```

Flujo esperado:

* Especialidad
* Doctor
* Fecha
* Confirmación
* Guardado en Excel

---

Probar también:

```text
Cancel my appointment
```

---

# 📖 ¿Qué aprendiste?

En este laboratorio aprendiste a:

* Crear Topics estructurados
* Usar IA generativa para construir flujos
* Controlar conversación con variables
* Persistir datos en Excel Online (Business)
* Construir un sistema básico de reservas
* Separar flujos (reservar vs cancelar)

---

# 🧠 Conceptos importantes

## 🔹 Topics

Flujos controlados dentro del agente.

## 🔹 Variables

Datos temporales dentro del conversation flow.

## 🔹 Excel Online (Business)

Base de datos simple basada en tablas.

## 🔹 IA vs Topics

* IA → conversación libre
* Topics → flujo estructurado

## 🔹 Excel como backend

Permite persistencia sin Dataverse ni Power Automate.

---

# 🎉 Fin del laboratorio

Ahora tenés un agente funcional de reservas de turnos usando:

* Copilot Studio
* Topics
* Variables
* Excel Online (Business)

Todo sin Dataverse y sin Power Automate 🚀
