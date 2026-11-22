---
name: brasaland-domain-validation
description: Audita propuestas y cambios de producto para verificar su conformidad funcional y de dominio con Brasaland.
---

# Brasaland Domain Validation

## Objetivo único

Auditar propuestas, pantallas, endpoints o flujos de producto en el monorepo de Brasaland para verificar que cumplen con la identidad de marca, el modelo de negocio y las restricciones definidas en `BRIEFING.md` y `memory-bank/projectbrief.md`. Esta skill evalúa conformidad de dominio; no implementa ni modifica código de aplicación.

## Inputs requeridos

- `BRIEFING.md` — fuente de verdad del negocio y sus necesidades.
- `memory-bank/projectbrief.md` — objetivos, alcance y restricciones del proyecto.
- `memory-bank/techContext.md` — decisiones técnicas observadas, rutas y pendientes.
- Archivos modificados o propuestos dentro de `uis/`, `services/`, `agents/` o `skills/`.
- Cuando existan, descripción de la propuesta, criterios funcionales y archivos nuevos identificados por `git status`/`git diff`.

Lee las fuentes empresariales antes de evaluar. Examina únicamente los archivos propuestos o afectados y los README de las carpetas pertinentes.

## Procedimiento de auditoría

1. Identifica el alcance funcional y las rutas/archivos afectados. Distingue interfaz pública, herramienta interna, API/servicio, agente y capacidad reutilizable.
2. Verifica que la terminología, propuesta de valor, contenido y casos de uso correspondan fielmente a Brasaland: cadena de restaurantes de cocina a la brasa, fundada en Medellín, con 14 locales propios en Colombia y Florida, alrededor de 115 empleados y unos 20 proveedores. No aceptes datos genéricos de plantilla ni cifras, sucursales, clientes, funcionalidades o hechos inventados presentados como reales.
3. Comprueba la identidad de marca: consistencia de comida entre locales, servicio cálido y consistente, cocina rápida y crecimiento sin perder el carácter de la marca.
4. Comprueba la separación de espacios y responsabilidades:
   - `uis/website`: sitio corporativo público; su ruta de entrada es `/`.
   - `uis/backoffice`: aplicación interna con layout propio, separada del sitio público; su vista de entrada es `/`.
   - `services/`: APIs y servicios backend.
   - `agents/` y `skills/`: artefactos de producto en la raíz. No confundirlos con `.agents/`, que configura al asistente de desarrollo.
   - Rechaza árboles paralelos o duplicados de aplicaciones fuera de las ubicaciones oficiales.
5. Valida los flujos de datos, roles y reglas de negocio contra todas las restricciones del briefing y `projectbrief.md`. Entre otras: operación Colombia/Florida y COP/USD; diferencias culturales y laborales; integración de POS actualmente inexistente; ausencia actual de API interna, telemetría y datos consolidados; necesidades funcionales de cada área; consistencia y rapidez operativas.
6. Comprueba que las propuestas no conviertan necesidades en capacidades actuales ni inventen políticas. No se ha definido política de tipo de cambio, privacidad, seguridad, retención, cumplimiento, autorización, reglas de aprobación ni calidad/interfaz de fuentes; si una propuesta depende de ellas, registra la decisión pendiente en vez de asumirla.
7. Registra cada hallazgo con archivo/ruta y motivo concreto. Si no se puede acceder a una fuente o verificar una afirmación, indícalo como pendiente; no lo marques como conforme sin evidencia.

## Criterios de aceptación verificables

1. **Cero placeholders:** ninguna referencia a empresas ficticias (por ejemplo, TrackFlow o Nexova), nombres de compañía de plantilla, texto genérico de placeholder ni datos ficticios presentados como datos reales en el código o copy de la entrega.
2. **Separación comprobada:** el sitio público corresponde a `uis/website` con `/`, el backoffice interno con layout propio corresponde a `uis/backoffice` con vista `/`, y APIs/servicios backend corresponden a `services/`. No hay duplicados ni árboles paralelos.
3. **Restricciones sin contradicción:** todas las restricciones aplicables del `BRIEFING.md` están cubiertas por la propuesta y no hay contradicciones conocidas sobre marca, mercados, moneda, usuarios, datos, roles o flujos.
4. **Evidencia identificable:** la evaluación se basa en los documentos requeridos y en los archivos propuestos/modificados; cada desviación señala archivo/ruta y motivo.

## Output esperado

Entrega un reporte estructurado de conformidad de dominio:

```text
## Brasaland Domain Validation
- Alcance revisado: ...
- Identidad, terminología y casos de uso: OK / Desviación detectada — [archivo y motivo]
- Placeholders y datos ficticios: OK / Desviación detectada — [archivo y motivo]
- Separación website / backoffice / services: OK / Desviación detectada — [archivo y motivo]
- Flujos, roles y restricciones de negocio: OK / Desviación detectada — [archivo y motivo]
- Decisiones o evidencias pendientes: Ninguna / [detalle]
- Resultado: Conforme / No conforme — [resumen]
```

Usa **OK** solo cuando haya evidencia suficiente. Para cada desviación, incluye la ruta afectada y explica la contradicción o el dato faltante. El resultado es **Conforme** únicamente si se cumplen todos los criterios de aceptación; de lo contrario, es **No conforme**.
