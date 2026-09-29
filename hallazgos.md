# Hallazgos del Taller de Postman

## Tabla de experimentación (Fase 2)

| # | Petición | Código esperado | Código obtenido | ¿Coincide? |
|---|---|---|---|---|
| 1 | `GET /posts/1` | 200 | 200 | Sí |
| 2 | `GET /posts` | 200 | 200 | Sí |
| 3 | `GET /posts/9999` | 404 | 404 | Sí |

## Pregunta de análisis sobre el error 404 (Tarea 5)
* **¿Este caso de prueba pasó o falló?** Pasó exitosamente. El caso de prueba evaluaba el comportamiento del sistema ante un recurso inexistente; esperábamos un código `404` y el servidor devolvió un `404`. Un defecto o fallo en el software ocurre cuando el resultado obtenido difiere del resultado esperado, no simplemente cuando el código es diferente de 200.