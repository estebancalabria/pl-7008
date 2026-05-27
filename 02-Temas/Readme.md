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
````

El agente detecta automáticamente que “Seattle” es una ciudad.

---

# Ramificación de temas

La ramificación permite crear conversaciones no lineales.

Se pueden generar rutas distintas según:

* Respuestas del usuario
* Variables
* Condiciones
* Resultados de automatizaciones

Ejemplo:

```text
¿En qué país vive?
```

* Si vive en Estados Unidos → mostrar ofertas especiales.
* Si vive en otro país → seguir otro flujo.

Las preguntas de opción múltiple generan ramas automáticamente.

---

# Mensajes enriquecidos

Los mensajes pueden incluir:

* Texto
* Imágenes
* Videos
* Tarjetas básicas
* Tarjetas adaptables
* Respuestas rápidas

## Variaciones de mensajes

Permiten generar conversaciones más naturales.

Ejemplo:

* “Claro, puedo ayudarte.”
* “Será un placer ayudarte.”

El agente selecciona una variante aleatoriamente.

---

# Tarjetas adaptables

Las tarjetas adaptables utilizan JSON para crear experiencias dinámicas y visuales.

Pueden incluir:

* Gráficos
* Botones
* Formularios
* Información dinámica

Las tarjetas pueden mostrarse como:

* Carrusel
* Lista

---

# Respuestas rápidas

Las respuestas rápidas muestran botones sugeridos para facilitar la interacción y mejorar la detección de intención.

---

# Eventos y desencadenadores

Los temas también pueden activarse mediante eventos externos.

Ejemplos:

* Nuevo correo en Outlook
* Archivo creado en OneDrive
* Cambios en Dataverse
* Elementos creados en SharePoint

Esto permite integrar el agente con procesos empresariales y automatizaciones.

---

# Uso de Power Automate

El nodo **Llamar a una acción** permite ejecutar flujos de Power Automate para:

* Enviar correos
* Consultar APIs
* Crear registros
* Obtener información externa
* Automatizar procesos

---

# Temas sugeridos mediante IA

Copilot Studio puede crear temas automáticamente a partir de:

* FAQs
* Sitios de soporte
* Contenido web existente

La IA:

* Analiza páginas web
* Detecta preguntas frecuentes
* Genera frases desencadenadoras
* Crea temas sugeridos

Los temas sugeridos pueden:

* Editarse
* Agregarse al agente
* Eliminarse

---

# Temas alternativos del sistema

Cuando el agente no comprende la intención del usuario:

1. Intenta pedir aclaraciones.
2. Si falla nuevamente:

   * puede escalar la conversación
   * o usar un tema alternativo.

El tema alternativo permite:

* Hacer preguntas adicionales
* Mostrar categorías
* Redirigir conversaciones
* Ejecutar automatizaciones

La frase no reconocida se almacena en:

```text
UnrecognizedTriggerPhrase
```

---

# Administración de temas

Cada tema puede estar:

* Activado
* Desactivado

Los temas desactivados:

* no responden
* no pueden ejecutarse
* no aceptan redirecciones

---

# Comprobador de temas

Microsoft Copilot Studio incluye un validador llamado:

## Comprobador de temas

Permite detectar:

* Errores
* Advertencias
* Problemas de configuración

Tipos de errores:

* Nodo inválido
* Campo incompleto
* Expresión inválida
* Variables eliminadas

Los temas con errores no pueden publicarse en producción.

---

# Copiar temas

Los temas pueden duplicarse para reutilizar:

* Frases desencadenadoras
* Flujos conversacionales
* Nodos
* Configuraciones

Esto acelera el desarrollo de nuevos agentes.

---

# Capacidades de Bot Framework

Copilot Studio permite integrar capacidades de Bot Framework para ampliar funcionalidades.

Ventajas:

* Componentes reutilizables
* Automatización avanzada
* Integraciones complejas
* Conversaciones sofisticadas
* Capacidades personalizadas

Las capacidades pueden utilizarse para:

* Atención al cliente
* Programaciones
* Consultas especializadas
* Integraciones empresariales

---

# Objetivos del módulo

Al finalizar este módulo podrás:

* Crear y administrar temas.
* Diseñar rutas conversacionales.
* Configurar frases desencadenadoras.
* Utilizar preguntas y variables.
* Implementar ramificaciones.
* Crear temas automáticamente mediante IA.
* Configurar temas alternativos.
* Detectar errores con el comprobador de temas.
* Integrar Power Automate.
* Utilizar tarjetas adaptables.
* Integrar capacidades de Bot Framework.

---

# Conclusión

Microsoft Copilot Studio permite construir agentes conversacionales avanzados utilizando temas, nodos, ramificaciones, variables y automatizaciones. Gracias a la integración con inteligencia artificial, Power Automate y Bot Framework, es posible crear experiencias conversacionales modernas, escalables y personalizadas capaces de integrarse con sistemas empresariales y resolver múltiples escenarios de atención y automatización.

```
```
