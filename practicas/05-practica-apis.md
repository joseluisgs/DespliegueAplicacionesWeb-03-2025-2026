# 📝 Práctica de Investigación: Análisis Comparativo de Paradigmas de API

- [📝 Práctica de Investigación: Análisis Comparativo de Paradigmas de API](#-práctica-de-investigación-análisis-comparativo-de-paradigmas-de-api)
  - [Título: **REST, GraphQL y WebSocket: ¿Cuál elegir y por qué?**](#título-rest-graphql-y-websocket-cuál-elegir-y-por-qué)
    - [🎯 Objetivo de la Práctica](#-objetivo-de-la-práctica)
    - [📚 Tareas y Contenido a Investigar (Documento Técnico)](#-tareas-y-contenido-a-investigar-documento-técnico)
      - [1. Introducción](#1-introducción)
      - [2. Desarrollo Detallado por Tecnología (REST, GraphQL, WebSocket)](#2-desarrollo-detallado-por-tecnología-rest-graphql-websocket)
      - [3. Análisis Comparativo y Toma de Decisiones](#3-análisis-comparativo-y-toma-de-decisiones)
      - [4. Casos de Uso y Conclusión](#4-casos-de-uso-y-conclusión)
    - [🛠 Requisitos de Entrega y Formato](#-requisitos-de-entrega-y-formato)


## Título: **REST, GraphQL y WebSocket: ¿Cuál elegir y por qué?**

### 🎯 Objetivo de la Práctica

El objetivo de esta práctica es que investigues a fondo y compares tres arquitecturas clave para la comunicación entre cliente y servidor en el desarrollo web moderno: **RESTful API**, **GraphQL** y **WebSocket**. Deberás desgranar sus bases a nivel de **protocolo, sintaxis y gestión de errores** para comprender sus diferencias fundamentales.

Al finalizar, deberás ser capaz de **justificar técnicamente** qué arquitectura es la más adecuada para distintos tipos de proyectos.

---

### 📚 Tareas y Contenido a Investigar (Documento Técnico)

Tu trabajo debe entregarse como un **Informe Técnico** estructurado con los siguientes apartados obligatorios.

#### 1. Introducción

* Presentación del trabajo y el objetivo.
* Breve contextualización de la importancia de elegir la arquitectura de comunicación correcta.

***

#### 2. Desarrollo Detallado por Tecnología (REST, GraphQL, WebSocket)

Para cada una de las tres tecnologías, crea un subapartado con la siguiente información, centrándote en el **detalle técnico y de protocolo**:

| Aspecto a Investigar            | Pregunta de Investigación Técnica                                                                                                                                                                                                                    |
| :------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Concepto y Filosofía**        | ¿Cuál es la **filosofía** de diseño principal de cada uno? (¿Se orienta a **Recursos**, a un **Grafo de Datos**, o a un **Canal Persistente**?).                                                                                                     |
| **Protocolo Base**              | ¿Sobre qué protocolo de red opera o se basa cada arquitectura (HTTP/1.1, TCP, etc.)?                                                                                                                                                                 |
| **Operaciones y Métodos**       | ¿Qué **mecanismos y sintaxis** utiliza el cliente para solicitar acciones al servidor? (Investiga los **Verbos HTTP** en REST y las **operaciones** en GraphQL y WebSocket).                                                                         |
| **Estructura de la Petición**   | **Técnico:** ¿Cómo se estructura la solicitud? ¿Se usan **URLs con recursos**? ¿Existe un ***endpoint* único**? ¿Cuál es el papel del ***payload*** (cuerpo de la solicitud)?                                                                        |
| **Códigos de Estado y Errores** | **Técnico:** ¿Qué **Códigos de Estado HTTP** se utilizan en REST y qué indican sobre el estado del **recurso**? ¿Cómo se gestionan los errores en **GraphQL** (a nivel HTTP y a nivel de datos)? ¿Y los errores en **WebSocket** (a nivel de canal)? |
| **Pros y Contras**              | Enumera y explica al menos 3 **Ventajas** y 3 **Desventajas** de la tecnología.                                                                                                                                                                      |

***

#### 3. Análisis Comparativo y Toma de Decisiones

En este apartado, cruza la información para comparar directamente las arquitecturas, analizando el **porqué de sus diferencias técnicas**:

1.  **Eficiencia de Datos:** ¿Qué es el **sobre-recuperación de datos (*over-fetching*)** y la **infra-recuperación de datos (*under-fetching*)**? ¿Qué tecnología ofrece la solución más eficiente para evitar estos problemas y por qué?
2.  **Modelo de Comunicación:** Compara la comunicación **orientada a la solicitud-respuesta** (REST/GraphQL) frente a la **bidireccionalidad y persistencia** (WebSocket). Incluye un diagrama simple para ilustrar el flujo de datos en cada caso.
3.  **Tecnologías:** Menciona *frameworks* o tecnologías comunes para implementar cada una (Ej. Express.js, Apollo Server, Librerías del *Browser*).

***

#### 4. Casos de Uso y Conclusión

1.  **Justificación de Elección (Toma de Decisión):**
    * Describe **tres proyectos diferentes** (uno para cada tecnología).
    * **Justifica:** Indica cuál de las tres arquitecturas **elegirías como la mejor opción para cada proyecto** y **por qué**, basándote en el análisis técnico de protocolo, rendimiento y modelo de comunicación.
2.  **Conclusión Final:**
    * Resumen de los principales hallazgos y una conclusión clara sobre cuándo y por qué se debería elegir cada arquitectura en el desarrollo profesional.

---

### 🛠 Requisitos de Entrega y Formato

* **Formato:** Documento PDF profesional con índice de contenidos y paginado.
* **Investigación:** Utiliza fuentes fiables (documentación oficial, RFCs, artículos técnicos) y **cita las fuentes** utilizadas.
* **Claridad:** El lenguaje debe ser técnico y preciso.
* **Apoyo Visual:** Incluye al menos un diagrama o esquema que ilustre el flujo de peticiones/respuestas o el modelo de conexión de cada arquitectura.

**¡Comienza la investigación en profundidad!**