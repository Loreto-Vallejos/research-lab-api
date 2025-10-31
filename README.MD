# **Trabajo de Investigación: HTTP, HTTPS y Comunicación Web**

**Autor:** María Loreto Vallejos | **Cohorte:** 22

---

## 🧩 **1. Diferencia entre HTTP y HTTPS**

- **HTTP** (*HyperText Transfer Protocol*):  
  Es el protocolo que permite la comunicación entre un cliente (como un navegador) y un servidor web. 
  Es la base del funcionamiento de la web, ya que permite transferir información en forma de hipertexto.  
 

- **HTTPS** (*HyperText Transfer Protocol Secure*):  
  Es la versión segura de HTTP. Utiliza **TLS/SSL** para cifrar la comunicación entre el navegador y el servidor, protegiendo los datos del usuario.  
  

---

### 🔒 **Cómo funciona el cifrado SSL/TLS**

1. El navegador solicita una conexión segura (`https://`).
2. El servidor responde enviando su **certificado digital**.
3. El navegador **verifica** que el certificado sea válido.
4. Se negocian los algoritmos de cifrado.
5. Ambos establecen una **clave de sesión** para cifrar la información.

Gracias a este proceso, la información viaja de forma segura y no puede ser interceptada.  

---

### 🛡️ **Por qué HTTPS es más seguro**

- **Cifra los datos:** evita que terceros los intercepten.  
- **Autentica la identidad del servidor:** asegura que el sitio es legítimo.  
- **Mantiene la integridad:** los datos no pueden ser modificados.  
- **Mejora la confianza:** los navegadores marcan los sitios sin HTTPS como “No seguros”.

---

### 🔍 **Ejemplo visual del candado en el navegador**

![Sitio seguro en Chrome](https://xneelo.co.za/help-centre/wp-content/uploads/2009/08/securexneelo.png)
![Sitio no seguro](https://www.twilo.net/wp-content/uploads/chrome-68-browser-alert.jpg)

- 🔒 Candado: conexión segura con HTTPS.  
- ⚠️ “No seguro”: el sitio usa HTTP sin cifrado.

---

### ⚠️ **Qué pasa si un sitio no usa HTTPS**

- La información puede ser interceptada.  
- No se puede verificar la autenticidad del sitio.  
- Formularios y contraseñas quedan expuestos.  
- Navegadores muestran advertencias y baja el SEO.  

---

## 🔹 **2. Puertos de comunicación**

### 🔸 **Qué es un puerto y por qué es importante**

Un **puerto** es un número que identifica un punto de conexión dentro de una dirección IP. Sirve para distinguir diferentes servicios que se ejecutan en un mismo servidor.  
En el caso de **HTTP**, los navegadores utilizan el puerto **80** por defecto para enviar y recibir solicitudes.

---

### 🔸 **Puertos 80 y 8080**

- **Puerto 80:** usado por HTTP sin cifrado.  
- **Puerto 8080:** alternativa al 80, normalmente para entornos de desarrollo o pruebas.

Ejemplo:  
`http://localhost:8080` → el navegador se conecta al puerto 8080 del servidor local.

---

### 🔸 **Otros puertos conocidos**

| Puerto | Servicio | Descripción |
|--------|-----------|-------------|
| 21     | FTP       | Transferencia de archivos. |
| 22     | SSH       | Conexión remota segura. |
| 443    | HTTPS     | Tráfico web cifrado. |
| 3306   | MySQL     | Conexión a bases de datos. |

---

### 🔸 **Puerto de HTTPS**

Por defecto, **HTTPS utiliza el puerto 443**, ya que requiere cifrado con TLS/SSL.

---

## ⚙️ **3. Códigos de estado de respuesta HTTP**

Los **status codes** son mensajes que un servidor envía para indicar el resultado de una solicitud. Permiten saber si la operación fue exitosa, si hubo un error o si se requiere otra acción.

---

### 🔸 **Tabla de códigos por categoría**

| Categoría                | Rango   | Descripción general                                  | Ejemplo                   |
|--------------------------|---------|------------------------------------------------------|---------------------------|
| 1xx – Informativos       | 100–199 | El servidor recibió la solicitud y sigue procesando. | 100 Continue              |
| 2xx – Éxito              | 200–299 | La solicitud fue procesada correctamente.            | 200 OK                    |
| 3xx – Redirección        | 300–399 | La solicitud se redirige a otro recurso.             | 301 Moved Permanently     |
| 4xx – Error del cliente  | 400–499 | El error fue causado por el cliente.                 | 404 Not Found             |
| 5xx – Error del servidor | 500–599 | El error ocurre dentro del servidor.                 | 500 Internal Server Error |

---

### 🔸 **Códigos importantes**

- **200 OK:** Todo salió bien, el servidor devolvió una respuesta exitosa.  
- **404 Not Found:** El recurso solicitado no existe o fue movido.  
- **500 Internal Server Error:** El servidor tuvo un problema al procesar la solicitud.

---

### 💬 **Uso práctico**

En una API o página web, estos códigos ayudan a diagnosticar errores:
- Si obtengo un **404**, sé que la URL o el recurso está mal escrito.  
- Si recibo un **500**, debo revisar la lógica del servidor.  
- Si veo un **200**, todo está funcionando correctamente.

---

## 🧱 **4. Métodos HTTP**

Los **métodos HTTP** definen qué tipo de acción se quiere realizar sobre un recurso.

| Método      | Acción     | Uso principal                                | Ejemplo              |
|-------------|------------|----------------------------------------------|----------------------|
| **GET**     | Consultar  | Obtener información del servidor.            | `GET /usuarios`      |
| **POST**    | Crear      | Enviar datos para crear un recurso nuevo.    | `POST /usuarios`     |
| **PUT**     | Actualizar | Reemplazar o modificar un recurso existente. | `PUT /usuarios/5`    |
| **DELETE**  | Eliminar   | Borrar un recurso específico.                | `DELETE /usuarios/5` |

---

### 💡 **Otros métodos menos comunes**

- **PATCH:** actualiza solo una parte del recurso.  
- **HEAD:** igual que GET, pero solo obtiene los encabezados.  
- **OPTIONS:** muestra qué métodos permite un servidor para una URL específica.

---

## 📨 **5. Cabeceras (Headers)**

Las **cabeceras HTTP** son pares de clave–valor que viajan junto a una solicitud o respuesta.  
Sirven para enviar **información adicional** sobre la comunicación, como tipo de contenido, autenticación o detalles del cliente.

---

### 🔸 **Tipos de información en los headers**

| Cabecera          | Función                                                         |
|-------------------|-----------------------------------------------------------------|
| **Content-Type**  | Indica el formato del cuerpo (por ejemplo, `application/json`). |
| **Authorization** | Envía tokens o credenciales de acceso.                          |
| **User-Agent**    | Describe el navegador o cliente que hace la solicitud.          |
| **Accept**        | Define qué tipos de respuesta acepta el cliente.                |

---

### 🔸 **Ejemplo de solicitud HTTP con cabeceras**

```http
GET /api/usuarios HTTP/1.1
Host: ejemplo.com
Content-Type: application/json
Authorization: Bearer 12345tokenabc
User-Agent: Mozilla/5.0
Accept: application/json

##Permite que el servidor entienda cómo procesar la solicitud y qué tipo de respuesta enviar.
Incluye método, URL, cabeceras y, en otros casos, el cuerpo de la solicitud.


## Fuentes consultadas

Mozilla Developer Network. (s.f.). HTTP Overview. MDN Web Docs. Recuperado el 30 de octubre de 2025, de https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview

Mozilla Developer Network. (s.f.). HTTPS. MDN Web Docs. Recuperado el 30 de octubre de 2025, de https://developer.mozilla.org/en-US/docs/Glossary/HTTPS

Mozilla Developer Network. (s.f.). Transport Layer Security (TLS) Handshake. MDN Web Docs. Recuperado el 30 de octubre de 2025, de https://developer.mozilla.org/en-US/docs/Web/Security/Transport_Layer_Security

Cloudflare. (s.f.). What happens in a TLS handshake? Cloudflare Learning Center. Recuperado el 30 de octubre de 2025, de https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/

W3Schools. (s.f.). HTTP Methods. Recuperado el 30 de octubre de 2025, de https://www.w3schools.com/tags/ref_httpmethods.asp

Mozilla Developer Network. (s.f.). HTTP Response Status Codes. MDN Web Docs. Recuperado el 30 de octubre de 2025, de https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

Mozilla Developer Network. (s.f.). HTTP Headers. MDN Web Docs. Recuperado el 30 de octubre de 2025, de https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
