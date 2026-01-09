- [4. El Protocolo HTTP y HTTPS](#4-el-protocolo-http-y-https)
  - [4.1. Características y Ventajas del Protocolo HTTP](#41-características-y-ventajas-del-protocolo-http)
  - [4.2. Formato de Peticiones y Respuestas HTTP](#42-formato-de-peticiones-y-respuestas-http)
  - [4.3. Cabeceras HTTP](#43-cabeceras-http)
  - [4.4. Métodos/Verbos HTTP (GET, POST, PUT, DELETE, HEAD)](#44-métodosverbos-http-get-post-put-delete-head)
  - [4.5. Códigos de Estado HTTP](#45-códigos-de-estado-http)
  - [4.6. El Protocolo HTTPS (SSL/TLS y Certificados Digitales)](#46-el-protocolo-https-ssltls-y-certificados-digitales)


# 4. El Protocolo HTTP y HTTPS

## 4.1. Características y Ventajas del Protocolo HTTP

El **Protocolo HTTP (HyperText Transfer Protocol)** es la base de la comunicación en la World Wide Web. Es un protocolo **no orientado a la conexión**, lo que significa que cada petición entre cliente y servidor es independiente y no requiere mantener una conexión continua.

```mermaid
sequenceDiagram
    participant Cliente
    participant Servidor
    
    Cliente->>Servidor: GET /index.html HTTP/1.1
    Servidor-->>Cliente: HTTP/1.1 200 OK
    
    Note over Cliente,Servidor: Cada petición es independiente

    Cliente->>Servidor: POST /login HTTP/1.1
    Servidor-->>Cliente: HTTP/1.1 200 OK
```

Sus principales **características** son:

*   **Sencillo**: Es en modo texto y fácil de usar directamente por una persona.
*   **Extensible**: Se pueden enviar más metadatos que los que están por defecto.
*   **Sin estado**: Cada petición es independiente. Esto es un problema para sitios como un carrito de la compra, pero se soluciona con *cookies* y sesiones.

📝 **Nota del Profesor**: HTTP es la lingua franca de la web. Aunque haya protocolos como gRPC o WebSocket por debajo usan TCP/HTTP2. Entender HTTP es fundamental.

HTTP es fundamental en arquitecturas distribuidas como los microservicios y es la base para la creación de APIs REST. Ofrece ventajas como la mejora de la velocidad al controlar la **caché** de las páginas, la **autenticación** de usuarios, el uso transparente de **proxies** y el mantenimiento del estado entre peticiones gracias a las **sesiones**. También permite indicar el formato de lo que se envía, pide y retorna.

💡 **Tip del Examinador**: Pregunta clásica: "¿Qué significa que HTTP sea stateless?" Respuesta: Cada petición es independiente, el servidor no recuerda las anteriores.

---

## 4.2. Formato de Peticiones y Respuestas HTTP

La interacción en la web se basa en un intercambio constante de peticiones y respuestas HTTP entre el navegador del cliente y el servidor.

**Estructura de una Petición HTTP**:

```http
GET /pagina/ejemplo.html HTTP/1.1
Host: www.ejemplo.com
User-Agent: Mozilla/5.0
Accept: text/html
Accept-Language: es-ES
```

**Estructura de una Respuesta HTTP**:

```http
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Content-Length: 1234
Server: Apache/2.4.41

<!DOCTYPE html>
<html>...</html>
```

Una **petición HTTP** tiene una primera línea que incluye el método (ej. GET), la ruta del recurso solicitado (ej. `/index.html`), y la versión del protocolo (ej. `HTTP/1.1`), seguida de varias líneas con cabeceras que proporcionan metadatos.

La **respuesta HTTP** del servidor comienza con la versión del protocolo (ej. `HTTP/1.1`), seguida de un código de estado (ej. `200 OK`) y un texto que indica el resultado de la operación. Después de una línea vacía, se incluye el contenido del recurso solicitado (ej. HTML).

📝 **Nota del Profesor**: La línea en blanco entre cabeceras y cuerpo es fundamental. Sin ella, el servidor no sabe dónde terminan las cabeceras y dónde empieza el contenido.

![img](/images/http.png)

💡 **Tip del Examinador**: En el examen práctico, os pueden pedir identificar las partes de una petición/respuesta HTTP. Fijaos en la primera línea y en la línea vacía.

---

## 4.3. Cabeceras HTTP

Las cabeceras HTTP son mensajes adicionales que se envían tanto en las peticiones como en las respuestas para proporcionar información clave sobre la comunicación.

| Cabecera de Petición | Descripción | Ejemplo |
|----------------------|-------------|---------|
| `Accept` | Formato MIME deseado | `application/json` |
| `Accept-Language` | Idioma preferido | `es-ES, en-US` |
| `Host` | Dominio destino | `www.ejemplo.com` |
| `Content-Type` | Formato del cuerpo | `application/x-www-form-urlencoded` |
| `Content-Length` | Tamaño del cuerpo | `1024` |
| `User-Agent` | Información del cliente | `Mozilla/5.0` |

**Cabeceras de Petición Comunes**:

*   `Accept`: El formato MIME type en el que se quieren los datos (ej., `text/html`, `application/json`).
*   `Accept-Language`: El idioma preferido para la respuesta (ej., `fr`).
*   `Host`: El dominio al que se dirige la petición, muy útil para alojar varios dominios en un mismo servidor.
*   `Content-Type`: Describe el formato y la codificación de los datos que se envían en el cuerpo de la petición.
*   `Content-Length`: Tamaño en bytes de los datos que se envían.
*   `User-Agent`: Información sobre el navegador del cliente.

**Cabeceras de Respuesta Comunes**:

| Cabecera de Respuesta | Descripción | Ejemplo |
|----------------------|-------------|---------|
| `Content-Type` | Formato del cuerpo | `text/html; charset=utf-8` |
| `Content-Language` | Idioma del contenido | `es` |
| `Content-Length` | Tamaño en bytes | `4096` |
| `Cache-Control` | Política de caché | `max-age=3600` |
| `Server` | Información del servidor | `Apache/2.4.41` |

*   `Content-Type`: El formato y la codificación de los datos que se retornan (ej., `text/html; charset=utf-8`), crucial para que el navegador interprete correctamente el contenido.
*   `Content-Language`: El idioma de los datos que se retornan.
*   `Content-Length`: Tamaño en bytes de los datos que se retornan.
*   `Cache-Control`: Cuánto tiempo pueden estar cacheados los datos.
*   `Server`: Indica información del servidor (ej. Apache/2.2.3).

💡 **Tip del Examinador**: `Content-Type` es una de las cabeceras más importantes. Un error aquí puede hacer que el navegador muestre texto plano en lugar de HTML renderizado.

⚠️ **Advertencia de Seguridad**: La cabecera `Server` revela información del servidor (versión). En producción, es recomendable ocultarla para no facilitar ataques.

---

## 4.4. Métodos/Verbos HTTP (GET, POST, PUT, DELETE, HEAD)

Los métodos HTTP, también llamados verbos, definen la acción que un cliente desea realizar sobre un recurso en el servidor.

| Método | Acción | ¿Body? | Idempotente | Uso Típico |
|--------|--------|--------|-------------|------------|
| **GET** | Obtener recurso | No | Sí | Leer datos |
| **POST** | Crear recurso | Sí | No | Formularios, crear |
| **PUT** | Actualizar completo | Sí | Sí | Reemplazar recurso |
| **PATCH** | Actualizar parcial | Sí | No | Modificar parcialmente |
| **DELETE** | Borrar recurso | No | Sí | Eliminar recurso |
| **HEAD** | Solo cabeceras | No | Sí | Verificar recurso |

*   **GET**: Se utiliza para **obtener** o recuperar un recurso. Generalmente, no se envían datos en el cuerpo de la petición; cualquier parámetro se adjunta a la URL como una cadena de consulta (*query string*).

*   **POST**: Se usa para **añadir** un nuevo recurso o **enviar** datos al servidor. Los datos se incluyen en el cuerpo de la petición, después de las cabeceras, y no son visibles en la URL.

*   **PUT**: Se utiliza para **actualizar** o **reemplazar** completamente un recurso existente en el servidor con los datos proporcionados.

*   **DELETE**: Se usa para **borrar** un recurso o entidad específica del servidor.

*   **HEAD**: Solicita las mismas cabeceras de respuesta que un método GET, pero sin el cuerpo de la respuesta. Es útil para verificar la existencia de un recurso o sus metadatos sin descargar el contenido completo.

📝 **Nota del Profesor**: GET no debe modificar estado en el servidor. Si haces un GET que cambia datos, estás violando los principios de HTTP. POST para modificar, GET para leer.

💡 **Tip del Examinador**: Diferencia clave POST vs GET: POST tiene body (más seguro para contraseñas), GET tiene parámetros en URL (visible en historial).

📝 **Regla Nemotécnica**: "GET = Obtener (en la URL), POST = Enviar (en el body)"

![img](/images/http-metodos.gif)

⚠️ **Advertencia de Seguridad**: Los parámetros de GET se ven en URLs, logs y historial. Nunca envies contraseñas o datos sensibles por GET.

---

## 4.5. Códigos de Estado HTTP

Después de cada petición, el servidor envía una respuesta que incluye un código de estado HTTP. Este código es un número de tres dígitos que indica el resultado y el estado de la petición.

```mermaid
graph TD
    A[Código de Estado] --> B[1xx Informativa]
    A --> C[2xx Éxito]
    A --> D[3xx Redirección]
    A --> E[4xx Error Cliente]
    A --> F[5xx Error Servidor]
    
    B --> B1[100 Continue]
    B --> B2[101 Switching Protocols]
    
    C --> C1[200 OK]
    C --> C2[201 Created]
    C --> C3[204 No Content]
    
    D --> D1[301 Moved Permanently]
    D --> D2[302 Found]
    D --> D3[304 Not Modified]
    
    E --> E1[400 Bad Request]
    E --> E2[401 Unauthorized]
    E --> E3[403 Forbidden]
    E --> E4[404 Not Found]
    
    F --> F1[500 Internal Server Error]
    F --> F2[502 Bad Gateway]
    F --> F3[503 Service Unavailable]
```

*   **1XX (Informativa)**: La petición ha sido recibida y el proceso continúa.
*   **2XX (Éxito)**: La acción del cliente fue recibida, entendida y aceptada. Por ejemplo, **200 OK** indica que la petición se ha procesado correctamente.
*   **3XX (Redirección)**: El cliente necesita realizar una acción adicional para completar la petición (ej., el recurso se ha movido).
*   **4XX (Error del Cliente)**: La petición contiene un error o no puede ser completada debido a un problema en el lado del cliente (ej. **403 Forbidden**, **404 Not Found**).
*   **5XX (Error del Servidor)**: El servidor falló al completar una petición aparentemente válida.

| Código | Significado | Uso Típico |
|--------|-------------|------------|
| 200 | OK | Petición exitosa |
| 201 | Created | Recurso creado (POST) |
| 204 | No Content | Petición exitosa sin respuesta |
| 301 | Moved Permanently | Redirección permanente |
| 304 | Not Modified | Usar caché |
| 400 | Bad Request | Petición mal formada |
| 401 | Unauthorized | No autenticado |
| 403 | Forbidden | Autenticado pero sin permiso |
| 404 | Not Found | Recurso no existe |
| 500 | Internal Server Error | Error en servidor |
| 503 | Service Unavailable | Servidor sobrecargado |

📝 **Nota del Profesor**: El 404 es el más famoso, pero conocer los de autenticación (401 vs 403) es importante para seguridad.

💡 **Tip del Examinador**: Pregunta asegurada: "¿Cuál es la diferencia entre 401 y 403?" 401 = No identificado, 403 = Identificado pero sin permiso.

⚠️ **Advertencia de Seguridad**: El 500 revela errores internos. En producción, mostrar una página genérica y logger el error real.

![img](/images/status-code.png)

---

## 4.6. El Protocolo HTTPS (SSL/TLS y Certificados Digitales)

**HTTPS** (HyperText Transfer Protocol Secure) es la versión segura del protocolo HTTP, esencial para la transferencia confidencial y segura de información entre el cliente y el servidor. A diferencia de HTTP, que transmite datos en texto claro y vulnerable a la intercepción, HTTPS **cifra** la información, asegurando su privacidad.

```mermaid
sequenceDiagram
    participant Cliente
    participant Servidor
    
    Note over Cliente: Genera clave pública/privada
    Cliente->>Servidor: Hola, quiero conectar (certificado)
    Servidor-->>Cliente: Aquí está mi certificado (firmado por CA)
    Note over Cliente: Verifica certificado con CA
    Cliente->>Servidor: Generamos clave compartida (cifrado asimétrico)
    Servidor-->>Cliente: OK (cifrado simétrico)
    Note over Cliente,Servidor: Comunicación cifrada
```

La seguridad en HTTPS se basa en el uso de **certificados digitales**. Estos documentos electrónicos vinculan una clave pública a la identidad de un propietario (servidor web). Son emitidos por **Autoridades de Certificación (AC)**, que son entidades de confianza que firman digitalmente los certificados para validar su autenticidad. Los navegadores web confían en estas AC y alertan al usuario si un certificado no es válido, está autofirmado o no coincide con el sitio, lo que puede generar advertencias de seguridad.

| Componente | Descripción |
|------------|-------------|
| **Certificado SSL/TLS** | Documento que vincula clave pública a identidad |
| **CA (Certificate Authority)** | Entidad que firma y verifica certificados |
| **Clave Pública** | Para cifrar, visible en el certificado |
| **Clave Privada** | Para descifrar, solo el servidor la conoce |
| **Cifrado Asimétrico** | Clave pública/privada para establecer conexión |
| **Cifrado Simétrico** | Una clave única para la comunicación |

El proceso de cifrado utiliza el **cifrado de clave pública o asimétrico**. El navegador cifra la información con la clave pública del servidor, y solo el servidor, con su clave privada correspondiente, puede descifrarla, garantizando así la confidencialidad. Los protocolos **SSL/TLS** (Secure Sockets Layer/Transport Layer Security) son los estándares criptográficos que hacen posibles estas conexiones seguras, proporcionando autenticación y privacidad. El cifrado requiere recursos computacionales, lo que puede tener un impacto mínimo en el rendimiento del servidor web. HTTP y HTTPS pueden coexistir en un mismo dominio.

📝 **Nota del Profesor**: HTTPS es obligatorio hoy en día. Google penaliza en SEO a webs sin HTTPS, y los navegadores muestran advertencias.

💡 **Tip del Examinador**: En producción, TODO debe ser HTTPS. LetsEncrypt ofrece certificados gratuitos.

⚠️ **Advertencia de Seguridad**: Un certificado autofirmado no es seguro para producción. Permite ataques man-in-the-middle.

📝 **Regla Nemotécnica**: "HTTPS = HTTP + Seguridad + TLS/SSL"

---
