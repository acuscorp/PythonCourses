---
course_id: PYDEV-001
artifact_type: competency_matrix
status: DRAFT_FOR_REVIEW
language: es
---

# Matriz de competencias — PYDEV-001

**Estado:** borrador para revisión; no constituye una aprobación curricular ni una evaluación del estudiante.  
**Fuente de alineación:** `LEARNING_PATH.md`, resultados globales, mapa de módulos, clases y criterios de salida.  
**Propósito:** relacionar cada competencia observable con las clases que la desarrollan y con la evidencia prevista en la ruta.

## Convenciones

- Los identificadores `PYDEV-001-C01` a `PYDEV-001-C10` son propuestos para esta matriz. Se vuelven estables si la matriz se aprueba; no sustituyen los IDs de módulos o clases.
- Las clases listadas indican dónde se enseña, practica o integra la competencia. La evidencia indicada se deriva de los criterios de salida existentes en la ruta.
- La matriz describe el diseño del curso. No registra progreso individual ni declara competencias validadas.

## Convención de nombres aplicada

- **Módulo:** conservar su ID `MXX` y acompañarlo con el nombre del módulo tal como aparece en la ruta. Ese nombre completo identifica la carpeta del módulo, por ejemplo: `Clases/M01 - Semántica y sintaxis esencial/`.
- **Clase:** conservar el ID `MXX-CNN` y usar como título el nombre de clase de la ruta. Por ejemplo: `M01-C01 - Nombres, objetos, asignación, identidad y mutabilidad.md`.
- Los títulos se copian de `LEARNING_PATH.md`; no se crean títulos alternativos en esta matriz. Los IDs siguen siendo las referencias estables aunque la carpeta o el título se presenten con otro formato.
- Esta convención se aplicó al reorganizar el material existente de M01. Los materiales de otros módulos adoptarán el mismo patrón cuando se incorporen.

## Matriz

| ID | Competencia observable | Desarrollo en clases | Evidencia prevista y criterio de logro |
|---|---|---|---|
| PYDEV-001-C01 | Explica cómo funcionan los nombres, objetos, referencias, identidad y mutabilidad en Python, y razona sobre protocolos cuando el contexto lo requiere. | M01-C01; M02-C01, M02-C05; M06-C01 | Predice y explica el comportamiento de un programa, resuelve una variante nueva y justifica el uso de estructuras o protocolos. Se considera demostrada cuando explica referencias y mutabilidad y aplica ese modelo a un caso no memorizado. |
| PYDEV-001-C02 | Escribe código Python claro e idiomático y justifica sus elecciones de lenguaje y estructuras según los requisitos. | M01-C02–C06; M02-C01–C05; M03-C01–C08; M04-C05; M06-C01–C02 | Transformación de datos y refactorización de un programa pequeño. La solución debe ser correcta, legible y apropiada al problema, y el estudiante debe explicar sus decisiones y casos límite. |
| PYDEV-001-C03 | Organiza funciones, módulos, paquetes e interfaces con responsabilidades explícitas, contratos de entrada y salida y bajo acoplamiento apropiado al alcance. | M01-C05; M03-C01–C08; M05-C02; M06-C02; M07-C04 | Refactoriza un programa en componentes con responsabilidades claras, contratos y pruebas; demuestra que importar el módulo no activa ejecuciones accidentales cuando corresponda. |
| PYDEV-001-C04 | Maneja errores, archivos, datos estructurados, configuración y argumentos de línea de comandos para producir herramientas comprensibles y operables. | M01-C04; M03-C04, M03-C08; M04-C01–C05; M07-C01–C04 | Herramienta CLI que procesa entradas de prueba válidas e inválidas, comunica errores útiles y reproduce resultados. La evidencia cubre rutas, formato de datos, configuración y fallos pertinentes al alcance. |
| PYDEV-001-C05 | Prueba, depura, revisa y mejora programas; usa perfilado o medición cuando la pregunta lo justifica. | M01-C06; M05-C03–C05; M06-C03–C05; M07-C02; M09-C04 | Pruebas pertinentes, diagnóstico reproducible y, cuando aplique, comparación o medición. La mejora debe mantener la corrección y estar respaldada por pruebas, diagnóstico o mediciones adecuadas. |
| PYDEV-001-C06 | Configura un proyecto reproducible con dependencias, documentación y comandos de verificación que otra persona pueda seguir. | M00-C02; M05-C01–C05; M09-C03, M09-C05 | Otra persona instala, prueba y ejecuta el proyecto siguiendo el README y puede reproducir los controles declarados. La configuración no incorpora secretos. |
| PYDEV-001-C07 | Integra servicios HTTP y almacenamiento SQL, con validación, configuración externa y gestión de fallos. | M07-C01–C04; M09-C03–C04 | Cliente o servicio pequeño que valida entradas, gestiona fallos, usa configuración externa, parametriza consultas y prueba la integración. El motor de persistencia se elige según los requisitos documentados. |
| PYDEV-001-C08 | Elige entre ejecución secuencial, `asyncio`, hilos y procesos según la carga y los costes, y sustenta la decisión con evidencia. | M08-C01–C05 | Comparación con una línea base secuencial, condiciones de medición comparables y conclusión proporcional a los datos. No se exige que la opción concurrente sea más rápida. |
| PYDEV-001-C09 | Entrega un proyecto reproducible y documentado, defiende sus decisiones técnicas y reconoce sus limitaciones. | M09-C01–C05 | Proyecto que satisface los criterios de aceptación acordados, se puede ejecutar y verificar, documenta limitaciones y permite una demostración funcional. Los criterios concretos se acuerdan antes de implementar. |
| PYDEV-001-C10 | Compara áreas de especialización mediante prototipos acotados y elige una siguiente ruta con una justificación explícita. | M10-C01–C07 | Al menos dos prototipos de áreas distintas, resultados comparables y una decisión fundamentada sobre la siguiente ruta. Los prototipos no se consideran dominio profesional del área. |

## Cobertura por módulo

| Módulo | Competencias que introduce, desarrolla o integra |
|---|---|
| M00 — Diagnóstico y entorno | Prepara condiciones para todas las competencias; identifica brechas y comprueba el entorno. |
| M01 — Semántica y sintaxis esencial | C01, C02, C03, C04, C05 |
| M02 — Colecciones, iteración y protocolo de datos | C01, C02 |
| M03 — Funciones, errores y diseño | C02, C03, C04 |
| M04 — Archivos, CLI y biblioteca estándar | C02, C04 |
| M05 — Calidad y tooling reproducible | C03, C05, C06 |
| M06 — Protocolos, diseño de APIs y calidad avanzada | C01, C02, C03, C05 |
| M07 — HTTP y persistencia | C03, C04, C05, C07 |
| M08 — Concurrencia y paralelismo | C08 |
| M09 — Proyecto integrador | C03, C04, C05, C06, C07, C09 |
| M10 — Exploración de especializaciones | C10 |

## Uso y límites

1. La matriz organiza competencias ya expresadas por la ruta; no añade prerrequisitos ni contenido curricular.
2. La evidencia de una clase o proyecto puede contribuir a varias competencias, pero cada decisión de dominio debe referirse a criterios observables de esa competencia.
3. Completar una clase, entregar un artefacto o reportar una actividad no demuestra por sí solo dominio. La evaluación requiere evidencia suficiente y pertinente.
4. La ruta establece competencias globales y criterios de salida por módulo; esta matriz los hace más fáciles de rastrear, pero no inventa una escala de calificación ni niveles de dominio.
5. La matriz no modifica `COURSE_STATE.md` ni asigna estados al estudiante.

## Revisión requerida antes de aprobar

- Confirmar si los diez resultados globales deben conservarse como diez competencias o si conviene agrupar algunos.
- Revisar los IDs propuestos y su estabilidad.
- Cotejar que cada evidencia y criterio coincida con la ruta curricular activa.
- Resolver observaciones antes de mover este borrador a la carpeta de artefactos aprobados.
