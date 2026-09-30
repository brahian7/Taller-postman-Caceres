# Hallazgos del Taller de Postman

## Tabla de experimentación (Fase 2)

| # | Petición | Código esperado | Código obtenido | ¿Coincide? |
|---|---|---|---|---|
| 1 | `GET /posts/1` | 200 | 200 | Sí |
| 2 | `GET /posts` | 200 | 200 | Sí |
| 3 | `GET /posts/9999` | 404 | 404 | Sí |
| 4 | `POST /posts` | 201 | 201 | Sí |
| 5 | `PUT /posts/1` | 200 | 200 | Sí |
| 6 | `PATCH /posts/1` | 200 | 200 | Sí |
| 7 | `DELETE /posts/1` | 200 | 200 | Sí |

## Pregunta sobre el error 404 (Tarea 5)
* **¿Este caso de prueba pasó o falló?** Pasó exitosamente. El caso de prueba evaluaba el comportamiento del sistema ante un recurso inexistente; esperábamos un código `404` y el servidor devolvió un `404`. Un defecto o fallo en el software ocurre cuando el resultado obtenido difiere del resultado esperado, no simplemente cuando el código es diferente de 200.

## Análisis de la creación con POST (Tarea 6)
* **¿Qué observaste en los IDs?** Al ejecutar la petición POST cinco veces seguidas, se observa que el servidor siempre devuelve el mismo ID simulado (el número `101`).
* **¿Por qué crees que ocurre?** Ocurre porque JSONPlaceholder es una API pública de pruebas y simulación (un *mock*); no guarda los registros permanentemente en una base de datos real, por lo que siempre emite una respuesta estática simulando que el recurso fue creado con éxito.
* **¿Cómo comprobarías, en una API real, que el recurso se creó de verdad?** En una API real con persistencia en base de datos, se comprobaría realizando una petición `GET` utilizando el ID devuelto en la respuesta (por ejemplo, `GET /posts/101`) para verificar que el recurso ya existe y contiene los datos enviados, o consultando directamente la base de datos del sistema.

¿Qué diferencia encontraste entre ambas respuestas? PUT reemplaza o sobreescribe todo el recurso por completo, por lo que si omites algún campo (como el body o el userId), este puede perderse o quedar vacío en el servidor. En cambio, PATCH realiza una actualización parcial, modificando únicamente el campo que se envió en la petición (title) y conservando intactos los demás campos originales del recurso.

## Idempotencia (Tarea 8)
* **¿Qué es la idempotencia?** Es una propiedad del diseño de software y de las APIs que indica que realizar una o varias solicitudes idénticas produce exactamente el mismo efecto secundario en el servidor, sin alterar el estado más allá de la primera llamada.
* **Clasificación de los métodos HTTP probados:**
  * **Idempotentes:** `GET`, `PUT`, `DELETE` (Ejecutar un `PUT` o `DELETE` varias veces sobre el mismo recurso no cambia el estado del servidor tras la primera ejecución exitosa).


## Límites de la API (Tarea 10)
* **ID más alto que devuelve 200:** `100` (En JSONPlaceholder existen exactamente 100 publicaciones).
* **Primer ID que devuelve 404:** `101` (A partir de este valor, la API no encuentra el recurso y responde con error de cliente).
* **¿Cómo se llama ese tipo de caso de prueba?** Se denominan **Casos de prueba de valores límite** (*Boundary Value Analysis*), una técnica de caja negra donde se prueban los extremos o fronteras de los rangos de entrada válidos e inválidos.
* **¿Por qué se dice que los defectos se concentran ahí?** Porque estadísticamente es donde más fallan los desarrolladores al programar las validaciones lógicas (por ejemplo, confundir un operador menor que `<` con un menor o igual `<=`), generando errores de desbordamiento o fallas de lógica en los límites del sistema.