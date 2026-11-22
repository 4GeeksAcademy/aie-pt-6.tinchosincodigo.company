# Guardrails del dominio Brasaland

**Alcance: por patrón de archivo** — aplica a archivos bajo `uis/**`, `services/**`, `agents/**` y `skills/**`.

Antes de diseñar o implementar una interfaz, endpoint, integración, agente o capacidad reutilizable en esos patrones, consulta `BRIEFING.md` y `memory-bank/projectbrief.md`. Contrasta también las decisiones y restricciones técnicas de `memory-bank/techContext.md`.

## Guardrails obligatorios

- Representa fielmente a Brasaland: cadena rentable de cocina a la brasa fundada en Medellín, 14 locales propios en Colombia y Florida, aproximadamente 115 personas y alrededor de 20 proveedores.
- Preserva los compromisos de marca: comida consistente en cada ubicación, servicio cálido y consistente y cocina rápida. No diseñes flujos que sacrifiquen esos atributos sin una decisión explícita de negocio.
- Considera el contexto de dos países, mercados culturalmente distintos y monedas COP/USD. No inventes tipo de cambio, reglas de conversión ni políticas regulatorias; déjalas como decisiones pendientes si afectan al diseño.
- No asumas que existen datos consolidados, telemetría, API interna ni conectividad con los POS: el briefing indica que aún no existen y los POS difieren por país. Identifica dependencias, calidad de datos y limitaciones antes de proponer automatización.
- Para decisiones de compras o inventario, diferencia recomendaciones y alertas de acciones aprobadas. La idea del agente de reposición requiere datos de inventario, ventas, proveedores, plazos, mínimos, costos, capacidad y estacionalidad; no presentes datos no disponibles como hechos.
- Las necesidades de personas deben considerar legislaciones laborales diferentes. Políticas de privacidad, seguridad, retención, cumplimiento, acceso por rol y reglas de aprobación no están establecidas; no las inventes como políticas acordadas.
- Español e inglés son mercados/idiomas relevantes; el soporte bilingüe es altamente recomendado en formación, comenzando por un idioma base. No presupongas que toda interfaz debe estar traducida antes de que se defina el alcance.
- Distingue necesidades descritas en el briefing de decisiones de arquitectura aún pendientes. Si falta información esencial, documenta el supuesto y pide definición antes de fijarlo en una API o flujo de negocio.

Si una solicitud contradice estos guardrails o los documentos de referencia, detén la implementación de la parte afectada, expón la contradicción y solicita confirmación.
