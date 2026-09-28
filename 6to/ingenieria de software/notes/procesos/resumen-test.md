---
Tag: Course
Curso: ingenieria-de-software.md
Status: In Progress
Done: false
---

# Resumen para la prueba — Procesos de Desarrollo de Software

> [!quote] Tesis del capítulo
> "En el desarrollo de software, perfecto es un verbo, no un adjetivo. No existe un proceso perfecto. No existe un diseño perfecto. No existen historias perfectas. Sin embargo, puedes perfeccionar tu proceso, tu diseño y tus historias." — *Kent Beck*

Fuente principal: [[procesos/index|index]] · Completa el capítulo con [[procesos/xp|XP]], [[procesos/scrum|Scrum]], [[procesos/kanban|Kanban]] y [[procesos/otros_procesos|Otros Métodos Iterativos]]. Ver también [[ingsoft]].

---

## 1. Las tres ideas que sostienen todo el capítulo

1. **Siempre existe un proceso** — incluso si es "caótico". La pregunta nunca es *si*, sino *cuál*.
2. **El software es diferente** a los productos de la ingeniería tradicional: los requisitos cambian, el cliente muchas veces no sabe qué quiere, y por eso falla el modelo Waterfall importado de la ingeniería civil/electrónica.
3. **Ágil ≠ Waterfall en trozos pequeños** — el error conceptual más importante (ver §6).

## 2. ¿Por qué importan los procesos?

La objeción clásica: *"¿Qué proceso usó Linus Torvalds para Linux? ¿O cuál usó Donald Knuth para TeX?"*

| Situación | ¿Importa el proceso? | Por qué |
| --- | --- | --- |
| Proyecto individual (Linux en sus inicios, TeX) | **Menos importante** | Un único líder; el proceso es *personal* y su impacto es solo sobre él mismo |
| Sistemas modernos | **Esencial** | Demasiado complejos para una persona; los "héroes" son cada vez más raros — todo se desarrolla en **equipos** |

**Valor para la empresa:** coordinar, motivar, organizar y **evaluar** el trabajo de los desarrolladores → productividad y sistemas alineados con los objetivos de la organización. Sin proceso: trabajo descoordinado → productos sin valor para el negocio.

**Valor para el desarrollador:** tomar conciencia de las tareas y los resultados que se esperan de él. Sin proceso: se sienten perdidos, trabajan de manera errática y sin alineación con el resto del equipo.

## 3. Línea de tiempo — memorizar fechas y cifras

| Año | Hecho |
| --- | --- |
|década de 1970 | Procesos tipo **Waterfall**; estrictamente secuenciales (especificación de requisitos → implementación → pruebas → mantenimiento) |
| 1970–1990 | Fracasos sistemáticos: cronogramas y presupuestos incumplidos, proyectos enteros cancelados tras años sin entregar nada funcional |
| **1994** | **CHAOS Report** (Standish Group) |
| década de 1950 | **Kanban** nace en las fábricas de **Toyota** |
| **1995** | **Scrum** propuesto por **Sutherland y Schwaber** (artículo) |
| **1999** (2ª ed. **2004**) | **XP** publicado por **Kent Beck** |
| **2001** | Reunión de **Snowbird, Utah** → *Manifiesto Ágil* |
| 1986 | **Modelo en Espiral**, Barry Boehm |
| 2004 | Kanban usado por primera vez en software en **Microsoft** (David Anderson) |
| 2018 | Encuesta Stack Overflow, 57 mil respuestas |

> [!warning] CHAOS Report 1994 — cifras clave
> - **> 55%** de los proyectos excedieron sus plazos entre un **51% y un 200%**
> - **≥ 12%** excedieron los plazos en **más de un 200%**
> - Casi el **40%** superó el presupuesto entre un **51% y un 200%**

> [!tip] Encuesta Stack Overflow 2018 (57.000 desarrolladores profesionales)
> Scrum **63%** · Kanban **36%** · XP **16%** · Waterfall solo **15%**

## 4. Manifiesto Ágil — los cuatro pares, en orden

> Por medio de este trabajo, hemos llegado a valorar:

1. **Individuos e interacciones**, más que procesos y herramientas
2. **Software funcionando**, más que documentación exhaustiva
3. **Colaboración con el cliente**, más que negociación de contratos
4. **Respuesta al cambio**, más que seguir un plan

Dos cosas que enfatizar: (a) el manifiesto es una declaración de **valores**, no un método; (b) **los tres métodos (XP 1999, Scrum 1995, Kanban 1950s) son anteriores** a la reunión de Utah de 2001 — el manifiesto les dio nombre a ideas que ya circulaban.

## 5. Características de los procesos ágiles

**Mecánica central:** ciclos cortos e iterativos → el sistema se construye **incrementalmente**, empezando por lo más urgente para el cliente ("para ayer"). Primera versión → el cliente la valida → si la aprueba, nueva iteración con más funcionalidades priorizadas. Ciclos cortos, **alrededor de un mes o algo menos**. Cada incremento es aprobado expresamente. El desarrollo **termina cuando el cliente decide que todos los requisitos están implementados**.

- **Menor énfasis en la documentación** — solo se documenta lo esencial
- **Menor énfasis en planes detallados** — ni el cliente ni los ingenieros saben los requisitos al inicio; la comprensión surge a medida que se producen y validan incrementos. Lo importante es *avanzar con información imperfecta, parcial y cambiante*
- **No existe fase de diseño *big design up front*** — el diseño también es incremental
- **Equipos pequeños** — alrededor de una decena de desarrolladores; *"equipos que puedan alimentarse con dos pizzas"* (Jeff Bezos, Amazon)
- **Énfasis en nuevas prácticas** (para los inicios de los 2000): programación en parejas, pruebas automatizadas, integración continua

**Conclusión:** son procesos **ligeros**, con pocas prescripciones y pocos documentos.

## 6. Las dos trampas clásicas del examen

> [!danger] Trampa 1 — "cada iteración ágil es un mini-waterfall"
> **Falso.** Las iteraciones en métodos ágiles **no son una línea de ensamblaje de tareas** como en Waterfall. La figura engaña y el texto lo dice explícitamente.

> [!danger] Trampa 2 — "al final de cada iteración hay que poner el sistema en producción"
> **Falso.** El objetivo es entregar un sistema **funcional** (que realice tareas útiles). La decisión de ponerlo en producción involucra otras variables: riesgos para el negocio, disponibilidad de servidores, campañas de marketing, manuales, capacitación de usuarios.

> [!danger] Trampa 3 — cuidado con los adjetivos
> - Scrum: *producto potencialmente listo para entrar en producción* — el "potencialmente" carga peso real.
> - XP: una *release* **no** es una release de gestión de configuración. No toda release llega a producción.

## 7. Vocabulario que sí o sí se examina

| Término | Definición |
| --- | --- |
| **Proceso** | Conjunto de pasos, etapas y tareas para construir software. Toda organización usa uno: ágil, Waterfall, o quizá caótico |
| **Método** | Define y especifica un proceso de desarrollo determinado. Del griego, *camino para llegar a un objetivo*. XP, Scrum y Kanban son métodos ágiles |
| **Metodología** | En sentido estricto (Diccionario Houaiss), la rama de la lógica que se ocupa de los métodos de las ciencias. Puede usarse como sinónimo de *método*, pero **los autores la evitan y usan siempre _método_** |

> [!note] El "Aviso" del texto — probable pregunta de desarrollo
> Todo método debe entenderse como un **conjunto de recomendaciones**; le corresponde a cada organización analizar cada una y decidir si tiene sentido en su contexto, incluso **adaptarlas**. Por tanto, **probablemente no existan dos organizaciones que sigan exactamente el mismo proceso**, aunque ambas digan que desarrollan con Scrum.

---

# 8. El resto del capítulo — cheat sheet

## XP — [[procesos/xp]]

**Kent Beck, 1999** (2ª ed. 2004). Para sistemas comerciales con requisitos vagos o sujetos a cambios. **No es prescriptivo**: no define un paso a paso, se define mediante **valores → principios → prácticas**, y son los valores y principios los que **dan sentido** a las prácticas. Si la organización no está preparada para el modelo mental de XP, no se recomienda adoptar sus prácticas.

- **Valores:** comunicación, simplicidad, retroalimentación (+ coraje, respeto, calidad de vida). *Brooks: "Planea desechar partes de tu sistema, porque lo harás."*
- **Principios:** humanidad (*peopleware*, Tom DeMarco), economicidad, beneficios mutuos, mejoras continuas, las fallas ocurren, pasos pequeños, responsabilidad personal
- **Prácticas, en tres grupos:**
  - *Proceso de desarrollo:* representante de clientes, historias de usuario, iteraciones, releases, planificación de releases, planificación de iteraciones, planning poker, slack
  - *Programación:* diseño incremental, programación en parejas, TDD, build automatizado, integración continua
  - *Gestión de proyectos:* métricas, ambiente de trabajo, contratos con alcance abierto
- **Cifras:** iteraciones de **1 a 3 semanas**; releases de **2 a 3 meses**; velocidad = story points por iteración; escala de Fibonacci **1, 2, 3, 5, 8, 13**; las historias son de 2 o 3 oraciones, en tarjetas de papel, en el lenguaje del cliente
- **Mundo real:** **Chrysler C3** (*Chrysler Comprehensive Compensation*), un sistema de nómina. El proyecto comenzó a inicios de 1995 y, como no presentó resultados concretos, fue **reiniciado al año siguiente** bajo el liderazgo de Kent Beck, con **Martin Fowler** como consultor

## Scrum — [[procesos/scrum]]

**Sutherland y Schwaber, 1995.** El método ágil más conocido y utilizado; alrededor de él creció una industria completa (libros, cursos, consultoría, certificaciones).

> [!tip] La comparación que más se pregunta — XP vs Scrum
> **XP** está orientado **exclusivamente a proyectos de desarrollo de software** e incluye prácticas de programación. **Scrum** es un método para la **gestión de proyectos** (puede ser la escritura de un libro), con un enfoque más amplio, y **no propone ninguna práctica de programación**.

- **Roles:** Propietario del Producto (PO) · Scrum Master · 3 a 9 desarrolladores
- **Artefactos:** Backlog del Producto · Backlog del Sprint · Tablero Scrum · Gráfico de Burndown
- **Eventos y *time-box*:**

| Evento | Time-box |
| --- | --- |
| Planificación del Sprint | máximo de 8 horas |
| Sprint | menos de 1 mes |
| Reunión Diaria | 15 minutos |
| Revisión del Sprint | máximo de 4 horas |
| Retrospectiva | máximo de 3 horas |

- **Mecánicas clave:** equipos **cross-funcionales** y **autoorganizados**, todos al mismo nivel jerárquico. El **Scrum Master** es especialista en Scrum, facilitador y *eliminador de impedimentos* — **no** es gerente de proyecto tradicional, **no** es líder del equipo, y **no** requiere título universitario en Computación. El **PO** escribe y prioriza historias, es dueño del Backlog del Producto y maximiza el ROI; solo puede haber **uno**, nunca un comité.
- **Sprint:** iteración de hasta un mes; produce un *producto potencialmente listo para producción*. El **sprint goal es inalterable dentro del sprint**: Scrum se adapta al cambio, pero **entre sprints**.
- **Planificación en dos partes:** el PO propone → el equipo decide según su **velocidad**; luego los desarrolladores descomponen historias en tareas y estiman, con el PO presente para resolver dudas.
- **Criterios de *done*** acordados por todo el equipo (pruebas unitarias pasando, código revisado, integrado) para que nadie mueva tareas a "concluido" con baja calidad.
- **Burndown:** horas restantes por día; la curva debe ser **descendente** y llegar a **cero** al final del sprint.
- **FAQ:** *Scrum* no es sigla — es el *scrum* del rugby (la reunión donde se decide quién se queda con la pelota). *Squad* (popularizado por Spotify) = equipo ágil; el conjunto de squads es una *tribu*. **Sí existen gerentes**: contratan y asignan personas a los equipos, fijan objetivos, gestionan RR.HH. y evalúan si los resultados generan valor.

## Kanban — [[procesos/kanban]]

Del japonés, **"tarjeta visual"**. De las fábricas de **Toyota en la década de 1950** — TPS, luego *manufactura lean*; las tarjetas controlan el flujo de producción. En software se usó por primera vez en **Microsoft, 2004**, liderado por **David Anderson**: ritmo sostenible, eliminar desperdicios, entregar valor con frecuencia, mejora continua.

- **Más simple que Scrum:** sin eventos (ni sprints), sin roles rígidos, sin artefactos de Scrum — **una única excepción: el Tablero Kanban**, que además incluye el Backlog del Producto.
- **Tablero:** columna de backlog + columnas de pasos (Especificación, Implementación, Revisión de Código…), cada paso dividido en dos subcolumnas: **en ejecución** y **concluidas**. Las historias (**H**) se convierten en tareas (**T**). Lo terminado se **jala** al paso siguiente → sistema *pull*.
- **Límites WIP:** número máximo de elementos en cada paso, sumando ambas subcolumnas (salvo el último paso, donde solo cuenta la primera subcolumna). Buscan **evitar la sobrecarga** para que no caiga la calidad, y dan al equipo una forma legítima de **rechazar trabajo empujado desde arriba**. Si un paso está en su límite, el elemento del backlog **no puede** ser jalado.
- **Fórmula (Ley de Little, Teoría de Colas):** $WIP = TP \times LT$, donde WIP = tareas en un paso, TP = tasa de llegada (throughput), LT = permanencia en el paso, **incluyendo el tiempo en cola**.
- **Ejemplo de Brechner — saberlo hacer:** LT(especificación)=5d, LT(implementación)=12d, LT(revisión)=6d. Throughput del paso **más lento** (implementación) = 8 tareas/mes ÷ **21 días hábiles** = **0.38 tareas/día** → WIP(esp.) = 1.9 → **2**; WIP(impl.) = 4.57 → **5**; WIP(rev.) = 2.29 → **3**. Se redondea **hacia arriba**; Brechner sugiere añadir un **margen del 50%**.
- **FAQ:** no define roles fijos; **no prescribe criterios de priorización**; las ceremonias de Scrum no están ni obligadas ni prohibidas; se recomienda tablero **físico** (visualización), aunque puede tener respaldo en software.

## Otros métodos iterativos — [[procesos/otros_procesos]]

La transición fue gradual: Waterfall dominó las décadas de 1970 y 1980, y los métodos ágiles —que comenzaron a surgir en la década de 1990— solo ganaron popularidad a fines de los años 2000. Los métodos surgidos en ese período de transición **no son estrictamente secuenciales**: tienen iteraciones, pero duran **meses** en vez de semanas, y **conservan características de Waterfall**: énfasis en la documentación y en una fase inicial de levantamiento de requisitos y luego de diseño.

**Modelo en Espiral — Barry Boehm, 1986.** Cuatro etapas por vuelta de la espiral:

1. Definición de objetivos y restricciones (costos, cronogramas)
2. Evaluación de alternativas y **análisis de riesgos** (p. ej. puede concluirse que es más conveniente comprar un sistema ya hecho que desarrollarlo internamente)
3. Desarrollo y pruebas (posiblemente con Waterfall) → debe generar un **prototipo** que pueda mostrarse a los usuarios
4. Planificación de la siguiente iteración **o la decisión de detenerse**

Cada iteración: **6 a 24 meses**, mucho más que XP o Scrum. Característica definitoria: **fase explícita de análisis de riesgos**.

---

## 9. Autoevaluación

- [ ] ¿Cuáles son las dos cifras de plazos del CHAOS Report y qué pasó con los costos?
- [ ] ¿Por qué es débil la objeción "Linus Torvalds / Donald Knuth" y para qué tipo de proyecto sí aplica?
- [ ] Escribe los cuatro valores del Manifiesto Ágil en orden. ¿Cuál trata más sobre tolerar la incertidumbre?
- [ ] Verdadero o falso, justificando: (a) una iteración ágil es un mini-waterfall; (b) cada sprint termina en una release en producción.
- [ ] Distingue **proceso**, **método** y **metodología**. ¿Qué dice Houaiss y por qué evitan una de esas palabras?
- [ ] ¿Por qué dos organizaciones pueden decir ambas "usamos Scrum" y tener procesos distintos?
- [ ] XP: los tres grupos de prácticas, y duraciones típicas de iteración y release.
- [ ] Scrum: los cinco eventos con sus *time-box*. ¿Qué no puede cambiar dentro de un sprint?
- [ ] Scrum: tres cosas que el Scrum Master **no** es.
- [ ] Kanban: con LT=12 días y throughput de 8 tareas/mes en 21 días hábiles, ¿cuál es el límite WIP de ese paso? Mostrar el cálculo.
- [ ] Espiral: las cuatro etapas, autor, año y duración de una iteración.
