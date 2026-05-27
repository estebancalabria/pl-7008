# Administrar temas en Microsoft Copilot Studio

## Introducción

Microsoft Copilot Studio permite crear agentes virtuales inteligentes capaces de interactuar con usuarios mediante conversaciones dinámicas y contextuales. Estos agentes utilizan **temas (topics)** para organizar y controlar las distintas rutas conversacionales.

Un tema representa una conversación enfocada en un objetivo específico, como:

- Saludos
- Consultas sobre cuentas
- Clima
- Soporte técnico
- Escalación a agentes humanos
- Finalización de conversaciones

Los agentes usan inteligencia artificial y comprensión del lenguaje natural para identificar la intención del usuario y activar el tema adecuado.

---

# Componentes principales de un tema

Cada tema está compuesto por:

## Frases desencadenadoras
Son palabras, frases o preguntas que permiten detectar cuándo debe iniciarse un tema.

Ejemplos:

- “¿Qué tiempo hace?”
- “Necesito devolver un producto”
- “Horario de atención”

Buenas prácticas:

- Usar frases cortas y naturales.
- Agregar entre 5 y 10 frases iniciales.
- Evitar ambigüedades entre temas.

---

## Nodos de conversación

Definen el flujo de la conversación y las acciones que realizará el agente.

Tipos de nodos:

- Enviar mensajes
- Formular preguntas
- Agregar condiciones
- Administrar variables
- Llamar acciones de Power Automate
- Transferir conversaciones
- Finalizar conversaciones
- Utilizar respuestas generativas y HTTP

---

# Diseño de rutas conversacionales

Los temas permiten construir rutas dinámicas según las respuestas del usuario.

Ejemplo:

1. El usuario consulta sobre el clima.
2. El agente pregunta la ciudad.
3. Guarda la respuesta en una variable.
4. Consulta un servicio externo.
5. Devuelve una respuesta personalizada.

---

# Uso de preguntas y variables

Los nodos de preguntas permiten:

- Capturar información del usuario.
- Validar entradas.
- Guardar datos en variables.
- Modificar el flujo conversacional.

Copilot Studio incluye entidades predefinidas como:

- Ciudad
- Correo electrónico
- Fecha
- Número telefónico
- Nombre de persona

Ejemplo:

```text
Usuario: Vivo en Seattle
