# Referencia de seguridad

## Contenido
- OWASP Top 10:2025 — checklist por categoría
- Niveles OWASP ASVS 5.0
- Modelo de amenazas STRIDE
- Cabeceras HTTP de seguridad
- Herramientas por stack

## OWASP Top 10:2025 — checklist

**A01 Broken Access Control** (incluye SSRF)
- [ ] Denegar por defecto; autorización comprobada en servidor en cada endpoint y cada objeto (anti-IDOR)
- [ ] Aislamiento entre tenants/sucursales probado automáticamente
- [ ] CORS restrictivo; tokens CSRF o `SameSite` en formularios con cookies
- [ ] Peticiones salientes con URL de usuario validadas contra lista blanca (SSRF)

**A02 Security Misconfiguration**
- [ ] Sin debug, listados de directorio, páginas por defecto ni cuentas por defecto en producción
- [ ] Cabeceras de seguridad (ver abajo); permisos mínimos en nube, BD y archivos
- [ ] Configuración igual entre staging y producción, automatizada

**A03 Software Supply Chain Failures**
- [ ] Lockfile versionado; dependencias de fuentes confiables; escaneo continuo (Dependabot/OSV/audit)
- [ ] SBOM generado; acciones de CI fijadas por hash; token de CI con permisos mínimos
- [ ] Revisar dependencias nuevas (mantenimiento, popularidad, typosquatting)

**A04 Cryptographic Failures**
- [ ] TLS 1.2+ en todo; HSTS
- [ ] Contraseñas con Argon2id (o bcrypt costo ≥ 12); nunca MD5/SHA1
- [ ] Datos sensibles cifrados en reposo (AES-256-GCM); claves fuera del código y rotables
- [ ] Aleatoriedad criptográfica para tokens

**A05 Injection**
- [ ] Consultas parametrizadas/ORM; nunca concatenar SQL
- [ ] Validación de entrada por lista blanca en servidor; codificación de salida contextual
- [ ] CSP estricta; sin `eval`; sanitización de HTML enriquecido (DOMPurify)
- [ ] Sin comandos de sistema con entrada del usuario

**A06 Insecure Design**
- [ ] Modelo de amenazas en F2; casos de abuso en historias críticas
- [ ] Límites de tasa y anti-automatización en login, registro, recuperación, pagos
- [ ] Límites de negocio (montos, cantidades) validados en servidor

**A07 Authentication Failures**
- [ ] MFA disponible (obligatorio para administradores)
- [ ] Bloqueo progresivo y detección de credenciales filtradas
- [ ] Sesiones: cookie `HttpOnly; Secure; SameSite=Lax/Strict`, regenerar ID al iniciar sesión, expiración e invalidación al cerrar
- [ ] Recuperación de contraseña con token de un uso y caducidad corta; mensajes que no revelan si el usuario existe

**A08 Software or Data Integrity Failures**
- [ ] Sin deserialización insegura; webhooks verificados por firma
- [ ] Integridad de artefactos y actualizaciones (firma, SRI para scripts de CDN)

**A09 Security Logging & Alerting Failures**
- [ ] Registrar login (éxito/fallo), cambios de permisos, accesos denegados, operaciones administrativas
- [ ] Logs sin contraseñas, tokens ni datos personales innecesarios; protegidos contra manipulación
- [ ] Alertas accionables sobre patrones anómalos

**A10 Mishandling of Exceptional Conditions**
- [ ] Fallar cerrado (si la verificación falla, se deniega)
- [ ] Manejo de errores centralizado; sin trazas al usuario
- [ ] Transacciones revertidas ante error; recursos liberados; timeouts en todo I/O

## OWASP ASVS 5.0 — elección de nivel
- **L1**: apps de bajo riesgo, sin datos sensibles.
- **L2** (por defecto): apps de negocio con datos personales o lógica crítica.
- **L3**: pagos, salud, finanzas, infraestructura crítica.
Usar los capítulos de ASVS como checklist de verificación del nivel elegido y registrar el nivel en un ADR.

## STRIDE — plantilla rápida por flujo
| Amenaza | Pregunta | Mitigaciones típicas |
|---|---|---|
| Suplantación | ¿Alguien puede hacerse pasar por otro? | Autenticación fuerte, MFA, firma de webhooks |
| Manipulación | ¿Se pueden alterar datos en tránsito o reposo? | TLS, validación en servidor, integridad |
| Repudio | ¿Alguien puede negar una acción? | Logs de auditoría con usuario y hora |
| Divulgación | ¿Se pueden filtrar datos? | Autorización por objeto, cifrado, minimización |
| Denegación | ¿Se puede tumbar el servicio? | Rate limiting, timeouts, colas, límites de tamaño |
| Elevación | ¿Se pueden obtener más permisos? | Denegar por defecto, verificación de rol en servidor |

## Cabeceras HTTP de seguridad
```
Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
Content-Security-Policy: default-src 'self'; script-src 'self' 'nonce-{random}'; object-src 'none'; base-uri 'self'; frame-ancestors 'none'
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=()
Cross-Origin-Opener-Policy: same-origin
```
Ajustar CSP a los orígenes reales del proyecto (pasarelas de pago, analítica, CDN).

## Herramientas por stack
- Secretos: gitleaks, trufflehog
- Dependencias: `npm audit`, `pnpm audit`, `composer audit`, `pip-audit`, OSV-Scanner, Dependabot
- SAST: Semgrep, CodeQL; revisión de seguridad asistida (`/security-review` en Claude Code)
- DAST: OWASP ZAP contra staging
- SBOM: Syft, CycloneDX
