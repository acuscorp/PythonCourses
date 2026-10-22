---
course_id: PYDEV-001
artifact_id: M02-C01
artifact_type: class
status: DRAFT
version: 2
language: es
module_id: M02
class_id: M02-C01
competencies:
  - PYDEV-001-C01
  - PYDEV-001-C02
prerequisites:
  - M01 or equivalent evidence
---

# M02-C01 — `list`, `tuple`, `dict` y `set`: selección y semántica

## 1. Objetivo observable

Al terminar la clase, podrás **seleccionar y justificar** entre `list`, `tuple`, `dict` y `set` para un requisito nuevo, considerando:

- si importa conservar el orden;
- si se permiten duplicados;
- cómo se consultan los datos;
- si la colección debe poder modificarse;
- si necesitas representar una secuencia, una relación clave-valor o un conjunto de elementos únicos.

El objetivo no es memorizar cuatro definiciones: es convertir requisitos en una decisión técnica y explicar los trade-offs.

## 2. Prerrequisitos y alcance

**Prerrequisitos:** fundamentos de M01 o evidencia equivalente: nombres y objetos, asignación, mutabilidad, tipos básicos, condiciones y bucles. Si aliasing o mutabilidad todavía resultan confusos, conviene repasarlos antes de interpretar los ejemplos.

**Incluye:** comportamiento observable, creación, acceso, pertenencia, orden, duplicados, mutabilidad, usos típicos y costes prácticos aproximados de operaciones comunes.

**No incluye en profundidad:** slicing y desempaquetado avanzado (M02-C02), comprensiones y herramientas de iteración (M02-C03), el protocolo de iteración y generadores (M02-C04), ni hashabilidad, copias y análisis de complejidad más detallado (M02-C05). Se mencionarán únicamente cuando sea necesario para explicar una decisión.

## 3. Fuentes consultadas y límites

1. **Python Software Foundation, Tutorial oficial de Python, sección 5 — Estructuras de datos.** Consultado para las operaciones básicas de listas, tuplas, conjuntos y diccionarios: https://docs.python.org/es/3/tutorial/datastructures.html
2. **Python Software Foundation, documentación de tipos integrados.** Consultada para contrastar la semántica de secuencias, mapeos, conjuntos y mutabilidad: https://docs.python.org/3/library/stdtypes.html
3. **Fluent Python, 2.ª edición**, capítulos 2 y 3. Se consultaron los extractos públicos del editor:
   - Capítulo 2, *An Array of Sequences*: https://www.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch02.html
   - Capítulo 3, *Dictionaries and Sets*: https://www.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch03.html
4. **The Quick Python Book, 3.ª edición**, capítulos 5 y 7. Se consultó el extracto público del capítulo 5 y el índice editorial:
   - Capítulo 5, *Lists, tuples, and sets*: https://livebook.manning.com/book/the-quick-python-book-third-edition/chapter-5
   - Índice editorial: https://livebook.manning.com/book/the-quick-python-book-third-edition/table-of-contents

**Trazabilidad:** se consultaron directamente las dos páginas oficiales de Python y extractos públicos de los capítulos 2 y 3 de *Fluent Python* y del capítulo 5 de *The Quick Python Book*. También se verificaron los títulos y el alcance general de los capítulos en los índices editoriales. No se tuvo acceso al texto completo de todos los capítulos asignados, en particular al capítulo 7 de *The Quick Python Book*; por tanto, no se afirma una lectura completa ni se atribuyen a ese capítulo explicaciones específicas sin verificar. Los escenarios y ejercicios son ejemplos didácticos elaborados para esta clase, no citas de las fuentes.


## 4. Conceptos y explicación

### 4.1 Primero decide qué representa tu dato

Imagina que desarrollas una aplicación que procesa pedidos. Necesitas guardar:

- los productos de un pedido en el orden en que se agregaron;
- las coordenadas de una ubicación;
- el precio de cada producto identificado por su código;
- los códigos de producto que aparecen en un lote, sin repetirlos.

Todos son datos, pero **no representan la misma clase de problema**. Elegir una colección por costumbre puede complicar el código o introducir errores. La estructura debe expresar la intención.

Las cuatro opciones se pueden resumir así:

| Tipo | Modelo mental | Orden observable | Duplicados | Modificable |
| --- | --- | --- | --- | --- |
| `list` | Secuencia de elementos | Sí, conserva posiciones | Sí | Sí |
| `tuple` | Secuencia fija de elementos | Sí, conserva posiciones | Sí | No se pueden reasignar sus posiciones |
| `dict` | Claves asociadas a valores | Conserva orden de inserción | Las claves son únicas; los valores pueden repetirse | Sí |
| `set` | Conjunto de elementos únicos | No ofrece orden posicional | No | Sí |

Los diccionarios conservan el orden de inserción como parte del comportamiento del lenguaje desde Python 3.7. Eso no los convierte en secuencias indexadas por posición: se consulta una entrada mediante su clave. Un conjunto no ofrece orden posicional y no debe utilizarse cuando la lógica dependa de la posición o del orden de aparición.

### 4.2 `list`: una secuencia que cambia

Una lista sirve cuando necesitas conservar una colección ordenada por posición, permitir duplicados y modificar su contenido. «Ordenada» aquí significa que las posiciones están definidas y se conservan; no significa que Python ordene automáticamente los valores de menor a mayor.

~~~python
productos = ["café", "té", "café"]

productos.append("pan")

print(productos)
print(productos[0])
print("té" in productos)
~~~

Resultado esperado:

~~~text
['café', 'té', 'café', 'pan']
café
True
~~~

**Cómo razonar sobre el ejemplo:**

- Cada elemento ocupa una posición, comenzando en el índice `0`.
- Los dos valores `"café"` se conservan porque los duplicados están permitidos.
- `append` agrega un elemento al final y modifica la lista existente.
- La expresión `"té" in productos` pregunta si hay un elemento igual a ese valor.

**Elige una lista cuando** el orden y las posiciones importen, necesites recorrer los elementos en secuencia o el contenido deba crecer, reducirse o cambiar.

Ejemplos: líneas de un archivo, pasos de un flujo, resultados en orden de llegada o artículos de un carrito.

**No asumas que** una lista representa automáticamente una colección de elementos únicos. Si necesitas unicidad, tendrás que imponerla mediante lógica adicional o elegir otra estructura.

### 4.3 `tuple`: una secuencia que no permite reasignar sus posiciones

Una tupla también mantiene posiciones y admite duplicados, pero no permite reemplazar, agregar o quitar elementos mediante las operaciones normales de modificación de la secuencia.

~~~python
coordenadas = (19.70, -101.19)

latitud = coordenadas[0]
longitud = coordenadas[1]

print(latitud, longitud)
~~~

Resultado esperado:

~~~text
19.7 -101.19
~~~

**¿Por qué usar una tupla en vez de una lista?** Cuando el conjunto de posiciones representa un valor compuesto que debe permanecer fijo, como un par de coordenadas o un registro pequeño de valores relacionados. La tupla comunica que no se espera modificar su estructura.

La inmutabilidad tiene un límite importante: **la tupla no permite reasignar sus elementos, pero puede contener referencias a objetos mutables**. Por ejemplo:

~~~python
registro = ("pedido-17", ["pendiente", "pagado"])
registro[1].append("enviado")

print(registro)
~~~

La lista interna puede cambiar aunque la tupla no permita asignar otro objeto a `registro[1]`. La inmutabilidad de la tupla no vuelve recursivamente inmutables todos los objetos que contiene.

Una tupla de un solo elemento requiere una coma:

~~~python
uno = ("solo",)
no_es_tupla = ("solo")

print(type(uno).__name__)
print(type(no_es_tupla).__name__)
~~~

Resultado esperado:

~~~text
tuple
str
~~~

Los paréntesis por sí solos no crean la tupla de un elemento; la coma es lo decisivo.

**Elige una tupla cuando** tengas una secuencia de tamaño fijo cuyo orden y posiciones tengan significado. No la elijas solo porque parezca más profesional o porque asumas que siempre será más rápida.

### 4.4 `dict`: buscar un valor mediante una clave

Un diccionario representa asociaciones entre claves y valores. En lugar de preguntar «¿qué hay en la posición 2?», preguntas «¿qué valor corresponde a esta clave?».

~~~python
precios = {
    "café": 45,
    "té": 30,
    "pan": 18,
}

print(precios["té"])
precios["té"] = 32
precios["jugo"] = 25

print(precios)
~~~

Resultado esperado:

~~~text
30
{'café': 45, 'té': 32, 'pan': 18, 'jugo': 25}
~~~

**Cómo funciona:**

- Cada clave identifica como máximo una entrada dentro del diccionario.
- Asignar un valor a una clave existente reemplaza el valor asociado; no crea una segunda entrada con esa misma clave.
- Asignar un valor a una clave nueva agrega una entrada.
- Los valores sí pueden repetirse.
- En un diccionario moderno de Python, la iteración sigue el orden de inserción, pero el acceso normal se realiza mediante claves, no por posición.

Para consultar una clave que podría no existir, decide qué comportamiento quieres:

~~~python
precios = {"café": 45}

print(precios.get("agua"))
print(precios.get("agua", 0))
~~~

Resultado esperado:

~~~text
None
0
~~~

En cambio, `precios["agua"]` lanza `KeyError` porque la clave no existe. Usa acceso directo cuando la ausencia de la clave deba tratarse como un error; usa `get` cuando quieras proporcionar un valor alternativo.

**Elige un diccionario cuando** debas recuperar datos por un identificador: precio por código de producto, configuración por nombre, usuario por ID o conteo por categoría.

La expresión `clave in precios` comprueba si la clave existe; no busca entre los valores. Por ejemplo, `32 in precios` es falso aunque 32 sea uno de los precios, mientras que `"té" in precios` es verdadero.

Las claves de un diccionario y los elementos de un conjunto deben ser hashables. Para esta clase basta con una regla práctica: cadenas e enteros suelen funcionar; una lista no puede usarse directamente como clave ni como elemento de un conjunto. Las reglas y excepciones de hashabilidad se estudiarán con más detalle en M02-C05.

### 4.5 `set`: pertenencia y unicidad

Un conjunto guarda elementos únicos. Resulta útil cuando la pregunta principal es si un elemento pertenece a una colección o cuando necesitas eliminar duplicados.

~~~python
codigos = {"A12", "B07", "A12", "C33"}

print(len(codigos))
print("B07" in codigos)
codigos.add("D21")
print(len(codigos))
~~~

Salida:

~~~text
3
True
4
~~~

Aunque el literal contiene cuatro apariciones, el conjunto conserva solo tres elementos distintos. Al agregar "D21", su tamaño pasa a cuatro. Evitamos imprimir el conjunto completo porque el orden de su representación no es parte del contrato; la pertenencia y el tamaño son las propiedades relevantes para este ejemplo.

Las operaciones de conjuntos expresan relaciones entre grupos:

~~~python
web = {"Ana", "Luis", "Marta"}
movil = {"Luis", "Marta", "Noé"}

print(web & movil)   # presentes en ambos
print(web | movil)   # presentes en uno u otro
print(web - movil)   # presentes en web, pero no en movil
~~~

Resultados semánticos:

- Intersección (`&`): Ana no aparece; Luis y Marta sí aparecen en ambos.
- Unión (`|`): incluye Ana, Luis, Marta y Noé.
- Diferencia (`-`): contiene Ana.

El orden concreto al imprimir cada conjunto no es parte del contrato.

Para crear un conjunto vacío, utiliza `set()`, no `{}`: las llaves vacías crean un diccionario vacío. Puedes comprobar la diferencia con `type(set()).__name__` y `type({}).__name__`, que producen `"set"` y `"dict"`, respectivamente.

**Elige un conjunto cuando** la unicidad y las pruebas de pertenencia sean centrales: permisos disponibles, etiquetas únicas, IDs ya procesados o elementos compartidos por dos grupos.

### 4.6 Comparar las estructuras desde los requisitos

Supongamos que recibes esta petición:

> Procesar los nombres de archivos en el orden recibido, conservar todas las apariciones y permitir agregar archivos al final.

La elección natural es una `list`: el orden importa, los duplicados pueden ser significativos y el contenido cambia.

Ahora cambia el requisito:

> Registrar si cada nombre de archivo ya fue procesado; no necesitamos el orden.

Un `set` expresa mejor la unicidad y la pertenencia. Si además necesitas conservar el orden de procesamiento, una lista puede ser necesaria; si necesitas consultar un estado o resultado por nombre, un diccionario puede representar esa relación.

La elección no depende solo del tipo de dato disponible. Depende de las operaciones que el programa debe realizar.

### 4.7 Coste práctico: qué operación importa

Como orientación general, las listas ofrecen acceso por índice eficiente; buscar un valor mediante `in` normalmente requiere recorrer elementos. Los diccionarios y conjuntos suelen ofrecer búsquedas por clave o pertenencia eficientes en promedio, gracias a tablas hash. Estas son expectativas prácticas, no garantías de tiempo constante para todos los casos.

| Operación principal | Estructura que conviene evaluar primero |
| --- | --- |
| Acceder a un elemento por posición | `list` o `tuple` |
| Agregar elementos conservando una secuencia | `list` |
| Recuperar un valor por identificador | `dict` |
| Verificar pertenencia sin duplicados | `set` |
| Representar un pequeño registro fijo | `tuple` |

No hace falta elegir la estructura supuestamente más rápida antes de entender el requisito. Empieza por la semántica correcta; mide el rendimiento cuando el volumen o el perfil de ejecución hagan que esa decisión importe. El análisis detallado de complejidad se profundizará en M02-C05.

### 4.8 Un procedimiento de decisión reutilizable

Cuando recibas un requisito nuevo, toma la decisión en este orden:

1. **¿Necesitas consultar por identificador?** Evalúa primero un `dict` si cada clave debe apuntar a un valor o estado actual.
2. **¿Necesitas unicidad o comprobar pertenencia?** Evalúa un `set` si no necesitas posiciones ni duplicados.
3. **¿Necesitas una secuencia con posiciones?** Elige entre `list` y `tuple`: usa `list` si la colección debe cambiar; usa `tuple` si las posiciones del registro deben permanecer fijas.
4. **¿Qué información se perdería con otra opción?** Comprueba si eliminar duplicados, cambiar el orden de representación o perder una asociación clave-valor rompería el requisito.
5. **¿Qué operación será habitual?** Si varias estructuras cumplen la semántica, compara las operaciones que el programa hará con más frecuencia.

No es un algoritmo que siempre produzca una única respuesta. A veces dos estructuras cumplen funciones complementarias: una lista conserva el historial de eventos y un conjunto registra cuáles IDs ya aparecieron. En ese caso no duplican inútilmente el modelo; conservan información distinta para consultas distintas.

## 5. Ejemplos resueltos

### Ejemplo A — Historial de eventos

**Requisito:** guardar eventos en el orden en que llegan; dos eventos con el mismo texto pueden ser dos sucesos distintos.

**Decisión:** `list`.

~~~python
eventos = ["inicio", "conexión", "conexión", "cierre"]
print(len(eventos))
~~~

Resultado: `4`. Quitar duplicados cambiaría la información: dos conexiones podrían representar dos sucesos diferentes.

### Ejemplo B — Precio actual por SKU

**Requisito:** consultar el precio actual de un producto mediante su SKU y actualizarlo cuando cambie.

**Decisión:** `dict`.

~~~python
precios = {"SKU-10": 100, "SKU-20": 250}
precios["SKU-10"] = 110
print(precios["SKU-10"])
~~~

Resultado: `110`. La clave identifica la entrada y la asignación actualiza su valor.

### Ejemplo C — Etiquetas únicas

**Requisito:** combinar etiquetas de dos fuentes sin conservar repeticiones y obtener las etiquetas comunes.

**Decisión:** `set`.

~~~python
a = {"python", "backend", "testing"}
b = {"backend", "testing", "linux"}
print(a & b)
~~~

El resultado contiene `"backend"` y `"testing"`; no se debe exigir un orden específico al imprimirlo.

### Ejemplo D — Par de valores que viajan juntos

**Requisito:** representar una coordenada como latitud y longitud, sin permitir reasignar accidentalmente cada posición.

**Decisión:** `tuple`.

~~~python
punto = (19.70, -101.19)
latitud, longitud = punto
~~~

La tupla mantiene las dos posiciones y permite desempaquetarlas. La técnica de desempaquetado se desarrollará en M02-C02.

## 6. Comprobación de comprensión

Antes de seguir, responde sin ejecutar el código.

~~~python
a = ["rojo", "azul", "rojo"]
b = {"rojo", "azul", "rojo"}
c = {"rojo": 1, "azul": 2, "rojo": 3}
~~~

1. ¿Cuántos elementos contiene cada estructura?
2. ¿Qué valor queda asociado a la clave `"rojo"` en `c`?
3. ¿Cuál de las tres estructuras conserva dos apariciones de `"rojo"`?
4. ¿Qué comprueba `"rojo" in c`: si aparece como clave o si aparece como valor?
5. Explica por qué el conjunto no es apropiado si necesitamos saber en qué posición apareció cada color.

**Respuestas para autocorrección:** `a` contiene 3 elementos, `b` contiene 2 y `c` contiene 2 claves. En `c["rojo"]` queda el valor `3`, porque la segunda asignación a esa clave reemplaza la anterior. La lista conserva las dos apariciones de `"rojo"`. La expresión `"rojo" in c` comprueba las claves del diccionario y devuelve `True`; no comprueba sus valores.

**Criterio:** no basta con enumerar resultados; explica la regla de la estructura que produce cada resultado.

## 7. Práctica guiada

Un servicio procesa los IDs de pedidos recibidos, guarda el estado actual de cada pedido y mantiene una coordenada de entrega.

Requisitos:

- conservar el orden de llegada de todos los pedidos, incluidos los IDs repetidos;
- recuperar el estado actual de un pedido mediante su ID;
- saber rápidamente si un ID ya fue visto, sin importar el orden;
- representar latitud y longitud como un par fijo.

### Paso 1

Asigna a cada requisito una estructura entre `list`, `tuple`, `dict` y `set`. Puedes usar más de una estructura para los mismos datos si cumplen propósitos diferentes.

### Paso 2

Para cada elección, explica qué requisito resuelve y qué propiedad de las otras estructuras la haría menos adecuada.

### Paso 3

Revisa tu propuesta: ¿el conjunto de IDs vistos reemplaza a la lista de llegadas o ambos conservan información distinta? ¿Qué estructura debe utilizarse para recuperar el estado por ID?

**Pista:** piensa por separado en historial, consulta por clave, pertenencia y par fijo. No escribas una solución completa hasta que la decisión semántica esté clara.

**Comprueba tu decisión después de intentarlo:**

~~~python
llegadas = ["P-17", "P-18", "P-17"]
estado_por_id = {"P-17": "en preparación", "P-18": "enviado"}
ids_vistos = {"P-17", "P-18"}
coordenada_entrega = (19.70, -101.19)

print(llegadas)
print(estado_por_id["P-17"])
print("P-18" in ids_vistos)
print(coordenada_entrega)
~~~

Salida esperada:

~~~text
['P-17', 'P-18', 'P-17']
en preparación
True
(19.7, -101.19)
~~~

La lista conserva las tres llegadas, incluido el ID repetido. El diccionario permite consultar el estado actual mediante el ID. El conjunto responde si un ID ya fue visto sin guardar duplicados. La tupla expresa un par fijo de coordenadas. En una aplicación real, podrías mantener tanto la lista como el conjunto porque responden preguntas distintas.

## 8. Práctica independiente y transferencia

Diseña una representación para un sistema sencillo de inventario con estos requisitos:

1. conservar los movimientos de inventario en orden, incluidos movimientos repetidos;
2. recuperar la cantidad actual por código de producto;
3. obtener los códigos distintos que aparecen en un archivo importado;
4. representar una versión fija de un producto con nombre y categoría para mostrarla en un reporte.

Entrega:

- la estructura elegida para cada requisito;
- un fragmento de código breve que cree las estructuras;
- un ejemplo de consulta o modificación;
- dos casos límite y el comportamiento esperado;
- una justificación de por qué no elegiste la alternativa más tentadora.

No es necesario construir una aplicación completa. Se evalúa el razonamiento sobre las colecciones, no el tamaño del código.

## 9. Errores previsibles y remediación

| Confusión | Por qué falla | Remediación |
| --- | --- | --- |
| Elegir `set` y luego depender del orden | Un conjunto no ofrece posiciones ni orden de iteración contractual | Si el orden importa, modela una secuencia; vuelve a explicar qué información se perdería al quitar duplicados |
| Elegir `list` para buscar repetidamente por una clave | La búsqueda por valor suele recorrer la lista y no expresa una relación clave-valor | Usa un `dict` si cada identificador corresponde a un valor; comprueba con un ejemplo de actualización |
| Creer que `tuple` hace inmutable todo lo que contiene | Los objetos mutables internos pueden cambiar | Distingue entre reasignar una posición de la tupla y mutar un objeto referenciado; predice ambos casos |
| Suponer que un diccionario puede tener claves duplicadas | Una nueva asignación a la misma clave reemplaza el valor anterior | Ejecuta mentalmente dos asignaciones a la misma clave y explica cuál es el valor final |
| Crear `{}` pensando que es un conjunto vacío | En Python, `{}` crea un diccionario vacío | Usa `set()` para el conjunto vacío; comprueba los tipos con `type(...).__name__` |
| Tratar el orden de un conjunto como estable | La representación impresa no define el orden de los elementos | Compara pertenencia y contenido, no la secuencia textual impresa |

Si aparece una confusión, vuelve al requisito que define la colección, usa el ejemplo mínimo de la tabla y responde otra vez con un caso distinto. No pases a una práctica independiente si todavía no puedes explicar la diferencia relevante.

## 10. Evidencia y criterio de éxito

**Evidencia revisable:** la solución de la práctica independiente, con código y justificaciones escritas.

Se considera que el objetivo de esta clase está demostrado cuando la evidencia:

1. selecciona estructuras adecuadas para los cuatro requisitos;
2. justifica orden, duplicación, acceso y mutabilidad de manera correcta;
3. distingue acceso por posición de acceso por clave;
4. identifica al menos un caso límite relevante;
5. predice el comportamiento de una modificación o consulta sin depender de ensayo y error.

Una respuesta parcialmente correcta sirve para identificar qué concepto repasar. Completar la actividad o leer la clase no valida por sí solo una competencia global ni significa que todo el módulo esté dominado.

## 11. Cierre y siguiente paso

Recupera la idea central: **elige la colección según la información que necesitas conservar y las operaciones que el programa debe expresar**.

- `list`: secuencia mutable con posiciones y duplicados.
- `tuple`: secuencia cuyas posiciones no se reasignan.
- `dict`: relación de claves únicas con valores.
- `set`: colección de elementos únicos orientada a pertenencia y operaciones de conjuntos.

La siguiente clase, M02-C02 — *Slicing, desempaquetado y operaciones de secuencia*, profundizará en cómo extraer, reorganizar y desempaquetar secuencias. No necesitas dominar esos temas para justificar las decisiones de esta clase.

## 12. Revisión del material

| Criterio | Resultado | Justificación |
| --- | --- | --- |
| ID, título, objetivo y prerrequisitos alineados con la ruta | PASS | Se conservan el ID y título curricular; el objetivo se centra en seleccionar estructuras según los requisitos. |
| Límites curriculares | PASS | Se reservan slicing, comprensiones, protocolo de iteración, hashabilidad profunda, copias y complejidad detallada para clases posteriores. |
| Fuentes rastreables y honestidad de acceso | PASS | Se registran los extractos editoriales consultados, las páginas oficiales y el límite de acceso al capítulo 7 de The Quick Python Book. |
| Explicaciones y ejemplos resueltos | PASS | Cada estructura tiene semántica, ejemplo y guía de selección; se aclara que `in` en diccionarios comprueba claves. |
| Comprobación, práctica guiada e independiente | PASS | La predicción conceptual incluye autocorrección; la práctica guiada muestra una solución razonada tras la pista. |
| Errores previsibles y remediación | PASS | Se explican confusiones frecuentes y se propone una comprobación alternativa. |
| Ejemplos deterministas ejecutados | PASS | Se ejecutaron los ejemplos principales y la comprobación conceptual en un intérprete Python; las aserciones y el caso de `KeyError` pasaron. |
| Lectura completa de los capítulos asignados | FIX | Se revisaron extractos editoriales de tres capítulos, pero no el texto completo de todos los capítulos asignados; falta consultar directamente el capítulo 7 de The Quick Python Book y completar el cotejo. |
| Aprobación académica del material | NOT APPLICABLE | La revisión técnica del borrador no equivale a aprobación curricular ni demuestra aprendizaje del estudiante. |

**Resultado de aceptación:** `DRAFT`. La estructura didáctica, el alcance y los ejemplos principales pasan la revisión actual. Se conserva `DRAFT` porque falta consultar directamente el texto completo de todos los capítulos asignados —en particular el capítulo 7 de The Quick Python Book— y completar el cotejo bibliográfico antes de la aprobación académica. La clase no está marcada `READY`.
