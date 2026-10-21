---
course_id: PYDEV-001
module_id: M01
class_id: M01-C04
artifact_type: class_material
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01-C04 — Cadenas, f-strings, slicing y excepciones

### Objetivos

- Construir cadenas con f-strings.
- Usar operaciones básicas, índices y slicing.
- Entender que las cadenas son inmutables.
- Capturar una excepción esperable de forma específica.

### Ejemplo de cadenas

```python
text = "Python"
print(text[0])
print(text[-1])
print(text[1:4])
print(f"Lenguaje: {text}")
```

Salida:

```text
P
n
yth
Lenguaje: Python
```

El slice incluye el inicio y excluye el límite final. Las cadenas no se modifican por índice; para cambiar el contenido se construye otra cadena.

### Ejemplo de excepción

```python
raw_value = "abc"

try:
    number = int(raw_value)
except ValueError:
    print("La entrada debe ser un entero.")
else:
    print(number)
```

Salida:

```text
La entrada debe ser un entero.
```

`except ValueError` captura el error esperado de conversión. `else` se ejecuta si no hubo excepción en el bloque `try`.

### Ejercicios

1. Predice índices y slices, incluidos los límites.
2. Corrige un intento de modificar una cadena por índice.
3. Formatea una salida con f-string.
4. Maneja `ValueError` sin ocultar otros errores.
5. Explica qué bloque se ejecuta cuando ocurre la excepción.

**Criterio de salida:** transformar una cadena en memoria y manejar una entrada inválida explícitamente.
