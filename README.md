# Taller-postman-Caceres

## Marco conceptual

### ¿Qué es una API REST?
Una API REST (*Representational State Transfer*) es un conjunto de reglas y protocolos arquitectónicos que permiten la comunicación entre diferentes sistemas y aplicaciones a través de la web utilizando el protocolo HTTP. Que sea "REST" significa que es un estilo de arquitectura sin estado (*stateless*), donde cada solicitud del cliente debe contener toda la información necesaria para que el servidor la procese, y las respuestas pueden ser cacheadas o interpretadas de manera estándar (generalmente usando formatos como JSON).

* **¿Qué es un recurso?:** Es cualquier objeto, entidad o dato que el sistema puede almacenar y exponer para que sea consultado o modificado (por ejemplo, un usuario, un producto, una publicación o una canción).
* **¿Qué es un endpoint?:** Es la URL específica o punto de acceso digital donde una API recibe las peticiones de los clientes para interactuar con un recurso determinado (por ejemplo, `https://api.ejemplo.com/posts`).
* **Ejemplo cotidiano:** Una aplicación que usamos a diario y que depende fuertemente de APIs es **Spotify**. Cuando buscas una canción en la app de tu teléfono (el cliente), la aplicación realiza una petición a los servidores de Spotify a través de un endpoint para solicitar los datos de la canción, el artista y la carátula, trayendo la información en tiempo real para que puedas reproducirla.

**Fuente consultada:** Red Hat - ¿Qué es una API REST? (https://www.redhat.com/es/topics/api/what-is-a-rest-api)