# Evaluación Técnica: Fundamentos del Protocolo HTTP

Este documento reúne las respuestas teóricas sobre el funcionamiento del protocolo HTTP, abarcando desde conceptos básicos de arquitectura cliente-servidor hasta estándares de intercambio de datos como REST y SOAP.

---

## 1. ¿Qué es un servidor HTTP?

Un **servidor HTTP** es un software que se ejecuta en una máquina (física o virtual) y que entiende el protocolo de transferencia de hipertexto (HTTP). Su función principal es **escuchar** las peticiones (requests) provenientes de clientes (como navegadores web o aplicaciones móviles) y **responder** entregando los recursos solicitados (archivos HTML, imágenes, datos JSON, etc.) o realizando una acción específica.

Ejemplos populares: *Apache, Nginx, Microsoft IIS.*

---

## 2. Verbos HTTP

Los verbos (o métodos) HTTP indican la **acción** que se desea realizar sobre un recurso identificado. Los más conocidos y utilizados son:

| Verbo | Descripción | Uso común |
| :--- | :--- | :--- |
| **GET** | Solicita una representación del recurso especificado. | Obtener datos. |
| **POST** | Envía datos al servidor para crear un nuevo recurso. | Enviar formularios, crear usuarios. |
| **PUT** | Reemplaza todas las representaciones actuales del recurso de destino con la carga útil de la petición. | Actualizar un registro completo. |
| **PATCH** | Aplica modificaciones parciales a un recurso. | Actualizar solo un campo de un registro. |
| **DELETE** | Borra el recurso especificado. | Eliminar datos. |

---

## 3. Request, Response y Headers

En una comunicación HTTP estándar existe un ciclo de petición y respuesta:

* **Request (Petición):** Es el mensaje que envía el cliente al servidor pidiendo un recurso. Contiene el verbo, la URL, la versión del protocolo, los headers y, opcionalmente, un cuerpo (body).
* **Response (Respuesta):** Es el mensaje que el servidor envía de vuelta. Contiene el código de estado, los headers y, habitualmente, el recurso solicitado en el cuerpo del mensaje.
* **Headers (Encabezados):** Son pares de `clave: valor` que se envían tanto en la petición como en la respuesta. Transmiten **metadatos** o información adicional sobre la comunicación (ej. tipo de navegador, cookies, tipo de contenido, caché).

---

## 4. QueryString

El **QueryString** es una parte de la URL que asigna valores a parámetros específicos. Se ubica después del signo de interrogación `?` y se utiliza para enviar pequeñas cantidades de datos al servidor, generalmente para filtrar o buscar información.

**Estructura:**
`?clave1=valor1&clave2=valor2`

**Ejemplo:**
`https://tienda.com/productos?categoria=zapatos&color=negro`

---

## 5. Response Codes (Códigos de Estado)

El **Response Code** es un número de tres dígitos que el servidor envía para indicar el resultado de la petición. Se agrupan en cinco clases según su primer dígito:

* **1xx (Informativos):** La petición fue recibida y el proceso continúa.
* **2xx (Éxito):** La acción fue recibida, entendida y aceptada correctamente.
    * *Ej: 200 OK, 201 Created.*
* **3xx (Redirección):** Se necesitan acciones adicionales para completar la petición.
    * *Ej: 301 Moved Permanently.*
* **4xx (Error del Cliente):** La petición contiene sintaxis incorrecta o no puede cumplirse.
    * *Ej: 400 Bad Request, 404 Not Found.*
* **5xx (Error del Servidor):** El servidor falló al intentar cumplir una petición aparentemente válida.
    * *Ej: 500 Internal Server Error.*

---

## 6. Envío de datos: GET vs POST

| Característica | Método GET | Método POST |
| :--- | :--- | :--- |
| **Ubicación de datos** | En la URL (QueryString). | En el cuerpo (Body) del mensaje. |
| **Visibilidad** | Visible para todos en la barra de direcciones. | Oculto al usuario promedio (visible en inspección de red). |
| **Límite de tamaño** | Limitado por la longitud máxima de la URL (aprox. 2048 caracteres). | Sin límite teórico (depende de la configuración del servidor). |
| **Uso ideal** | Búsquedas, filtros, lectura de datos. | Envío de contraseñas, subida de archivos, creación de registros. |

---

## 7. Comportamiento del Navegador

Cuando escribimos una URL en la barra de direcciones y presionamos Enter, o cuando hacemos clic en un enlace estándar, el navegador utiliza por defecto el verbo **GET** para solicitar la página web.

---

## 8. Estructuras de Datos: JSON vs XML

Ambos son formatos de texto para el intercambio de datos, pero tienen sintaxis y propósitos ligeramente distintos.

### JSON (JavaScript Object Notation)
Es ligero, fácil de leer por humanos y máquinas, y es el estándar actual para APIs REST y aplicaciones web modernas. Se basa en pares clave-valor.

```json
{
  "usuario": {
    "id": 101,
    "nombre": "Ana García",
    "intereses": ["Programación", "Lectura"],
    "activo": true
  }
}