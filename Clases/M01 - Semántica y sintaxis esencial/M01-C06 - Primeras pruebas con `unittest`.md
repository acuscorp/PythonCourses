---
course_id: PYDEV-001
module_id: M01
class_id: M01-C06
artifact_type: class_material
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01-C06 — Primeras pruebas con `unittest`

### Objetivos

- Entender una prueba como una comprobación de comportamiento.
- Escribir pruebas sencillas con `unittest`.
- Observar un fallo, corregir el defecto y explicar la corrección.

Archivo `text_tools.py`:

```python
def normalize_spaces(text):
    return " ".join(text.split())
```

Archivo `test_text_tools.py`:

```python
import unittest
from text_tools import normalize_spaces


class NormalizeSpacesTests(unittest.TestCase):
    def test_collapses_repeated_spaces(self):
        self.assertEqual(normalize_spaces("hola   mundo"), "hola mundo")

    def test_handles_leading_and_trailing_spaces(self):
        self.assertEqual(normalize_spaces("  hola mundo  "), "hola mundo")


if __name__ == "__main__":
    unittest.main()
```

Ejecuta:

```bash
python -m unittest -v
```

Las pruebas comprueban comportamiento observable. No se estudian todavía cobertura, mocks, pruebas de integración ni CI. En esta clase se elige `unittest` como único framework inicial.

### Ejercicios

1. Ejecuta las pruebas y explica qué comprueba cada una.
2. Introduce un defecto pequeño y observa qué prueba falla.
3. Corrige el defecto y vuelve a ejecutar.
4. Añade un caso límite pertinente.
5. Explica por qué una prueba debe comprobar el comportamiento y no limitarse a repetir la implementación.

**Criterio de salida:** crear al menos tres pruebas pertinentes y demostrar que una detecta un defecto real.

---
