# Create Copilot

## Crear un Entorno

* Ir a URL

> https://admin.powerplatform.microsoft.com/

* Crear un entorno nuevo
  * En Microsoft Power Platform, un environment (entorno) es básicamente un “espacio aislado” donde viven tus recursos:

> Manage... Enviroments..Nuevo...
> Tipo : Developer
> Nombre :  dev-lab-001-create-copilot

* Ir al enviroment una vez creado y copiar el ID

 > <ID_ENVIROMENT>

* Ir a la pagina de copilot

> https://copilotstudio.microsoft.com/environments/<ID_ENVIROMENT>/home

* Elegir menu agentes para ver agentes existentes

## Crear un Agente

* Crear un agente

 <img width="1492" height="360" alt="image" src="https://github.com/user-attachments/assets/98152bb4-54f7-4433-a899-da16db287850" />

```
Crear un asistente para ayudar a los empleados a gestionar sus rendiciones de gastos.
```

* Cambiar la parte de directices generales de las instrucciones (system prompt)

```
## Directrices Generales
- Mantén un tono amigable, profesional, claro y servicial.
- Proporciona instrucciones paso a paso para completar las reclamaciones.
- Verifica que los gastos cumplan con las políticas internas antes de proceder.
- Nunca compartas información confidencial con personas no autorizadas.
- Evita proporcionar cualquier tipo de asesoramiento fiscal.
```

* En la seccion de knowledge o conocimiento
 * Deshabilitar la busqueda web

* Probar el agente

```
¿Con quién debo comunicarme para presentar una rendición de gastos?”
```

```
¿Cuál es el límite de gasto para una estadía en hotel?
```

## Agregar Temas

* Agregar temas
  * Nombre
    * Pregunta sobre contacto de gastos
  * Descripcion
    * Cuando el usuario pregunte a quién contactar sobre reclamaciones de gastos, indícale que envíe un correo electrónico a finance@contoso.com

<img width="450" height="546" alt="image" src="https://github.com/user-attachments/assets/cbe1830a-8ae6-4b79-8114-4a1901955b6b" />

* Probar

```
A quien contacto para registrar mis gastos?
```

## Agregar conocimiento

* Ir a la pagina inicial del agente
* Ir a agregar Conocimiento/Knowledge
* Descargar este archivo
 *  https://raw.githubusercontent.com/estebancalabria/pl-7008/refs/heads/main/Labs/Lab-001-Create%20Copilot/politica-gastos.md
*  Subir el archivo y agregarlo al agente

## Configurar el agente

* Ir arriba a donde dice Configuracion/Settings
 * Ir a seguridad...Autenticacion..
  * Poner Sin Autenticacion

* Ir a la opcion de Canales/Channels
* Elegir la opcin de Sitio web de Prueba
* Configurar y copiar el link del sitio
* Probar una vez que este subido el archivo de conocimiento
* ** Publicar agente con publish**

>[!NOTE]
>El paso de publish es super importante para poder usarlo en sitio web

## Probar agente en su sitio web PErsonalizado

* Abrir el link a su propia web de prueba
* Probar este prompt

```
Como registro mis gastos de hoteles? Cuanto es el maxmo?
```

## Usarlo en tu propio sitio web

* Abrir canales
* Elegir Aplicacion Web
* Copiar la URL del iframe
* Reemplazarla en el siguietne codigo

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        #chatbot {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 350px;
            height: 500px;
            display: none;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
        }

        #botonChat {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #0078d4;
            color: white;
            border: none;
            border-radius: 50%;
            width: 60px;
            height: 60px;
            font-size: 20px;
            cursor: pointer;
        }
    </style>

</head>

<body>

    <button id="botonChat" onclick="toggleChat()">💬</button>

    <div id="chatbot">
        <iframe src="TU_URL_DEL_IFRAME" width="100%" height="100%"></iframe>
    </div>

    <script>
        function toggleChat() {
            const chat = document.getElementById("chatbot");
            chat.style.display = chat.style.display === "none" ? "block" : "none";
        }
    </script>
</body>

</html>
```
