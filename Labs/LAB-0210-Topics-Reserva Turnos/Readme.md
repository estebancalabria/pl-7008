# 🧪 Laboratorio - Manage Topics en un Agente de Reserva de Turnos (Copilot Studio)

En este laboratorio vas a aprender a trabajar con **Topics en Microsoft Copilot Studio** creando un agente de reserva de turnos médicos.

Vas a ver cómo los topics permiten estructurar conversaciones, controlar el flujo de preguntas y evitar que la IA responda de forma libre cuando necesitamos un proceso ordenado.

No necesitás integración con sistemas externos.
Este laboratorio se enfoca exclusivamente en **cómo funcionan los Topics**.

---

# 🎯 Objetivos del laboratorio

Al finalizar este laboratorio vas a poder:

* Entender qué es un Topic y cuándo se dispara
* Crear topics usando Copilot (lenguaje natural)
* Crear topics manuales con trigger phrases
* Editar conversaciones con variables
* Forzar flujos estructurados paso a paso
* Probar cómo los topics compiten con la IA generativa
* Controlar conversaciones con confirmaciones

---

# 📌 Requisitos

Antes de comenzar necesitás:

* Una cuenta Microsoft
* Acceso a [Microsoft Copilot Studio](https://copilotstudio.microsoft.com)

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

💡 El agente se generará automáticamente con capacidades de IA generativa habilitadas.

---

# 🧠 Paso 3 - Entender el comportamiento inicial

Probá en el panel de test:

```text
I need a doctor
```

💡 En este punto el agente responde con IA generativa porque todavía no definiste topics.

---

# 🧹 Paso 4 - Revisar topics existentes

Ir a:

```text
Topics
```

Revisar los system topics disponibles.

Deshabilitar el topic:

* **Start Over**

💡 Esto reduce interferencias en la resolución de intenciones.

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
Help the user book a medical appointment by collecting specialty, preferred doctor, and appointment date.
```

3. Seleccionar **Create**

💡 Copilot generará automáticamente el flujo de conversación.

---

# ✏️ Paso 6 - Revisar el topic generado

Abrí el topic creado y verificá que incluya:

* Pregunta por especialidad médica
* Pregunta por doctor (opcional)
* Pregunta por fecha del turno

💡 Cada respuesta se guarda en variables del tipo:

* Topic.Specialty
* Topic.Doctor
* Topic.Date

---

# 🧩 Paso 7 - Personalizar la conversación

Editar la segunda pregunta:

```text
What doctor would you like to see?
```

Cambiarla usando Copilot:

```text
Thank the user by name and then ask for the preferred doctor.
```

💡 Esto demuestra cómo los topics permiten edición guiada con lenguaje natural.

---

# 🔁 Paso 8 - Agregar confirmación

Agregar un nuevo nodo de pregunta:

```text
Do you confirm the appointment details?
```

Opciones:

* Yes
* No

💡 Esto introduce control de flujo dentro del topic.

---

# 🎯 Paso 9 - Crear Topic manual (Cancelar turno)

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

💡 Este topic se dispara por coincidencia de frases del usuario.

---

# 🧠 Paso 10 - Definir flujo de cancelación

Agregar preguntas:

* “What is your email or booking ID?”

Luego:

* “Are you sure you want to cancel?”

Opciones:

* Yes → confirmación
* No → salir del flujo

---

# 🧪 Paso 11 - Probar el comportamiento del agente

Abrir el panel de test y probar:

```text
I want to book a doctor
```

Luego:

* responder especialidad
* responder doctor
* responder fecha
* confirmar

---

Probar también:

```text
Cancel my appointment
```

---

Y finalmente:

```text
What is Copilot Studio?
```

💡 Este último debería responder con IA generativa si no coincide con ningún topic.

---

# 🧠 Paso 12 - Observar el comportamiento de Topics vs IA

Durante las pruebas observar:

* cuándo se dispara un topic
* cuándo responde la IA generativa
* cómo el topic fuerza estructura
* cómo se almacenan variables
* cómo el sistema prioriza intents

---

# 📖 ¿Qué aprendiste?

En este laboratorio aprendiste a:

✅ Crear topics con IA generativa
✅ Crear topics manuales con trigger phrases
✅ Forzar flujos estructurados de conversación
✅ Usar variables dentro de topics
✅ Implementar confirmaciones
✅ Entender la competencia entre topics y IA generativa
✅ Controlar conversaciones paso a paso

---

# 🧠 Conceptos importantes

## 🔹 Topics

Son flujos estructurados que controlan la conversación del agente.

---

## 🔹 Trigger de topics

Un topic se activa por:

* frases del usuario (manual topics)
* interpretación del modelo (generative topics)
* contexto conversacional

---

## 🔹 Variables

Permiten almacenar información dentro del flujo.

Ejemplo:

* Specialty
* Doctor
* Date

---

## 🔹 IA generativa vs Topics

* IA → respuestas libres
* Topics → flujos controlados

---

# 🎉 Fin del laboratorio

Ya entendés cómo los Topics permiten transformar una conversación libre en un flujo estructurado y controlado dentro de Microsoft Copilot Studio 🚀
