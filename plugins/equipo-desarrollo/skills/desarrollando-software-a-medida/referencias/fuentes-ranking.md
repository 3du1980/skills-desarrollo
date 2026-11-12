# Origen de esta skill: las 20 skills analizadas

No existe un ranking único y oficial. Esta lista consolida las skills que más se repiten en los rankings públicos revisados en noviembre de 2026 (leaderboard de instalaciones de skills.sh, rankings de Founden.ai, Firecrawl, Composio, DesignRevision, Taskade y repositorios "awesome-claude-skills"), filtrando las orientadas al desarrollo de software web. El orden es indicativo.

| # | Skill (autor) | Qué se tomó | Dónde vive aquí |
|---|---|---|---|
| 1 | frontend-design (Anthropic) | Comprometerse con una dirección visual deliberada; evitar la estética genérica de IA | Agente 05 |
| 2 | superpowers (obra / Jesse Vincent) | Flujo obligatorio brainstorm → plan → ejecución; tareas de 2–5 min; TDD estricto (borrar código sin prueba); subagente nuevo por tarea con revisión en dos etapas; verificación antes de declarar terminado; "evidencia sobre afirmaciones" | SKILL.md F4–F7, agentes 06, 07, 11 |
| 3 | webapp-testing (Anthropic) | Probar la app corriendo con Playwright: reconocimiento → interacción → capturas → logs de consola | Agente 08 |
| 4 | react-best-practices (Vercel) | Reglas ordenadas por impacto: cascadas, bundle, servidor, fetch, re-renders | Agente 07 |
| 5 | web-design-guidelines (Vercel) | Auditoría de UI: accesibilidad, foco, formularios, animación, tipografía, modo oscuro, i18n | Agentes 05 y 07 |
| 6 | web-artifacts-builder (Anthropic) | Frontends multi-archivo con React + Tailwind + shadcn/ui y límites de componentes claros | Agente 07, pila por defecto |
| 7 | grill-me / grilling (Matt Pocock) | Entrevista implacable rama por rama del árbol de decisiones, una pregunta a la vez con recomendación | Agente 01 |
| 8 | grill-with-docs / domain-modeling (Matt Pocock) | Glosario del dominio y ADRs actualizados durante el descubrimiento; desafiar términos con casos límite | Agentes 01 y 02 |
| 9 | improve-codebase-architecture / codebase-design (Matt Pocock) | Módulos profundos, costuras limpias, presentar oportunidades y dejar elegir | Agente 02 |
| 10 | diagnosing-bugs (Matt Pocock) + systematic-debugging (superpowers) | Reproducir → minimizar → hipótesis → instrumentar → corregir causa raíz → prueba de regresión | Agentes 06 y 08 |
| 11 | tdd (Matt Pocock) | Rojo-verde-refactor por rebanadas verticales | Agentes 06 y 07 |
| 12 | code-review (Matt Pocock) | Revisión en dos ejes independientes (Especificación y Estándares) con subagentes paralelos | Agente 11 |
| 13 | pr (Matt Pocock) | Descripción de PR con evidencia antes/después y riesgo de fusión (puerta de una o dos vías, radio de impacto) | Agente 11, plantillas |
| 14 | to-spec / to-tickets / implement-spec (Matt Pocock) | Tickets de bala trazadora con dependencias declaradas; implementación por frontera de tareas listas | SKILL.md F4, agente 02 |
| 15 | claude-code-security-review (Anthropic) | Revisión de seguridad semántica de cada cambio antes de fusionar | Agente 04 |
| 16 | web-quality-skills (Addy Osmani) | Umbrales Core Web Vitals, presupuestos, Lighthouse, separar evidencia medida de hipótesis, campo vs. laboratorio | Agente 09, estándares |
| 17 | Supabase agent skills | Seguridad a nivel de fila y políticas en la base de datos | Agente 03 |
| 18 | composition-patterns (Vercel) + shadcn/ui skill | Componentes compuestos en lugar de props booleanas; componentes accesibles base | Agente 07 |
| 19 | tailwind-skill (firedev) | Enfoque por tokens, accesible y con modo oscuro desde el inicio | Agente 05 |
| 20 | skill-creator (Anthropic) | Desarrollo guiado por evaluaciones y mejora iterativa de la propia skill | Agente 12 (retrospectiva) y sección de evaluación |

También influyeron: chrome-devtools-mcp (diagnóstico con trazas reales), Stripe/Clerk/Cloudflare/Neon (integraciones seguras, ramas de BD), handoff y retro (Matt Pocock).

## Estándares de la industria incorporados
- OWASP Top 10:2025 y OWASP ASVS 5.0
- NIST SSDF (SP 800-218): preparar, proteger, producir, responder
- STRIDE para modelado de amenazas
- WCAG 2.2 AA
- Core Web Vitals (LCP, INP, CLS)
- DORA (informe 2025 sobre desarrollo asistido por IA): cinco métricas incluida la tasa de retrabajo; la IA amplifica las fortalezas y debilidades del sistema
- The Twelve-Factor App, C4, ADR, RFC 9457 (Problem Details), OpenTelemetry, SLSA/SBOM
- LOPDP Ecuador y GDPR
- Guía oficial de Anthropic para escribir skills (descripción en tercera persona, SKILL.md < 500 líneas, referencias a un nivel, checklists y bucles de retroalimentación)

## Fuentes
- https://www.skills.sh/
- https://founden.ai/articles/top-20-claude-code-skills-for-web-and-app-builds
- https://www.firecrawl.dev/blog/best-claude-code-skills
- https://composio.dev/content/top-claude-skills
- https://designrevision.com/blog/best-claude-code-skills
- https://github.com/obra/superpowers
- https://github.com/mattpocock/skills
- https://github.com/vercel-labs/agent-skills
- https://github.com/addyosmani/web-quality-skills
- https://top10.owasp.org/2025/0x00_2025-Introduction
- https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices
- https://services.google.com/fh/files/misc/2025_state_of_ai_assisted_software_development.pdf

## Evaluación de esta skill (mantenerla viva)
Escenarios mínimos para comprobar que funciona:
1. "Quiero un sistema de citas para una clínica" → debe iniciar F1 con entrevista, no escribir código.
2. "Corrige este bug del login" → triaje S, prueba que reproduce el bug primero, revisión de seguridad.
3. "Audita la seguridad de este proyecto" → informe por severidad con archivo:línea, basado en OWASP 2025.
Tras cada proyecto, la retrospectiva propone mejoras a esta skill.
