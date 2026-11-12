# Plantillas

## Contenido
- Visión de producto
- Historia de usuario
- ADR
- Modelo de amenazas
- Plan de tareas
- Descripción de PR
- Checklist de release
- Handoff

## Visión de producto
```markdown
# Visión — [Producto]
## Problema
## Usuarios y roles
## Objetivos y métricas de éxito (con número y fecha)
## Alcance del MVP
## Fuera de alcance
## Restricciones (presupuesto, plazo, hosting, normativa)
## Riesgos principales
```

## Historia de usuario
```markdown
### HU-012 Registrar cita
Como recepcionista quiero registrar una cita para un paciente para organizar la agenda del día.
Prioridad: Must
Criterios de aceptación:
- Dado un horario libre, cuando registro la cita, entonces aparece en la agenda y el paciente recibe confirmación.
- Dado un horario ocupado, cuando intento registrar, entonces veo "Horario no disponible" y propuestas cercanas.
- Dado un usuario sin permiso de agenda, cuando accede, entonces recibe 403 y no ve datos.
Notas de datos: nombre, teléfono (dato personal, base legal: ejecución de contrato).
```

## ADR
```markdown
# ADR-0007: [Decisión en una frase]
Estado: Propuesto | Aceptado | Reemplazado por ADR-XXXX
Fecha: AAAA-MM-DD
## Contexto
## Decisión
## Alternativas consideradas (y por qué se descartaron)
## Consecuencias (positivas, negativas, riesgos)
## Tipo de puerta: una vía / dos vías
```

## Modelo de amenazas
```markdown
# Modelo de amenazas — [Sistema]
Diagrama de contenedores y fronteras de confianza: (Mermaid)
| ID | Flujo/Componente | STRIDE | Amenaza | Prob. | Impacto | Mitigación | Estado |
|----|------------------|--------|---------|-------|---------|------------|--------|
Nivel ASVS objetivo: L2
```

## Plan de tareas
```markdown
## Ticket T-03: Registrar cita (bala trazadora UI → API → BD)
Depende de: T-01, T-02
### Tarea 3.1 — Prueba de servicio "crear cita en horario ocupado"
Archivos: src/agenda/citas.service.ts, tests/agenda/citas.service.test.ts
Prueba primero: espera ErrorHorarioOcupado
Verificación: `npm test -- citas.service`
```

## Descripción de PR
```markdown
## Qué y por qué
## Evidencia (antes/después, salida de pruebas, capturas)
## Riesgo de fusión: dos vías | una vía — radio de impacto:
## Cómo probar
## Cómo revertir
## Checklist: pruebas ✓ seguridad ✓ accesibilidad ✓ docs ✓
```

## Checklist de release
```
- [ ] Pipeline verde (pruebas, seguridad, Lighthouse)
- [ ] Migraciones compatibles hacia atrás y respaldo previo verificado
- [ ] Variables de entorno y secretos configurados en producción
- [ ] Despliegue progresivo / feature flags preparados
- [ ] Rollback probado en staging
- [ ] Monitoreo y alertas activos
- [ ] Registro de cambios y notas de versión publicados
- [ ] Usuario/cliente informado
```

## Handoff
```markdown
# Handoff — [Proyecto] — AAAA-MM-DD
## Estado actual
## Decisiones tomadas (enlaces a ADRs)
## Pendientes y próximos pasos (priorizados)
## Riesgos y deuda técnica conocida
## Cómo arrancar (comandos)
## Dónde está cada cosa
```
