# LAB-PL7008 — Agente de clima con Copilot Studio

**Curso:** PL-7008 Create Agents in Microsoft Copilot Studio  
**Cliente:** Chevron  
**Duración estimada:** 40 minutos  
**Módulos que cubre:** M2 (Topics), M3 (Entities & Variables), M4 (HTTP actions)

---

## Objetivo

Construir un agente que:
1. Reconoce cuando el usuario pregunta por el clima
2. Le pide la ciudad
3. Llama directamente a la API de Open-Meteo desde el topic (sin Power Automate)
4. Muestra temperatura y condición actual
5. Maneja el caso en que la ciudad no se encuentra

---

## Prerrequisitos

- Acceso a un environment de Power Platform (trial o corporativo)
- Acceso a [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)

> **Nota:** Open-Meteo es una API pública gratuita, sin registro ni API key.

---

## Verificación previa — Probar la API en el navegador

Antes de empezar, abrir estas dos URLs y verificar que devuelven datos.

**Geocoding** (ciudad → coordenadas):
```
https://geocoding-api.open-meteo.com/v1/search?name=Buenos%20Aires&count=1&language=es&format=json
```

Respuesta esperada:
```json
{
  "results": [
    {
      "name": "Buenos Aires",
      "latitude": -34.61315,
      "longitude": -58.37723,
      "country": "Argentina"
    }
  ],
  "generationtime_ms": 0.45
}
```

**Forecast** (coordenadas → clima):
```
https://api.open-meteo.com/v1/forecast?latitude=-34.61315&longitude=-58.37723&current_weather=true
```

Respuesta esperada:
```json
{
  "current_weather": {
    "temperature": 18.2,
    "windspeed": 12.5,
    "weathercode": 3,
    "time": "2025-01-15T14:00"
  }
}
```

> **Problema frecuente:** Si geocoding devuelve solo `{ "generationtime_ms": 0.63 }` sin el array `results`, la ciudad no fue encontrada. La causa más común es el espacio sin codificar. En el lab usamos `EncodeUrl()` para resolverlo automáticamente.

---

## Parte 1 — Crear el agente base

1. Ir a [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
2. Verificar el environment seleccionado (arriba a la derecha)
3. Clic en **Create** → **New agent**
4. Nombre: `Agente Clima Lab`
5. Descripción: `Consulta el clima actual de cualquier ciudad`
6. Clic en **Create**

---

## Parte 2 — Crear el topic de clima

### Paso 2.1 — Nuevo topic

1. Menú lateral → **Topics** → **Add a topic** → **From blank**
2. Nombre: `Consulta de clima`

### Paso 2.2 — Trigger phrases

```
¿Cómo está el clima?
Qué tiempo hace hoy
Quiero saber el clima
Cómo va a estar el tiempo
Temperatura de hoy
```

### Paso 2.3 — Mensaje de bienvenida

Agregar nodo **Send a message** → `¡Claro! Puedo consultarte el clima actual.`

### Paso 2.4 — Preguntar la ciudad

1. Agregar nodo **Ask a question**
2. Pregunta: `¿De qué ciudad querés saber el clima?`
3. En **Identify**: buscar y seleccionar **City** de la lista de entidades prebuilt
4. En **Save response as**: Copilot Studio genera automáticamente la variable `Topic.city`

> **Importante:** No escribir el nombre de la variable a mano. Copilot Studio lo asigna automáticamente como `Topic.city` al seleccionar la entidad City. Si se intenta renombrar o tipear manualmente aparece el error "El nombre no es válido".

---

## Parte 3 — Primera llamada HTTP: Geocoding

### Paso 3.1 — Agregar el nodo HTTP

1. Agregar nodo → **Advanced** → **Send HTTP request**
2. **Method**: GET
3. **URL**: abrir el editor de fórmulas Power Fx y escribir:
```
"https://geocoding-api.open-meteo.com/v1/search?name=" & EncodeUrl(Topic.city) & "&count=1&language=es&format=json"
```

> `EncodeUrl()` convierte los espacios en `%20` automáticamente. Sin esto, "Buenos Aires" llega a la API como "BuenosAires" y no devuelve resultados.

### Paso 3.2 — Definir el schema de respuesta

Aquí está la clave: en lugar de elegir un tipo del dropdown, hay que darle a Copilot Studio un ejemplo del JSON que devuelve la API para que genere el schema automáticamente.

1. En el nodo HTTP, en **Response data type** → seleccionar **From sample data**
2. Clic en **Get schema from sample JSON**
3. Pegar este JSON de ejemplo:
```json
{
  "results": [
    {
      "name": "Buenos Aires",
      "latitude": -34.61315,
      "longitude": -58.37723,
      "country": "Argentina"
    }
  ],
  "generationtime_ms": 0.45
}
```
4. Clic en **Confirm**

Copilot Studio genera el schema y habilita intellisense para acceder a los campos.

5. En **Save response as**: crear variable `Topic.geoResponse`

### Paso 3.3 — Verificar que la ciudad fue encontrada

1. Agregar nodo **Condition**
2. Condición (Power Fx):
```
IsEmpty(Topic.geoResponse.results)
```
3. Rama **True** (no encontrada):
   - **Send a message**: `No encontré esa ciudad. ¿Podés escribirla de otra forma?`
   - **Redirect** → volver al nodo Ask a question del Paso 2.4
4. Rama **False**: continuar al Paso 4

---

## Parte 4 — Segunda llamada HTTP: Clima actual

### Paso 4.1 — Agregar el nodo HTTP

1. Agregar nodo → **Advanced** → **Send HTTP request**
2. **Method**: GET
3. **URL** (Power Fx):
```
"https://api.open-meteo.com/v1/forecast?latitude=" & Text(First(Topic.geoResponse.results).latitude) & "&longitude=" & Text(First(Topic.geoResponse.results).longitude) & "&current_weather=true"
```

### Paso 4.2 — Definir el schema de respuesta

1. En **Response data type** → **From sample data** → **Get schema from sample JSON**
2. Pegar:
```json
{
  "current_weather": {
    "temperature": 18.2,
    "windspeed": 12.5,
    "weathercode": 3,
    "time": "2025-01-15T14:00"
  }
}
```
3. Clic en **Confirm**
4. En **Save response as**: crear variable `Topic.climaResponse`

---

## Parte 5 — Mostrar el resultado

### Paso 5.1 — Mensaje de respuesta

1. Agregar nodo **Send a message**
2. Usar el editor de fórmulas para componer el mensaje:
```
"El clima en " & Topic.city & " es de " & Text(Topic.climaResponse.current_weather.temperature) & "°C. Viento: " & Text(Topic.climaResponse.current_weather.windspeed) & " km/h."
```

### Paso 5.2 — Cerrar conversación

Agregar nodo **End conversation**

---

## Parte 6 — Probar el agente

Clic en **Test your agent** (panel derecho)

**Prueba 1 — ciudad con espacio:**
- Escribir: `Quiero saber el clima`
- Responder: `Buenos Aires`
- Resultado esperado: `El clima en Buenos Aires es de 18°C. Viento: 12 km/h.`

**Prueba 2 — ciudad inválida:**
- Escribir: `Quiero saber el clima`
- Responder: `asdfghjk`
- Resultado esperado: `No encontré esa ciudad. ¿Podés escribirla de otra forma?`

---

## Parte 7 — Mejora opcional (alumnos avanzados)

### 7.1 — Traducir weathercode a texto

Agregar un nodo **Condition** que convierta el código numérico a texto legible:

| Código | Condición |
|---|---|
| 0 | Cielo despejado |
| 1–3 | Parcialmente nublado |
| 45–48 | Niebla |
| 61–67 | Lluvia |
| 71–77 | Nieve |
| 80–82 | Chaparrones |
| 95 | Tormenta |

### 7.2 — Mostrar el nombre oficial de la ciudad

Reemplazar `Topic.city` en el mensaje final por `First(Topic.geoResponse.results).name` para mostrar el nombre que devuelve la API (más preciso que lo que escribió el usuario).

---

## Referencia rápida — API Open-Meteo

| Endpoint | Uso |
|---|---|
| `geocoding-api.open-meteo.com/v1/search?name={ciudad}` | Ciudad → coordenadas |
| `api.open-meteo.com/v1/forecast?latitude={lat}&longitude={lon}&current_weather=true` | Coordenadas → clima actual |

Sin autenticación. Límite: 10.000 llamadas/día.

