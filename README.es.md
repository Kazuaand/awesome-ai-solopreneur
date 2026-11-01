[English](README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md)

# Awesome AI Solopreneur [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Una selección de recursos probados en la práctica para quienes llevan un negocio en solitario con un equipo de agentes de IA.

Inglés | [日本語](README.ja.md)

Lo importante es el negocio. Tu organización de IA —agentes con funciones, asignación de tareas y revisión— y tu estrategia de llegada al mercado son herramientas al servicio de ese negocio unipersonal, no aficiones independientes. Cada entrada explica, en una o dos líneas, por qué se ha ganado un lugar en el trabajo diario. Cada sección termina con notas **Desde la práctica**: lecciones de operar este sistema, no resúmenes de los enlaces.

Las entradas marcadas con *(Kazuaand)* son herramientas y documentos de código abierto del propio responsable de esta lista.

<a id="contents"></a>
## Índice

- [Principios](#principles)
- [Organización de IA](#ai-organization)
  - [Funciones y delegación](#roles-and-delegation)
  - [Verificación y revisión](#verification-and-review)
  - [Cuándo consultar a una persona](#when-to-ask-the-human)
- [Entorno de ejecución y operaciones](#harness-and-operations)
  - [Instrucciones y contexto](#instructions-and-context)
  - [Memoria y decisiones](#memory-and-decisions)
  - [Tareas y reanudación del trabajo](#tasks-and-resuming-work)
  - [Sesiones y ventana de contexto](#sessions-and-the-context-window)
- [Llegada al mercado](#go-to-market)
  - [Posicionamiento y ofertas](#positioning-and-offers)
  - [Contenido, búsqueda y búsqueda con IA](#content-search-and-ai-search)
  - [Lanzamientos](#launching)
- [Publicación segura](#safe-publishing)
- [Medición y costes](#measurement-and-cost)
- [Contribuciones](#contributing)
- [Licencia](#license)

<a id="principles"></a>
## Principios

- [Haz cosas que no escalen](https://paulgraham.com/ds.html) - Haz las primeras ejecuciones a mano. Si trabajas en solitario, ese recorrido manual te enseña qué pasos merece la pena delegar en agentes.
- [MAKE](https://readmake.com/) - Un manual para crear una startup independiente, desde la idea hasta los ingresos sin formar un equipo. Sigue siendo la explicación más clara de lo que una persona puede sacar adelante.
- [Cómo crear agentes eficaces](https://www.anthropic.com/research/building-effective-agents) - Empieza por el patrón más sencillo que funcione. Muchos problemas de «agentes» resultan ser problemas del flujo de trabajo.
- [Guía práctica para crear agentes](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) - Cuándo merece la pena usar un agente, cómo añadir controles y cómo traspasar trabajo entre agentes. Una lista de comprobación útil antes de empezar a construir.

> **Desde la práctica**
>
> - Asume pocos compromisos personales. Deja que los agentes ejecuten todas las tácticas cuyo coste marginal y carga mental sean casi nulos.
> - Dedica tu atención al rumbo: qué problema resolver, para quién y si el resultado refleja el criterio adecuado. Deja a las máquinas la comprobación de los requisitos acordados.

<a id="ai-organization"></a>
## Organización de IA

<a id="roles-and-delegation"></a>
### Funciones y delegación

- [Graph Compound Engineering](https://github.com/Kazuaand/graph-compound-engineering) *(Kazuaand)* - Un manual para delegar en agentes trabajos que duran varios días: redacta una especificación, un grafo de trabajo y un organigrama, asigna cada puesto según el peso de sus decisiones y haz que cada retrospectiva facilite el siguiente encargo.
- [Cómo construimos nuestro sistema de investigación multiagente](https://www.anthropic.com/research/multi-agent-research-system) - Explica con franqueza el coste en tokens de repartir trabajo en paralelo y cuánto condicionan el resultado las instrucciones del encargo.
- [Compound engineering](https://every.to/chain-of-thought/compound-engineering-how-every-codes-with-agents) - La idea de que cada unidad de trabajo debe facilitar la siguiente. El origen del ciclo de mejora acumulativa.
- [Compound Engineering plugin](https://github.com/EveryInc/compound-engineering-plugin) - Un ciclo funcional de planificación, ejecución, revisión y mejora acumulativa que puedes instalar y estudiar.
- [Awesome Graph Engineering](https://github.com/DEEP-JLU/Awesome-Graph-Engineering) - Una revisión y una lista de artículos que comparan la ingeniería de grafos, ciclos, entornos de ejecución, contexto y prompts. Útil para situar tu propio sistema.
- [Subagentes de Claude Code](https://code.claude.com/docs/en/sub-agents) - Cómo funcionan en la práctica las ventanas de contexto aisladas y las herramientas específicas de cada agente.

> **Desde la práctica**
>
> - Una pregunta decide si conviene delegar: ¿quieres los resultados intermedios en bruto —volcados de archivos, resultados de consultas, ensayo y error— en tu propio contexto? Si no, delega.
> - Antes de delegar, prueba a sacar el material de la ventana de contexto: guárdalo en un archivo y conserva solo su ruta y unos pocos datos clave.
> - Entrega el encargo mediante la ruta de un archivo, no con un resumen contado de nuevo. Incluye en cada encargo un presupuesto y un punto de parada.
> - Pide que cada devolución termine con una línea que enumere qué preguntas están resueltas y cuáles siguen abiertas.
> - Nunca dejes que quien hizo el trabajo lo evalúe. Revisa en un contexto nuevo.

<a id="verification-and-review"></a>
### Verificación y revisión

- [Tu producto de IA necesita evaluaciones](https://hamel.dev/blog/posts/evals/) - Examina fallos reales antes de diseñar métricas. Los consejos más útiles sobre evaluación para equipos pequeños.
- [promptfoo](https://github.com/promptfoo/promptfoo) - Pruebas reproducibles de prompts y agentes que se ejecutan en integración continua.
- [Hooks de Claude Code](https://code.claude.com/docs/en/hooks) - Comprobaciones deterministas que se ejecutan en cada llamada a una herramienta. Úsalas para imponer límites que una instrucción por sí sola no puede garantizar.

> **Desde la práctica**
>
> - Trata toda afirmación como una hipótesis: notas de traspaso, archivos de memoria, informes de subagentes e incluso las suposiciones que tú mismo das por sentadas. Antes de apoyarte en ella, intenta refutarla de la forma más barata posible.
> - Afirmar que algo «no está» exige al menos tres comprobaciones independientes. Una búsqueda sin resultados demuestra poco.
> - El sistema que se está probando no puede darse el visto bueno a sí mismo. Sus pruebas en verde o su aviso de éxito no descartan un fallo de sincronización o de entorno.
> - Después de un despliegue o un cambio de configuración, comprueba el estado esperado mediante un código de salida en lugar de leer el resultado a ojo.
> - Asigna un nivel a cada acción arriesgada: ejecución automática, ejecución con protección, intervención humana o prohibida. Si una acción no tiene una fila en la tabla, no se ejecuta.

<a id="when-to-ask-the-human"></a>
### Cuándo consultar a una persona

- [Medición de la autonomía de los agentes de IA en la práctica](https://www.anthropic.com/research/measuring-agent-autonomy) - Datos de millones de interacciones entre personas y agentes sobre cuánto tiempo trabajan hoy los agentes entre intervenciones humanas.

> **Desde la práctica**
>
> - Los subagentes consultan a su agente superior, no a ti. Ese agente resuelve lo que pueda resolverse con respuestas anteriores, reglas o investigación.
> - Solo llegan a la persona las cuestiones de dinero, mensajes al exterior, cambios en producción y rumbo, agrupadas en una sola ronda.
> - Cada pregunta incluye una recomendación, si es crítica y un plazo tras el cual, si no es crítica, se continúa con la recomendación.
> - El silencio, los tiempos de espera agotados y los fallos de entrega nunca equivalen a una aprobación.

<a id="harness-and-operations"></a>
## Entorno de ejecución y operaciones

<a id="instructions-and-context"></a>
### Instrucciones y contexto

- [AGENTS.md](https://agents.md/) - Un formato abierto de instrucciones que leen muchos agentes de programación. Mantén una fuente compartida y dale a cada herramienta un adaptador mínimo que apunte a ella.
- [Ingeniería de contexto eficaz para agentes de IA](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents) - El contexto es un presupuesto limitado. Carga solo lo que necesita el siguiente paso.
- [Agent Skills](https://agentskills.io/home) - Empaqueta un procedimiento para que se cargue solo cuando haga falta.
- [anthropics/skills](https://github.com/anthropics/skills) - Ejemplos de skills cuya estructura puedes tomar como modelo.
- [Memoria de Claude Code](https://code.claude.com/docs/en/memory) - Cómo se encuentran y cargan los archivos de instrucciones, y en qué orden.
- [Model Context Protocol](https://modelcontextprotocol.io/) - La forma estándar de conectar herramientas y datos a los agentes.
- [Arquitectura hexagonal](https://alistair.cockburn.us/hexagonal-architecture) - Puertos y adaptadores. Aplicados al trabajo con IA: mantén estables las etapas y convierte cada herramienta y modelo en un adaptador intercambiable.

> **Desde la práctica**
>
> - Cuando añadas una instrucción permanente, señala otra que puedas retirar. Las reglas se acumulan más rápido de lo que los modelos las necesitan.

<a id="memory-and-decisions"></a>
### Memoria y decisiones

- [Documentar decisiones de arquitectura](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) - El formato original de registro breve de decisiones. Dejar constancia del «porqué» evita que los agentes reabran cuestiones ya resueltas.
- [Plantillas de registros de decisiones de arquitectura](https://github.com/architecture-decision-record/architecture-decision-record) - Plantillas y ejemplos para empezar.

> **Desde la práctica**
>
> - Cuando una decisión sustituya a otra, marca la anterior como sustituida en lugar de borrarla.

<a id="tasks-and-resuming-work"></a>
### Tareas y reanudación del trabajo

- [beads](https://github.com/gastownhall/beads) - Un gestor de incidencias basado en git y diseñado para agentes. Su grafo de dependencias permite responder «¿qué puedo hacer ahora?» con una sola consulta.
- [Entornos de ejecución eficaces para agentes de larga duración](https://www.anthropic.com/research/effective-harnesses-for-long-running-agents) - Un archivo de progreso y el historial de git como memoria entre sesiones.

> **Desde la práctica**
>
> - Mantén una única fuente de verdad para el estado de las tareas: el gestor de incidencias. Cuenta lo ocurrido en un archivo de progreso y contrasta ambos con el historial de git antes de fiarte de ellos.
> - Guarda en disco cada unidad terminada sobre la marcha. Tras una interrupción, la ejecución debe retomar solo las unidades pendientes, nunca repetir las terminadas.
> - Registra el trabajo de seguimiento como una incidencia nueva en vez de dejar un TODO en el código o en el chat.

<a id="sessions-and-the-context-window"></a>
### Sesiones y ventana de contexto

- [Buenas prácticas de Claude Code](https://code.claude.com/docs/en/best-practices) - Hábitos prácticos de planificación, contexto y verificación para sesiones largas de programación.
- [Cómo aprovechar mejor tus sesiones de Claude Code](https://claude.com/resources/articles/maximizing-the-value-of-your-claude-code-sessions) - Consejos prácticos para sacar más partido a cada token, incluido cómo la caché de prompts influye en el coste de una sesión.

> **Desde la práctica**
>
> - No envíes nada a una sesión cuya caché haya caducado. Un solo «continúa» o mensaje de mantenimiento puede reescribir todo su contexto, a menudo cientos de miles de tokens.
> - Considera la caché vigente solo en función del tiempo desde la última respuesta completada con éxito y de si el proceso sigue vivo. Si no puedes saberlo, trátala como caducada.
> - Para una sesión con la caché caducada, deja la petición en un archivo que vaya a leer o abre una sesión nueva y pequeña con una nota de traspaso.
> - Delega las lecturas, exploraciones y consultas voluminosas en subagentes aislados y recibe solo una síntesis breve o una ruta.
> - Mantén la salida de las pruebas y las compilaciones fuera de la ventana principal. Devuelve solo los fallos.

<a id="go-to-market"></a>
## Llegada al mercado

<a id="positioning-and-offers"></a>
### Posicionamiento y ofertas

- [Libros de April Dunford](https://www.aprildunford.com/books) - Un método reproducible para definir el posicionamiento y convertirlo después en un discurso de ventas.

> **Desde la práctica**
>
> - Mide la producción a mayor escala gracias a la IA por la demanda captada, no por el volumen producido.
> - Antes de redactar algo para una persona, describe quién es ese lector basándote en evidencias. Entrega el mismo encargo breve a quien redacta y a quien revisa.

<a id="content-search-and-ai-search"></a>
### Contenido, búsqueda y búsqueda con IA

- [Crear contenido útil, fiable y pensado para las personas](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) - Las preguntas de autoevaluación de Google. Aplícalas a tus borradores elaborados con ayuda de IA.
- [Las funciones de IA y tu sitio web](https://developers.google.com/search/docs/appearance/ai-features) - Cómo las funciones de búsqueda con IA de Google utilizan tus páginas y enlazan a ellas.
- [llms.txt](https://llmstxt.org/) - Una propuesta de índice en texto plano que facilita a los modelos de lenguaje la lectura de tu sitio.
- [Schema.org](https://schema.org/) - Vocabulario de datos estructurados. La coherencia de los datos de las entidades cobra más importancia cuando las respuestas de IA te citan.
- [The Open Graph protocol](https://ogp.me/) - Controla cómo se ven tus enlaces al compartirlos.
- [Google Search Console](https://search.google.com/search-console/about) - Datos gratuitos sobre las búsquedas en las que apareces y los problemas de tu sitio.
- [PageSpeed Insights](https://pagespeed.web.dev/) - Comprobaciones rápidas de rendimiento con datos de uso real.

> **Desde la práctica**
>
> - Usa exactamente el mismo nombre, descripción y enlaces en todos los sitios donde figures. Las incoherencias en los datos de una entidad penalizan más en las respuestas de IA que en la búsqueda tradicional.
> - Algunas redes sociales devuelven HTTP 200 para cualquier identificador de publicación, exista o no. Para confirmar que una publicación existe, compara el texto que ve un rastreador —por ejemplo, la etiqueta `og:description`— con lo que publicaste.

<a id="launching"></a>
### Lanzamientos

- [Normas de Show HN](https://news.ycombinator.com/showhn.html) - Qué cumple los requisitos y cómo presentar algo que la gente pueda probar.

> **Desde la práctica**
>
> - Mantén un único archivo con los datos del producto: descripción en una línea, público, precios y enlaces. Genera desde él cada ficha de directorio en vez de volver a escribirla a mano.
> - Registra cada ficha en una tabla: dónde, cuándo, estado y enlace. Vuelve a comprobar la ficha publicada más adelante; los directorios cambian y a veces eliminan entradas.

<a id="safe-publishing"></a>
## Publicación segura

- [publish-gate](https://github.com/Kazuaand/publish-gate) *(Kazuaand)* - Un control de cuatro etapas antes de hacer público cualquier contenido: detectores independientes, una lista privada de términos prohibidos fuera del repositorio, dos revisores de IA con contextos nuevos que deben dar ambos el visto bueno y una autoprueba con secretos introducidos deliberadamente que debe superarse primero.
- [gitleaks](https://github.com/gitleaks/gitleaks) - Un detector rápido de secretos para repositorios git y directorios.
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - Encuentra secretos y puede comprobar si una credencial detectada sigue activa.
- [Presidio](https://github.com/data-privacy-stack/presidio) - Detecta datos personales en texto, como nombres, direcciones y números de teléfono.
- [leakgate](https://pypi.org/project/leakgate/) - Un control previo a la publicación para lo que se les escapa a los detectores genéricos: nombres de usuario locales, servidores internos y términos de proyectos propios aún no publicados, tanto en código como en transcripciones de agentes.
- [Acerca de la detección de secretos](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) - Lo que GitHub detecta por ti y lo que no.
- [Configurar tu dirección de correo para los commits](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address) - Usa la dirección noreply para que los commits no revelen tu correo personal.
- [Acerca de las claves de acceso](https://docs.github.com/en/authentication/authenticating-with-a-passkey/about-passkeys) - Inicio de sesión resistente al phishing para la cuenta desde la que publicas.

> **Desde la práctica**
>
> - Que un detector no encuentre nada no significa nada hasta que una autoprueba con secretos introducidos deliberadamente haya pasado en esa misma ejecución.
> - Los detectores diseñados para código fuente pasan por alto muchas credenciales escritas en prosa o HTML. Añade tus propios patrones para textos del tipo «etiqueta: valor» y vuelve a analizar el contenido sin las etiquetas HTML.
> - Publica un repositorio nuevo que contenga solo el árbol final ya comprobado. El historial de trabajo puede seguir conteniendo lo que eliminaste.
> - Mantén la lista de términos privados fuera del repositorio público y pásala al control cuando se ejecute.

<a id="measurement-and-cost"></a>
## Medición y costes

- [Caché de prompts de Anthropic](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) - Duración de la caché y precio de las escrituras frente a las lecturas. De ello depende la viabilidad de los agentes de larga duración.
- [Caché de prompts de OpenAI](https://developers.openai.com/api/docs/guides/prompt-caching) - El mismo mecanismo en otro proveedor. Conviene conocerlo si trabajas con más de uno.
- [Gestionar los costes en Claude Code](https://code.claude.com/docs/en/costs) - Las funciones integradas para consultar y limitar el gasto.
- [ccusage](https://github.com/ccusage/ccusage) - Informes de uso y costes elaborados a partir de los registros locales de los agentes.
- [LiteLLM](https://github.com/BerriAI/litellm) - Una pasarela común para muchos proveedores de modelos. Enruta por grupo de modelos y mantén los datos personales fuera de los niveles gratuitos.
- [Langfuse](https://github.com/langfuse/langfuse) - Trazabilidad y evaluación de código abierto para aplicaciones con modelos de lenguaje.
- [Plausible Analytics](https://github.com/plausible/analytics) - Analítica web ligera y respetuosa con la privacidad que puedes alojar por tu cuenta.
- [Umami](https://github.com/umami-software/umami) - Otra opción sencilla de analítica que puedes alojar por tu cuenta.
- [Monitorización de sistemas distribuidos](https://sre.google/sre-book/monitoring-distributed-systems/) - Las cuatro señales de oro y por qué cada alerta necesita a alguien que actúe ante ella.

> **Desde la práctica**
>
> - Informa de los costes en tres columnas: coste a tarifas estándar, créditos realmente consumidos y desembolso adicional. Una suscripción no convierte el uso en gratuito.
> - El uso desconocido sigue siendo «desconocido». Nunca lo registres como cero.
> - Revisa primero las automatizaciones programadas en segundo plano. En una auditoría, estas, y no el trabajo humano, representaban casi todo el consumo.
> - Repartir trabajo en paralelo consume cuota aunque todas las cachés sigan vigentes, porque cada turno relee todo su contexto. Comprueba la cuota restante antes de distribuir el trabajo.
> - Mantén un registro de cada comprobación programada y de quién lee sus resultados. Una comprobación cuyos resultados nadie lee está muerta sin que nadie lo advierta.
> - Evalúa por escalones: primero comprobaciones deterministas, después un clasificador pequeño y un modelo grande solo para lo que quede sin resolver.

<a id="contributing"></a>
## Contribuciones

Las sugerencias son bienvenidas. Lee primero las [normas de contribución](contributing.md).

<a id="license"></a>
## Licencia

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

En la medida en que lo permite la ley, quienes han contribuido a esta obra han renunciado a todos los derechos de autor y derechos afines sobre ella.
