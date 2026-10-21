---
course_id: PYDEV-001
module_id: M01
class_id: M01-C01
artifact_type: class_material
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01-C01 — Nombres, objetos, asignación, identidad y mutabilidad

### Objetivos

- Entender que un nombre se vincula a un objeto.
- Distinguir reasignación de mutación.
- Predecir cuándo dos nombres se refieren al mismo objeto.
- Diferenciar igualdad e identidad.

### Explicación

`x = 10` vincula el nombre `x` con un objeto entero. Después, `x = 20` vuelve a vincular el nombre; no transforma el objeto entero `10`.

Si dos nombres se refieren al mismo objeto mutable, una mutación de ese objeto puede observarse a través de ambos nombres: esto se denomina *aliasing*.

`==` comprueba igualdad según la operación de comparación del tipo. `is` comprueba identidad: si se trata del mismo objeto. No uses `is` como sustituto general de `==`. Un caso habitual de identidad es `value is None`.

### Ejemplo

```python
first = [1, 2]
second = first
second.append(3)

print(first)
print(second)
print(first is second)
print(first == second)
```

Salida:

```text
[1, 2, 3]
[1, 2, 3]
True
True
```

La asignación `second = first` no crea otra lista; ambos nombres se refieren al mismo objeto.

Contraste:

```python
x = 10
y = x
x = 20
print(x, y)
```

Salida:

```text
20 10
```

La reasignación de `x` no cambia el vínculo de `y`.

### Ejercicios

1. Antes de ejecutar el primer ejemplo, predice cada salida y explica por qué.
2. Cambia una sola línea y vuelve a predecir.
3. Resuelve un caso nuevo que combine aliasing y reasignación.
4. Explica si cambió el objeto, el vínculo de un nombre o ambos.

**Criterio de salida:** explicar correctamente un caso nuevo de aliasing y otro de reasignación, distinguiendo identidad e igualdad.
