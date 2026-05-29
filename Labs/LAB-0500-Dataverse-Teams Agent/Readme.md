# LAB-PL7008 — Agente interno con Copilot Studio y Dataverse for Teams

**Curso:** PL-7008 Create Agents in Microsoft Copilot Studio  
**Cliente:** Chevron  
**Duración estimada:** 45 minutos  
**Módulo que cubre:** M5 — Create an agent with Copilot Studio and Dataverse for Teams

---

## ¿Cuándo usar este enfoque?

Dataverse for Teams es la opción correcta cuando:

- El agente es **exclusivamente interno** — solo para empleados, no para clientes externos
- Los datos que maneja son **propios del equipo** — no viven en SharePoint ni en sistemas externos
- Se necesita **guardar información** que el agente recopila — solicitudes, registros, formularios
- No se quiere pagar licencias adicionales — está incluido en **Microsoft 365, sin costo extra**
- El equipo ya trabaja en Teams y no necesita otro canal

Ejemplos concretos para Chevron:
- Agente de mesa de ayuda IT que registra tickets
- Agente de RRHH que recibe solicitudes de vacaciones
- Agente de seguridad industrial que registra incidentes en campo
- Agente de onboarding que guía a nuevos empleados y registra su progreso

**La diferencia clave con el resto del curso:** en los otros labs el agente consulta datos externos (APIs, SharePoint, Excel). Acá el agente *es* la interfaz de una base de datos propia, y todo vive dentro de Teams.

---

## Prerrequisitos

- Microsoft 365 con Teams (cualquier plan — E1, E3, E5, Business)
- Acceso a Teams Desktop o Teams Web
- Sin licencias adicionales de Power Platform necesarias

---

## Verificación previa

Verificar que en Teams aparece la opción de agregar apps:

1. Abrir Microsoft Teams
2. En el panel izquierdo, clic en **Apps** (ícono de grilla)
3. Buscar **Power Apps** — debe aparecer en los resultados
4. Si no aparece, el administrador de M365 puede tener bloqueada la instalación de apps — avisar al instructor

---

## Parte 1 — Crear la app en Teams (esto activa Dataverse for Teams)

### Paso 1.1 — Agregar Power Apps a Teams

1. En Teams, clic en **Apps** en el panel izquierdo
2. Buscar **Power Apps** e instalarlo
3. Una vez instalado, aparece en el panel izquierdo

### Paso 1.2 — Crear una nueva app

1. Abrir **Power Apps** dentro de Teams
2. Clic en **Start now**
3. Seleccionar el equipo de Teams donde vivirá el agente — por ejemplo `Chevron IT Support`
4. Nombre de la app: `Gestión de Solicitudes`
5. Clic en **Save**

> **Qué pasa en este momento:** Al crear la app, Teams provisiona automáticamente un entorno de **Dataverse for Teams** para ese equipo. Es invisible para el usuario pero es lo que permite guardar datos estructurados sin configuración adicional.

---

## Parte 2 — Crear la tabla en Dataverse for Teams

### Paso 2.1 — Agregar una tabla

1. Dentro del editor de Power Apps en Teams, clic en **Data** en el panel izquierdo
2. Clic en **Add data** → **Create new table**
3. Nombre de la tabla: `Solicitudes`

### Paso 2.2 — Agregar columnas

Agregar las siguientes columnas:

| Nombre | Tipo |
|---|---|
| Nombre (viene por defecto) | Text |
| Descripcion | Text |
| Categoria | Choice (opciones: Hardware, Software, Accesos, Otro) |
| Estado | Choice (opciones: Pendiente, En proceso, Resuelto) |
| FechaCreacion | Date and time |

> La columna **Nombre** ya existe por defecto — usarla para el nombre del empleado que hace la solicitud.

### Paso 2.3 — Guardar la tabla

1. Clic en **Save table**
2. Cerrar el editor de Power Apps — la tabla ya está disponible

---

## Parte 3 — Crear el agente en Copilot Studio desde Teams

### Paso 3.1 — Abrir Copilot Studio dentro de Teams

1. En Teams, clic en **Apps**
2. Buscar **Copilot Studio** e instalarlo
3. Abrirlo desde el panel izquierdo

> **Importante:** Copilot Studio abierto desde Teams trabaja automáticamente con el entorno de Dataverse for Teams — no hay que configurar el environment manualmente.

### Paso 3.2 — Crear el agente

1. Clic en **New agent**
2. Nombre: `Agente de Soporte IT`
3. Descripción: `Registra solicitudes de soporte del equipo`
4. Clic en **Create**

---

## Parte 4 — Crear el topic para registrar solicitudes

### Paso 4.1 — Nuevo topic

1. **Topics** → **Add a topic** → **From blank**
2. Nombre: `Nueva solicitud`

### Paso 4.2 — Trigger phrases

```
Quiero hacer una solicitud
Necesito soporte
Tengo un problema
Abrir ticket
Pedir ayuda
```

### Paso 4.3 — Recopilar datos del usuario

Agregar los siguientes nodos **Ask a question** en secuencia:

**Pregunta 1:**
- Pregunta: `¿Cuál es tu nombre?`
- Identify: **Person name**
- Variable: `Topic.nombreUsuario`

**Pregunta 2:**
- Pregunta: `¿Cuál es la categoría del problema?`
- Identify: **Multiple choice options**
- Opciones: `Hardware`, `Software`, `Accesos`, `Otro`
- Variable: `Topic.categoria`

**Pregunta 3:**
- Pregunta: `Describí brevemente el problema`
- Identify: **User's entire response**
- Variable: `Topic.descripcion`

### Paso 4.4 — Guardar en Dataverse for Teams

1. Agregar nodo **Call an action** → **Create a new Power Automate flow**
2. En Power Automate, configurar el flow:
   - Trigger: **Run a flow from Copilot Studio**
   - Inputs: `nombreUsuario` (Text), `categoria` (Text), `descripcion` (Text)
   - Acción: **Add a new row** → tabla **Solicitudes**
   - Mapear:
     - Nombre → `nombreUsuario`
     - Descripcion → `descripcion`
     - Categoria → `categoria`
     - Estado → valor fijo `Pendiente`
     - FechaCreacion → expresión `utcNow()`
3. Guardar el flow con nombre: `Registrar Solicitud`
4. Volver al topic y conectar el flow

### Paso 4.5 — Confirmar al usuario

1. Agregar nodo **Send a message**:
```
¡Listo! Registré tu solicitud de {Topic.categoria}. Te contactaremos a la brevedad.
```
2. Agregar nodo **End conversation**

---

## Parte 5 — Publicar el agente en el canal de Teams

### Paso 5.1 — Publicar

1. Clic en **Publish** (arriba a la derecha)
2. Confirmar la publicación

### Paso 5.2 — Agregar al canal de Teams

1. Ir a **Settings** → **Channels**
2. Seleccionar **Microsoft Teams**
3. Clic en **Add to Teams**
4. Seleccionar el equipo `Chevron IT Support`
5. Elegir el canal donde va a vivir el agente

### Paso 5.3 — Probar en Teams

1. Ir al canal seleccionado
2. Buscar el agente en el chat
3. Escribir: `Necesito soporte`
4. Completar el flujo de preguntas
5. Verificar que el registro aparece en la tabla:
   - Volver a **Power Apps** en Teams
   - Abrir la tabla **Solicitudes**
   - El nuevo registro debe estar visible

---

## Comparación rápida: ¿cuándo usar cada enfoque?

| Escenario | Enfoque recomendado |
|---|---|
| Agente interno, datos propios del equipo, sin costo extra | **Dataverse for Teams** (este lab) |
| Agente que consulta una API externa | **HTTP request** (lab clima) |
| Agente que procesa archivos Excel o manda mails | **Power Automate** (lab flow) |
| Agente que muestra información rica visualmente | **Adaptive Cards** (lab tarjetas) |
| Agente público o para clientes | Publicación web / canal externo |

