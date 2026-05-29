# 🧪 Laboratorio — Rendición de Gastos con Adaptive Card + Excel (Copilot Studio)

En este laboratorio vas a crear un agente en **Microsoft Copilot Studio** que permita registrar gastos mediante una **Adaptive Card** y guardarlos automáticamente en un archivo Excel.

---

# 🎯 Objetivo

Aprender a:

- Crear un Topic
- Usar una Adaptive Card como formulario
- Capturar datos del usuario
- Guardarlos en variables
- Crear un Excel con tabla
- Crear un flujo desde Copilot Studio
- Guardar datos en Excel automáticamente
- Confirmar la operación al usuario

---

# 🧱 Arquitectura del laboratorio

```

Usuario → Copilot (Topic) → Flujo → Excel

```

📌 El agente conversa  
📌 El flujo ejecuta  
📌 Excel guarda  

---

# 🚀 Paso 1 — Crear el Excel

## 👉 1. Crear archivo

Abrí Excel (OneDrive o SharePoint)

Crear archivo:

```

RendicionGastos.xlsx

```

---

## 👉 2. Crear columnas

Primera fila:

```

Apellido | Dni | Monto | TipoGasto

```

---

## 👉 3. Convertir en tabla

Seleccionar toda la fila:

👉 Insert → Tabla  
👉 Confirmar que tiene encabezados  

📌 Importante: el flujo SOLO funciona con tabla  

---

## 👉 4. Nombrar la tabla

Ejemplo:

```

TablaGastos

```

---

# 🚀 Paso 2 — Crear el Flujo

## 👉 1. Crear flujo desde Copilot Studio

En el menú lateral izquierdo ir a:

```

Flujos

```

Luego presionar:

```

* Nuevo flujo

```

Copilot Studio te va a pedir:

```

¿Qué desea que haga su flujo?

```

Ejemplo:

```

Guardar una rendición de gastos en Excel

```

Copilot generará automáticamente el flujo y se abrirá el editor para configurarlo.

---

## 👉 2. Configurar el trigger

Elegir:

```

Cuando un agente llama al flujo

```

---

## 👉 3. Crear inputs

Agregar:

| Nombre     | Tipo   |
|-----------|--------|
| apellido  | Texto  |
| dni       | Texto  |
| monto     | Número |
| tipoGasto | Texto  |

---

## 👉 4. Acción Excel

Agregar:

```

Agregar una fila en una tabla

```

Completar:

- Archivo: Excel creado  
- Tabla: `TablaGastos`  

---

## 👉 5. Mapear campos

| Columna Excel | Valor      |
|--------------|-----------|
| Apellido     | apellido  |
| Dni          | dni       |
| Monto        | monto     |
| TipoGasto    | tipoGasto |

---

## 👉 6. Guardar flujo

---

# 🚀 Paso 3 — Crear el Topic

## 👉 1. Ir a Topics

```

* Add a topic

```

Nombre:

```

Rendir gasto

```

---

## 👉 2. Frases disparadoras

```

Quiero rendir un gasto
Registrar gasto
Cargar viáticos
Ingresar gasto

```

---

# 🚀 Paso 4 — Crear Adaptive Card

Agregar nodo:

```

Send a message → Adaptive Card

````

---

## 👉 JSON

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
        { "title": "Viaje", "value": "Viaje" },
        { "title": "Hotel", "value": "Hotel" },
        { "title": "Comida", "value": "Comida" },
        { "title": "Entretenimiento", "value": "Entretenimiento" }
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
````

***

# 🚀 Paso 5 — Variables

Copilot crea automáticamente:

```
Topic.tipoGasto  
Topic.apellido  
Topic.dni  
Topic.monto  
```

***

# 🚀 Paso 6 — Llamar al flujo

Agregar nodo:

```
+ → Acción / Herramienta
```

Seleccionar el flujo creado.

***

## 👉 Mapear inputs

| Flujo     | Valor           |
| --------- | --------------- |
| apellido  | Topic.apellido  |
| dni       | Topic.dni       |
| monto     | Topic.monto     |
| tipoGasto | Topic.tipoGasto |

***

# 🚀 Paso 7 — Confirmación

Agregar mensaje:

```
✅ Ok, registrado.
```

***

# 🚀 Paso 8 — Probar

Abrir panel de prueba:

```
Quiero rendir un gasto
```

Completar:

* Tipo de gasto
* Apellido
* DNI
* Monto

***

## ✅ Resultado esperado

* Se guarda en Excel ✅
* El agente responde:

```
✅ Ok, registrado.
```

***

# 🧠 Qué aprendiste

| Concepto      | Uso                  |
| ------------- | -------------------- |
| Topic         | Flujo conversacional |
| Adaptive Card | Formulario visual    |
| Variables     | Guardan datos        |
| Flujo         | Ejecuta lógica       |
| Excel Table   | Persistencia         |

***

# 🎯 Resultado final

```
1. Detecta intención
2. Muestra formulario
3. Captura datos
4. Llama flujo
5. Guarda en Excel
6. Confirma
```

***

# 💡 Insight clave (para tu clase)

👉 Esto es LO más importante:

```
Copilot → conversa  
Flujo → ejecuta  
Excel → guarda  
```

