<!--
Título del PR: [CLAVE-JIRA] <servicio o repo>: <qué entrega> (otras claves que cierra)
Ejemplo: [CORE-27] identity-service multi-tenant: release/multi-tenant → develop (CORE-21 CORE-24 CORE-25)
Sin autoría de herramientas ni enlaces de sesión en el título, el cuerpo ni los commits.
-->

## Historias de Jira que cierra

| Clave | Historia | Estado al mergear |
|---|---|---|
| CORE-nn | <título de la historia> | Done / sigue abierta porque ... |

## Alcance

- Spec o slice que implementa (repo de arquitectura, servicio y versión).
- Qué cambia para el negocio en una frase.
- Qué NO cambia (compatibilidad): consumidores, topics, contratos públicos que siguen igual.

## Commits

Reglas: un PR por servicio y release; cada commit pertenece a UNA sola historia (o subtarea) y la lleva al inicio del
asunto; una historia tiene pocos commits, por concern (migración, código, pruebas, infra), tres a cinco como máximo.
Formato: `[CORE-nn] tipo(ámbito): descripción técnica`.

- `hash` [CORE-nn] tipo(ámbito): asunto

## Base de datos y mensajería

- Migraciones EF: nombres y si son reversibles.
- SQL post-deploy por ambiente (seed, backfill, NOT NULL): archivos y ambientes.
- Topics y suscripciones de Service Bus nuevos o retirados: declarados en el manifest de devops (PR o commit).

## Configuración e infraestructura

- Claves de configuración nuevas o retiradas (`.env`, Helm `values.<ambiente>.yml`, Key Vault: nombres de secretos, nunca valores).
- Versiones de SDK Nucleus referenciadas y la inmediata anterior para retroceder.

## Pruebas

- `dotnet build`: resultado.
- `dotnet test`: pasan / fallan / omitidos.
- Prueba en el stack local (Docker) con la copia de dev: qué se validó y cómo (health, flujos, evidencia en logs o tablas).
- Regresión del flujo actual: qué se verificó que sigue igual.

## Despliegue y retroceso

- Orden de despliegue (dependencias con otros servicios o SDK).
- Cómo se retrocede: imagen o versión anterior, migración, config.

## Lista de verificación

- [ ] El título lleva la clave de Jira y cada commit lleva la de su historia o subtarea al inicio del asunto.
- [ ] CHANGELOG, README y `.codex/SYNC_LOG.md` del repo al día con la versión del spec.
- [ ] Sin secretos, sin valores de `.env`, sin datos personales en el PR ni en los tests.
- [ ] Sin autoría de herramientas ni enlaces de sesión en commits y PR.
- [ ] Flujo actual sin regresión: probado, no supuesto.
