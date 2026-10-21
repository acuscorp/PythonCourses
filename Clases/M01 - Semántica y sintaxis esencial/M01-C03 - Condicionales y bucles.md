---
course_id: PYDEV-001
module_id: M01
class_id: M01-C03
artifact_type: class_material
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01-C03 — Condicionales y bucles

### Objetivos

- Escribir condiciones con `if`, `elif` y `else`.
- Trazar un `for` o `while` paso a paso.
- Comprender que el límite final de `range` no se incluye.
- Explicar `break` y `continue`.

### Explicación

`if` selecciona una rama. `for` recorre elementos; en esta clase se trabajará principalmente con `range` y cadenas. `while` repite mientras su condición sea verdadera.

`range(start, stop, step)` produce enteros desde `start` y se detiene antes de `stop`. `break` termina el bucle más cercano; `continue` pasa a la siguiente iteración.

### Ejemplo

```python
total = 0

for number in range(1, 5):
    if number == 3:
        continue
    total += number

print(total)
```

Salida: `7`, porque se suman `1`, `2` y `4`.

### Ejercicios

1. Traza los valores de las variables en cada iteración.
2. Cambia los límites de `range` y predice cuántas iteraciones ocurren.
3. Resuelve un problema breve con una condición y un acumulador numérico.
4. Encuentra y corrige un `while` que no termina.
5. Explica un caso límite.

**Criterio de salida:** resolver una variante nueva con condición y bucle, y explicar sus casos límite.
