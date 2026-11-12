# skills-desarrollo

Marketplace de plugins para Claude Code con el plugin **equipo-desarrollo**: un equipo senior de 12 agentes (25 años de experiencia cada uno) que cubre todo el ciclo de vida del software a medida, con puertas de calidad entre fases.

## Qué incluye

- **Skill `desarrollando-software-a-medida`**: el Director de Ingeniería que enruta el trabajo por fases (F0 a F9) y exige evidencia en cada puerta de calidad.
- **12 subagentes**: analista de producto, arquitecto de software, arquitecto de datos, ingeniero de seguridad y privacidad, diseñador UX/UI, desarrollador backend, desarrollador frontend, ingeniero QA, ingeniero de rendimiento, DevOps/SRE, revisor de código y documentador técnico.
- **Referencias**: OWASP Top 10:2025, ASVS 5.0, LOPDP Ecuador/GDPR, WCAG 2.2, Core Web Vitals, DORA y plantillas (ADR, historias, modelo de amenazas, PR, release, handoff).

## Instalación

En Claude Code:

```
/plugin marketplace add 3du1980/skills-desarrollo
/plugin install equipo-desarrollo@skills-desarrollo
```

Reinicia la sesión. La skill se activa sola al pedir desarrollo de software, o con `/desarrollando-software-a-medida`.

## Actualizar

```
/plugin marketplace update skills-desarrollo
```

## Instalación manual (sin marketplace)

Copia `plugins/equipo-desarrollo/skills/desarrollando-software-a-medida` a `.claude/skills/` de tu proyecto (o a `~/.claude/skills/` para todos tus proyectos) y, opcionalmente, los archivos de `plugins/equipo-desarrollo/agents/` a `.claude/agents/`.

## Licencia

MIT
