---
course_id: PYDEV-001
module_id: M01
class_id: M01-C02
artifact_type: class_material
language: es
status: DRAFT_FOR_TUTOR_USE
---

# M01-C02 — Tipos básicos, conversiones, operadores y truthiness

**Estado del desarrollo:** esta sección conserva el esquema de la clase y un ejemplo breve. La lección detallada está pendiente de elaboración; no hay un archivo independiente que enlazar.

### Objetivos

- Explicar tipado dinámico sin confundirlo con ausencia de tipos.
- Reconocer `None`, `bool`, `int`, `float` y `str`.
- Predecir conversiones y distinguir errores `ValueError` y `TypeError`.
- Evaluar operadores aritméticos, comparaciones, precedencia, truthiness y cortocircuito.
- Distinguir `if value:` de `if value is None:`.

### Ejemplo breve

```python
value = "12"
number = int(value)
print(type(value).__name__)
print(type(number).__name__)
print(number + 3)
print(bool(""))
print(bool("0"))
```

Salida: `str`, `int`, `15`, `False`, `True`. Este ejemplo es introductorio; la explicación detallada y la práctica completa siguen pendientes.

### Práctica y criterio de salida

Práctica adaptativa de una pregunta por turno, con opciones, justificación obligatoria y envío explícito. Evaluar tipos/conversiones, operadores y truthiness en ejemplos nuevos; no avanzar solo por acertar opciones sin poder justificar. Registrar evidencia en `COURSE_STATE.md` después de la sesión, no antes.
