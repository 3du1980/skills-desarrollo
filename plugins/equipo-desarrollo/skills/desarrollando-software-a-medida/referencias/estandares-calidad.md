# Estándares de calidad

## Contenido
- Definición de terminado (DoD)
- Core Web Vitals y presupuestos
- Accesibilidad WCAG 2.2 AA
- Pirámide de pruebas
- Métricas DORA
- Calidad de código

## Definición de terminado (aplica a toda tarea)
- [ ] Criterios de aceptación cumplidos y demostrados con pruebas
- [ ] Pruebas, linter y tipos verdes en CI
- [ ] Revisión de código sin hallazgos Críticos/Altos
- [ ] Checklist de seguridad aplicable revisado
- [ ] Accesible con teclado y lector de pantalla (si hay UI)
- [ ] Sin errores de consola ni del servidor
- [ ] Documentación y registro de cambios actualizados
- [ ] Desplegable y reversible

## Core Web Vitals (percentil 75, datos de campo)
| Métrica | Bueno | Mejorable | Malo |
|---|---|---|---|
| LCP | ≤ 2.5 s | 2.5–4.0 s | > 4.0 s |
| INP | ≤ 200 ms | 200–500 ms | > 500 ms |
| CLS | ≤ 0.1 | 0.1–0.25 | > 0.25 |

Presupuestos iniciales: página < 1.5 MB · JS < 300 KB · CSS < 100 KB · imágenes sobre el pliegue < 500 KB · fuentes < 100 KB · terceros < 200 KB.
Lighthouse mínimos: Rendimiento ≥ 90 · Buenas prácticas ≥ 95 · SEO ≥ 95 · Accesibilidad sin fallos automáticos. Las puntuaciones detectan regresiones; no prueban por sí solas accesibilidad ni experiencia real.

## Accesibilidad WCAG 2.2 AA — verificación
Automática: axe/Lighthouse sin violaciones.
Manual:
- [ ] Recorrer todo con Tab/Shift+Tab/Enter/Espacio/Esc; foco visible y no tapado
- [ ] Lector de pantalla (NVDA/VoiceOver) en flujos críticos
- [ ] Zoom 200 % y ancho 320 px sin pérdida de contenido
- [ ] Contraste ≥ 4.5:1 (texto) y ≥ 3:1 (componentes)
- [ ] Errores de formulario identificados en texto y asociados al campo
- [ ] Objetivos táctiles ≥ 24×24 px
- [ ] Alternativa a arrastrar; sin pruebas cognitivas en autenticación

## Pirámide de pruebas
- Unitarias: lógica de dominio, rápidas, sin I/O.
- Integración: API + base de datos real en contenedor; contratos de API.
- E2E: solo flujos críticos de negocio, en navegadores reales (Playwright).
- Además según el caso: carga (k6), seguridad (ZAP), accesibilidad (axe), regresión visual.

## Métricas DORA (entrega de software)
- Rendimiento: frecuencia de despliegue, lead time de cambios, tiempo de recuperación de despliegues fallidos.
- Estabilidad: tasa de fallo de cambios, tasa de retrabajo.
La IA acelera el rendimiento pero puede aumentar la inestabilidad: por eso las puertas de calidad, las pruebas automáticas y los lotes pequeños son obligatorios.

## Calidad de código
- Tipado estricto donde el lenguaje lo permita.
- Formateador y linter automáticos en pre-commit y CI.
- Complejidad baja por función; módulos con interfaz pequeña.
- Commits convencionales y pequeños; versionado semántico.
- Cero advertencias ignoradas sin justificación escrita.
