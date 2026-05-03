
## Requisitos

* Tener importada la solucion de bookings del laboratorio pasado

## Crear o elegir enviroment

* Ir a
  * https://admin.powerplatform.microsoft.com/
* Ver enviroments
* Crear enviroment o copiar id del enviroment


## I

* Ir al home del enviroment
  * https://copilotstudio.microsoft.com/environments/<ID ENVIROMENT>/home
* Ir a Agentes
* Crear agente en blanco y elegir "creacion Avanzada:
  * Solucion: Elegir Bookings
  * Schema Name: LabAgent
 * **En la sección Detalles**

  * Selecciona **Editar**
  * En el campo **Nombre**

    * Escribe: **Real Estate Booking Service**
  * En el campo **Descripción**

    * Escribe: **Crear reservas para propiedades inmobiliarias**
  * Selecciona **Guardar**

* **En la sección Instrucciones**

  * Selecciona **Editar**
  * Actualiza las instrucciones a:

    * **Crear un agente para temas relacionados con la creación de reservas para propiedades inmobiliarias**
  * Selecciona **Guardar**

* **En el panel derecho “Probar tu agente”**

  * Escribe: **Como hago una reserva?**
  * Observa la respuesta generada

>[!NOTE]
>Deja esta ventana abierta

### Deshabilitar orquestacion

* **Selecciona Settings (Configuración)**

* **En la opción “¿Usar la orquestación con IA generativa para las respuestas de su agente?”**

  * Selecciona: **No**

    * Usar la orquestación clásica, limitando las respuestas al contenido y comportamiento definidos en los temas del agente
    * Esto desactiva la orquestación para este laboratorio

* **Selecciona Save (Guardar)**

* **Cierra la ventana de Settings (Configuración)**

### Agregar fuente de conocimiento

* **Selecciona la pestaña Knowledge (Conocimiento)**

* **Selecciona + Add knowledge (Agregar conocimiento)**

* **Selecciona Public websites (Sitios web públicos)**

* **En el campo “Public website link (Enlace del sitio web público)”**

  * Ingresa: **[https://www.realtor.com/marketing/resources](https://www.realtor.com/marketing/resources)**
  * Este sitio contiene consejos de marketing inmobiliario que pueden ser útiles para tu agente

* **Selecciona Add (Agregar)**

* **Selecciona Add to agent (Agregar al agente)**

* **Selecciona la pestaña Overview (Descripción general)**

* **En el panel “Test your agent (Probar tu agente)”**

  * Abre el menú de los **tres puntos (… )** en la parte superior
  * Activa la opción: **Track between topics (Seguir entre temas)**

* **En la parte superior del panel “Test your agent”**

  * Selecciona el ícono **Start a new test session (Iniciar nueva sesión de prueba)**

* **En el campo “Ask a question or describe what you need (Haz una pregunta o describe lo que necesitas)”**

  * Escribe: **¿Cómo puedo mejorar la promoción inmobiliaria?**
  * Revisa la respuesta generada**
