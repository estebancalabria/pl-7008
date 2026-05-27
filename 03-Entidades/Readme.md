# Trabajar con entidades y variables en Microsoft Copilot Studio

Microsoft Copilot Studio es una plataforma para la creación de agentes conversacionales basados en escenarios de negocio. Permite diseñar experiencias que interpretan lenguaje natural, extraen información estructurada y mantienen contexto a lo largo de múltiples interacciones.

El objetivo principal del modelo de Copilot Studio es transformar entradas de lenguaje natural en datos utilizables dentro de un flujo conversacional, reduciendo fricción en la interacción usuario-agente.

---

# 1. Modelo de interacción conversacional

El funcionamiento del agente se basa en tres capacidades principales:

* Comprensión del lenguaje natural (NLU)
* Extracción de entidades desde el texto
* Persistencia y reutilización de datos mediante variables

Este modelo permite que el agente:

* Interprete intención sin frases rígidas
* Extraiga datos relevantes automáticamente
* Mantenga contexto dentro de la sesión
* Reutilice información entre diferentes partes del flujo

---

# 2. Entidades

Las entidades representan unidades de información estructurada dentro del texto del usuario.

Ejemplos típicos:

* Personas
* Fechas
* Ciudades
* Números
* Correos electrónicos
* Direcciones
* Valores monetarios

## 2.1 Entidades predefinidas

Microsoft Copilot Studio incluye entidades listas para usar que permiten reconocer información común sin configuración adicional.

Ejemplos:

* DateTime
* Number
* Money
* City
* Email
* Phone number

Estas entidades son la base del reconocimiento automático de datos en conversaciones.

---

## 2.2 Entidades personalizadas

Permiten modelar información específica del dominio de negocio.

Casos típicos:

* Catálogo de productos
* Categorías de servicios
* Códigos internos
* Dominios específicos de industria

### Tipos de entidades personalizadas

**Lista cerrada**

* Conjunto finito de valores
* Ej: categorías de productos

**Expresiones regulares (Regex)**

* Extracción basada en patrones
* Ej: IDs, tracking numbers, IPs, códigos estructurados

---

## 2.3 Inteligencia aplicada a entidades

### Coincidencia inteligente

Permite interpretar variaciones semánticas o errores de escritura.

Ejemplo:

* “sóftbol” → “béisbol”

### Sinónimos

Permiten extender manualmente el significado de una entidad.

Ejemplo:

* Esquí → snowboard, raquetas de nieve

---

## 2.4 Slot filling y extracción contextual

El sistema puede mapear automáticamente partes del texto a entidades sin requerir preguntas explícitas.

Ejemplo:

* “Quiero botas de senderismo” → categoría = senderismo

---

## 2.5 Relleno proactivo de espacios

Permite extraer múltiples entidades desde una sola entrada.

Ejemplo:

* “Quiero botas de senderismo por menos de 100$”

Extracción:

* Producto
* Categoría
* Presupuesto

Este mecanismo reduce la cantidad de turnos conversacionales necesarios.

---

# 3. Variables

Las variables representan el mecanismo de persistencia de datos dentro del agente.

Permiten almacenar información extraída o ingresada por el usuario para su reutilización posterior.

Ejemplos:

* UserName
* UserCity

## Capacidades principales

* Almacenamiento de contexto conversacional
* Personalización de respuestas
* Control de flujo (condiciones y rutas)
* Reutilización de datos en múltiples nodos

---

## 3.1 Creación de variables

Se generan automáticamente al usar nodos de pregunta.

Inicialmente pueden tener nombres genéricos (Var1, Var2), por lo que se recomienda su renombrado para mejorar mantenibilidad.

---

## 3.2 Uso dentro de un tema

Las variables pueden utilizarse en:

* Mensajes
* Condiciones
* Lógica de enrutamiento

Ejemplo:

“Hola {UserName}, ¿en qué puedo ayudarte?”

---

# 4. Reutilización de variables entre temas

Uno de los elementos clave del diseño en Copilot Studio es la capacidad de compartir estado entre distintos temas.

## 4.1 Tipos de variables

### Variables de tema

* Scope local
* Solo disponibles dentro del mismo tema

### Variables globales

* Scope a nivel de agente
* Disponibles en todos los temas durante la sesión

Ejemplo:

* Global.UserName
* Global.UserCity

---

## 4.2 Paso de variables entre temas

Permite transferir contexto entre flujos conversacionales.

Flujo típico:

1. Tema A captura información
2. Tema B la reutiliza sin volver a preguntar

Beneficio directo:

* Eliminación de redundancia en la conversación

---

## 4.3 Recepción de valores desde otros temas

Un tema puede configurarse para recibir valores externos y evitar repreguntar información ya disponible.

Esto permite:

* Continuidad de contexto
* Menos fricción conversacional
* Mayor naturalidad en la interacción

---

## 4.4 Inicialización desde fuentes externas

Las variables globales pueden inicializarse desde sistemas externos antes de iniciar la conversación.

Ejemplo:

* Usuario autenticado en web
* El sistema envía nombre y contexto al agente
* El agente inicia conversación personalizada

Esto permite un modelo de experiencia “state-aware”.

---

## 4.5 Gestión y trazabilidad

El entorno permite:

* Identificar origen de variables
* Ver dónde se utilizan
* Analizar dependencias entre temas

Esto es clave para agentes complejos y escalables.

---

# 5. Arquitectura conceptual del agente

El modelo completo puede resumirse como:

1. El usuario envía lenguaje natural
2. El sistema interpreta intención (NLU)
3. Se extraen entidades automáticamente
4. Se almacenan en variables
5. Se reutilizan dentro o entre temas
6. Se mantiene contexto durante la sesión

---

# 6. Conclusión

El modelo de Microsoft Copilot Studio se basa en la combinación de:

* Entidades para estructurar información
* Variables para persistir contexto
* Flujo entre temas para modularidad
* Reutilización para evitar redundancia

Este enfoque permite construir agentes conversacionales que no solo responden preguntas, sino que mantienen contexto, optimizan interacciones y mejoran progresivamente la experiencia del usuario.
