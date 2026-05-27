# Microsoft Copilot Studio 

## Introducción

Microsoft Copilot Studio es una plataforma de Microsoft Power Platform que permite crear agentes conversacionales impulsados por Inteligencia Artificial para clientes y empleados. Estos agentes pueden responder preguntas, acceder a conocimiento empresarial, ejecutar acciones, automatizar procesos y proporcionar asistencia contextual utilizando IA generativa.

## Objetivos de aprendizaje

* Crear agentes.
* Administrar entornos.
* Diseñar conversaciones mediante temas.
* Incorporar conocimiento empresarial.
* Utilizar IA generativa.
* Probar agentes.
* Publicar agentes.
* Analizar el rendimiento y uso.

---

# Entornos

## ¿Qué es un entorno?

Un entorno es un espacio aislado donde se almacenan y administran los recursos de una organización.

Dentro de un entorno pueden existir:

* Agentes de Copilot Studio.
* Aplicaciones Power Apps.
* Flujos Power Automate.
* Datos empresariales.
* Configuraciones de seguridad.

Cada entorno puede tener:

* Roles y permisos específicos.
* Configuraciones de seguridad independientes.
* Diferentes públicos objetivo.
* Requisitos de cumplimiento y privacidad propios.

## Uso de múltiples entornos

### Por departamento

* Recursos Humanos
* Ventas
* Finanzas
* Soporte

### Por región geográfica

* Unión Europea
* Alemania
* China
* Singapur

Esta separación resulta especialmente útil cuando existen requisitos regulatorios o de residencia de datos.

## Creación de entornos

Al crear el primer agente se genera automáticamente un entorno predeterminado.

Los entornos adicionales se crean y administran desde el Centro de Administración de Microsoft Power Platform.

---

# Creación de agentes

## Planificación previa

Antes de crear un agente es recomendable definir:

* Qué problema resolverá.
* Qué consultas responderá.
* Qué acciones ejecutará.
* Qué sistemas utilizará.
* Qué conocimiento necesitará consultar.

Una correcta planificación simplifica el diseño de conversaciones y temas.

## Métodos de creación

### Mediante lenguaje natural

El creador describe el comportamiento esperado y Copilot Studio genera una configuración inicial.

### Mediante plantillas

Permite utilizar escenarios preconfigurados como punto de partida.

### Desde cero

Permite construir completamente el agente.

## Creación conversacional

Durante el proceso es posible:

* Describir el propósito del agente.
* Configurarlo manualmente.
* Asociar sitios web.
* Incorporar conocimiento empresarial.
* Habilitar respuestas generativas.

> La creación del primer agente en un entorno puede tardar varios minutos.

## Eliminación de agentes

Los agentes pueden eliminarse cuando:

* Son reemplazados por otros.
* Quedan obsoletos.
* Ya no responden a una necesidad de negocio.

---

# Interfaz de Microsoft Copilot Studio

## Crear

Permite crear nuevos agentes.

## Agentes

Muestra todos los agentes disponibles.

## Biblioteca

Proporciona acceso a:

* Conectores.
* Componentes reutilizables.
* Recursos compartidos.

## Descripción general

Página principal de administración del agente.

## Conocimiento

Permite administrar las fuentes de información utilizadas por el agente.

## Temas

Permite diseñar y administrar conversaciones.

## Acciones

Permite agregar:

* Automatizaciones.
* Integraciones.
* Plugins.
* Acciones personalizadas.

## Actividad

Muestra información relacionada con el uso de IA generativa y las interacciones realizadas.

## Análisis

Permite consultar indicadores de rendimiento y uso.

## Canales

Permite publicar e implementar agentes en distintos medios.

## Configuración

Permite administrar:

* Seguridad.
* Autenticación.
* IA generativa.
* Habilidades.
* Canales.

## Probar agente

Permite validar el comportamiento del agente antes de su publicación.

---

# Temas

## ¿Qué son?

Los temas representan escenarios específicos de conversación.

Ejemplos:

* Horarios de atención.
* Devoluciones.
* Consultas de cuenta.
* Soporte técnico.

Un agente puede tener hasta **1000 temas**.

## Componentes de un tema

### Frases desencadenadoras

Son expresiones que determinan cuándo debe activarse un tema.

Ejemplos:

* ¿Cuál es el horario?
* ¿Cuándo abren?
* Necesito ayuda con una devolución.

Las frases desencadenadoras deben ser únicas para evitar conflictos.

### Nodos de conversación

Definen cómo responde y actúa el agente.

Permiten:

* Mostrar mensajes.
* Hacer preguntas.
* Ejecutar acciones.
* Generar respuestas con IA.
* Capturar información.

---

# Tipos de temas

## Temas personalizados

Son creados o modificados por el desarrollador.

Ejemplos:

* Saludo.
* Despedida.
* Reiniciar conversación.

## Temas del sistema

Gestionan situaciones comunes.

Ejemplos:

* Escalación a un agente humano.
* Finalización de conversación.
* Resolución de conflictos.
* Tema alternativo (Fallback).

El tema alternativo se activa cuando el agente no encuentra una coincidencia adecuada para la consulta del usuario.

---

# Diseño de conversaciones

Los temas se construyen mediante un editor visual basado en nodos.

## Nodo Mensaje

Muestra información al usuario.

## Nodo Hacer una pregunta

Solicita información necesaria para continuar.

## Conversaciones ramificadas

Permiten construir diferentes rutas según las respuestas del usuario.

## Capacidades avanzadas

Los temas pueden utilizar:

* Variables.
* Entidades.
* Condiciones.
* Power Automate.
* Acciones personalizadas.

---

# Inteligencia Artificial Generativa

Copilot Studio incorpora IA generativa para aumentar la productividad y reducir el esfuerzo de configuración.

La IA generativa puede utilizarse para:

* Crear agentes.
* Crear temas.
* Generar respuestas.
* Orquestar conversaciones.

---

# Respuestas generativas

## Uso como alternativa

Cuando un tema no puede responder una consulta, el agente puede generar una respuesta utilizando IA y fuentes de conocimiento.

Esto reduce significativamente la necesidad de crear numerosos temas manualmente.

## Fuentes de conocimiento compatibles

### Recursos externos

* Bing Web Search.
* Bing Custom Search.
* Sitios web públicos.

### Recursos internos

* SharePoint.
* OneDrive.
* Dataverse.
* Azure OpenAI sobre datos propios.
* Microsoft Graph.
* Datos personalizados.

## Nodo Crear respuestas generativas

Permite utilizar IA generativa dentro de temas específicos.

Las fuentes configuradas en el nodo tienen prioridad sobre las fuentes configuradas a nivel del agente.

---

# Uso de sitios web como conocimiento

Los sitios web públicos pueden utilizarse como fuente de conocimiento para respuestas generativas.

## Recomendaciones

### Utilizar

* Sitios corporativos.
* Documentación oficial.
* Portales de conocimiento.

### Evitar

* Redes sociales.
* Foros públicos.
* Motores de búsqueda.

## Consideraciones sobre URLs

* Se admiten URLs con hasta dos niveles de profundidad.
* El contenido accesible bajo el dominio especificado puede utilizarse para generar respuestas.
* Es recomendable evitar URLs de motores de búsqueda.

---

# SharePoint como fuente de conocimiento

SharePoint puede utilizarse como origen de información para respuestas generativas.

Limitaciones:

* Máximo dos niveles de profundidad.
* Los archivos ASPX no se utilizan para generar respuestas.

---

# Carga de documentos

Los documentos cargados pueden utilizarse como fuente de conocimiento para todo el agente.

## Características

* Se almacenan en Dataverse.
* Tamaño máximo: 512 MB por archivo.
* Limitados únicamente por la capacidad de almacenamiento disponible.

## Archivos no compatibles

* Ejecutables.
* Imágenes.
* Audio.
* Vídeo.

> Todo el contenido cargado estará disponible para cualquier usuario que interactúe con el agente.

---

# Integración con Microsoft 365

Los agentes pueden utilizar datos empresariales procedentes de Microsoft 365.

## Tecnologías utilizadas

* SharePoint.
* Microsoft Graph Connectors.

## Conectores compatibles

* SharePoint
* ServiceNow
* Azure SQL
* Salesforce
* Zendesk

Estos datos pueden utilizarse tanto en respuestas generativas como en agentes configurados con orquestación generativa.

---

# Orquestación generativa

La IA generativa puede decidir dinámicamente qué temas, acciones y conocimientos utilizar para responder a una consulta.

## Modo clásico

* Basado en temas.
* Basado en desencadenadores.
* Basado en acciones predefinidas.

## Modo generativo (Preview)

* Selecciona automáticamente temas y acciones.
* Puede combinar múltiples temas.
* Gestiona consultas multintención.
* Genera planes de ejecución dinámicamente.

### Beneficios

* Conversaciones más naturales.
* Menor dependencia de frases exactas.
* Mayor flexibilidad.

> Actualmente es una funcionalidad en versión preliminar.

---

# Moderación de contenido

Permite controlar el equilibrio entre precisión y creatividad.

## Alta (predeterminada)

* Menos respuestas.
* Mayor precisión.

## Media

* Equilibrio entre precisión y cobertura.

## Baja

* Más respuestas.
* Más creatividad.
* Mayor riesgo de imprecisiones.

---

# Soporte multilingüe

Las respuestas generativas pueden trabajar con la mayoría de los idiomas compatibles con Copilot Studio.

Es posible crear temas específicos para detectar idiomas distintos al idioma principal configurado y responder automáticamente en el idioma del usuario.

## Beneficios

* Experiencias multilingües.
* Menor necesidad de crear temas específicos por idioma.
* Cobertura global más amplia.

---

# Pruebas de agentes

Antes de publicar un agente es fundamental validar su comportamiento.

## Panel Probar agente

Permite interactuar con el agente como si se fuera un usuario final.

Se utiliza para:

* Validar temas.
* Verificar desencadenadores.
* Comprobar respuestas.
* Revisar flujos conversacionales.

## Seguimiento de temas

La opción **Realizar seguimiento de un tema a otro** permite visualizar:

* Qué tema se activa.
* Qué ruta sigue la conversación.
* Qué nodos se ejecutan.

Esto facilita la depuración y optimización de los flujos.

## Ciclo de mejora continua

Proceso recomendado:

1. Crear o modificar un tema.
2. Guardar los cambios.
3. Probar el comportamiento.
4. Ajustar la conversación.
5. Volver a probar.

---

# Pruebas de respuestas generativas

Las respuestas generativas también deben validarse.

## Cómo probarlas

Se recomienda realizar preguntas que:

* Estén relacionadas con las fuentes de conocimiento configuradas.
* No puedan responderse mediante temas existentes.

Si no existe un tema adecuado, el agente utilizará IA generativa para responder.

## Conservación del contexto

Las respuestas generativas mantienen el contexto de la conversación.

Ejemplo:

Usuario:

> ¿Para qué sirve la función IF de Excel?

Usuario:

> Dame un ejemplo.

El agente entiende que la segunda pregunta continúa hablando de la función IF y responde en consecuencia.

---

# Publicación de agentes

Una vez finalizado el desarrollo y las pruebas, el agente debe publicarse para que los usuarios puedan interactuar con él.

La publicación permite distribuir el agente en:

* Sitios web.
* Aplicaciones móviles.
* Microsoft Teams.
* Microsoft 365 Copilot.
* Facebook.
* Slack.
* Line.
* GroupMe.
* Canales de telefonía.

Cada vez que se realizan cambios en el agente, es necesario volver a publicarlo para que las modificaciones estén disponibles para los usuarios.

## Proceso de publicación

1. Seleccionar **Publicar**.
2. Copilot Studio valida la configuración.
3. Se detectan posibles errores.
4. Se genera una nueva versión publicada.

Si la publicación es exitosa, se muestra una confirmación visual.

---

# Seguridad y autenticación

Antes de publicar un agente es recomendable configurar sus opciones de seguridad.

## Opciones de autenticación

### Sin autenticación

* No requiere inicio de sesión.
* Puede utilizarse públicamente.

### Autenticación con Microsoft

Utiliza Microsoft Entra ID.

Compatible con:

* Microsoft Teams.
* Power Apps.
* Microsoft 365 Copilot.

Es la configuración predeterminada.

### Autenticación manual

Permite configurar:

* OAuth 2.0
* Microsoft Entra ID personalizado

Compatible con cualquier canal admitido.

---

# Seguridad empresarial

Copilot Studio incorpora capacidades empresariales de gobernanza y cumplimiento.

## Características

* Autenticación habilitada por defecto.
* Protección de conversaciones.
* Control administrativo centralizado.

## Auditoría y cumplimiento

Los administradores pueden consultar información mediante Microsoft Purview.

Información disponible:

* Uso de agentes.
* Inventario.
* Registros de auditoría.
* Infracciones DLP.
* Agentes inactivos.

---

# Sitio web de demostración

Después de la primera publicación, el agente puede compartirse mediante un sitio web de demostración.

## Beneficios

* Obtener comentarios tempranos.
* Realizar pruebas con usuarios de negocio.
* Evaluar la experiencia real del usuario.

## Requisito

La autenticación debe configurarse como:

**Sin autenticación**

---

# Administración de licencias y consumo

Los administradores pueden consultar información de uso y facturación desde el Centro de Administración de Power Platform.

## Información disponible

### Licencias

* Compra de capacidad.
* Administración de planes.
* Facturación.

### Mensajes

* Capacidad asignada.
* Mensajes consumidos.
* Tendencias de uso.

### Sesiones

* Sesiones utilizadas.
* Capacidad disponible.
* Consumo por entorno.

### Informes

* Uso por entorno.
* Uso por producto.
* Consumo histórico.

---

# Análisis y rendimiento

Una vez publicado, Copilot Studio recopila métricas sobre el comportamiento del agente.

Toda esta información se encuentra en la sección **Análisis**.

## Indicadores clave (KPI)

### Volumen de sesiones

Cantidad de conversaciones iniciadas.

### Resolución de problemas

Capacidad del agente para resolver consultas sin intervención humana.

### Escalaciones

Cantidad de conversaciones derivadas a agentes humanos.

### Abandono

Usuarios que abandonan la conversación antes de completarla.

## Satisfacción del cliente

Permite medir la percepción y experiencia de los usuarios.

Ayuda a identificar:

* Temas problemáticos.
* Conversaciones ineficientes.
* Oportunidades de mejora.

## Mejora continua

Proceso recomendado:

1. Analizar métricas.
2. Detectar oportunidades de mejora.
3. Ajustar temas y conocimiento.
4. Publicar nuevamente.
5. Medir resultados.

---

# Resumen final

Microsoft Copilot Studio permite crear agentes empresariales impulsados por Inteligencia Artificial capaces de responder preguntas, acceder a conocimiento corporativo y ejecutar acciones. Los agentes se organizan mediante entornos, utilizan temas para modelar conversaciones y pueden enriquecerse con información procedente de SharePoint, Dataverse, Microsoft Graph y sistemas externos. Gracias a la IA generativa, es posible crear agentes y temas más rápidamente, generar respuestas dinámicas, utilizar documentos y sitios web como fuentes de conocimiento, trabajar en múltiples idiomas y orquestar conversaciones complejas de forma automática. Las herramientas integradas de prueba, publicación, seguridad, análisis y monitoreo permiten implementar soluciones conversacionales robustas, seguras y escalables para distintos escenarios empresariales.
