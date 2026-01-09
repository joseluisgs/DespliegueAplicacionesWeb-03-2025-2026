- [2. Componentes de una Web: Front-end, Back-end, Página Web vs. Aplicación Web](#2-componentes-de-una-web-front-end-back-end-página-web-vs-aplicación-web)
  - [2.1. Front-end y Back-end: La División y la Universalidad del Back-end](#21-front-end-y-back-end-la-división-y-la-universalidad-del-back-end)
  - [2.2. Página Web vs. Aplicación Web: Diferencias y Tecnologías Clave](#22-página-web-vs-aplicación-web-diferencias-y-tecnologías-clave)


# 2. Componentes de una Web: Front-end, Back-end, Página Web vs. Aplicación Web

## 2.1. Front-end y Back-end: La División y la Universalidad del Back-end

El desarrollo web actual ha especializado los perfiles en dos roles principales, reflejando la división entre el cliente y el servidor:

| Aspecto | Front-end | Back-end |
|---------|-----------|----------|
| **Ubicación** | Navegador del usuario | Servidor |
| **Lenguajes** | HTML, CSS, JavaScript | PHP, Python, Java, C#, Node.js |
| **Responsabilidad** | Interfaz y UX | Lógica de negocio y datos |
| **Objetivo** | Presentar información | Procesar y almacenar |

*   El **Front-end** es la parte visible de la aplicación, con la que el usuario interactúa directamente. Se encarga del diseño, maquetación y la lógica interactiva en el navegador, utilizando tecnologías como HTML, CSS y JavaScript (y sus *frameworks*). Un desarrollador Front-end también se preocupa por la correcta presentación en cualquier tipo de dispositivo e incluso por el posicionamiento en buscadores.

*   El **Back-end** es la parte del desarrollo que se ejecuta en el servidor. Incluye la lógica de negocio, la interacción con bases de datos y la administración del servidor de aplicaciones. Tecnologías como PHP, Java (Servlets/JSP), Python, ASP.NET (C#) o Ruby se utilizan en el Back-end.

📝 **Nota del Profesor**: Full-stack developer es el profesional que domina ambos lados. Aunque es posible conocer ambos, en equipos grandes cada especialidad se profundiza más.

La tendencia actual es que el **Back-end se vuelva universal o agnóstico**. Esto significa que el servidor expone su funcionalidad a través de **APIs (Application Programming Interfaces)** que pueden ser consumidas por cualquier tipo de cliente. Esta separación del Back-end del Front-end es crucial porque permite que el mismo Back-end pueda servir a:

*   **Aplicaciones web** (ej., Single Page Applications - SPAs) que se ejecutan en navegadores.
*   **Aplicaciones móviles** (iOS y Android).
*   **Aplicaciones de escritorio** (con interfaces nativas).
*   **Otros servicios o sistemas**.

💡 **Tip del Examinador**: La palabra clave aquí es "API". El Back-end moderno se diseña para ser consumido por múltiples clientes a través de APIs.

De esta manera, el Back-end se desvincula de una interfaz de usuario específica, ofreciendo datos en formatos estandarizados (como JSON o XML) que los clientes interpretan y renderizan según sus propias capacidades. Este enfoque es fundamental para la integración de diferentes servicios y para la creación de aplicaciones más flexibles y escalable.

![img](/images/front-back-api.jpg)

---

## 2.2. Página Web vs. Aplicación Web: Diferencias y Tecnologías Clave

Es fundamental distinguir entre una página web y una aplicación web:

| Característica | Página Web | Aplicación Web |
|----------------|------------|----------------|
| **Complejidad** | Simple a moderada | Compleja |
| **Interactividad** | Limitada | Alta |
| **Estado** | Stateless (sin estado) | Stateful (mantiene estado) |
| **Ejemplo** | Blog, landing page | Gmail, Netflix, Spotify |

*   Una **página web** es un documento o un conjunto de documentos que se muestran en un navegador. Puede ser **estática** (su contenido no cambia dinámicamente, a menos que un desarrollador la modifique manualmente), o **dinámica** (su contenido varía según interacciones, usuario o datos del servidor). Una página web estática puede visualizarse localmente sin un servidor web, pero una dinámica requiere de uno.

*   Una **aplicación web** es una herramienta de software más compleja, que utiliza páginas dinámicas (y puede incluir estáticas) y tecnologías web para proporcionar un **servicio o conjunto de servicios** al usuario. Es similar a una aplicación de escritorio, pero ejecutada en un navegador, lo que la independiza del sistema operativo cliente. Las aplicaciones web siempre requieren de un servidor web y de otros componentes.

📝 **Nota del Profesor**: La frontera entre página y aplicación web es cada vez más difusa. Hoy en día, hasta un blog tiene funciones de aplicación. Lo importante es entender el espectro de complejidad.

**Tabla de Tecnologías más usadas en el lado del cliente y servidor**:

| Perfil | Tipo de Entorno | Tecnología | Usos comunes |
|--------|-----------------|------------|--------------|
| **Front-end / Cliente** | Navegador Web | **HTML + CSS + JavaScript** | Estructura, estilo e interactividad de la interfaz de usuario. Animaciones, validación de formularios, comunicación asíncrona (AJAX). Frameworks JS (React.js, Vue.js, Angular, Svelte) para SPAs. |
| **Back-end / Servidor** | Servidor Web + BBDD | **PHP, Python, Ruby, Java / JSP, .Net / .asp (C#)** | Generación de páginas dinámicas, lógica de negocio, acceso a bases de datos, APIs. JavaScript (Node.js) también es popular. |

💡 **Tip del Examinador**: Pregunta habitual en el examen: "¿Qué diferencia hay entre página web estática y dinámica?" Respuesta: La dinámica se genera en el servidor según la petición, la estática ya existe como archivo.

⚠️ **Advertencia de Seguridad**: Las páginas web dinámicas son más vulnerables a ataques como SQL Injection y XSS. Siempre hay que sanitizar las entradas del usuario.

---

