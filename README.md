# Taller-postman-Caceres

## Marco conceptual

### ¿Qué es una API REST?
Una API REST (*Representational State Transfer*) es un conjunto de reglas y protocolos arquitectónicos que permiten la comunicación entre diferentes sistemas y aplicaciones a través de la web utilizando el protocolo HTTP. Que sea "REST" significa que es un estilo de arquitectura sin estado (*stateless*), donde cada solicitud del cliente debe contener toda la información necesaria para que el servidor la procese, y las respuestas pueden ser cacheadas o interpretadas de manera estándar (generalmente usando formatos como JSON).

* **¿Qué es un recurso?:** Es cualquier objeto, entidad o dato que el sistema puede almacenar y exponer para que sea consultado o modificado (por ejemplo, un usuario, un producto, una publicación o una canción).
* **¿Qué es un endpoint?:** Es la URL específica o punto de acceso digital donde una API recibe las peticiones de los clientes para interactuar con un recurso determinado (por ejemplo, `https://api.ejemplo.com/posts`).
* **Ejemplo cotidiano:** Una aplicación que usamos a diario y que depende fuertemente de APIs es **Spotify**. Cuando buscas una canción en la app de tu teléfono (el cliente), la aplicación realiza una petición a los servidores de Spotify a través de un endpoint para solicitar los datos de la canción, el artista y la carátula, trayendo la información en tiempo real para que puedas reproducirla.

**Fuente consultada:** Red Hat - ¿Qué es una API REST? (https://www.redhat.com/es/topics/api/what-is-a-rest-api)

## Métodos HTTP

| Método | Operación CRUD | Qué hace |
| :--- | :--- | :--- |
| **GET** | Read (Leer) | Solicita y recupera información o recursos de un servidor sin alterar su estado. |
| **POST** | Create (Crear) | Envía datos nuevos al servidor para la creación de un nuevo recurso. |
| **PUT** | Update (Actualizar) | Reemplaza por completo un recurso existente o lo crea si no existe, enviando todos sus campos. |
| **PATCH** | Update (Actualizar / Modificar) | Modifica parcialmente un recurso, actualizando únicamente los campos que se envían en la petición. |
| **DELETE** | Delete (Borrar) | Elimina un recurso específico del servidor. |


## Códigos de estado

Las respuestas HTTP se agrupan en cinco grandes familias según el resultado de la solicitud:
* **1xx (Informational / Informativas):** Indican que la petición fue recibida y el proceso continúa (ejemplo: `100 Continue`).
* **2xx (Successful / Éxito):** Indican que la acción fue recibida, comprendida y aceptada exitosamente (ejemplo: `200 OK` o `201 Created`).
* **3xx (Redirection / Redirección):** Indican que se deben tomar acciones adicionales para completar la solicitud, generalmente redirigiendo a otra URL (ejemplo: `301 Moved Permanently`).
* **4xx (Client Error / Errores del cliente):** Indican que hubo un error en la solicitud enviada, por parte de quien consume la API (ejemplo: `404 Not Found` cuando el recurso no existe o `400 Bad Request` por datos mal formados).
* **5xx (Server Error / Errores del servidor):** Indican que el servidor falló al intentar procesar una solicitud que en apariencia era válida (ejemplo: `500 Internal Server Error`).

#### ¿Por qué se separan los errores 4xx de los 5xx? ¿Quién tiene la culpa?
Se separan principalmente para identificar **de quién es la responsabilidad o la "culpa" del fallo**:
* Con los errores **4xx**, la culpa es del **cliente** (la persona o aplicación que hace la petición). Ocurre porque se envió una URL incorrecta, faltan datos obligatorios, no hay autorización o se pide algo que no existe.
* Con los errores **5xx**, la culpa es del **servidor**. El cliente hizo todo bien, pero el servidor falló internamente (se cayó la base de datos, hubo un fallo en el código del backend o el servidor se quedó sin recursos).