---
type: llm
weight: 1
---

La respuesta pasa si cumple TODO lo siguiente:

1. Identifica el problema como control de acceso roto / IDOR (referencia insegura directa a objetos).
2. Da una corrección concreta del lado del servidor que verifica que la cita pertenece al usuario autenticado (Policy/Gate con `authorize`, o consulta filtrada por el paciente del usuario), considerando a roles que sí pueden ver citas ajenas (p. ej. dentista o recepcionista) o al menos preguntándolo.
3. Propone una prueba automatizada que reproduzca el fallo (un paciente recibe 403/404 al pedir la cita de otro) y que quede como prueba de regresión.
4. Es proporcional: NO arranca un proceso completo de descubrimiento del producto ni hace una entrevista larga antes de dar la corrección; va directo al arreglo.
5. Responde en español.

Suma calidad (no obligatorio): recomienda revisar otros endpoints con el mismo patrón, o evitar IDs secuenciales como única defensa.
