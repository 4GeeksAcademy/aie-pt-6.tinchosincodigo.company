# Technical Context — Brasaland Digital monorepo

## Estado técnico observado

El repositorio parte de una plantilla de monorepo documental para proyectos transversales de AI Engineering. El README raíz declara explícitamente que todavía no contiene aplicaciones ejecutables ni scripts globales. Existe `packages/shared/package.json` (`@repo/shared-types`), pero no hay orquestador de workspaces configurado en la raíz. `CONTEXT.md` y `CONTEXT.es.md` contienen el briefing de Brasaland; `BRIEFING.md` es también la fuente empresarial detallada. No se debe inferir un stack ya implantado más allá de lo que documenta la plantilla.

## Stack esperado y decisiones documentadas

- **Backend:** README raíz recomienda una API centralizada FastAPI para la empresa, con routers/módulos por dominio (por ejemplo, locales, menús, ventas y telemetría). Evitar microservicios al inicio; separar workers solo si realmente necesitan ejecutarse aparte.
- **Frontend:** aplicaciones de interfaz bajo `uis/`. El README de `uis/` identifica website público y backoffice interno como proyectos diferenciados.
- **Datos:** `data/` organiza datos fuente, pipelines ETL/ELT, resultados procesados y conjuntos/métricas de evaluación. El README raíz describe el flujo conceptual `raw → pipelines → process`, consumido por servicios, interfaces o agentes.
- **IA:** agentes concretos en `agents/`; capacidades reutilizables en `skills/`; servidores de herramientas y recursos para modelos en `mcps/`; orquestación y automatización en `workflows/`.
- **Reutilización:** bibliotecas versionables y tipos compartidos en `packages/` (incluido el paquete existente `@repo/shared-types`); recursos sueltos compartidos en `shared/`.
- **Infraestructura y operación:** `infra/` para Dockerfiles, Terraform, manifiestos de despliegue y configuración de infraestructura; `docker-compose.yml`, si se incorpora para desarrollo local, pertenece a la raíz. `scripts/` para scripts auxiliares y `internal/` para herramientas internas estructuradas.
- **Documentación transversal:** `docs/` para arquitectura, decisiones y convenciones globales.
- La plantilla propone documentar cada nueva aplicación, servicio, agente o pipeline con subcarpeta y README. No se define todavía framework de frontend, base de datos, proveedor cloud, modelo/SDK de IA, sistema de identidad, CI/CD ni protocolo de despliegue. Esas tecnologías siguen pendientes de decisión.

## Rutas oficiales de futuras piezas

Se respeta el mapa oficial de carpetas ya existente; no se crean árboles paralelos:

- `./uis/website`: web corporativa pública, ruta `/`; identidad, contenido y copy deben reflejar Brasaland: cadena de cocina a la brasa, Medellín/Colombia y Florida/EE. UU., consistencia, servicio cálido y cocina rápida. El detalle visual/tecnológico no está decidido.
- `./uis/backoffice`: aplicación interna de empresa, separada del sitio público y con layout propio; su vista de entrada será `/`. Alojará las experiencias internas que se prioricen (por ejemplo, operaciones y gestión), sin convertir la web pública en backoffice.
- `./services`: APIs y servicios backend de empresa; la recomendación actual es comenzar con una API central FastAPI, no dispersar el dominio en microservicios prematuros.
- `./data`: datos fuente, pipelines, datos procesados y evaluación; debe tratar con cuidado datos de ventas, clientes, personal e inventario. La política de PII todavía requiere definición.
- `./agents`: agentes de producto de Brasaland, como el posible agente de reposición, con documentación, herramientas, fuentes de memoria/conocimiento, pruebas y evaluación.
- `./skills` (en raíz): capacidades reutilizables del producto/equipo según el README de la plantilla.
- `./mcps`: servidores MCP de integración; `./workflows`: automatizaciones; `./packages`: librerías/tipos compartidos; `./shared`: esquemas y recursos sueltos; `./docs`: ADRs y documentación global; `./infra`, `./scripts` e `./internal`: infraestructura, scripts y herramientas internas respectivamente.
- `./agents` y `./skills` en raíz son carpetas de producto definidas por la plantilla. Son distintas de `./.agents/`, que se reserva para configuración del asistente de desarrollo solicitada para una fase posterior (por ejemplo reglas y skills de trabajo), no para agentes de negocio.
- El directorio `./memory-bank/` contiene únicamente estos documentos de contexto y progreso; no sustituye las ubicaciones oficiales del código.

## Restricciones técnicas y decisiones pendientes

La realidad actual tiene POS distintos por país, sin integración, ausencia de API interna, datos consolidados y telemetría, y procesos apoyados en hojas de cálculo y comunicación manual. La arquitectura futura debe poder integrar fuentes heterogéneas y atender dos mercados/monedas; no afirmar disponibilidad de interfaces de POS ni calidad de datos que todavía no se ha comprobado. La plantilla recomienda mantener baja la complejidad inicial mediante API centralizada.

No están establecidos aún framework UI, contratos API, esquema de datos, autenticación/autorización, permisos por rol, estrategia de sincronización, almacenamiento, observabilidad, infraestructura de ejecución, despliegue, seguridad, privacidad ni cumplimiento normativo. Deben ser decisiones explícitas antes del código que dependa de ellas. No se crea ni presupone una estructura de aplicaciones en paralelo a las rutas oficiales.
