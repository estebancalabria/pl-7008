# Create Copilot

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



Pregunta sobre contacto sobre gastos
```

* 

