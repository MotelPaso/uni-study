---
Tag: Course
Curso: ingenieria-de-software.md
Status: Done
Done: true
---

# Resumen de la carpeta `requisitos`

La carpeta contiene 5 notas que cubren el ciclo completo de **Ingeniería de Requisitos**, desde la definición teórica hasta las técnicas ágiles y experimentales. Todas provienen del mismo material base (danielsanmartin.cl).

| Nota       | Tema central                                            |
| ---------- | ------------------------------------------------------- |
| [[index]]  | Conceptos base de requisitos e Ingeniería de Requisitos |
| [[hu]]     | Historias de Usuario (técnica ágil)                     |
| [[cu]]     | Casos de Uso (técnica tradicional / Waterfall)          |
| [[mvp]]    | Producto Mínimo Viable (Lean Startup)                   |
| [[testab]] | Pruebas A/B (selección guiada por datos)                |

---

## 1. [[index]] — Requerimientos de software

### Clasificación de requisitos

- **Funcionales**: lo que el sistema *debe hacer* (transferencias, pagar boletos, etc.). Se especifican en lenguaje natural.
- **No funcionales**: las *restricciones* bajo las que debe operar. Se especifican con **métricas cuantitativas**, no con adjetivos.

| Atributo | Métricas típicas |
| --- | --- |
| Desempeño | transacciones/s, tiempo de respuesta, *throughput* |
| Espacio | disco, RAM, caché |
| Confiabilidad | % disponibilidad, MTBF |
| Robustez | MTTR, probabilidad de pérdida de datos |
| Usabilidad | tiempo de entrenamiento |
| Portabilidad | % de líneas de código portables |

> Regla práctica: en vez de "el sistema debe ser rápido", escribir algo como "el 99 % de las transacciones en cualquier ventana de 5 minutos debe responder en menos de 1 segundo".

- **Requisitos de usuario** (altos, escritos por usuarios, cerca del *problema*) vs. **requisitos de sistema** (técnicos, precisos, escritos por desarrolladores, cerca de la *solución*). Un requisito de usuario se expande en varios de sistema.

### Ingeniería de Requisitos

Es el conjunto de actividades de descubrimiento, análisis, especificación y mantenimiento, hechas de forma **sistemática y a lo largo de todo el ciclo de vida**.

- **Elicitación** = "hacer salir" los requisitos de los stakeholders. Técnicas: entrevistas, cuestionarios, lectura de documentos, talleres, prototipos, escenarios de uso y **etnografía** (el desarrollador se integra al entorno de trabajo y observa en silencio, sin interferir).

**Pipeline de los requisitos elicitados**: documentar → verificar/validar → priorizar.

- **Documentación**: ágil → historias de usuario; Waterfall → *Documento de Especificación de Requisitos* (estándar **IEEE 830**).
- **Validación**: correctos, precisos (sin ambigüedad), completos, consistentes, verificables.
- **Priorización**: no todo lo que pide el cliente entra en la primera versión.
- **Mantenimiento**: los requisitos cambian con el mundo → aparece la **trazabilidad** (código ↔ requisito en ambos sentidos).

**Obstáculos reales**: factores políticos, falta de tiempo de los stakeholders y la barrera cognitiva entre el vocabulario de negocio y el técnico.

**Mundo real (encuesta 2016, 228 empresas, 10 países)**: requisitos incompletos/no documentados (48 %), fallas de comunicación con clientes (41 %), requisitos en constante cambio (33 %).

**Idea puente**: *los requisitos son el puente entre un problema del mundo real y el sistema que lo resuelve*. Esta idea justifica las técnicas que se estudian a continuación según el nivel de incertidumbre.

---

## 2. [[hu]] — Historias de Usuario

Nacen como reacción al Waterfall: documentos extensos que se obsoletan, son ambiguos e incompletos. En ágil se sustituye la especificación textual por **conversación verbal**.

**Fórmula de Ron Jeffries (las tres "C")**:

$$
\text{Historia de Usuario} = \text{Tarjeta (Card)} + \text{Conversaciones} + \text{Confirmación}
$$

- **Tarjeta**: el cliente escribe en su lenguaje, en pocas oraciones, la funcionalidad esperada.
- **Conversaciones**: el representante del cliente participa a tiempo completo en el equipo y refina la historia durante el sprint.
- **Confirmación**: prueba de aceptación escrita por el cliente (no automatizada). Debe escribirse al inicio de la iteración (a veces en el reverso de la tarjeta).

La tarjeta es un *recordatorio/promesa*, no una especificación completa.

### Criterios INVEST

| Letra | Criterio | Idea clave |
| --- | --- | --- |
| I | Independiente | X e Y implementables en cualquier orden |
| N | Negociable | ambos ceden en las conversaciones |
| V | Valiosa | escrita y priorizada por el cliente; no hay "historias técnicas" |
| E | Estimable | dimensionable en días |
| S | Small | en el tope del backlog (< 1 semana); las grandes son **épicos** |
| T | Testeable | criterios de aceptación objetivos |

**Formato**: `Como un [rol de usuario], me gustaría [realizar algo con el sistema]`. Se parte de definir **roles de usuario** y suele realizarse un **taller de escritura de historias** para generar el backlog inicial.

**Notas importantes**
- **Requisitos no funcionales (RNF)**: pueden escribirse como historias, pero **no van al backlog del producto**. Sirven para reforzar los criterios de finalización (*done criteria*).
- **Spikes**: no se crean historias para aprender tecnología. Ese aprendizaje se gestiona como **spike** (tarea interna).
- **Gold plating**: evitar que los desarrolladores añadan funcionalidades no solicitadas. Las pruebas de aceptación escritas por el cliente ayudan a prevenirlo.

---

## 3. [[cu]] — Casos de Uso

Documentos textuales detallados, propios de **Waterfall** (fase de Especificación). Los redacta el desarrollador/Ingeniero de Requisitos y los usuarios los validan. El **diagrama UML** es solo un índice gráfico; el valor está en el texto.

### Estructura

- **Nombre**: verbo en infinitivo.
- **Actor principal**: entidad externa (persona, otro sistema).
- **Flujo normal** (*happy path*).
- **Extensiones**: (a) detallan pasos del flujo normal, (b) tratan errores/excepciones. Suelen tener más pasos que el flujo normal → **nunca usar "si" en el flujo normal**; va en extensiones.
- **Opcionales**: propósito, precondiciones, postcondiciones, casos relacionados.
- **Inclusión**: otro caso de uso (nombre subrayado), se ejecuta completo antes de continuar.

### Buenas prácticas

- Lenguaje simple (como para primaria). Actor como sujeto + verbo; "el sistema..." cuando actúa el sistema.
- **Máximo ~9 pasos** en el flujo normal (Cockburn). Si excede, dividir o agrupar.
- No son algoritmos: evitar `si`, `repetir hasta`, etc.
- Sin tecnología, diseño ni interfaz.
- Evitar CRUD trivial: preferir un caso de uso agregado (ej.: *Gestionar Profesor*) en lugar de cuatro CRUD separados.
- Estandarizar vocabulario mediante un **glosario** (Thomas & Hunt, *The Pragmatic Programmer*).

**Origen**: Ivar Jacobson (fines de los años 80), como parte del **Proceso Unificado (UP)**.

**Diferencia con historias (Mike Cohn)**: los casos de uso documentan un **acuerdo** entre cliente y equipo; las historias sirven para **planificar iteraciones** y recordar conversaciones.

---

## 4. [[mvp]] — Producto Mínimo Viable

Popularizado por Eric Ries (*Lean Startup*), inspirado en la **Manufactura Lean** (Toyota, años 50). El mayor desperdicio es invertir años en un sistema que nadie quiere usar.

**MVP** = sistema funcional con el conjunto mínimo de funcionalidades para **probar una hipótesis de negocio** (incluso para validar si el problema existe realmente).

### Ciclo construir → medir → aprender

1. **Construir**: implementar MVP.
2. **Medir**: ponerlo a disposición de clientes reales y recoger datos.
3. **Aprender**: analizar → generar **aprendizaje validado**.

Tres posibles decisiones: repetir ciclo (faltan pruebas), **market fit** (invertir más), o **fracaso** (perecer o hacer **pivote**).

### Métricas

- **Vanity metrics** (ej.: pageviews): superficiales, no accionables. Evitar.
- **Actionable metrics** (ej.: % de compras, valor de orden, ítems por orden, costo de adquisición): permiten tomar decisiones concretas.
- **Funnel metrics**: Adquisición → Activación → Retención → Ingresos → Recomendación.

### Ejemplos

- **Zappos (1999)**: MVP manual (fotos en web + procesamiento manual). Validó mercado; adquirido por Amazon por > USD 1.000M.
- **Dropbox**: video de 3 minutos mostrando funcionalidades. Lista de espera pasó de 5.000 a 75.000 usuarios.
- **CoreBR/CSIndexbr (UFMG, 2018)**: MVP real en Python (<200 líneas) sobre 15 conferencias, con Google Spreadsheets embebidos. Creció hasta cubrir ~900 profesores en múltiples áreas.

### FAQ

- **¿Solo startups?** No. Es para lidiar con incertidumbre en cualquier tipo de organización.
- **¿Cuándo no usarlo?** Mercado estable/conocido o sistemas de misión crítica (ej.: monitoreo en UCI).
- **¿MVP vs prototipado?** Prototipos no son necesariamente mínimos, ni productos, ni siempre se prueban con usuarios finales.
- **¿Baja calidad?** Debe tener la **calidad mínima** para validar la hipótesis. Más allá es desperdicio; pero no tan baja que genere **falsos negativos** (fallo por problemas de disponibilidad, no por el producto).

**Primer MVP**: Lean Startup no lo define. **Design Sprint** (Knapp, Zeratsky, Kowitz): 5 días, equipo multidisciplinario de 7 personas con decisor. Días 1-2-3: converge-diverge-converge; día 4: prototipo; día 5: prueba con 5 clientes reales.

---

## 5. [[testab]] — Pruebas A/B

Enfoque **guiado por datos** para elegir entre dos (o más) versiones cuál es mejor.

- **Versión de control** (requisito A, original) vs. **versión de tratamiento** (requisito B, nuevo).
- Requiere una **métrica de éxito**: la **tasa de conversión**.
- Requiere **asignación aleatoria** 50/50 a los usuarios.
- Requiere **tamaño de muestra calculado** (no cortar antes de completarlo). Ej.: 1 % conversión + 10 % mejora → ~200.000 usuarios por grupo (95 % confianza); 10 % conversión + 25 % mejora → ~1.800 por grupo.

### Marco estadístico

Prueba de hipótesis: **H0** = nada cambia (B no es mejor); **H1** = B es mejor. Se asume H0 verdadera e intenta refutarse. **α** = nivel de significancia (probabilidad de falso positivo, ej. 5 %); **1−α** = nivel de confianza.

### FAQ

- **¿Más de dos versiones?** Sí, **pruebas A/B/n** (división en n grupos).
- **¿Qué es A/A?** Ambos grupos usan la misma versión; deberían fracasar. Sirven para **validar la infraestructura experimental**. Si "gana" A/A, hay que buscar la *root cause*.
- **¿Origen?** **Experimentos aleatorizados controlados** (medicina): control = placebo, tratamiento = fármaco. Método aceptado para probar causalidad.

### Casos reales

- **Facebook**: libera cambios a usuarios reales y compara contra caso base; descubre necesidades sin elicitar todo por adelantado; detecta usos inesperados.
- **Netflix**: trata cada funcionalidad como experimento; si no funciona en ninguna posición, se elimina.
- **Microsoft Bing**: >200 experimentos concurrentes diarios (2013); aceleró innovación y generó millones de dólares en ingresos.

---

## Hilo conductor

Las cuatro técnicas responden a distintos niveles de incertidumbre definidos en [[index]]:

| Escenario | Técnica |
| --- | --- |
| Requisitos volátiles, sistema no crítico | [[hu]] — Historias de Usuario |
| Requisitos estables / certificación / vidas humanas | [[cu]] — Casos de Uso |
| Problema o mercado incierto | [[mvp]] — Producto Mínimo Viable |
| Después de lanzar, ¿qué requisito gana? | [[testab]] — Pruebas A/B |
