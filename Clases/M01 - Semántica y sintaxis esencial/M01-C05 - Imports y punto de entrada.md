---
course_id: PYDEV-001
module_id: M01
class_id: M01-C05
artifact_type: class_material
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01-C05 — Imports y punto de entrada

### Objetivos

- Distinguir `import math` de `from math import sqrt`.
- Entender que las instrucciones de nivel superior se ejecutan al importar un módulo.
- Usar `if __name__ == "__main__":`.

### Ejemplo

Archivo `geometry_demo.py`:

```python
import math

def circle_area(radius):
    return math.pi * radius ** 2

if __name__ == "__main__":
    print(circle_area(2))
```

Al ejecutar el archivo como programa se imprime el área. Al importarlo, se define `circle_area` sin ejecutar ese `print`.

Con `import math`, se usa `math.sqrt(9)`. El nombre `sqrt` no se incorpora directamente al espacio de nombres. Para usarlo directamente habría que ejecutar `from math import sqrt`.

No se estudian ciclos de importación ni diseño avanzado de paquetes; corresponden a módulos posteriores.

### Ejercicios

1. Predice qué nombres están disponibles tras cada forma de importación.
2. Explica por qué `sqrt(9)` no funciona después de `import math`, mientras `math.sqrt(9)` sí.
3. Detecta el efecto secundario de un `print` al nivel superior de un módulo.
4. Separa la lógica de una demostración ejecutable.

**Criterio de salida:** crear un módulo que se pueda importar sin ejecutar la demostración.
