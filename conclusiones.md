# Conclusiones y Preguntas de Reflexión

## Idempotencia (Tarea 8)
* **¿Qué es la idempotencia?** Es una propiedad del diseño de software y de las APIs que indica que realizar una o varias solicitudes idénticas produce exactamente el mismo efecto secundario en el servidor, sin alterar el estado más allá de la primera llamada.
* **Clasificación de los métodos HTTP probados:**
  * **Idempotentes:** `GET`, `PUT`, `DELETE` (Ejecutar un `PUT` o `DELETE` varias veces sobre el mismo recurso no cambia el estado del servidor tras la primera ejecución exitosa).
  * **No idempotentes:** `POST` (Cada vez que se ejecuta crea un recurso nuevo con un ID diferente), `PATCH` (Dependiendo de cómo esté implementada la lógica del servidor, aplicar actualizaciones parciales múltiples veces podría acumular cambios).

  ## Cabeceras de la respuesta / Headers (Tarea 9)
Se analizaron tres cabeceras clave en las respuestas de la API:
1. **`Content-Type`**: Especifica el tipo de medio (*media type*) de los datos devueltos (por ejemplo, `application/json; charset=utf-8`). **Importancia**: Es vital al probar APIs porque le indica al cliente cómo debe deserializar e interpretar el cuerpo de la respuesta recibido.
2. **`Cache-Control`**: Define las directivas de almacenamiento en caché tanto para los navegadores como para los servidores intermediarios.
3. **`Date`**: Indica la fecha y hora exacta en la que el servidor procesó y emitió la respuesta HTTP.