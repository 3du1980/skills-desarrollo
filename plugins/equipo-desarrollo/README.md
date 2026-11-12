# equipo-desarrollo

Plugin de Claude Code que pone a trabajar un equipo senior de 12 especialistas (25 años de experiencia cada uno) sobre todo el ciclo de vida del software a medida: descubrimiento, arquitectura, datos, seguridad y privacidad, diseño UX/UI, backend, frontend, QA, rendimiento, DevOps/SRE, revisión de código y documentación. Cada fase tiene una puerta de calidad que exige evidencia antes de avanzar.

## Qué incluye

- **Skill `desarrollando-software-a-medida`**: el Director de Ingeniería. Clasifica cada pedido por tamaño (ajuste, funcionalidad, producto, auditoría o bug difícil) y recorre solo las fases necesarias.
- **12 subagentes**: `analista-producto`, `arquitecto-software`, `arquitecto-datos`, `ingeniero-seguridad`, `disenador-ux-ui`, `desarrollador-backend`, `desarrollador-frontend`, `ingeniero-qa`, `ingeniero-rendimiento`, `ingeniero-devops-sre`, `revisor-codigo`, `documentador-tecnico`.
- **Referencias**: OWASP Top 10:2025, ASVS 5.0, STRIDE, LOPDP Ecuador y GDPR, WCAG 2.2, Core Web Vitals, DORA y plantillas (visión, historia, ADR, modelo de amenazas, plan, PR, release, handoff).

## Uso

Pide lo que necesitas en lenguaje natural ("quiero un sistema de citas para una clínica", "audita la seguridad de este proyecto", "corrige este bug del login") o invoca `/desarrollando-software-a-medida`. No requiere configuración ni claves.

## Instalación

```
/plugin marketplace add 3du1980/skills-desarrollo
/plugin install equipo-desarrollo@skills-desarrollo
```
