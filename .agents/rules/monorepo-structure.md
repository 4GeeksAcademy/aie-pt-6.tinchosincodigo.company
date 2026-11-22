# Estructura oficial del monorepo

**Alcance: siempre activa** — aplica a toda tarea, propuesta, edición y revisión en este repositorio.

## Reglas

- Mantén cada pieza de aplicación en su ubicación oficial: `uis/website/` para la web corporativa pública (ruta `/`), `uis/backoffice/` para la aplicación interna con layout separado (vista `/`), `services/` para APIs y servicios backend, `agents/` para agentes de producto de Brasaland y `skills/` para capacidades reutilizables de producto/equipo.
- No crees árboles paralelos ni dupliques aplicaciones fuera de esas rutas. No pongas una web o backoffice en la raíz, `services/`, `agents/` u otra ubicación no correspondiente.
- Conserva la distinción entre `./.agents/` y las carpetas de producto `./agents/` y `./skills/`: `.agents/` contiene configuración e instrucciones del asistente de desarrollo (reglas y skills de trabajo); `agents/` y `skills/` en raíz contienen artefactos de producto de Brasaland.
- Ubica los demás tipos de trabajo en sus carpetas oficiales: datos en `data/`, servidores MCP en `mcps/`, automatizaciones en `workflows/`, paquetes reutilizables en `packages/`, recursos compartidos en `shared/`, documentación transversal en `docs/`, infraestructura en `infra/`, scripts en `scripts/` y herramientas internas estructuradas en `internal/`.
- Antes de crear una ruta nueva, consulta `AGENTS.md` y el README correspondiente. Si el mapa no define el destino o dos responsabilidades parecen solaparse, solicita aclaración en lugar de inventar una ruta.
- Respeta las rutas y responsabilidades documentadas por los README de la plantilla. Esta regla no autoriza modificar archivos o carpetas protegidos.
