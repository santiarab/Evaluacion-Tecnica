# Protocolo HTTP – Resumen Técnico

## 1. Servidor HTTP
Un servidor HTTP es un software capaz de recibir solicitudes (HTTP requests) según el estándar HTTP/1.1 o HTTP/2 y devolver respuestas (HTTP responses). Gestiona recursos identificados por URIs y opera generalmente sobre TCP/IP en el puerto 80 (HTTP) o 443 (HTTPS).

---

## 2. Verbos HTTP
Los verbos HTTP definen la operación solicitada sobre un recurso.

### Verbos más utilizados:
- **GET**: lectura de recursos. No modifica estado. Idempotente.
- **POST**: creación/envío de datos. No idempotente.
- **PUT**: reemplazo completo de un recurso. Idempotente.
- **PATCH**: actualización parcial.
- **DELETE**: eliminación de un recurso.
- **HEAD**: igual a GET pero sin cuerpo.
- **OPTIONS**: consulta métodos soportados.

---

## 3. Request, Response y Headers

### Request
Estructura estándar:
