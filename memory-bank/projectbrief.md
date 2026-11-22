# Project Brief — Brasaland Digital

## Negocio y contexto

Brasaland es una cadena rentable de restaurantes de cocina a la brasa fundada en Medellín en 2008. En quince años pasó de un local familiar a 14 restaurantes propios en Colombia y Florida (Estados Unidos), con aproximadamente 115 empleados y unos USD 6 millones de facturación anual. La sede está en Medellín y una oficina en Miami coordina las operaciones de Florida. La CEO es Mariana Restrepo; el equipo interno Brasaland Digital tiene el mandato de modernizar los sistemas y permitir que la empresa crezca sin perder su identidad.

La propuesta de marca descansa en tres compromisos: comida consistente entre ubicaciones, servicio cálido y consistente y una cocina rápida. Esos atributos deben preservarse en las soluciones digitales.

## Usuarios y clientes

- **Clientes de restaurantes:** base fiel en Colombia y Florida. Se busca habilitar pedidos digitales, fidelización y experiencias relevantes; actualmente hay poca información sobre sus perfiles y preferencias.
- **Operaciones:** Felipe Guerrero y supervisores que necesitan visibilidad de las 14 ubicaciones, ventas y abastecimiento.
- **Compras y proveedores:** Lucía Fernández y equipo, responsables de unos 20 proveedores de alimentos, bebidas, packaging y limpieza.
- **Marketing y experiencia digital:** Camila Ospina y equipo, responsables de web, redes, fidelización y campañas en dos mercados.
- **Personas y Cultura:** Ashley Turner y equipo, que gestionan unas 115 personas y procesos sujetos a legislaciones laborales distintas.
- **Formación y estándares:** Jake Morrison y los equipos de los locales, que requieren recetas y procedimientos consistentes y fáciles de consultar.
- **Dirección ejecutiva:** Mariana Restrepo, que necesita información consolidada y oportuna para decidir.
- **Tecnología:** Nicolás Park y su pequeño equipo, responsables de construir la plataforma digital.

## Problema que resuelve y objetivos

La operación de dos países se gestiona con herramientas fragmentadas y apropiadas para un solo restaurante: POS diferentes sin integración, hojas de cálculo, pedidos de ingredientes por WhatsApp o teléfono, informes de turno en papel/Excel, fidelización con tarjetas físicas y una web de 2019 junto a una app obsoleta. La sede carece de telemetría y visibilidad consolidadas; la dirección depende de llamadas, PDFs semanales y experiencia personal. Esto contribuye a exceso y falta de stock, dificultad para conocer resultados de cada local y desventaja frente a competidores con pedidos digitales y decisiones basadas en datos.

Brasaland Digital debe construir herramientas, sistemas y automatizaciones para operar como una empresa moderna preservando calidad, calidez, consistencia y rapidez. Los objetivos funcionales descritos en el briefing incluyen:

- Operaciones: dashboard de ventas por local en COP y USD, recomendaciones inteligentes de compra basadas en ventas históricas y existencias, y alertas por ausencia de ventas durante horario de apertura.
- Compras: gestión de proveedores, historial y alertas de precios, y compras consolidadas para negociar entre mercados.
- Marketing: fidelización y pedidos digitales, CRM con historial y preferencias, y personalización basada en comportamiento.
- Personas: portal de vacaciones y ausencias, onboarding automatizado y KPIs de rotación, absentismo y cobertura de vacantes por país.
- Formación: catálogo de recetas con búsqueda, itinerarios estructurados y distribución simultánea de actualizaciones a los 14 locales.
- Tecnología: API central para locales, menús, ventas, clientes y proveedores; telemetría en tiempo real desde locales; pipeline de datos para dashboards.
- Dirección: ventas totales de la cadena en USD y COP, asistente consultable en lenguaje natural e informe semanal generado y enviado los lunes a las 7:00.
- Visión de IA: previsión de demanda de ingredientes, personalización de menú, agentes de soporte multilingüe y telemetría de ventas. La elección de empresa propone específicamente un agente de reposición que combine inventario, ventas, proveedores, plazos, cantidades mínimas, costos, capacidad de almacenamiento y estacionalidad para recomendar qué/cuándo/cuánto reponer y alertar riesgos.

## Alcance y restricciones de negocio

- Ámbito geográfico: Colombia y Florida, con operación multipaís y dos monedas (COP y USD). Se requiere normalizar y presentar ventas en ambas monedas; no se ha especificado una política de tipo de cambio.
- La consistencia de comida y estándares entre locales, la calidez del servicio y la rapidez de cocina son requisitos de negocio, no negociables de producto.
- Son 14 locales propios y aproximadamente 115 empleados; proveedores, procesos de compras y mercados deben contemplarse como una cadena, no como unidades aisladas.
- Los mercados tienen contextos culturales y legislaciones laborales diferentes. Español e inglés son los idiomas relevantes; para formación bilingüe se recomienda empezar por un idioma base.
- La disponibilidad de datos reales integrados no debe darse por sentada: hoy no hay API interna, telemetría ni datos consolidados; cada país tiene POS distinto y los pedidos de stock carecen de integración con inventario.
- El briefing describe necesidades y dirección, no especifica políticas de privacidad, seguridad, cumplimiento, retención, tipo de cambio ni reglas de aprobación. Esas decisiones deben definirse antes de implantar funciones que las requieran; no se deben inventar como hechos ya acordados.
- La empresa es rentable y busca modernización y crecimiento sin sacrificar lo que distingue la marca; reducir la complejidad tempranamente favorece una base integrada y evolutiva.

## Enfoque inicial seleccionado

`company-choice.md` elige Brasaland por la oportunidad de integrar procesos dispersos y crear soluciones replicables. Prioriza Operaciones, Compras y Proveedores, Dirección Ejecutiva y Tecnología. La idea de agente prioritaria allí es la gestión unificada de reposición de materias primas. Estas prioridades complementan el alcance transversal del briefing y sirven como foco inicial, sin descartar las otras necesidades empresariales.
