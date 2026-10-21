---
course_id: PYDEV-001
module_id: M01
artifact_type: module_plan_and_lessons
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01 — Semántica y sintaxis esencial

## 1. Propósito

Construir un modelo mental correcto de Python y aprender a leer, predecir, escribir y comprobar programas pequeños. El estudiante ya domina fundamentos generales de programación; por ello, el foco está en las particularidades de Python, no en volver a enseñar algoritmos desde cero.

## 2. Preparación de las clases

La tabla de `LEARNING_PATH.md` asigna fuentes y secciones propuestas para cada clase. Antes de redactar una lección, se deben consultar esas fuentes, confirmar edición e índice y leer la sección pertinente. La estructura obligatoria, el registro de fuentes efectivamente consultadas y la revisión previa a `READY` están definidos en [Guía para preparar las clases](../../GUIA_DE_CLASES.md).

## 3. Resultados de aprendizaje

Al terminar, el estudiante podrá:

1. Explicar nombres, objetos, asignación, referencias, aliasing y mutabilidad.
2. Distinguir igualdad (`==`) e identidad (`is`), y usar `is` correctamente en casos como `value is None`.
3. Interpretar tipado dinámico, tipos básicos, conversiones explícitas, operadores y truthiness.
4. Leer y escribir `if`/`elif`/`else`, `for`, `while`, `range`, `break` y `continue`.
5. Manipular cadenas con operaciones básicas, f-strings, índices y slicing inicial.
6. Manejar excepciones esperables sin ocultar fallos inesperados.
7. Explicar imports y `if __name__ == "__main__":`.
8. Escribir pruebas iniciales con un único framework: `unittest`.
9. Resolver una variante nueva y justificar el razonamiento.

## 4. Alcance y límites curriculares

**Incluido:** nombres y objetos; asignación, referencias, identidad, mutabilidad y aliasing; `None`, `bool`, `int`, `float`, `str`; conversiones, operadores y truthiness; condicionales y bucles; cadenas y slicing; excepciones básicas; imports y punto de entrada; pruebas iniciales con `unittest`.

**Reservado para otros módulos:**

- **M02:** estudio sistemático de `list`, `tuple`, `dict`, `set`, comprensiones, desempaquetado, iteradores, generadores, `yield`, hashabilidad y copias. Una lista aparece aquí solo como ejemplo mínimo de aliasing, no como lección de colecciones.
- **M03:** diseño avanzado de funciones, argumentos especiales, closures, decoradores, anotaciones de tipos, diseño de errores, clases y organización avanzada de módulos.
- **M04:** archivos, `pathlib`, JSON/CSV, CLI, `argparse` y `logging`.
- **M05:** entornos reproducibles, dependencias, `pyproject.toml`, formatters, linters, cobertura y CI.
- **M06:** protocolos, clases y diseño avanzado, depuración y perfilado.
- **M07:** HTTP y persistencia.
- **M08:** `asyncio`, hilos, procesos y concurrencia.
- `match` es opcional si los fundamentos ya están firmes; no es requisito de aprobación.

## 5. Secuencia y tiempo estimado

Estimación orientativa: 10–15 horas, ajustable a la evidencia. El plan global de referencia es 15 horas semanales. El avance depende del dominio demostrado, no de terminar en una fecha fija.

| Clase | Contenido | Tiempo | Evidencia |
|---|---|---:|---|
| 1 | Nombres, objetos, asignación, identidad y mutabilidad | 2 h | Predicciones justificadas y caso de aliasing |
| 2 | Tipos básicos, conversiones, operadores y truthiness | 1.5–2 h | Predicciones y programa corto |
| 3 | Condicionales y bucles | 2 h | Trazado y variante nueva |
| 4 | Cadenas, f-strings, slicing y excepciones | 2 h | Transformación de texto en memoria |
| 5 | Imports y punto de entrada | 1–1.5 h | Módulo importable sin ejecución accidental |
| 6 | Primeras pruebas con `unittest` | 1.5–2 h | Pruebas que detectan un defecto |
| Integración | Proyecto y checkpoint independiente | 1–3 h | Código, pruebas y explicación |

---

# 6. Clases

Las lecciones se mantienen en archivos separados con el ID y el título curricular de cada clase. El estado de cada material se indica en su encabezado.

- [M01-C01 — Nombres, objetos, asignación, identidad y mutabilidad](<M01-C01 - Nombres, objetos, asignación, identidad y mutabilidad.md>)
- [M01-C02 — Tipos básicos, conversiones, operadores y truthiness](<M01-C02 - Tipos básicos, conversiones, operadores y truthiness.md>)
- [M01-C03 — Condicionales y bucles](<M01-C03 - Condicionales y bucles.md>)
- [M01-C04 — Cadenas, f-strings, slicing y excepciones](<M01-C04 - Cadenas, f-strings, slicing y excepciones.md>)
- [M01-C05 — Imports y punto de entrada](<M01-C05 - Imports y punto de entrada.md>)
- [M01-C06 — Primeras pruebas con `unittest`](<M01-C06 - Primeras pruebas con unittest.md>)

# 7. Proyecto integrador — Analizador de texto en memoria

Este proyecto inicia P01, que continuará entre M01 y M04. **En M01 el texto se recibe como una cadena; no se leen archivos ni se construye una CLI.** Esas partes se incorporarán en M04.

## Requisitos

El programa recibe una cadena y produce un informe con:

- cantidad total de caracteres;
- cantidad de caracteres que no son espacios en blanco;
- primera y última letra no blanca, si existen;
- versión normalizada de los espacios;
- tratamiento explícito de una entrada vacía o compuesta solo por espacios.

El estudiante documentará las reglas de conteo. Para esta versión, cada elemento de la cadena cuenta como carácter y el segundo conteo excluye caracteres para los que `str.isspace()` devuelve `True`. Se incluyen saltos de línea en el conteo total.

## Restricciones didácticas

- Resolver primero con cadenas, condiciones y bucles.
- No usar comprensiones, generadores ni estructuras avanzadas de colecciones (M02).
- Separar la lógica de la ejecución principal.
- Añadir pruebas con `unittest`.
- No añadir archivos de entrada, `argparse`, dependencias externas, HTTP ni persistencia.

## Criterios de aceptación

- [ ] El resultado cumple las reglas documentadas.
- [ ] Se manejan cadenas vacías y espacios al inicio/final.
- [ ] La cadena original no se modifica.
- [ ] Hay pruebas para un caso normal y casos límite.
- [ ] Importar el módulo no ejecuta la demostración.
- [ ] El estudiante explica decisiones, flujo de control y casos límite.

## Evidencia en el repositorio

- `text_tools.py` (o nombre acordado).
- `test_text_tools.py`.
- `README.md` breve con reglas, comando de ejecución y ejemplos.
- Nota corta con decisiones y casos límite.

No exigir estructura de paquete, metadatos ni tooling de M05.

---

# 8. Evaluación y condiciones de cierre

## Checkpoint individual

Sin consultar soluciones, el estudiante debe:

1. Predecir la salida de código que combine aliasing y reasignación.
2. Distinguir `==` e `is`, y justificar un uso válido de `is`.
3. Explicar la truthiness de `0`, `""`, `"0"` y `None`.
4. Trazar un bucle con `range` y `continue` o `break`.
5. Predecir un slice y explicar una excepción de conversión.
6. Explicar el guard de punto de entrada.
7. Añadir una prueba para un caso nuevo.

## Rúbrica

Registrar cada dimensión como `PENDIENTE`, `CON APOYO` o `VALIDADO`:

- Corrección y ejecución.
- Explicación del razonamiento.
- Casos límite.
- Pruebas pertinentes, incluida una que detecte un defecto real.
- Resolución independiente de una variante.
- Legibilidad.

`VALIDADO` solo se asigna después de demostrar la habilidad en una tarea independiente. Si persisten brechas críticas en referencias/mutabilidad, conversiones o flujo de control, se refuerzan antes de avanzar.

## Protocolo de tutoría

- Trabajar una actividad a la vez y esperar la respuesta antes de presentar la siguiente.
- Pedir predicción y razonamiento antes de ejecutar cuando se evalúe lectura de código.
- No revelar la solución antes del intento. Si hay error, ofrecer una pista concreta y permitir otra tentativa.
- Después del intento, explicar la semántica y mostrar una corrección cuando sea útil.
- Separar desconocimiento de sintaxis de desconocimiento conceptual.
- Usar Java, Kotlin, Go o C++ solo para contrastar una diferencia relevante.
- Registrar brechas, evidencia y estado.
- No afirmar que un comando o test fue ejecutado si no existe evidencia de ejecución.
- Al terminar cada clase, resumir dominio demostrado, errores a reforzar, evidencia y siguiente actividad.

## Registro del progreso individual

El progreso del estudiante se registra únicamente en [`COURSE_STATE.md`](../../COURSE_STATE.md).

---

# 9. Revisión de consistencia

- Alineado con M01 de `LEARNING_PATH.md`: semántica, tipos, flujo de control, cadenas, excepciones, imports y pruebas iniciales.
- M02 conserva colecciones, comprensiones, iteración avanzada y copias; la lista aparece solo en un ejemplo mínimo de aliasing.
- M03 conserva funciones avanzadas, diseño de errores, clases y organización avanzada de módulos.
- M04 conserva archivos, CLI y biblioteca estándar aplicada; el proyecto de M01 trabaja solo con una cadena en memoria.
- No se incorporan tooling profesional, HTTP, persistencia ni concurrencia de M05–M08.
- Se eligió `unittest` como único framework inicial.
- Las fuentes de cada clase se registran según `GUIA_DE_CLASES.md`; no se asignan páginas o capítulos que no se hayan cotejado.
- Los resultados esperados de los ejemplos de código se comprobaron mediante ejecución de fragmentos equivalentes. Esto no verifica automáticamente todo el proyecto final ni sustituye las pruebas que deberá escribir el estudiante.

**Estado del material:** preparado para tutoría. Las habilidades del estudiante siguen pendientes de evaluación.