# Instrucciones para agentes de desarrollo — Brasaland

## Lectura obligatoria al inicio de cada sesión

Antes de proponer cambios o editar código, lee íntegramente:

1. `BRIEFING.md`.
2. `memory-bank/projectbrief.md`.
3. `memory-bank/techContext.md`.
4. `memory-bank/progress.md`.

Consulta además los `README.md` de las carpetas afectadas antes de trabajar en ellas. Si hay discrepancias entre la documentación técnica, no inventes decisiones: señala la discrepancia y solicita aclaración cuando afecte la implementación.

## Arquitectura y ubicaciones oficiales

Respeta las responsabilidades documentadas en el monorepo. No crees árboles paralelos, duplicados de aplicaciones ni código de aplicación fuera de las ubicaciones canónicas:

- `uis/website/`: web corporativa pública de Brasaland. La ruta de entrada es `/`; la marca y el copy deben corresponder a la cadena de cocina a la brasa, sus mercados Colombia/Florida y sus compromisos de consistencia, servicio cálido y rapidez.
- `uis/backoffice/`: aplicación interna, separada del sitio público, con layout propio y vista de entrada en `/`.
- `services/`: APIs y servicios backend de la empresa. La plantilla recomienda comenzar con una API central FastAPI y evitar microservicios prematuros.
- `agents/`: agentes de producto de Brasaland, con documentación, herramientas y pruebas.
- `skills/`: capacidades reutilizables de producto/equipo según la plantilla.

`.agents/` es configuración del asistente de desarrollo (reglas y skills de trabajo); no es la ubicación de agentes ni skills de producto. Las carpetas de producto `agents/` y `skills/` permanecen en la raíz. Datos, MCPs, workflows, paquetes, infraestructura y documentación deben residir en sus carpetas oficiales ya existentes (`data/`, `mcps/`, `workflows/`, `packages/`, `infra/`, `docs/`, etc.), no en rutas alternativas. No dupliques una app en la raíz u otra carpeta.

## Flujo obligatorio antes de cada commit

Completa estos pasos en orden antes de cualquier commit:

1. **Alineación:** contrasta los cambios con `BRIEFING.md` y las restricciones técnicas y de negocio de `memory-bank/projectbrief.md` y `memory-bank/techContext.md`. No asumas datos, integraciones o políticas que no estén documentados.
2. **Validaciones:** ejecuta validaciones de formato aplicables, `git diff --check` y los checks/tests disponibles para cada carpeta afectada, en particular `uis/*` y `services/*`. Informa si no existen checks configurados; no afirmes que se ejecutaron si no fue así.
3. **Memoria del proyecto:** actualiza `memory-bank/progress.md` con el estado y próximos pasos. Actualiza también `memory-bank/techContext.md` si cambió una decisión o arquitectura.
4. **Revisión del diff y alcance:** revisa `git status` y `git diff`; confirma que no se modificaron archivos protegidos sin autorización explícita y que no se añadieron carpetas de aplicación fuera del mapa oficial. Si alguna verificación falla, no hagas commit y reporta el bloqueo.

## Archivos y carpetas protegidos

Está prohibido modificar, renombrar o eliminar sin confirmación explícita del desarrollador:

- `BRIEFING.md`
- `company-choice.md`
- `CONTEXT.md`
- `CONTEXT.es.md`
- `.devcontainer/`
- `infra/`
- `internal/`
- Los `README.md` raíz de plantilla: `README.md` y `README.es.md`

Si una tarea parece requerir cambios en estos elementos, detente y solicita confirmación explícita antes de actuar.
