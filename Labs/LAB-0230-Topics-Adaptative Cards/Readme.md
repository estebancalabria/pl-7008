# 🧪 Laboratorio — Tarjetas Adaptativas en un Topic de Rendición de Gastos (Copilot Studio)

En este laboratorio vas a crear un agente en [Microsoft Copilot Studio](https://copilotstudio.microsoft.com?utm_source=chatgpt.com) que permita cargar una rendición de gastos usando una **Adaptive Card**.

El usuario podrá completar:

* Tipo de gasto (`Viaje`, `Hotel`, `Comida`, `Entretenimiento`)
* Apellido
* DNI
* Monto

Y el agente responderá:

> ✅ Ok, registrado.

---

# 🎯 Objetivo

Aprender a:

* Crear un Topic
* Usar una Adaptive Card
* Capturar datos ingresados por el usuario
* Guardarlos en variables
* Mostrar una confirmación

---

# 🚀 Paso 1 — Entrar a Copilot Studio

Ingresá a:

[Microsoft Copilot Studio](https://copilotstudio.microsoft.com?utm_source=chatgpt.com)

Iniciá sesión con tu cuenta Microsoft.

---

# 🚀 Paso 2 — Crear un Agente

1. Presioná:

   * **Create**
   * o **Nuevo agente**

2. Nombre:

```text
Agente Rendición Gastos
```

3. Idioma:

```text
Español
```

4. Crear agente.

---

# 🚀 Paso 3 — Ir a Topics

En el menú lateral:

```text
Topics
```

---

# 🚀 Paso 4 — Crear un Topic Nuevo

Presioná:

```text
+ Add a topic
```

Nombre:

```text
Rendir gasto
```

---

# 🚀 Paso 5 — Agregar Frases Disparadoras

Agregá ejemplos:

```text
Quiero rendir un gasto
Registrar gasto
Cargar viáticos
Rendir viático
Ingresar gasto
```

Guardar.

---

# 🚀 Paso 6 — Agregar una Tarjeta Adaptativa

Dentro del flujo del topic:

Presioná el botón:

```text
+
```

Luego:

```text
Send a message
```

Y elegí:

```text
Adaptive Card
```

---

# 🚀 Paso 7 — Pegar el JSON de la Adaptive Card

Pegá esta tarjeta:

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.5",
  "body": [
    {
      "type": "TextBlock",
      "text": "Rendición de Gastos",
      "weight": "Bolder",
      "size": "Large"
    },
    {
      "type": "Input.ChoiceSet",
      "id": "tipoGasto",
      "label": "Tipo de gasto",
      "style": "compact",
      "choices": [
        {
          "title": "Viaje",
          "value": "Viaje"
        },
        {
          "title": "Hotel",
          "value": "Hotel"
        },
        {
          "title": "Comida",
          "value": "Comida"
        },
        {
          "title": "Entretenimiento",
          "value": "Entretenimiento"
        }
      ]
    },
    {
      "type": "Input.Text",
      "id": "apellido",
      "label": "Apellido"
    },
    {
      "type": "Input.Text",
      "id": "dni",
      "label": "DNI"
    },
    {
      "type": "Input.Number",
      "id": "monto",
      "label": "Monto"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Registrar"
    }
  ]
}
```

---

# 🚀 Paso 8 — Guardar Respuestas en Variables

Después de pegar la tarjeta:

Copilot Studio detectará automáticamente los campos.

Vas a ver variables similares a:

| Campo     | Variable    |
| --------- | ----------- |
| tipoGasto | `tipoGasto` |
| apellido  | `apellido`  |
| dni       | `dni`       |
| monto     | `monto`     |

Estas variables contendrán los datos ingresados por el usuario.

---

# 🚀 Paso 9 — Agregar Mensaje de Confirmación

Debajo de la tarjeta:

Presioná:

```text
+
```

Luego:

```text
Send a message
```

Escribí:

```text
✅ Ok, registrado.
```

---

# 🚀 Paso 10 — Guardar el Topic

Presioná:

```text
Save
```

---

# 🚀 Paso 11 — Probar el Agente

Abrí el panel de prueba.

Escribí:

```text
Quiero rendir un gasto
```

La tarjeta aparecerá.

Completá:

* Tipo de gasto
* Apellido
* DNI
* Monto

Presioná:

```text
Registrar
```

Resultado esperado:

```text
✅ Ok, registrado.
```

---

# 🧠 Qué aprendiste

En este laboratorio viste:

| Concepto        | Uso                  |
| --------------- | -------------------- |
| Topic           | Flujo conversacional |
| Trigger phrases | Activan el topic     |
| Adaptive Card   | Formulario visual    |
| Variables       | Guardan datos        |
| Action.Submit   | Envía la información |

---

# 📌 Resultado Final

El agente:

1. Detecta intención de rendir gasto
2. Muestra un formulario visual
3. Captura datos
4. Confirma el registro

