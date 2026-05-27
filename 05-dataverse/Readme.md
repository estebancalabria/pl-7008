# Crear un agente con Microsoft Copilot Studio y Dataverse for Teams

## Guía completa 

Este documento resume de forma estructurada el proceso completo para crear, configurar, extender y publicar agentes utilizando Microsoft Copilot Studio junto con Dataverse for Teams, incluyendo integración con Power Automate, uso de temas, variables, condiciones y publicación en Microsoft Teams.

El objetivo es construir agentes de bajo código capaces de interactuar con usuarios, consultar datos dinámicos y automatizar procesos dentro de una organización.

---

# 1. Introducción

Los agentes inteligentes permiten mejorar el acceso a la información dentro de una organización, ayudando a:

* Tomar mejores decisiones
* Reducir errores operativos
* Ahorrar tiempo y costos
* Estandarizar respuestas

Microsoft Copilot Studio junto con Dataverse for Teams permiten crear estas soluciones sin necesidad de desarrollo tradicional.

Además, el enfoque incluye principios de IA responsable, considerando el impacto del sistema completo (tecnología, usuarios y contexto).

---

# 2. Creación del agente

## 2.1 Instalación en Microsoft Teams

Para comenzar, se instala Microsoft Copilot Studio dentro de Microsoft Teams:

1. Abrir Microsoft Teams
2. Ir a “Aplicaciones”
3. Buscar “Copilot”
4. Instalar Copilot Studio (o Power Virtual Agents en versiones antiguas)

---

## 2.2 Crear un nuevo agente

Pasos:

* Seleccionar “Comenzar ahora”
* Elegir el equipo propietario
* Esperar la configuración inicial
* Definir:

  * Nombre del agente
  * Idioma (no modificable luego)
  * Icono opcional
* Crear el agente

---

## 2.3 Capacidades del entorno

Una vez creado, el agente permite:

* Crear y editar conversaciones
* Probar el comportamiento
* Publicar en Teams u organización
* Analizar uso y rendimiento

---

# 3. Microsoft 365 Copilot Chat

También es posible crear agentes desde Microsoft 365 Copilot Chat:

* Creación sin código usando lenguaje natural
* Uso de plantillas o descripciones
* Publicación directa en Copilot Chat
* Refinamiento posterior en Copilot Studio

---

# 4. Temas en Copilot Studio

Los agentes se construyen mediante **temas**, que definen el flujo conversacional.

## 4.1 Tipos de nodos

### Nodos desencadenadores

* Detectan intención del usuario
* Basados en frases o palabras clave
* Recomendado: 5 a 10 variaciones

### Nodos de conversación

Definen cómo responde el agente:

* Mostrar mensaje
* Formular pregunta
* Aplicar condiciones
* Llamar acciones o flujos
* Redirigir a otro tema
* Finalizar conversación

---

## 4.2 Temas del sistema

Incluyen:

* Saludo
* Despedida
* Escalamiento
* Reinicio

El tema **Saludo** es clave para establecer contexto y expectativas del usuario.

---

# 5. Ejemplo de agente: Event Contacts

## 5.1 Frases desencadenadoras

* event contacts
* who are the event contacts
* event info
* event contact information

## 5.2 Lógica

El agente:

1. Detecta intención
2. Solicita información o usa datos predefinidos
3. Responde con contactos por país
4. Finaliza conversación

Ejemplo de salida:

* EE. UU. → Lynne Robbins
* Canadá → Lidia Holloway
* Francia → Miriam Graham
* España → Christie Cline

---

# 6. Variables, entradas y condiciones

## 6.1 Conceptos clave

* **Entradas**: respuestas del usuario
* **Variables**: almacenan datos para reutilizar
* **Condiciones**: definen ramificación del flujo

---

## 6.2 Ejemplo práctico

* Variable: `VarCountry`
* El usuario selecciona un país
* El agente responde según la selección

---

## 6.3 Variables del sistema

* `bot.UserDisplayName` → personalización del saludo
* `bot.UserID` → identificación del usuario

Ejemplo:

> Hola Juan, bienvenido al asistente…

---

# 7. Integración con Dataverse for Teams

En lugar de respuestas estáticas, se utilizan datos dinámicos desde Dataverse for Teams.

---

## 7.1 Caso: Sales Project Team

Tabla:

| Campo  | Tipo               |
| ------ | ------------------ |
| Nombre | Texto              |
| Email  | Correo electrónico |

Datos:

* Joseph Price
* Nathan Rigby
* Amber Rodriguez
* Monica Thomson

---

# 8. Llamar a una acción (Power Automate)

## 8.1 Objetivo

Permitir que el agente consulte datos dinámicos sin modificar su lógica.

---

## 8.2 Flujo: Get Sales Team Members

Estructura:

1. Trigger desde Copilot Studio
2. Inicializar variable `varContactInfo`
3. Listar filas desde Dataverse
4. Recorrer resultados (Apply to each)
5. Construir lista en formato Markdown
6. Retornar resultado al agente (`ContactData`)

---

## 8.3 Resultado

El agente devuelve una lista actualizada como:

* Joseph Price – [JosephP@contoso.com](mailto:JosephP@contoso.com)
* Nathan Rigby – [NathanR@contoso.com](mailto:NathanR@contoso.com)
* Amber Rodriguez – [AmberR@contoso.com](mailto:AmberR@contoso.com)
* Monica Thomson – [MonicaT@contoso.com](mailto:MonicaT@contoso.com)

---

# 9. Publicar y compartir el agente

## 9.1 Concepto clave

La publicación hace que el agente esté disponible para usuarios finales.

* Se puede republicar tras cambios
* La versión publicada no afecta usuarios inmediatamente

---

## 9.2 Opciones de distribución

Desde el panel de publicación en Microsoft Copilot Studio:

* Copiar vínculo
* Agregar a un equipo
* Publicar en Microsoft Teams Store

---

## 9.3 Alcance de publicación

### Nivel equipo

* Disponible solo para miembros del equipo
* Acceso inmediato

### Nivel organización

* Requiere aprobación del administrador
* Aparece en “Generado por su organización”
* Disponible para todos los usuarios de Teams

---

# 10. Resultado final del módulo

Al completar el módulo, el agente es capaz de:

* Manejar conversaciones con temas estructurados
* Usar variables y condiciones dinámicas
* Personalizar respuestas por usuario
* Integrarse con Dataverse for Teams
* Ejecutar flujos de Power Automate
* Consultar datos en tiempo real
* Publicarse en Microsoft Teams
* Escalar a nivel organizacional

---

# 11. Conclusión

Este recorrido muestra el ciclo completo de un agente en Microsoft Copilot Studio:

* Diseño conversacional (temas)
* Lógica dinámica (variables y condiciones)
* Integración con datos (Dataverse)
* Automatización (Power Automate)
* Publicación y distribución (Teams)

El resultado es una solución empresarial escalable, mantenible y orientada a datos reales.
