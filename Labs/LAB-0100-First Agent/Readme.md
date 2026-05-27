# 🧪 Laboratorio - Crear un Agente Declarativo en Microsoft Copilot Studio

En este laboratorio vas a aprender a crear un agente en [Microsoft Copilot Studio](https://copilotstudio.microsoft.com?utm_source=chatgpt.com) utilizando lenguaje natural, agregando instrucciones, temas (topics) y una fuente de conocimiento basada en documentos.

No necesitás experiencia previa.
La idea es entender cómo construir un agente paso a paso y probarlo desde un sitio web de demostración.

---

# 🎯 Objetivos del laboratorio

Al finalizar este laboratorio vas a poder:

* Crear un agente desde una descripción
* Configurar instrucciones del agente
* Deshabilitar la búsqueda web
* Probar conversaciones
* Crear y editar temas (Topics)
* Agregar conocimiento desde un archivo `.docx`
* Publicar el agente
* Usar el sitio web de demostración

---

# 📌 Requisitos

Antes de comenzar necesitás:

* Una cuenta Microsoft
* Acceso a [Microsoft Copilot Studio](https://copilotstudio.microsoft.com?utm_source=chatgpt.com)

---

# 🚀 Paso 1 - Ingresar a Copilot Studio

Abrí el navegador e ingresá a:

[Microsoft Copilot Studio](https://copilotstudio.microsoft.com?utm_source=chatgpt.com)

---

# 🤖 Paso 2 - Crear un nuevo agente

1. En el menú lateral, seleccioná **Agentes**
2. Hacé clic en **Nuevo agente**
3. En la descripción del agente escribí:

```text
Create an agent to help employees with expense claims.
```

💡 **¿Qué está pasando acá?**

Copilot Studio puede generar automáticamente un agente a partir de una descripción escrita en lenguaje natural.
La IA interpreta el objetivo y configura una base inicial del agente.

---

# 📝 Paso 3 - Configurar instrucciones

En la sección **Instructions** agregá:

```text
Maintains a friendly and professional tone.
```

Luego agregá otra instrucción:

```text
Avoid providing any tax advice.
```

💡 **¿Para qué sirven las instrucciones?**

Las instrucciones ayudan a controlar:

* El tono del agente
* Qué tipo de respuestas debe dar
* Qué cosas debe evitar responder

Son similares a un *prompt del sistema*.

---

# 🌐 Paso 4 - Deshabilitar búsqueda web

1. Ir a la sección **Knowledge**
2. Buscar la opción de **Web search**
3. Deshabilitarla

💡 Esto evita que el agente busque información en internet y hace que responda únicamente usando su configuración y las fuentes de conocimiento definidas.

---

# 🧪 Paso 5 - Probar el agente

Usá el panel de prueba y escribí:

```text
Who should I contact about submitting an expense claim?
```

Luego probá:

```text
What's the expense limit for a hotel stay?
```

💡 En este punto el agente todavía tiene poco conocimiento, por lo que algunas respuestas pueden ser genéricas.

---

# 🧠 Paso 6 - Explorar Topics (Temas)

Ir a:

```text
Topics
```

Los Topics representan conversaciones o intenciones que el agente puede manejar.

Existen:

* Topics personalizados
* Topics generados automáticamente
* System Topics (temas del sistema)

---

# ✏️ Paso 7 - Editar el tema de agradecimiento

1. Abrí el topic de agradecimiento (Thank you)
2. Editá el mensaje si querés personalizar la respuesta

💡 Los System Topics permiten controlar comportamientos comunes como:

* Saludos
* Agradecimientos
* Errores
* Conversaciones desconocidas

---

# ➕ Paso 8 - Crear un Topic desde una descripción

Crear un nuevo Topic usando IA.

## Nombre

```text
Ask about expenses contact
```

## Descripción

```text
When the user asks who to contact about expense claims, tell them to send an email to finance@contoso.com
```

💡 Nuevamente Copilot Studio genera automáticamente la lógica conversacional usando lenguaje natural.

---

# 🧪 Paso 9 - Probar el nuevo Topic

Probá nuevamente:

```text
Who should I contact about submitting an expense claim?
```

Ahora el agente debería responder indicando:

```text
finance@contoso.com
```

---

# 💾 Paso 10 - Guardar el agente

Hacé clic en:

```text
Save
```

---

# 📄 Paso 11 - Descargar archivo de políticas

Descargá el siguiente archivo:

[Expenses_Policy.docx](https://github.com/MicrosoftLearning/mslearn-copilotstudio/raw/main/expenses/Expenses_Policy.docx?utm_source=chatgpt.com)

Este archivo contiene políticas de gastos que el agente podrá consultar.

---

# 📚 Paso 12 - Agregar fuente de conocimiento

1. Ir a **Knowledge**
2. Seleccionar **Add knowledge**
3. Subir el archivo:

```text
Expenses_Policy.docx
```

💡 Ahora el agente podrá responder preguntas basadas en el contenido del documento.

---

# 🔐 Paso 13 - Deshabilitar autenticación

Ir a:

```text
Settings → Security → Authentication
```

Deshabilitar la autenticación.

⚠️ Esto se hace únicamente para simplificar las pruebas del laboratorio.

---

# ⏳ Paso 14 - Esperar el indexado del archivo

El archivo necesita procesarse antes de poder usarse.

1. Ir nuevamente a **Knowledge**
2. Revisar el estado del archivo

Esperá hasta que aparezca:

```text
Ready
```

Si aparece:

```text
In progress
```

esperá unos minutos y refrescá la página.

💡 **¿Qué significa indexar?**

Copilot Studio analiza el documento y crea un índice para que el agente pueda buscar información rápidamente.

---

# 🧠 Paso 15 - Revisar el Topic de “Conversational boosting”

Ir a:

```text
Topics
```

Abrir:

```text
Conversational boosting
```

💡 Este topic especial se activa cuando el agente no encuentra un topic específico y necesita generar respuestas usando IA y fuentes de conocimiento.

Es el mecanismo que permite responder preguntas basadas en documentos cargados.

---

# 🚀 Paso 16 - Publicar el agente

Para usar el sitio web de demostración, el agente debe estar publicado.

1. Hacer clic en **Publish**
2. Volver a seleccionar **Publish**

💡 Publicar significa que la última versión del agente queda disponible para usarse en canales externos.

---

# 🌍 Paso 17 - Abrir el sitio web de demostración

1. Ir a **Channels**
2. Seleccionar:

```text
Demo website
```

3. Hacer clic en:

```text
Open demo website
```

---

# 🧪 Paso 18 - Probar preguntas sobre políticas de gastos

Escribí:

```text
What's the expense limit for a hotel stay?
```

Ahora la respuesta debería basarse en el documento cargado y mostrar citas o referencias.

---

# 🔍 Paso 19 - Hacer preguntas adicionales

Probá también:

```text
What about flights?
```

```text
What guidelines are there for entertainment expenses?
```

```text
What are the expense limits for meals?
```

💡 El agente buscará información dentro del documento utilizando IA generativa.

---

# 📖 ¿Qué aprendiste?

En este laboratorio aprendiste a:

✅ Crear agentes usando lenguaje natural
✅ Configurar instrucciones
✅ Trabajar con Topics
✅ Agregar conocimiento desde documentos
✅ Utilizar respuestas generativas
✅ Publicar agentes
✅ Probar un agente desde un sitio web

---

# 🧠 Conceptos importantes

## 🔹 Topics

Son flujos conversacionales que representan intenciones del usuario.

---

## 🔹 Conversational Boosting

Permite generar respuestas utilizando IA y fuentes de conocimiento.

---

## 🔹 Knowledge Sources

Son documentos o datos que el agente utiliza para responder preguntas.

---

## 🔹 Publicación

Un agente debe publicarse antes de poder utilizarse en canales externos.

---

# 🎉 Fin del laboratorio

Ya creaste y publicaste tu primer agente declarativo en Microsoft Copilot Studio 🚀
