---
course_id: PYDEV-001
version: 0.5.9
artifact_id: LP-PYDEV-001-v0.5.9
artifact_type: learning_path
status: APPROVED_WITH_DOCUMENTED_SCOPE_LIMIT
language: es
supersedes: 0.5.8
format_standard: UT-LP-1.0
revision_scope: FORMAT_AND_STATUS_RECONCILIATION
content_change: no_curricular_content_change
change_proposal: PYDEV-001-CP-0059
source_version: 0.5.8
approval_scope_inherited_from: 0.5.8
---

> **Aprobación curricular heredada de v0.5.8 (2026-10-21):** esta revisión v0.5.9 armoniza únicamente formato y metadatos con `UT-LP-1.0`. No cambia el contenido curricular, los 58 IDs, los prerrequisitos, las actividades ni los criterios. Se conserva exactamente el alcance y la limitación de la aprobación de v0.5.8: no se completó una comparación exhaustiva línea por línea con v0.5.1 porque el archivo completo no estuvo disponible. Esta revisión no aprueba materiales de clase ni migra el estado individual.

# Ruta curricular v0.5.9 — Python para desarrolladores

## Índice general

1. [Propósito y perfil de entrada](#1-proposito-y-perfil-de-entrada)
2. [Resultados globales](#2-resultados-globales)
3. [Jerarquía curricular y reglas de organización](#3-jerarquia-curricular-y-reglas-de-organizacion)
4. [Mapa de módulos, prerrequisitos y evidencias](#4-mapa-de-modulos-prerrequisitos-y-evidencias)
   - [Índice tabular de submódulos y clases](#41-indice-tabular-de-submodulos-y-clases)
5. [Índice detallado de clases](#5-indice-detallado-de-clases)
   - [Criterios mínimos de calidad por clase](#51-criterios-minimos-de-calidad-por-clase)
   - [M00 — Diagnóstico y entorno](#m00)
   - [M01 — Semántica y sintaxis esencial](#m01)
   - [M02 — Colecciones, iteración y protocolo de datos](#m02)
   - [M03 — Funciones, errores y diseño](#m03)
   - [M04 — Archivos, CLI y biblioteca estándar](#m04)
   - [M05 — Calidad y tooling reproducible](#m05)
   - [M06 — Protocolos, diseño de APIs y calidad avanzada](#m06)
   - [M07 — HTTP y persistencia](#m07)
   - [M08 — Concurrencia y paralelismo](#m08)
   - [M09 — Proyecto integrador](#m09)
   - [M10 — Exploración de especializaciones](#m10)
6. [Prerrequisitos y reglas de avance](#6-prerrequisitos-y-reglas-de-avance)
7. [Proyectos incrementales](#7-proyectos-incrementales)
8. [Evaluación y evidencia de dominio](#8-evaluacion-y-evidencia-de-dominio)
9. [Metodología de tutoría](#9-metodologia-de-tutoria)
10. [Materiales de referencia](#10-materiales-de-referencia)
11. [Registro y seguimiento del progreso](#11-registro-y-seguimiento-del-progreso)
12. [Decisiones pendientes](#12-compatibilidad-migracion-y-decisiones-pendientes)
13. [Historial de versiones](#13-historial-de-versiones)

---

<a id="01-proposito-y-perfil-de-entrada"></a>
## 1. Propósito y perfil de entrada

Esta ruta enseña Python con profundidad suficiente para leer, escribir, probar, depurar y mantener software idiomático. La ruta curricular v0.5.8 fue aprobada el 2026-10-21 dentro del alcance documentado en el registro de aprobación: coherencia estructural, integridad de IDs/enlaces y decisiones curriculares identificadas. No se afirma una comparación exhaustiva línea por línea con v0.5.1, cuyo archivo completo no estuvo disponible durante la revisión. La aprobación no valida automáticamente materiales de clase ni migra el estado individual. La ruta aprovecha la experiencia previa declarada del estudiante en Java, Kotlin, Go y C++; no vuelve a enseñar desde cero fundamentos generales salvo que el diagnóstico detecte una brecha relevante.

La ruta es generalista. Primero cubre el lenguaje y el flujo de trabajo profesional; después integra sistemas externos y concurrencia; finalmente permite explorar áreas y escoger una especialización posterior. La prioridad práctica es construir software Python mantenible, con especial atención a herramientas para desarrolladores y automatización local. Los contenidos de backend, datos, IA/ML y código nativo se exploran como opciones, no como especializaciones completas dentro de esta ruta.

**Dedicación orientativa:** 10–20 horas por semana; planificación inicial de referencia: 15 horas. El avance depende de la evidencia de dominio, no de fechas fijas ni de completar una cantidad arbitraria de lecciones.

<a id="02-resultados-globales"></a>
## 2. Resultados globales

Al terminar y demostrar las competencias previstas, el estudiante podrá:

1. Explicar el modelo de nombres, objetos, referencias, mutabilidad y protocolos de Python.
2. Escribir código claro, idiomático y mantenible, justificando elecciones de lenguaje y estructuras.
3. Organizar funciones, módulos, paquetes e interfaces con responsabilidades explícitas.
4. Manejar errores, archivos, datos estructurados, configuración y argumentos de línea de comandos.
5. Probar, depurar, revisar, perfilar y mejorar programas con herramientas adecuadas.
6. Configurar un proyecto reproducible con dependencias, documentación y comandos de verificación.
7. Integrar servicios HTTP y almacenamiento SQL, contemplando fallos y validación.
8. Elegir con fundamento entre ejecución secuencial, `asyncio`, hilos y procesos.
9. Entregar un proyecto reproducible y documentado, explicar sus decisiones y reconocer sus limitaciones.
10. Comparar opciones de especialización y decidir qué ruta continuar.

<a id="03-jerarquia-curricular-y-reglas-de-organizacion"></a>
## 3. Jerarquía curricular y reglas de organización

La jerarquía curricular oficial de esta ruta será:

**Módulo → Submódulo (cuando aporte claridad) → Clase.**

- **Módulo (`M00`–`M10`):** área grande de aprendizaje con objetivo, prerrequisitos, evidencia integradora y criterio de salida.
- **Submódulo (`SMxx-nn`):** agrupación temática opcional dentro de un módulo. Se crea cuando hay varios grupos conceptuales distinguibles; no se añade por obligación.
- **Clase (`Mxx-Cnn`):** unidad de enseñanza y práctica con objetivos observables, conceptos delimitados, prerrequisitos, actividades y evidencia.
- **Secciones, ejercicios y actividades:** componentes internos de una clase; no son niveles curriculares adicionales.
- **Subclase:** no se utiliza como nivel formal de la ruta. Si una clase es extensa, se divide en secciones o actividades, o se crea otra clase con objetivo independiente.

### Reglas de consistencia

1. Cada clase tiene un ID único, título, objetivo observable, contenido delimitado y evidencia. En este índice, el objetivo observable describe el resultado esperado; el material de clase debe desarrollar explicación, ejemplos, actividad, criterios de revisión, errores frecuentes y remediación pertinente. Como regla, hereda los prerrequisitos del módulo y presupone las clases anteriores del mismo submódulo; cualquier excepción o dependencia cruzada debe declararse en el material detallado. El material debe indicar además un criterio observable de éxito y una remediación concreta para las brechas previsibles.
2. Una clase no debe impartir en profundidad contenido reservado a módulos posteriores. Puede mencionarlo o usar un ejemplo mínimo para explicar un concepto actual.
3. El índice describe la ruta planificada; que una clase aparezca aquí no significa que su material completo ya exista.
4. Los identificadores de módulo y clase son estables. Si cambia de forma sustancial el alcance, se registra en el historial y se comprueba su impacto en materiales dependientes.
5. Las lecciones detalladas pueden añadir secciones, ejemplos y actividades, pero no deben contradecir el alcance declarado aquí.
6. Los temas opcionales se marcan como tales y no se convierten en requisitos de aprobación sin actualizar la ruta.

<a id="04-mapa-de-modulos-prerrequisitos-y-evidencias"></a>
## 4. Mapa de módulos, prerrequisitos y evidencias

| Módulo | Área | Prerrequisitos principales | Evidencia de salida |
|---|---|---|---|
| M00 | Diagnóstico y entorno | Ninguno | Informe diagnóstico y entorno ejecutable |
| M01 | Semántica y sintaxis esencial | M00; adaptación según diagnóstico | Programa pequeño con pruebas iniciales y explicación de semántica |
| M02 | Colecciones, iteración y protocolo de datos | M01 o evidencia equivalente | Transformación de datos con casos límite y pruebas |
| M03 | Funciones, errores y diseño | M01; conceptos de M02 cuando se requieran colecciones | Refactor modular con interfaces y pruebas |
| M04 | Archivos, CLI y biblioteca estándar | M01–M03 según las funciones usadas | Herramienta CLI que procesa archivos reales de prueba |
| M05 | Calidad y tooling reproducible | M01–M04; Git y pruebas iniciales | Repositorio instalable, verificable y documentado |
| M06 | Modelo de datos, APIs y calidad avanzada | M02, M03 y M05 | Refactor revisado, pruebas, depuración y medición justificada |
| M07 | HTTP y persistencia | M03–M05; fundamentos de datos/archivos | Cliente o servicio pequeño con HTTP y almacenamiento SQL |
| M08 | Concurrencia y paralelismo | M03, M05 y fundamentos de HTTP/I/O de M07 | Experimento secuencial y concurrente medido y explicado |
| M09 | Proyecto integrador | M01–M08 según el alcance acordado | Repositorio reproducible que satisface criterios de aceptación |
| M10 | Exploración de especializaciones | La exploración orientativa puede adelantarse; los prototipos técnicos con herramientas requieren al menos M04 o evidencia equivalente | Dos o más prototipos breves y una decisión de siguiente ruta |


<a id="04a-indice-resumido-de-submodulos-y-clases"></a>
### 4.1 Índice tabular de submódulos y clases

Este es el índice de consulta rápida. La descripción de contenido, objetivos y evidencias aparece en la sección 5, agrupada por módulo.

| Módulo | Submódulo | ID de clase | Clase |
|---|---|---|---|
| M00 | SM00-01 | `M00-C01` | Intérprete, terminal y ejecución de scripts |
| M00 | SM00-01 | `M00-C02` | Git y espacio de trabajo del curso |
| M00 | SM00-02 | `M00-C03` | Diagnóstico de lectura y razonamiento |
| M01 | SM01-01 | `M01-C01` | Nombres, objetos, asignación, identidad y mutabilidad |
| M01 | SM01-01 | `M01-C02` | Tipos básicos, conversiones, operadores y truthiness |
| M01 | SM01-01 | `M01-C03` | Condicionales y bucles |
| M01 | SM01-02 | `M01-C04` | Cadenas, f-strings, slicing y excepciones |
| M01 | SM01-02 | `M01-C05` | Imports y punto de entrada |
| M01 | SM01-02 | `M01-C06` | Primeras pruebas con `unittest` |
| M02 | SM02-01 | `M02-C01` | `list`, `tuple`, `dict` y `set`: selección y semántica |
| M02 | SM02-01 | `M02-C02` | Slicing, desempaquetado y operaciones de secuencia |
| M02 | SM02-02 | `M02-C03` | Comprensiones, `enumerate`, `zip` y ordenamiento |
| M02 | SM02-02 | `M02-C04` | Iterables, iteradores y generadores |
| M02 | SM02-03 | `M02-C05` | Igualdad, hashabilidad, copias y complejidad práctica |
| M03 | SM03-01 | `M03-C01` | Parámetros y firmas de función |
| M03 | SM03-01 | `M03-C02` | Alcance, funciones como valores y closures |
| M03 | SM03-01 | `M03-C03` | Decoradores y composición funcional introductoria |
| M03 | SM03-02 | `M03-C04` | Excepciones y diseño de errores |
| M03 | SM03-02 | `M03-C05` | Anotaciones de tipo y contratos |
| M03 | SM03-03 | `M03-C06` | Módulos, paquetes e imports sin efectos secundarios |
| M03 | SM03-03 | `M03-C07` | Clases, `dataclasses`, composición y herencia |
| M03 | SM03-03 | `M03-C08` | Context managers y gestión de recursos |
| M04 | SM04-01 | `M04-C01` | Rutas, codificación y archivos con `pathlib` |
| M04 | SM04-01 | `M04-C02` | JSON, CSV y datos temporales |
| M04 | SM04-02 | `M04-C03` | Argumentos, configuración y códigos de salida |
| M04 | SM04-02 | `M04-C04` | Logging y manejo de fallos operativos |
| M04 | SM04-02 | `M04-C05` | Biblioteca estándar para transformar datos |
| M05 | SM05-01 | `M05-C01` | Entornos virtuales y dependencias |
| M05 | SM05-01 | `M05-C02` | `pyproject.toml`, paquetes y versiones |
| M05 | SM05-02 | `M05-C03` | Pruebas, formato, lint y tipado estático |
| M05 | SM05-02 | `M05-C04` | Git, documentación, secretos y automatización |
| M05 | SM05-02 | `M05-C05` | Reproducibilidad y mantenimiento de herramientas |
| M06 | SM06-01 | `M06-C01` | Métodos especiales y protocolos de Python |
| M06 | SM06-01 | `M06-C02` | Diseño de APIs, composición y documentación |
| M06 | SM06-02 | `M06-C03` | Pruebas unitarias, parametrizadas y de integración |
| M06 | SM06-02 | `M06-C04` | Debugger, tracebacks y diagnóstico sistemático |
| M06 | SM06-03 | `M06-C05` | Perfilado, benchmarking y memoria |
| M07 | SM07-01 | `M07-C01` | HTTP, serialización y cliente de API |
| M07 | SM07-01 | `M07-C02` | Validación, autenticación y resiliencia |
| M07 | SM07-02 | `M07-C03` | SQL, consultas parametrizadas y transacciones |
| M07 | SM07-02 | `M07-C04` | Separación de lógica e integración |
| M08 | SM08-01 | `M08-C01` | I/O-bound, CPU-bound, concurrencia y paralelismo |
| M08 | SM08-01 | `M08-C02` | Coroutines, `async`/`await` y event loop |
| M08 | SM08-01 | `M08-C03` | Concurrencia limitada, cancelación y errores |
| M08 | SM08-02 | `M08-C04` | Hilos y procesos |
| M08 | SM08-02 | `M08-C05` | Comparación experimental de modelos |
| M09 | SM09-01 | `M09-C01` | Requisitos, alcance y aceptación |
| M09 | SM09-01 | `M09-C02` | MVP, arquitectura mínima y plan de entrega |
| M09 | SM09-02 | `M09-C03` | Implementación incremental y control de cambios |
| M09 | SM09-02 | `M09-C04` | Pruebas, logging y gestión de errores |
| M09 | SM09-03 | `M09-C05` | Documentación, demostración y retrospectiva técnica |
| M10 | SM10-01 | `M10-C01` | Método de comparación de especializaciones |
| M10 | SM10-01 | `M10-C02` | Automatización y herramientas para desarrolladores |
| M10 | SM10-01 | `M10-C03` | Backend y servicios |
| M10 | SM10-01 | `M10-C04` | Análisis de datos |
| M10 | SM10-01 | `M10-C05` | Machine Learning e IA |
| M10 | SM10-01 | `M10-C06` | Integración con sistemas y código nativo |
| M10 | SM10-01 | `M10-C07` | Decisión de siguiente ruta |

**Secuencia principal propuesta:** M00 → M01 → M02 → M03 → M04 → M05 → M06 → M07 → M08 → M09 → M10.

### Hitos de avance

| Hito | Evidencia mínima para continuar | Si no se alcanza |
|---|---|---|
| H0 — Entorno | Ejecutar un script y registrar el diagnóstico | Resolver el bloqueo del entorno; adaptar el diagnóstico sin repetir fundamentos ya demostrados |
| H1 — Lenguaje esencial (M01) | Explicar referencias/mutabilidad, resolver una variante nueva y ejecutar pruebas básicas | Repasar únicamente las brechas observadas antes de depender de ellas en M02–M03 |
| H2 — Datos y diseño (M02–M03) | Transformar datos y refactorizar una solución en funciones/módulos con errores definidos | Practicar estructuras, contratos o modularidad según la evidencia fallida |
| H3 — Herramienta usable (M04) | CLI que procesa archivos de prueba, valida entradas y comunica errores | Corregir manejo de rutas, datos, configuración o fallos operativos |
| H4 — Proyecto reproducible (M05) | Otra persona puede instalar, probar y ejecutar siguiendo instrucciones | Corregir reproducibilidad antes de introducir tooling avanzado |
| H5 — Calidad e integración (M06–M07) | Diagnóstico y pruebas pertinentes; integración externa con configuración y fallos controlados | Reforzar solo la dependencia concreta que falle |
| H6 — Concurrencia (M08) | Comparación justa con línea base secuencial y conclusión respaldada por datos | Revisar diseño experimental; no exigir que concurrencia gane |
| H7 — Proyecto integrador (M09) | Criterios de aceptación acordados, ejecución reproducible y limitaciones documentadas | Reducir alcance o resolver bloqueos antes de ampliar funciones |
| H8 — Siguiente ruta (M10) | Comparar al menos dos prototipos distintos y justificar la elección | Completar la evidencia faltante; no se exige probar todas las áreas |

Estos hitos son puertas de evidencia, no exámenes de memoria ni fechas fijas. Se puede abreviar contenido cuando una tarea independiente o de transferencia demuestre el mismo resultado.

La secuencia es una guía de dependencia, no una exigencia de enseñar todos los temas de manera lineal. El diagnóstico puede permitir omitir o abreviar práctica ya dominada si hay evidencia suficiente. En M10, la exploración orientativa (comparar áreas, revisar ejemplos y discutir intereses) puede adelantarse si ayuda a definir el proyecto; los prototipos técnicos que requieran herramientas se realizan después de M04 o cuando exista evidencia equivalente de los prerrequisitos. La exploración temprana no sustituye la base generalista ni implica que se haya completado el módulo.

<a id="05-indice-detallado-de-clases"></a>
## 5. Índice detallado de clases

El listado siguiente es el índice curricular propuesto de las clases previstas. Cada entrada especifica objetivo observable, contenidos y evidencia esperada. Los criterios de evaluación de cada clase deben concretarse en su material didáctico; el índice no afirma que esos 58 materiales detallados ya existan ni que estén aprobados.

<a id="m00"></a>
### M00 — Diagnóstico y entorno

**Objetivo del módulo:** verificar que el entorno funciona y separar los fundamentos de programación ya dominados de las particularidades aún no conocidas de Python.

**SM00-01 — Entorno y flujo inicial**

- **M00-C01 — Intérprete, terminal y ejecución de scripts**
  - **Objetivo observable:** Verificar el intérprete y ejecutar un script desde la terminal, explicando el comando y el directorio de trabajo.
  - Contenido: versión de Python, `python`, `python -m pip`, ejecutar un archivo, directorio de trabajo, rutas básicas en WSL 2/Ubuntu y lectura de errores de ejecución.
  - Evidencia: ejecutar un script propio, explicar el comando y guardar un reporte breve del entorno.
- **M00-C02 — Git y espacio de trabajo del curso**
  - **Objetivo observable:** Preparar un espacio de trabajo versionado y reproducible sin confundir configuración del repositorio con configuración global.
  - Contenido: comprobar Git, configurar identidad del repositorio cuando corresponda, crear/inspeccionar un repositorio y registrar comandos útiles.
  - Evidencia: repositorio de trabajo accesible y registro de los pasos necesarios para reproducir el entorno.

**SM00-02 — Diagnóstico de conocimientos**

- **M00-C03 — Diagnóstico de lectura y razonamiento**
  - **Objetivo observable:** Identificar fortalezas y brechas de Python a partir de predicciones y explicaciones razonadas, sin calificar el diagnóstico como dominio.
  - Contenido: predicción de código, referencias/mutabilidad, colecciones, funciones, excepciones, imports y pruebas; distinguir conocimiento general de sintaxis específica de Python.
  - Evidencia: respuestas razonadas con clasificación de brechas. Es diagnóstico, no examen de dominio.

**Criterio de salida:** el entorno puede ejecutar programas y las fortalezas/brechas quedan registradas para adaptar M01. No se exige dominar sintaxis Python antes de empezar.

<a id="m01"></a>
### M01 — Semántica y sintaxis esencial

**Objetivo del módulo:** construir un modelo mental correcto del lenguaje y leer, predecir, escribir y probar programas pequeños.

**SM01-01 — Modelo de objetos y flujo de control**

- **M01-C01 — Nombres, objetos, asignación, identidad y mutabilidad**
  - **Objetivo observable:** Predecir cómo nombres y referencias afectan a objetos, distinguiendo reasignación, mutación, igualdad e identidad.
  - Contenido: vínculo entre nombres y objetos, reasignación frente a mutación, referencias, aliasing, `==` frente a `is`, `None`.
  - Evidencia: predicciones justificadas de fragmentos nuevos y explicación de aliasing.
- **M01-C02 — Tipos básicos, conversiones, operadores y truthiness**
  - **Objetivo observable:** Usar tipos básicos, conversiones y condiciones de forma explícita, justificando truthiness y cortocircuito.
  - Contenido: `None`, `bool`, `int`, `float`, `str`, tipado dinámico, conversiones explícitas, comparación, precedencia, verdad/falsedad y cortocircuito.
  - Evidencia: predicciones y programa corto que maneja conversiones y condiciones.
- **M01-C03 — Condicionales y bucles**
  - **Objetivo observable:** Implementar flujo condicional e iterativo y explicar el recorrido de ejecución en casos representativos.
  - Contenido: `if`/`elif`/`else`, `for`, `while`, `range`, `break`, `continue`; `match` queda como extensión opcional.
  - Evidencia: trazado de ejecución y solución independiente con casos límite.

**SM01-02 — Texto, módulos y pruebas iniciales**

- **M01-C04 — Cadenas, f-strings, slicing y excepciones**
  - **Objetivo observable:** Procesar texto con operaciones de cadenas y manejar entradas inválidas mediante excepciones específicas.
  - Contenido: operaciones de cadenas, índices y slicing inicial, inmutabilidad, f-strings, `try`/`except` específico y flujo `else`/`finally` cuando corresponda.
  - Evidencia: transformación de texto en memoria y manejo explícito de entrada inválida.
- **M01-C05 — Imports y punto de entrada**
  - **Objetivo observable:** Separar código importable de la ejecución de un programa y evitar efectos secundarios involuntarios al importar.
  - Contenido: `import`, `from ... import ...`, nombres disponibles, ejecución de nivel superior al importar y `if __name__ == "__main__":`.
  - Evidencia: módulo importable sin ejecutar accidentalmente la demostración.
- **M01-C06 — Primeras pruebas con `unittest`**
  - **Objetivo observable:** Escribir y ejecutar pruebas de comportamiento con unittest, interpretar un fallo y demostrar que una prueba detecta un defecto.
  - Contenido: prueba de comportamiento, `TestCase`, aserciones básicas, ejecutar `python -m unittest -v`, observar un fallo, corregirlo y añadir un caso límite.
  - Evidencia: al menos tres pruebas pertinentes y demostración de que una detecta un defecto real.

**Proyecto del módulo:** analizador de texto en memoria. En M01 no incluye lectura de archivos ni CLI; esas partes se agregan en M04.

**Criterio de salida:** el estudiante explica referencias/mutabilidad, predice el flujo de ejecución, organiza un módulo básico y escribe pruebas iniciales. Resuelve una variante nueva sin copiar una receta.

<a id="m02"></a>
### M02 — Colecciones, iteración y protocolo de datos

**Objetivo del módulo:** elegir la estructura adecuada y entender cómo Python recorre, transforma, compara y almacena datos.

**SM02-01 — Estructuras fundamentales**

- **M02-C01 — `list`, `tuple`, `dict` y `set`: selección y semántica**
  - **Objetivo observable:** Seleccionar list, tuple, dict o set a partir de requisitos de orden, duplicación, acceso y mutabilidad.
  - Contenido: orden, duplicados, mutabilidad, acceso, pertenencia, uso habitual, límites y coste práctico de operaciones comunes.
  - Evidencia: elegir y justificar una estructura para requisitos nuevos.
- **M02-C02 — Slicing, desempaquetado y operaciones de secuencia**
  - **Objetivo observable:** Extraer, reorganizar y desempaquetar secuencias sin errores de índices o de cantidad de valores.
  - Contenido: slicing aplicado a secuencias, asignación por desempaquetado, intercambio de valores y errores comunes.
  - Evidencia: transformar y extraer datos de secuencias con casos límite.

**SM02-02 — Expresividad e iteración**

- **M02-C03 — Comprensiones, `enumerate`, `zip` y ordenamiento**
  - **Objetivo observable:** Transformar y ordenar colecciones con herramientas idiomáticas, priorizando claridad sobre concisión innecesaria.
  - Contenido: comprensiones de listas/conjuntos/diccionarios, `enumerate`, `zip`, `sorted`, `key` y selección entre claridad y concisión.
  - Evidencia: comparar dos soluciones y justificar cuál resulta más legible.
- **M02-C04 — Iterables, iteradores y generadores**
  - **Objetivo observable:** Explicar y utilizar el protocolo de iteración, distinguiendo iterable, iterador y generador y sus patrones de consumo.
  - Contenido: protocolo de iteración, `iter`, `next`, `yield`, consumo único, evaluación perezosa y efectos de materializar iterables.
  - Evidencia: construir o consumir un iterador/generador y explicar su comportamiento.

**SM02-03 — Semántica y costes de los datos**

- **M02-C05 — Igualdad, hashabilidad, copias y complejidad práctica**
  - **Objetivo observable:** Diagnosticar problemas de claves, aliasing y copias, y justificar el coste aproximado de operaciones comunes.
  - Contenido: requisitos de claves de `dict` y elementos de `set`, `__eq__`/hash a nivel conceptual, aliasing en estructuras anidadas, copia superficial/profunda, elección de algoritmos y mutaciones accidentales.
  - Evidencia: diagnosticar un error de claves/copia y explicar el coste aproximado de una elección.

**Criterio de salida:** transformar datos de forma correcta, explicar orden/consumo/mutabilidad y justificar estructuras según legibilidad, requisitos y coste práctico.

**Regla de alcance:** M02-C01 se limita a selección y semántica de `list`, `tuple`, `dict` y `set`, mutabilidad de contenedores y elementos anidados, y elección según requisitos. Slicing y desempaquetado en profundidad quedan en M02-C02; comprensiones, `enumerate`, `zip` y ordenamiento en M02-C03; iteradores y generadores en M02-C04; igualdad/hashabilidad, copias y complejidad práctica en M02-C05. Los materiales de clase pueden dar contexto de temas posteriores, pero no deben convertirlos en objetivos ni evaluaciones de M02-C01.

<a id="m03"></a>
### M03 — Funciones, errores y diseño

**Objetivo del módulo:** diseñar interfaces claras y separar responsabilidades en código mantenible.

**SM03-01 — Diseño y comportamiento de funciones**

- **M03-C01 — Parámetros y firmas de función**
  - **Objetivo observable:** Definir funciones con firmas explícitas y llamadas previsibles, evitando trampas de valores mutables por defecto.
  - Contenido: argumentos posicionales y nombrados, valores predeterminados, `*args`, `**kwargs`, parámetros keyword-only y el cuidado con valores mutables por defecto.
  - Evidencia: definir una función con contrato y llamadas claras.
- **M03-C02 — Alcance, funciones como valores y closures**
  - **Objetivo observable:** Razonar sobre alcance y cierre léxico, y utilizar funciones como valores para componer comportamiento.
  - Contenido: alcance local/enclosing/global/built-in a nivel práctico, funciones de orden superior, closures y capturas comunes.
  - Evidencia: predecir y explicar comportamiento de funciones que reciben o retornan funciones.
- **M03-C03 — Decoradores y composición funcional introductoria**
  - **Objetivo observable:** Implementar o interpretar un decorador pequeño y decidir cuándo la abstracción mejora o empeora la legibilidad.
  - Contenido: funciones envolventes, aplicación de decoradores y cuándo no aportan claridad.
  - Evidencia: explicar o implementar un decorador pequeño con comportamiento verificable.

**SM03-02 — Errores e interfaces**

- **M03-C04 — Excepciones y diseño de errores**
  - **Objetivo observable:** Diseñar y probar contratos de error mediante excepciones específicas y propagación apropiada.
  - Contenido: excepciones específicas, `raise`, encadenamiento, límites de captura, errores esperables frente a fallos inesperados.
  - Evidencia: definir un contrato de error explícito y probar los casos inválidos pertinentes.
- **M03-C05 — Anotaciones de tipo y contratos**
  - **Objetivo observable:** Anotar interfaces y explicar la diferencia entre documentación de tipos, análisis estático y validación en ejecución.
  - Contenido: anotaciones de parámetros y retorno, colecciones tipadas, límites de las anotaciones y relación con verificadores estáticos.
  - Evidencia: anotar una interfaz y explicar qué garantiza y qué no garantiza la anotación.

**SM03-03 — Modularidad y modelado con objetos**

- **M03-C06 — Módulos, paquetes e imports sin efectos secundarios**
  - **Objetivo observable:** Organizar código en módulos y paquetes con dependencias explícitas y sin ejecución accidental durante imports.
  - Contenido: responsabilidades, dependencias entre módulos, organización de paquetes, puntos de entrada y efectos secundarios al importar.
  - Evidencia: refactorizar un programa a módulos con interfaces explícitas.
- **M03-C07 — Clases, `dataclasses`, composición y herencia**
  - **Objetivo observable:** Elegir entre funciones, composición y clases, modelando estado e invariantes sin recurrir innecesariamente a herencia.
  - Contenido: cuándo conviene un objeto, estado e invariantes, composición, herencia cuando realmente aporte valor, propiedades y métodos básicos.
  - Evidencia: representar un concepto con funciones o una clase y justificar la elección.
- **M03-C08 — Context managers y gestión de recursos**
  - **Objetivo observable:** Usar `with` para garantizar la gestión ordenada de recursos y explicar cómo interactúa con el flujo de excepciones.
  - Contenido: protocolo de contexto a nivel de uso, `with`, liberación de recursos y relación con excepciones; la implementación de context managers propios queda como extensión opcional si el caso lo justifica.
  - Evidencia: resolver un caso con gestión de recursos usando un context manager y explicar qué ocurre ante éxito y excepción.

**Criterio de salida:** refactorizar un programa pequeño en componentes con responsabilidades claras, contratos de entrada/salida y pruebas.

<a id="m04"></a>
### M04 — Archivos, CLI y biblioteca estándar

**Objetivo del módulo:** construir una herramienta práctica que procese información externa de forma segura y comprobable.

**SM04-01 — Sistema de archivos y datos estructurados**

- **M04-C01 — Rutas, codificación y archivos con `pathlib`**
  - **Objetivo observable:** Leer y escribir archivos mediante rutas portables, controlando codificación y errores de sistema de archivos.
  - Contenido: rutas relativas/absolutas, directorios, codificación de texto, lectura/escritura, `with` y errores de sistema de archivos.
  - Evidencia: leer y generar archivos de prueba gestionando rutas y errores.
- **M04-C02 — JSON, CSV y datos temporales**
  - **Objetivo observable:** Serializar y validar datos JSON/CSV y gestionar fechas cuando los requisitos lo necesiten.
  - Contenido: serialización, lectura/escritura, estructura de datos resultante, validación de campos y fechas/horas cuando el problema lo requiera.
  - Evidencia: transformar una colección de registros y rechazar entradas inválidas de forma explícita.

**SM04-02 — Construcción de herramientas CLI**

- **M04-C03 — Argumentos, configuración y códigos de salida**
  - **Objetivo observable:** Diseñar una interfaz CLI con argumentos, configuración y códigos de salida comprensibles.
  - Contenido: `argparse`, variables de entorno según el caso, configuración separada del código, mensajes de uso y códigos de salida.
  - Evidencia: interfaz CLI documentada que valida argumentos.
- **M04-C04 — Logging y manejo de fallos operativos**
  - **Objetivo observable:** Registrar eventos operativos útiles y distinguir errores esperables de fallos que deben hacerse visibles.
  - Contenido: `logging`, nivel de mensajes, excepciones esperables, diagnósticos útiles y no ocultar errores inesperados.
  - Evidencia: ejecución con entradas válidas e inválidas y registro que facilite el diagnóstico.
- **M04-C05 — Biblioteca estándar para transformar datos**
  - **Objetivo observable:** Elegir una herramienta apropiada de la biblioteca estándar y justificarla frente a una dependencia externa.
  - Contenido: selección guiada de `collections`, `itertools`, `functools`, fecha/hora u otros módulos pertinentes; justificar antes de introducir dependencias externas.
  - Evidencia: emplear una herramienta de la biblioteca estándar de forma legible y justificar su pertinencia.

**Proyecto del módulo:** ampliar el procesador de texto/archivos a una CLI que consume archivos y genera un informe.

**Criterio de salida:** otro usuario puede ejecutar la herramienta con entradas válidas e inválidas, entender los errores y reproducir el resultado.

<a id="m05"></a>
### M05 — Calidad y tooling reproducible

**Objetivo del módulo:** dejar un proyecto que otra persona pueda instalar, verificar y ejecutar con instrucciones claras.

**SM05-01 — Entorno y dependencias**

- **M05-C01 — Entornos virtuales y dependencias**
  - **Objetivo observable:** Crear un entorno aislado e instalar dependencias sin contaminar el intérprete global.
  - Contenido: crear/activar entornos, instalar y registrar dependencias, separar dependencias de desarrollo y evitar contaminación del entorno global.
  - Evidencia: instalación limpia siguiendo instrucciones del proyecto.
- **M05-C02 — `pyproject.toml`, paquetes y versiones**
  - **Objetivo observable:** Declarar metadatos, estructura de paquete y configuración de proyecto en pyproject.toml.
  - Contenido: metadatos del proyecto, estructura de paquete, configuración de herramientas y estrategia de versiones adecuada al tamaño del proyecto.
  - Evidencia: proyecto con configuración consistente y comandos declarados.

**SM05-02 — Verificación de calidad**

- **M05-C03 — Pruebas, formato, lint y tipado estático**
  - **Objetivo observable:** Configurar controles complementarios de pruebas, formato, lint y tipos sin duplicación injustificada.
  - Contenido: seleccionar herramientas actuales de pruebas, formatter, linter y verificación estática; responsabilidades de cada herramienta; no duplicar herramientas sin motivo.
  - Evidencia: comandos de calidad que corren de manera reproducible y hallazgos corregidos.
- **M05-C04 — Git, documentación, secretos y automatización**
  - **Objetivo observable:** Documentar el flujo de trabajo, mantener secretos fuera del repositorio y automatizar controles proporcionados al proyecto.
  - Contenido: estructura del README, decisiones de Git, configuración segura, secretos fuera del repositorio y CI básico si el proyecto lo justifica.
  - Evidencia: repositorio con instrucciones, exclusiones correctas y una automatización mínima cuando corresponda.
- **M05-C05 — Reproducibilidad y mantenimiento de herramientas**
  - **Objetivo observable:** Reproducir la instalación y las verificaciones en un entorno limpio y diagnosticar diferencias de herramientas.
  - Contenido: documentar versiones o rangos razonables, verificar comandos contra documentación vigente, actualizar configuración y diagnosticar discrepancias de entorno.
  - Evidencia: reproducir la instalación y ejecutar los controles en un entorno limpio.

**Criterio de salida:** un desarrollador distinto puede instalar, probar y ejecutar el proyecto con el README y reproducir los controles declarados.

<a id="m06"></a>
### M06 — Protocolos, diseño de APIs y calidad avanzada

**Objetivo del módulo:** aplicar protocolos de Python y prácticas de calidad para mejorar mantenibilidad y rendimiento con evidencia.

**SM06-01 — Protocolos y diseño de API**

- **M06-C01 — Métodos especiales y protocolos de Python**
  - **Objetivo observable:** Aplicar un protocolo de Python solo cuando el contrato del objeto lo requiera y explicar sus implicaciones.
  - Contenido: representación, comparación, hash, iteración y contextos desde la perspectiva de contrato; uso de métodos especiales sin implementarlos automáticamente.
  - Evidencia: elegir y explicar un protocolo relevante para un caso concreto.
- **M06-C02 — Diseño de APIs, composición y documentación**
  - **Objetivo observable:** Diseñar una API con responsabilidades, contratos e interfaces documentadas y coherentes.
  - Contenido: contratos, invariantes, responsabilidades, composición, compatibilidad y documentación de interfaces públicas.
  - Evidencia: revisión de una API pequeña con propuestas justificadas de mejora.

**SM06-02 — Verificación y depuración**

- **M06-C03 — Pruebas unitarias, parametrizadas y de integración**
  - **Objetivo observable:** Seleccionar pruebas unitarias, parametrizadas y de integración según el comportamiento que se quiere verificar.
  - Contenido: alcance de cada tipo de prueba, aislamiento razonable, dobles de prueba cuando son necesarios y límites de los mocks.
  - Evidencia: conjunto de pruebas que cubre comportamiento, errores y una integración relevante.
- **M06-C04 — Debugger, tracebacks y diagnóstico sistemático**
  - **Objetivo observable:** Localizar la causa de un defecto a partir de tracebacks, depuración y una reproducción mínima.
  - Contenido: leer trazas, aislar la causa, depurar paso a paso, usar logging como instrumento de diagnóstico y crear una reproducción mínima.
  - Evidencia: localizar y corregir un defecto explicando el camino de diagnóstico.

**SM06-03 — Rendimiento y complejidad**

- **M06-C05 — Perfilado, benchmarking y memoria**
  - **Objetivo observable:** Medir rendimiento y memoria de forma reproducible y justificar optimizaciones con datos.
  - Contenido: medir antes de optimizar, diferenciar perfilado de benchmarking, observar complejidad y memoria, evitar conclusiones a partir de mediciones no controladas.
  - Evidencia: comparación antes/después reproducible con análisis de trade-offs.

**Criterio de salida:** presentar una mejora de diseño o rendimiento que mantenga la corrección y que esté respaldada por pruebas, diagnóstico o mediciones pertinentes.

<a id="m07"></a>
### M07 — HTTP y persistencia

**Objetivo del módulo:** integrar un programa con servicios externos y almacenamiento persistente sin acoplar toda la lógica a esas dependencias.

**SM07-01 — HTTP y APIs externas**

- **M07-C01 — HTTP, serialización y cliente de API**
  - **Objetivo observable:** Consumir una API HTTP distinguiendo respuestas válidas, códigos de estado, errores de red y límites de tiempo.
  - Contenido: solicitud/respuesta, códigos de estado, JSON, cliente HTTP, límites de tiempo y estructura de errores de red.
  - Evidencia: cliente que consume una API y distingue resultados satisfactorios de fallos.
- **M07-C02 — Validación, autenticación y resiliencia**
  - **Objetivo observable:** Validar respuestas, externalizar configuración y gestionar autenticación y reintentos de forma segura.
  - Contenido: validación de datos recibidos, configuración externa, secretos fuera de Git, reintentos limitados e idempotencia cuando corresponda.
  - Evidencia: cliente con configuración separada, fallos esperables y pruebas de comportamiento.

**SM07-02 — Persistencia e integración**

- **M07-C03 — SQL, consultas parametrizadas y transacciones**
  - **Objetivo observable:** Persistir y consultar datos mediante SQL parametrizado y transacciones apropiadas.
  - Contenido: conexión, esquema mínimo, operaciones CRUD pertinentes, consultas parametrizadas y límites transaccionales.
  - Evidencia: almacenar y recuperar datos de forma consistente con errores controlados.
- **M07-C04 — Separación de lógica e integración**
  - **Objetivo observable:** Integrar HTTP y persistencia sin acoplarlos a las reglas de negocio y verificar el flujo con pruebas.
  - Contenido: separar reglas de negocio, HTTP y persistencia; pruebas de integración con dependencias controladas y configuración del entorno.
  - Evidencia: flujo integrado que pueda verificarse sin credenciales o servicios secretos incrustados en el código.

**Criterio de salida:** entregar un cliente o servicio pequeño que valide entradas, gestione fallos, utilice configuración externa y pruebe la integración.

**Política de alcance para persistencia (decisión curricular v0.5.8):** para el primer proyecto, usar SQLite como opción predeterminada cuando los requisitos sean locales, de un solo usuario/proceso o de concurrencia moderada y no exijan un servidor de base de datos. Si los requisitos requieren acceso remoto multiusuario, operación administrada o capacidades que SQLite no cubra, seleccionar otra base de datos justificando la necesidad. La clase enseñará SQL parametrizado y transacciones sin convertir la selección de un motor concreto en objetivo independiente. La elección final del proyecto se registra en M09-C01/M09-C02; no se requiere infraestructura externa por defecto.

<a id="m08"></a>
### M08 — Concurrencia y paralelismo

**Objetivo del módulo:** elegir el modelo de ejecución a partir de las características de la carga y de mediciones adecuadas.

**SM08-01 — Fundamentos y `asyncio`**

- **M08-C01 — I/O-bound, CPU-bound, concurrencia y paralelismo**
  - **Objetivo observable:** Clasificar cargas por su cuello de botella y predecir cuándo investigar concurrencia o paralelismo.
  - Contenido: modelo de ejecución, espera de I/O, cálculo de CPU, costes y limitaciones según la biblioteca usada.
  - Evidencia: clasificar cargas y predecir qué estrategia vale la pena investigar.
- **M08-C02 — Coroutines, `async`/`await` y event loop**
  - **Objetivo observable:** Explicar el ciclo de eventos y ejecutar coroutines sin bloquear el event loop.
  - Contenido: coroutines, `await`, tareas y ciclo de eventos; qué bloquea el loop y cuándo una función asíncrona no aporta ventaja.
  - Evidencia: explicar el flujo de una tarea asíncrona y ejecutar un ejemplo controlado.
- **M08-C03 — Concurrencia limitada, cancelación y errores**
  - **Objetivo observable:** Limitar concurrencia y gestionar timeouts, cancelación, errores y cierre ordenado.
  - Contenido: timeouts, cancelación, cierre ordenado, semáforos, locks, carreras, tareas y manejo de excepciones.
  - Evidencia: programa concurrente que limita carga y se cierra correctamente ante fallos o cancelación.

**SM08-02 — Threads, procesos y medición**

- **M08-C04 — Hilos y procesos**
  - **Objetivo observable:** Elegir entre hilos y procesos según el trabajo, comunicación, estado compartido y costes.
  - Contenido: hilos para APIs bloqueantes/I/O según el caso; procesos para trabajo CPU-bound cuando compense; comunicación, estado compartido y costes.
  - Evidencia: seleccionar una estrategia y explicar sus costes y riesgos.
- **M08-C05 — Comparación experimental de modelos**
  - **Objetivo observable:** Comparar enfoques con una línea base y mediciones controladas, reportando límites y resultados reales.
  - Contenido: construir línea base secuencial, medir bajo condiciones comparables, manejar resultados y explicar límites del experimento.
  - Evidencia: informe con mediciones repetibles y conclusión acorde con los datos obtenidos.

**Criterio de salida:** elegir una estrategia en función de la carga y respaldar la decisión con una comparación controlada. No se exige que la opción concurrente siempre resulte más rápida.

<a id="m09"></a>
### M09 — Proyecto integrador

**Objetivo del módulo:** demostrar que el estudiante puede resolver un problema acotado de punta a punta y defender técnicamente la solución.

**SM09-01 — Definición y diseño**

- **M09-C01 — Requisitos, alcance y aceptación**
  - **Objetivo observable:** Convertir una necesidad en requisitos, restricciones y criterios de aceptación comprobables.
  - Contenido: usuario objetivo, problema, restricciones, criterios de aceptación, riesgos y exclusiones explícitas.
  - Evidencia: especificación breve revisable y comprobable.
- **M09-C02 — MVP, arquitectura mínima y plan de entrega**
  - **Objetivo observable:** Diseñar un MVP modular y un plan incremental acorde con alcance, riesgos y prioridades.
  - Contenido: diseño incremental, división en módulos, persistencia o integración cuando proceda, riesgos y prioridades.
  - Evidencia: plan de implementación con hitos pequeños y decisiones justificadas.

**SM09-02 — Implementación y verificación**

- **M09-C03 — Implementación incremental y control de cambios**
  - **Objetivo observable:** Implementar funcionalidad en cambios pequeños y mantener trazabilidad mediante Git y pruebas.
  - Contenido: cambios pequeños, Git, pruebas durante el desarrollo, revisión de los criterios de aceptación y refactorización controlada.
  - Evidencia: historial comprensible y funcionalidad integrada paso a paso.
- **M09-C04 — Pruebas, logging y gestión de errores**
  - **Objetivo observable:** Verificar requisitos, casos límite y fallos operativos y registrar defectos conocidos.
  - Contenido: cobertura de comportamientos principales y casos límite, diagnósticos, reproducción del entorno y validación funcional.
  - Evidencia: resultado de pruebas y lista de defectos corregidos/conocidos.

**SM09-03 — Entrega y reflexión**

- **M09-C05 — Documentación, demostración y retrospectiva técnica**
  - **Objetivo observable:** Entregar un proyecto reproducible, explicar sus decisiones y limitaciones y proponer siguientes pasos.
  - Contenido: README, decisiones técnicas, instrucciones, limitaciones, deuda pendiente y próximos pasos.
  - Evidencia: repositorio reproducible, demostración funcional y explicación de trade-offs.

**Criterio de salida:** el proyecto satisface los criterios de aceptación acordados, se puede ejecutar y verificar, está documentado y sus limitaciones se comunican con honestidad.

**Plantilla obligatoria de aceptación (se completa antes de implementar):**
1. **Problema y usuario:** quién tiene el problema y qué resultado útil se espera.
2. **Alcance:** funcionalidades incluidas y exclusiones explícitas del MVP.
3. **Criterios funcionales verificables:** al menos tres escenarios expresados como entrada/acción y resultado observable, incluyendo el flujo principal y un caso límite o de error pertinente.
4. **Calidad operativa:** instrucciones de instalación/ejecución reproducibles, configuración sin secretos incrustados y errores que puedan diagnosticarse.
5. **Pruebas y evidencia:** cómo se comprobará cada criterio y qué salida, prueba o demostración lo demuestra.
6. **Restricciones y riesgos:** tiempo disponible, dependencias, privacidad/seguridad y riesgos relevantes.
7. **Definición de terminado:** criterios anteriores aprobados, pruebas ejecutadas, README actualizado y limitaciones conocidas registradas.

No se fijan ahora las funcionalidades del proyecto: la plantilla es obligatoria, pero el problema concreto se acuerda al llegar a M09, con base en el diagnóstico, los intereses y las competencias demostradas. Los criterios deben ser observables y proporcionados al tamaño del MVP; no se impone un número de líneas, cobertura porcentual ni arquitectura predeterminada.

<a id="m10"></a>
### M10 — Exploración de especializaciones

**Objetivo del módulo:** experimentar con áreas de Python sin confundir una muestra introductoria con dominio profesional.

**SM10-01 — Prototipos de exploración**

**Límite de alcance:** cada prototipo es una exploración acotada, no una formación completa del área. Como referencia, dedicar 2–4 horas por prototipo; elegir al menos dos áreas distintas según interés y valor profesional. Se puede sustituir una opción por otra pertinente sin ampliar la duración total.

**Regla especial de prerrequisitos:** M10-C02, M10-C03, M10-C04, M10-C05 y M10-C06 son ramas alternativas; no son prerrequisitos entre sí y no es necesario completarlas todas. M10-C07 requiere M10-C01 y evidencia de al menos dos prototipos de ramas distintas. La regla general de orden dentro de un submódulo no convierte las cinco ramas en una secuencia obligatoria. Para prototipos que usen herramientas, aplicar el requisito de M04 o evidencia equivalente definido en las secciones 4 y 6.

- **M10-C01 — Método de comparación de especializaciones**
  - **Objetivo observable:** Comparar áreas mediante un protocolo común de experimentación y criterios explícitos.
  - Contenido: definir una pregunta por prototipo, acotar requisitos, registrar dependencias, tiempo, resultado, dificultades y afinidad; comparar opciones sin medir solo por familiaridad inicial.
  - Evidencia: plantilla de experimentación que permita comparar resultados.
- **M10-C02 — Automatización y herramientas para desarrolladores**
  - **Objetivo observable:** Construir un prototipo de automatización local o herramienta de desarrollo que resuelva una tarea concreta.
  - Contenido: procesamiento de tareas repetitivas, CLI y automatización local.
  - Evidencia: prototipo breve que resuelve una tarea reproducible.
- **M10-C03 — Backend y servicios**
  - **Objetivo observable:** Construir un prototipo de servicio/backend con validación y persistencia solo si el alcance lo permite.
  - Contenido: endpoint o pequeño servicio, validación y comunicación con persistencia cuando alcance el tiempo.
  - Evidencia: prototipo ejecutable y documentado.
- **M10-C04 — Análisis de datos**
  - **Objetivo observable:** Explorar datos tabulares y producir una transformación o visualización que responda una pregunta explícita.
  - Contenido: exploración inicial de conjuntos de datos tabulares y visualización/transformación básica; pandas solo si es pertinente al experimento.
  - Evidencia: cuaderno o script con pregunta, transformación y conclusión verificable.
- **M10-C05 — Machine Learning e IA**
  - **Objetivo observable:** Probar un flujo introductorio de ML/IA distinguiendo integración de servicios y entrenamiento de modelos.
  - Contenido: exploración introductoria de un flujo de datos/modelo o integración de un servicio de IA; distinguir uso de herramientas de entrenamiento avanzado.
  - Evidencia: prototipo breve con limitaciones y dependencias descritas.
- **M10-C06 — Integración con sistemas y código nativo**
  - **Objetivo observable:** Demostrar una integración acotada con un sistema externo o biblioteca nativa y documentar sus requisitos.
  - Contenido: una muestra acotada de interacción con un sistema externo o biblioteca nativa, si coincide con el objetivo profesional.
  - Evidencia: demostración pequeña con límites y requisitos documentados.
- **M10-C07 — Decisión de siguiente ruta**
  - **Objetivo observable:** Elegir la siguiente área de estudio comparando evidencia de prototipos, interés, valor y brechas.
  - Contenido: comparar al menos dos prototipos según interés, valor profesional, conocimientos faltantes y coste de profundización.
  - Evidencia: decisión razonada y plan de aprendizaje posterior.

**Criterio de salida:** haber completado al menos dos prototipos de áreas distintas, registrar resultados comparables y escoger el siguiente enfoque con una justificación explícita. No es obligatorio construir los cinco prototipos ni dominar o cursar a fondo todas las áreas.

<a id="05a-criterios-de-calidad-por-clase"></a>
### 5.1 Criterios mínimos de calidad por clase

Antes de impartir o marcar una clase como lista, su material detallado debe especificar:

1. **Prerrequisitos:** conocimientos y clases previas requeridos; indicar qué puede diagnosticarse o abreviarse.
2. **Criterio de éxito observable:** qué resultado concreto demuestra el objetivo, con condiciones y casos límite pertinentes.
3. **Secuencia didáctica:** explicación explícita, ejemplo resuelto, comprobación breve de comprensión, práctica guiada y actividad independiente cuando corresponda.
4. **Evidencia revisable:** código, salida, explicación o artefacto; no aceptar como evidencia únicamente haber leído o asistido.
5. **Errores previsibles y remediación:** al menos los errores conceptuales más probables, una pista o explicación alternativa y una comprobación posterior.
6. **Referencias reales:** registrar solo fuentes efectivamente consultadas; no inventar páginas, versiones, comandos ni resultados.

**Puerta de calidad (`READY`):** antes de marcar una clase como `READY`, revisar los seis requisitos anteriores: (1) prerrequisitos; (2) criterio de éxito observable; (3) secuencia didáctica; (4) evidencia revisable; (5) errores previsibles y remediación; y (6) referencias realmente consultadas y verificadas. Si algún elemento no es pertinente para el objetivo de la clase, registrar una excepción breve y justificada en su material; no inventar referencias ni exigir pruebas, tipado o benchmarking cuando no correspondan. Además, el material debe respetar el alcance de la clase y no depender de suposiciones esenciales no explicadas. Si falta un requisito aplicable o su excepción justificada, la clase no está `READY`.

**Generación progresiva de materiales:** las clases detalladas se crearán cuando el avance del estudiante las requiera mediante la skill de generación de clases de `@University Tutor`, no todas por adelantado. Por tanto, la auditoría de la ruta no exige que existan ya 58 lecciones completas. Al preparar cada clase, el tutor debe cargar el estado del curso y la ruta aprobada vigentes, comprobar versión, ID, prerrequisitos y alcance; generar un `DRAFT`; revisar fuentes, secuencia didáctica, ejercicios, evidencia y referencias; corregir los hallazgos; y solo entonces declarar el material `READY` para su uso, sujeto a las aprobaciones aplicables. Si falta un artefacto necesario o hay incompatibilidad de versiones, debe detenerse y reportar el problema en vez de improvisar una versión oficial. La auditoría continua verifica cada clase en el momento de generarse y antes de impartirla, y conserva los hallazgos y correcciones.

<a id="06-prerrequisitos-y-reglas-de-avance"></a>
## 6. Prerrequisitos y reglas de avance

### Dependencias principales

- M00 prepara el entorno y adapta el punto de entrada; no es una barrera conceptual para el estudiante que ya tenga un entorno validado.
- M01 es la base lingüística. Puede abreviarse solo cuando exista evidencia equivalente.
- M02 aporta el uso sistemático de colecciones e iteración; M03 lo utiliza cuando las interfaces manipulan colecciones.
- M03 es prerrequisito práctico para modularidad, tratamiento de errores y diseño de componentes en M04–M08.
- M04 introduce archivos, configuración y CLI; facilita proyectos de tooling, integración y el proyecto integrador.
- M05 establece herramientas reproducibles. Los módulos avanzados pueden usar herramientas antes, pero no deben asumir que el estudiante ya domina el tooling profesional.
- M06 depende de un mínimo de funciones, colecciones, pruebas y organización de proyectos.
- M07 necesita excepciones, serialización, configuración y tests básicos. No exige haber completado M06 si la evidencia necesaria se demuestra por otro medio.
- M08 requiere comprender funciones, excepciones, pruebas y una carga I/O representativa. Los fundamentos HTTP de M07 son el ejemplo recomendado, no una condición absoluta si se utiliza otro caso I/O apropiado.
- M09 utiliza el conjunto de conocimientos pertinente al alcance firmado; no obliga a incorporar todos los temas de la ruta.
- M10 es exploratorio y permite priorizar áreas sin declarar dominio avanzado.

### Estados de evidencia

- `NOT_YET`: la competencia todavía no se ha demostrado.
- `WITH_SUPPORT`: la resuelve con pistas o ayuda relevante.
- `INDEPENDENT`: la resuelve y explica sin guía sustantiva.
- `TRANSFER`: aplica la competencia a un problema nuevo, justifica decisiones y reconoce límites.
- `VALIDATED`: estado de dominio aprobado después de comprobar el criterio específico mediante evidencia suficiente; debe acompañarse del registro de evidencias y fecha.

Completar una clase, leer material o responder correctamente una única pregunta no convierte automáticamente una competencia en `VALIDATED`.

<a id="07-proyectos-incrementales"></a>
## 7. Proyectos incrementales

Los proyectos son vehículos para practicar conceptos; no tienen que ser cinco repositorios distintos. Se pueden desarrollar como etapas de un único repositorio si los entregables siguen siendo distinguibles.

- **P01 — Procesador de texto y archivos (M01–M04):** empieza como funciones que operan sobre cadenas en memoria; después incorpora archivos, validación y CLI.
- **P02 — Paquete mantenible (M03–M06):** módulos, interfaces, pruebas, tipado, documentación y tooling reproducible.
- **P03 — Integración HTTP y persistencia (M04–M07):** datos externos, configuración, validación, almacenamiento y tests de integración.
- **P04 — Comparación de concurrencia (M08):** línea base secuencial y alternativas concurrentes medidas con la misma carga.
- **P05 — Proyecto integrador (M09):** problema real de alcance limitado seleccionado según diagnóstico, intereses y aprendizaje demostrado.

Cada proyecto debe definir alcance, criterios de aceptación, restricciones, evidencia y qué temas quedan fuera. Evitar duplicar entregables sin que aporten una competencia distinta.

<a id="08-evaluacion-y-evidencia-de-dominio"></a>
## 8. Evaluación y evidencia de dominio

### Tipos de evaluación

- **Diagnóstico:** orienta el plan; no se usa como nota de dominio.
- **Formativa:** feedback y reintento durante el aprendizaje.
- **Checkpoint de módulo:** evidencia para avanzar, abreviar o reforzar contenidos.
- **Transferencia:** tarea nueva que requiere aplicar conceptos sin copiar una receta.
- **Proyecto:** comprobación de una solución integrada y documentada.

### Rúbrica base

Aplicar únicamente los criterios pertinentes a cada tarea:

1. Corrección funcional y ejecución.
2. Explicación del razonamiento.
3. Tratamiento de entradas inválidas y casos límite.
4. Pruebas pertinentes, cuando correspondan.
5. Legibilidad y uso idiomático del lenguaje.
6. Justificación de estructuras, dependencias y trade-offs.
7. Reproducibilidad y documentación, cuando correspondan.

No asignar calificaciones numéricas sin una escala acordada. Si una competencia crítica no se demuestra, se realiza remediación antes de depender de ella en una actividad posterior. Las brechas menores pueden quedar registradas mientras se avanza, si no bloquean los prerrequisitos siguientes.

<a id="09-metodologia-de-tutoria"></a>
## 9. Metodología de tutoría

Una clase suele incluir: objetivos y prerrequisitos; problema inicial; explicación explícita; ejemplos progresivos; preguntas de comprensión; práctica guiada; ejercicio independiente; revisión con criterios; resumen o recuperación activa; tarea/evidencia y siguiente paso. La estructura puede variar según el tema.

Reglas de interacción:

- Antes de práctica independiente sobre un concepto nuevo o difícil, incluir una comprobación breve de comprensión (por ejemplo, predecir una salida, explicar una distinción o seguir el estado de los objetos). Si aparece una brecha relevante, explicar el punto concreto con otro ejemplo y volver a comprobarlo; no exigir formulación perfecta ni bloquear la práctica guiada.
- Separar explicación, comprobación conceptual, práctica guiada y práctica independiente. No usar una pregunta de recuerdo como única prueba de comprensión cuando el objetivo exige razonamiento.

- Usar una actividad sustantiva a la vez cuando la respuesta del estudiante deba determinar el siguiente paso.
- Pedir predicción y razonamiento antes de ejecutar cuando se esté evaluando lectura de código.
- No entregar la solución completa antes del intento, salvo que se solicite una demostración.
- Si hay error, identificar si es conceptual, sintáctico, de lectura o de estrategia; dar una pista accionable y permitir corregir.
- Reducir gradualmente las pistas para fomentar autonomía.
- Utilizar Java, Kotlin, Go y C++ para comparar diferencias relevantes, no para repetir fundamentos ya dominados.
- Distinguir material planificado de material que ya existe y evidencia de aprendizaje de mera exposición.
- No afirmar que un comando, test o experimento se ejecutó si no existe resultado que lo demuestre.

Distribución semanal inicial para 15 horas: 3 h de clases interactivas; 4 h de ejercicios y razonamiento; 4 h de programación; 3 h de proyecto aplicado; 1 h de repaso y evaluación. Ajustar en el rango de 10–20 horas a partir de la evidencia y la carga real.

<a id="10-materiales-de-referencia"></a>
## 10. Materiales de referencia

Los libros aportados son referencias selectivas, no un programa que deba seguirse capítulo por capítulo. No se asignan páginas hasta verificar edición, integridad y correspondencia con el tema.

| Material | Uso previsto | Precaución |
|---|---|---|
| *Learning Python* | Fundamentos del lenguaje y modelo mental, especialmente M01–M03 | Confirmar edición y consultar capítulos concretos antes de asignar páginas |
| *Effective Python* | Idiomatismos, decisiones de diseño y calidad, cuando el fragmento disponible cubra el tema | Confirmar cobertura del archivo disponible; no asumir que la muestra contiene toda la obra |
| *The Python Standard Library by Example* | Consulta selectiva para M04 y más adelante | La edición aportada es antigua; contrastar nombres, APIs y ejemplos con documentación vigente |
| *Hypermodern Python Tooling* | Referencia selectiva para M05 | Contrastar herramientas, configuración y comandos con documentación vigente |
| *Python Concurrency with asyncio* — Matthew Fowler | M08 | Verificar ejemplos y APIs en la versión actual de Python y sus bibliotecas |
| *Python for Data Analysis* | M10 si se explora análisis de datos | No adelantarlo como requisito de la ruta generalista |
| Documentación oficial de Python | Resolver dudas concretas y confirmar semántica y APIs | Registrar URL y fecha cuando se use como fuente externa de una afirmación curricular |

Cada clase debe registrar las referencias realmente utilizadas, no solo las referencias que podrían ser útiles.

<a id="11-registro-y-seguimiento-del-progreso"></a>
## 11. Registro y seguimiento del progreso

El archivo `COURSE_STATE.md` debe registrar el estado real por módulo, clase o competencia, evidencia y fecha, y la siguiente acción. No usar el índice de esta ruta como señal de que el contenido fue estudiado.

Campos mínimos de una evidencia: módulo/clase; competencia o criterio; actividad realizada; resultado observado; nivel de apoyo; brecha pendiente; fecha; próxima acción. Actualizar el estado después de una sesión sustantiva o evaluación, no después de cada mensaje casual.

Separar siempre:

- **Declarado:** el estudiante informa que conoce o realizó algo.
- **Observado:** hay una respuesta, solución, salida o resultado visible.
- **Validado:** la evidencia observada cumple los criterios definidos, preferentemente en un problema independiente o de transferencia.

Antes de comenzar una clase, comprobar su ID, ubicación y estado de material. Si aún no existe una lección detallada, impartirla conforme a este índice y marcarla como material de trabajo, sin afirmar que el archivo ya existe.

<a id="12-decisiones-pendientes"></a>
## 12. Compatibilidad, migración y decisiones pendientes

### Compatibilidad con el progreso existente (añadido en v0.5.7)

Esta sección es una regla de migración individual; no altera los objetivos ni declara competencias nuevas como dominadas.

1. La ruta aprobada y el estado del estudiante son artefactos distintos. La migración solo puede prepararse contra una ruta aprobada y validada.
2. Se conserva una copia íntegra del estado previo y de sus referencias de evidencia antes de crear una nueva revisión de estado.
3. La correspondencia se determina por objetivo, competencia, criterio y evidencia; no solo por similitud de títulos o IDs.
4. Evidencia reportada por el estudiante se conserva como `COMPLETED_REPORTED`; no se convierte automáticamente en dominio validado.
5. Las clases con evidencia parcial se revisan criterio por criterio. Solo se solicita una comprobación breve de los criterios no cubiertos; no se repite toda la clase por defecto.
6. Una actividad en curso se conserva como pendiente en la nueva revisión, salvo que la evidencia existente satisfaga sus criterios en la ruta aprobada.
7. Los IDs curriculares estables no se renumeran. Las correspondencias antiguas/nuevas se registran en una matriz separada con estado `MATCH`, `PARTIAL`, `REVIEW` o `NO_MATCH` y justificación.
8. La migración no se aplica hasta que se apruebe tanto la ruta como la propuesta de migración; los elementos sin evidencia suficiente quedan en revisión.

### Decisiones curriculares aprobadas

1. **Pruebas:** M01 introduce `unittest` para enseñar los fundamentos sin añadir otro framework a la vez. M05 incorpora `pytest` como herramienta profesional y permite comparar ambos enfoques cuando corresponda.
2. **Proyecto integrador:** su dirección general será una herramienta para desarrolladores o agentes locales. El problema concreto, el alcance, las tecnologías y los criterios de aceptación se definirán después del diagnóstico y conforme avance el estudiante.
3. **Metodología:** cada clase utilizará, como patrón por defecto, explicación breve, ejemplo, ejercicio y revisión. Se profundizará cuando el tema o la evidencia lo requieran.
4. **Jerarquía:** módulo → submódulo opcional → clase. Ejercicios, secciones y actividades se mantienen dentro de cada clase, no como niveles curriculares formales.
5. **Aprobación histórica de v0.5.1:** la estructura y la secuencia general M00–M10 constan como aprobadas en esa versión. Las propuestas v0.5.2–v0.5.5 no heredaron automáticamente ese estado. La decisión posterior de v0.5.8 está registrada por separado y tiene alcance limitado; no debe confundirse con una aprobación exhaustiva de materiales o con una migración de progreso.
6. **Continuidad del curso:** conservar IDs existentes, el registro individual de progreso y la posición de estudio. Esta propuesta no actualiza `COURSE_STATE.md` ni declara nuevas competencias validadas.

### Cambios introducidos en v0.5.5

1. Añadir hitos H0–H8 con evidencia mínima y acción de recuperación, sin imponer fechas fijas.
2. Declarar explícitamente que M10-C02–C06 son ramas alternativas y que M10-C07 requiere dos prototipos de áreas distintas; así se evita interpretar las cinco áreas como una secuencia obligatoria.
3. Cambiar el título de M06 a «Protocolos, diseño de APIs y calidad avanzada» para diferenciarlo del consumo de APIs HTTP de M07.
4. Corregir la referencia histórica que identificaba v0.5.3 como la propuesta actual.
5. Aclarar el criterio de elección de persistencia para el primer proyecto de M07: preferir una opción local sencilla si cumple los requisitos y justificar cualquier servicio externo.

### Decisiones heredadas y conservadas de v0.5.2–v0.5.4

1. Mantener el límite de alcance entre M02-C01 y M02-C02–C05.
2. Añadir hitos de avance con evidencia y acciones de recuperación, sin imponer fechas fijas.
3. Aclarar que las cinco áreas prototipo de M10 son ramas alternativas y que basta con dos; corregir la contradicción potencial con la regla general de prerrequisitos.
4. Afinar el nombre de M06 para distinguir diseño de APIs de consumo de APIs HTTP, que se trabaja en M07.
5. Incluir una comprobación breve de comprensión antes de la práctica independiente de conceptos nuevos o difíciles, con reexplicación y segunda comprobación cuando sea necesario.
6. Mantener el enfoque para desarrolladores con experiencia, usando comparaciones selectivas con Java, Kotlin, Go y C++ sin repetir fundamentos generales salvo que la evidencia revele una brecha.
7. Conservar `unittest` como primer framework de pruebas en M01 y reservar `pytest` para M05.
8. Mantener la orientación del proyecto integrador hacia herramientas de desarrollo o agentes locales, sin fijar prematuramente su alcance.
9. Conservar los IDs de clase y exigir aprobación y validación de compatibilidad antes de migrar el estado del estudiante.

### Pendiente de resolver en el momento oportuno

1. Confirmar la versión exacta de Python y el conjunto de herramientas profesionales cuando se llegue a M05; verificar entonces la documentación oficial vigente. Esta es una decisión operativa diferida deliberadamente: la ruta define capacidades y criterios de selección, no congela versiones de herramientas con meses de antelación. No bloquea la aprobación curricular.
2. Definir el alcance concreto y los criterios de aceptación del proyecto integrador antes de iniciar M09.
3. Definir si la ruta posterior priorizará backend, automatización, datos, IA/ML u otra especialización tras M10.
4. Generar y auditar cada material de clase progresivamente, antes de impartirlo, mediante la skill de generación de clases de `@University Tutor`; no se exige producir las 58 lecciones por adelantado.
5. Selección de motor de persistencia en el proyecto concreto: SQLite es el valor predeterminado para el caso local simple; justificar otro motor solo si los requisitos lo necesitan. La política curricular ya queda definida en la sección M07.

<a id="13-historial-de-versiones"></a>
## 13. Historial de versiones

### v0.5.9 — Armonización de formato (2026-10-21)

- Se aplica el contrato de formato `UT-LP-1.0` y se normalizan los metadatos.
- No hay cambios curriculares ni cambios de IDs.
- Se conserva el alcance limitado de aprobación de v0.5.8; no se migra `COURSE_STATE` ni se aprueba material de clase.


- **0.5.8 — revisión curricular y aceptación (aprobada con alcance documentado el 2026-10-21):** define la política predeterminada de persistencia (SQLite cuando el caso local lo permita), añade una plantilla obligatoria y verificable de aceptación para M09, y aclara que verificar versiones/herramientas en M05 es una decisión operativa diferida que no bloquea la ruta. Conserva los 58 IDs y no cambia el estado del estudiante. La aprobación tiene los límites registrados: no afirma comparación exhaustiva contra v0.5.1, no aprueba materiales antiguos y no migra progreso.
- **0.5.7 — borrador de compatibilidad y migración explícita:** incorpora reglas para mapear progreso previo por objetivos, competencias, criterios y evidencia; preserva estados reportados, exige estado histórico inmutable y prohíbe aplicar la migración antes de aprobar y validar ruta y matriz. No modifica el progreso del estudiante ni activa esta ruta.

- **0.5.6 — borrador con auditoría progresiva de clases:** aclara que `@University Tutor` genera cada clase detallada al llegar a ella mediante su skill de generación, y que la auditoría se aplica a cada borrador antes de impartirlo, no a 58 materiales que todavía no existen. Conserva los 58 IDs, el flujo `DRAFT` → revisión → corrección → `READY` y el estado individual sin cambios. Sigue pendiente de revisión, aprobación y validación.
- **0.5.4 — borrador corregido tras revisión documental:** corrige el historial, incorpora la subsección 5.1 en el índice, hace explícita la puerta READY, distingue exploración temprana y prototipos técnicos de M10, normaliza «remediación» y aclara los límites de comparación con v0.5.1. Conserva los 58 IDs y no migra el estado del estudiante. Sigue pendiente de revisión y aprobación.
- **0.5.3 — borrador revisado con ajustes pedagógicos:** estrecha el alcance de M03-C08 a gestión de recursos, explicita una puerta mínima de calidad para los materiales de clase y acota temporalmente los prototipos de M10; conserva los IDs existentes, mantiene el estado del curso sin migrar y sigue pendiente de aprobación.
- **0.5.2 — borrador de actualización revisado:** se verificó la correspondencia entre el índice tabular y el desarrollo detallado (58 IDs únicos en ambas secciones, sin faltantes ni duplicados); se comprobó la integridad de los enlaces internos; se añadió objetivo observable explícito a cada clase y se aclaró que el índice no equivale a 58 materiales didácticos ya producidos. Conserva el resto de los cambios propuestos; sigue pendiente de aprobación y validación curricular. Parte de la base aprobada v0.5.1; explicita los límites curriculares de M02-C01 frente a M02-C02–C05; añade comprobación conceptual breve antes de práctica independiente; refuerza continuidad del estudiante, compatibilidad y migración explícita; mantiene `unittest` primero y `pytest` en M05; conserva la orientación del proyecto integrador hacia tooling/agentes locales sin fijar prematuramente su alcance. Estado: pendiente de revisión y aprobación; no cambia `COURSE_STATE.md`.
- **0.5.1 — base curricular aprobada:** registra las decisiones confirmadas sobre `unittest` y `pytest`, dirección general del proyecto integrador, metodología de clase y jerarquía curricular; aprueba la estructura y secuencia general M00–M10; conserva como pendientes las decisiones que dependen del progreso futuro, como el alcance concreto del proyecto integrador y la especialización posterior. No declara completadas las clases ni validadas las competencias.
- **0.5.0 — borrador para revisión:** añade un índice jerárquico explícito; establece módulo, submódulo opcional, clase y secciones/actividades; incorpora IDs y un índice de clases planificadas de M00–M10; aclara prerrequisitos, evidencias, avance, proyectos, seguimiento y fuentes; alinea M01 con el plan de seis clases y `unittest` disponible en M01 v0.4.3. Mantiene la secuencia principal general de M00 a M10.
- **0.4.2 — borrador anterior:** definía objetivos, temas, evidencias y prerrequisitos a nivel de módulo, pero no tenía un índice completo de clases ni una jerarquía formal por clase.

---

**Estado documental de la fuente v0.5.8:** `APPROVED_WITH_DOCUMENTED_SCOPE_LIMIT`, conforme al registro de aprobación del 2026-10-21. La aprobación cubre únicamente el alcance documentado; no afirma equivalencia textual exhaustiva con v0.5.1, no aprueba materiales de clase y no migra `COURSE_STATE.md`. La revisión de formato v0.5.9 conserva esos límites y no declara clases completadas ni competencias validadas.
