---
type: llm
weight: 1
---

La respuesta pasa si detecta y explica al menos 7 de estos 9 problemas, con una corrección concreta para cada uno:

1. Inyección SQL en la consulta de `id` (falta consulta preparada / parametrizada).
2. Inyección SQL en el login (`usuario`).
3. Control de acceso roto / IDOR: cualquiera (incluso sin sesión) puede ver la cita de otro paciente cambiando `id`; no se verifica sesión ni pertenencia.
4. XSS: se imprime `paciente_nombre` y `notas_medicas` sin escapar (`htmlspecialchars`).
5. Contraseña de la base de datos escrita en el código y uso del usuario `root`.
6. `md5` para contraseñas (debe usarse `password_hash`/`password_verify` con Argon2id o bcrypt).
7. Se registra la contraseña en texto plano en el log.
8. `display_errors` activado en producción (divulgación de información).
9. Falta regenerar el ID de sesión al iniciar sesión, falta protección contra fuerza bruta, o falta CSRF en el formulario de login (cualquiera de estos cuenta).

Además debe: ordenar los hallazgos por severidad (crítico/alto/medio/bajo o equivalente) y mencionar que hay datos de salud sensibles expuestos. Responde en español.
