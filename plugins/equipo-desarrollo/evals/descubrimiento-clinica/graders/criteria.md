---
type: llm
weight: 1
---

La respuesta pasa si cumple TODO lo siguiente:

1. NO entrega código de la aplicación ni un esquema de base de datos completo todavía: primero busca entender los requisitos.
2. Hace preguntas de descubrimiento concretas (roles y permisos, flujos de la cita, recordatorios, datos del paciente, hosting/presupuesto, integraciones), y lo hace de forma ordenada: una pregunta o un bloque muy corto a la vez, acompañada de una recomendación o propuesta por defecto.
3. Reconoce que el sistema maneja datos personales y/o de salud de pacientes y que eso requiere tratamiento de privacidad o protección de datos.
4. Explica brevemente cómo seguirá el trabajo (fases o pasos siguientes) sin un muro de texto.
5. Responde en español.

Falla si escribe código de la app, si lanza más de unas 8 preguntas de golpe sin recomendación, o si ignora la privacidad de los datos de salud.
