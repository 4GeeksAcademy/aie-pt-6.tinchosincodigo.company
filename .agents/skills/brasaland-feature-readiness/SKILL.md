---
name: brasaland-feature-readiness
description: Audita cambios de una rama Brasaland antes de commit o Pull Request y actualiza el memory bank.
---

# Brasaland Feature Readiness

## Objetivo único

Auditar los cambios pendientes de una rama de trabajo en el monorepo de Brasaland y actualizar el banco de memoria antes de permitir un `git commit` o Pull Request. Esta skill evalúa y reporta; no crea código de aplicación ni realiza el commit o abre el PR.

## Inputs requeridos

- `BRIEFING.md`
- `memory-bank/projectbrief.md`
- `memory-bank/techContext.md`
- `memory-bank/progress.md`
- Salida actual de `git status` (incluido `--short --branch`) y `git diff` (incluido `--check`)
- Autorización explícita del desarrollador, si un archivo protegido figura modificado

Leer los documentos de referencia y obtener estado/diff de la rama al comienzo de la auditoría. Revisar además el README y checks disponibles de las carpetas afectadas.

## Procedimiento

1. Comprueba que la rama y el diff corresponden a la tarea que se está auditando. Inspecciona `git status` y `git diff` para identificar cambios rastreados, nuevos y eliminados; usa `git diff --cached` también si hay cambios staged.
2. Contrasta los cambios con `BRIEFING.md`, `memory-bank/projectbrief.md` y `memory-bank/techContext.md`: identidad de marca, alcance multipaís, COP/USD, requisitos funcionales, disponibilidad real de datos y decisiones aún no tomadas.
3. Inspecciona rutas nuevas. Confirma que las aplicaciones solo se ubiquen en `uis/website`, `uis/backoffice` o `services/` según corresponda; agentes de producto y skills de producto van en `agents/` y `skills/`. `.agents/` es configuración del asistente, no código de producto. Otros artefactos deben estar en sus carpetas oficiales, sin árboles paralelos.
4. Comprueba los archivos protegidos definidos en `AGENTS.md`. Si alguno está modificado y no consta confirmación explícita, marca Fallo y bloquea la aprobación.
5. Ejecuta `git diff --check` y registra su código de salida. Ejecuta el formateo, lint, build y tests que estén disponibles para cada carpeta afectada; registra exactamente lo ejecutado y cualquier check inexistente. No declares éxito para checks no ejecutados.
6. Actualiza `memory-bank/progress.md` para reflejar la rama, cambios, verificaciones y próximos pasos. Si hubo cambios arquitectónicos, actualiza también `memory-bank/techContext.md`. Lee de nuevo el progreso actualizado para confirmar la escritura.
7. Vuelve a obtener `git status` y `git diff`; confirma que el propio cambio de memoria está incluido, que no aparecieron cambios inesperados y que no se añadieron carpetas de aplicación fuera del mapa oficial.
8. Emite el reporte estructurado de abajo. Solo considera la auditoría apta para commit/PR si todos los criterios verificables pasan. No hagas commit ni abras el PR.

## Criterios de aceptación verificables

1. `git status` no muestra carpetas de aplicación creadas fuera del mapa oficial (`uis/website`, `uis/backoffice`, `services`, `agents`, `skills`). Una ruta no oficial para otra responsabilidad también requiere justificación dentro del mapa del monorepo, no un árbol paralelo.
2. La ejecución final de `git diff --check` termina con código de salida `0`.
3. Ningún archivo protegido aparece modificado en `git status` sin autorización explícita documentada del desarrollador.
4. `memory-bank/progress.md` contiene una entrada actualizada que refleja el trabajo de la rama y el estado de las verificaciones.
5. Las verificaciones aplicables de formato, limpieza y checks/tests de las carpetas afectadas están ejecutadas o claramente marcadas como no disponibles; fallos no resueltos bloquean la aprobación.

## Output esperado

Devuelve un reporte conciso y estructurado, sin omitir estados:

```text
## Brasaland Feature Readiness
- Rama y alcance: OK / Fallo — ...
- Alineación con briefing y restricciones: OK / Fallo — ...
- Rutas oficiales / sin aplicaciones paralelas: OK / Fallo — ...
- Archivos protegidos y autorización: OK / Fallo — ...
- Formato y checks/tests disponibles: OK / Fallo — ...
- git diff --check (código de salida): OK / Fallo — ...
- memory-bank/progress.md actualizado y confirmado: OK / Fallo — ...
- Decisión: LISTO para commit/PR / BLOQUEADO — ...
```

La salida debe identificar checks no disponibles y explicar cada Fallo. Un reporte no sustituye la autorización del desarrollador para archivos protegidos.
