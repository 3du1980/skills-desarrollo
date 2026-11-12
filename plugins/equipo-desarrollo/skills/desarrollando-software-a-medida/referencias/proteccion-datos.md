# Referencia de protección de datos personales

> Guía técnica, no asesoría legal. Para decisiones con implicaciones jurídicas, recomendar al cliente validar con un abogado especializado.

## Contenido
- Marco legal aplicable
- Privacidad por diseño: controles técnicos
- Inventario de datos (plantilla)
- Derechos de los titulares en el software
- Incidentes y brechas

## Marco legal aplicable
- **Ecuador — Ley Orgánica de Protección de Datos Personales (LOPDP)** y su reglamento: principios de licitud, finalidad, minimización, proporcionalidad, confidencialidad, conservación limitada y seguridad; derechos de acceso, rectificación, eliminación, oposición, portabilidad y a no ser objeto de decisiones automatizadas; obligación de notificar brechas a la autoridad y a los titulares cuando corresponda; datos sensibles (salud, biométricos, etc.) con protección reforzada; evaluación de impacto para tratamientos de alto riesgo; delegado de protección de datos cuando la ley lo exija.
- **Unión Europea — GDPR**: aplica si se ofrecen servicios a personas en la UE.
- **Otras**: leyes locales de cada país donde opere el cliente; normativas sectoriales (salud, financiero) y PCI DSS si hay pagos con tarjeta.
Verificar siempre la versión vigente de la norma y el reglamento antes de afirmar plazos o requisitos concretos.

## Privacidad por diseño — controles técnicos
1. **Minimización**: recoger solo los campos necesarios para la finalidad declarada.
2. **Consentimiento** granular, registrado (quién, cuándo, qué versión del texto) y revocable tan fácil como se otorgó.
3. **Retención**: plazo por tipo de dato; job automático de eliminación o anonimización al vencer.
4. **Seudonimización/anonimización** en analítica, reportes y entornos de prueba.
5. **Cifrado** en tránsito (TLS) y en reposo para datos sensibles.
6. **Control de acceso** por necesidad de saber; auditoría de quién consultó datos sensibles.
7. **Sin datos personales** en logs, URLs, mensajes de error ni herramientas de terceros no declaradas.
8. **Proveedores (encargados)**: inventario de terceros que procesan datos, contrato de encargo, ubicación de servidores (transferencias internacionales).
9. **Entornos de desarrollo** solo con datos ficticios.
10. **Cookies y analítica**: banner con rechazo tan fácil como aceptación; sin cookies no esenciales antes del consentimiento.

## Inventario de datos (plantilla)
| Dato | Categoría (común/sensible) | Finalidad | Base legal | Retención | Dónde se guarda | Quién accede | Terceros |
|---|---|---|---|---|---|---|---|
| Correo | Común | Autenticación y avisos | Ejecución de contrato | Vida de la cuenta + N meses | BD principal | Sistema, admin | Proveedor de correo |

## Derechos de los titulares en el software
- Exportar los datos del titular en formato estructurado (portabilidad).
- Rectificar desde el perfil o mediante solicitud registrada.
- Eliminar/anonimizar respetando obligaciones legales de conservación (p. ej. contables/tributarias).
- Registrar cada solicitud con fecha, respuesta y plazo.

## Incidentes y brechas
- Detección (alertas, logs) → contención → evaluación de impacto → notificación a autoridad y titulares según la ley → corrección → lecciones aprendidas.
- Runbook de brecha en `docs/operacion/runbooks/brecha-datos.md`.
