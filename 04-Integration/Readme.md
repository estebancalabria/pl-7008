### Integracion en agentes en Microsoft Copilot Studio

Microsoft Copilot Studio es una plataforma que permite crear agentes conversacionales mediante una interfaz gráfica sin código, facilitando el desarrollo de soluciones de IA sin depender de perfiles técnicos avanzados. Su enfoque reduce la brecha entre expertos de negocio y equipos de desarrollo, acelera la implementación de mejoras y simplifica la construcción de experiencias conversacionales mediante IA generativa.

La plataforma integra capacidades de automatización, conectividad, orquestación conversacional e inteligencia artificial para construir agentes capaces de interactuar con usuarios, sistemas externos y datos empresariales dentro del ecosistema Microsoft.

---

## Acciones de agente

Las acciones permiten que el agente ejecute tareas específicas durante la conversación.

Desde la pestaña **Acciones** en Microsoft Copilot Studio se pueden configurar:

* Conectores predefinidos
* Conectores personalizados
* Flujos de Microsoft Power Automate
* Solicitudes de AI Builder
* Capacidades de Bot Framework

Estas acciones permiten que el agente use IA generativa para determinar automáticamente qué datos necesita, generando preguntas dinámicas sin diseño manual de nodos.

---

## Integración con Power Automate

Microsoft Power Automate permite ejecutar flujos desde los temas del agente mediante el nodo **“Llamar a una acción”**.

### Flujo de ejecución:

* **Ejecutar un flujo desde Copilot**: recibe entradas del agente
* **Responder a Copilot**: devuelve salidas procesadas

Los parámetros de entrada representan datos capturados en la conversación, y los de salida contienen resultados de sistemas externos.

Los flujos se almacenan en una solución dentro de Microsoft Power Apps.

---

## Ejecución de acciones

Las acciones se invocan desde temas y se combinan con nodos de pregunta para capturar datos del usuario. Luego, el agente usa las salidas del flujo para generar respuestas dinámicas y contextualizadas.

---

## Conectores y extensibilidad

Los conectores permiten integrar servicios externos y de Microsoft.

Incluyen:

* Excel Online
* Mail
* MSN El Tiempo
* Flujos de escritorio

También es posible crear conectores personalizados o flujos adicionales en Power Automate mediante APIs REST.

---

## Transferencia a agentes humanos

Microsoft Copilot Studio permite escalar conversaciones a agentes humanos mediante la Plataforma omnicanal para Customer Service.

### Acciones del sistema:

* Ir a otro tema
* Finalizar tema
* Finalizar todos los temas
* Transferir conversación
* Ir al paso
* Finalizar conversación

Existe el tema “Remitir a una instancia superior” para escalamiento automático.

---

## Destinos de transferencia

* Dynamics 365 Customer Service
* Genesys
* LivePerson
* Salesforce
* ServiceNow
* Zendesk
* Centros personalizados

La integración con Dynamics requiere registro de aplicación en Microsoft Entra ID.

---

## IVR y canal de voz

La integración de voz permite usar Copilot Studio en escenarios de atención telefónica.

Capacidades:

* DTMF
* Detección de silencio
* Entrada de voz
* Sensibilidad al ruido
* Mensajes de latencia

Configuraciones:

* Voz y DTMF
* SSML
* Mapeo de teclas DTMF

---

## Respuestas generativas en voz

Los usuarios pueden interactuar mediante DTMF y activar temas que capturan preguntas en variables para ser respondidas con IA generativa.

---

## IA generativa en Copilot Studio

La IA generativa permite:

* Respuestas como alternativa a temas
* Inserción de respuestas dentro de temas
* Creación de agentes con Copilot

Incluye el tema fallback “Acelerador de conversación”.

---

## Fuentes de conocimiento

* Sitios web públicos
* Archivos
* SharePoint
* Microsoft Dataverse

Conectores empresariales adicionales están en preview.

---

## Configuración de IA generativa

Modos:

* Clásico (basado en temas)
* Generativo (IA + acciones + conocimiento)

Moderación:

* Baja
* Media
* Alta

También incluye entrada de imágenes y mejoras en búsqueda para Microsoft 365 Copilot.

---

## URLs y documentos

Los agentes pueden usar:

* URLs (hasta 2 niveles de profundidad)
* SharePoint
* Documentos cargados

Los documentos se almacenan en Dataverse y se usan automáticamente como base de conocimiento.

---

## Respuestas generativas en temas

Se pueden insertar nodos “Crear respuestas generativas” para:

* Usar fuentes específicas
* Activar conocimiento general
* Ajustar moderación por tema

---

## Creación de temas con IA

Los agentes pueden responder sin temas definidos utilizando:

* Respuestas generativas
* Tema “Acelerador de conversación”
* Fuentes de conocimiento configuradas

---

## Tipo de desencadenadores

Los temas pueden activarse por distintos tipos de eventos:

* Frases
* Actividad recibida
* Mensaje recibido
* Evento recibido
* Actualización de conversación
* Invocación recibida (Teams y otros canales)
* Inactividad
* Desencadenado por agente
* Redireccionamiento
* Plan completado

---

## Prioridad de desencadenadores

Orden de ejecución:

1. Actividad recibida
2. Mensajes / eventos / invocaciones
3. Frases

Se puede ajustar mediante propiedad de prioridad. También se pueden usar condiciones con Power Fx.

---

## Transferencia de conversaciones (Omnicanal)

El agente puede transferir conversaciones manteniendo contexto completo a agentes humanos.

El sistema comparte:

* Historial de conversación
* Variables del agente
* Contexto completo

---

## Análisis del rendimiento del agente

Una vez en producción, Microsoft Copilot Studio ofrece una pestaña de **Análisis** con métricas clave:

### KPIs principales:

* Volumen de sesiones
* Tasa de resolución
* Tasa de escalación
* Tasa de abandono
* Satisfacción del cliente (CSAT)

---

## Resumen de analítica

Incluye:

* Gráficos de sesiones en el tiempo
* Resultados de sesión (resuelto, escalado, abandonado)
* Factores de impacto por tema
* Análisis de participación
* Factores de resolución, escalación y abandono

---

## Satisfacción del cliente (CSAT)

Incluye:

* Promedio de CSAT
* Evolución en el tiempo
* Tasa de respuesta de encuestas
* Temas con mayor impacto en satisfacción

---

## Análisis de temas

Cada tema tiene métricas específicas:

* Volumen de uso
* Impacto en KPIs
* Evolución temporal
* Relación con resolución o escalación

---

## Sesiones y transcripciones

En la pestaña **Sesiones** se puede:

* Ver conversaciones individuales
* Descargar transcripciones
* Analizar comportamiento del usuario

Cada sesión incluye:

* ID de sesión
* Mensaje inicial
* Tema activado
* Resultado (resuelto, escalado, abandonado)
* Transcripción completa

---

## Síntesis general

Microsoft Copilot Studio permite construir agentes empresariales completos que:

* Automatizan tareas con Power Automate
* Integran sistemas mediante conectores y APIs
* Usan IA generativa como fallback o núcleo
* Escalan a agentes humanos con contexto completo
* Operan en texto y voz (IVR)
* Usan múltiples fuentes de conocimiento
* Se adaptan mediante desencadenadores flexibles
* Permiten análisis avanzado de rendimiento y comportamiento

---

## Conclusión

En conjunto, Copilot Studio se posiciona como una plataforma integral para la creación de agentes inteligentes empresariales. Su valor principal no está solo en la conversación, sino en la capacidad de integrar automatización, IA generativa, orquestación de procesos, escalamiento humano y analítica avanzada en un único entorno.

Esto permite construir agentes que no solo responden, sino que ejecutan procesos, toman decisiones y evolucionan en base a datos reales de uso.
