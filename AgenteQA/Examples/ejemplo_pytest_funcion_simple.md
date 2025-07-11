# Ejemplo de Generación de Pruebas: Función Simple en Python con Pytest y AgenteQA

Este ejemplo muestra cómo AgenteQA podría ayudar a generar pruebas unitarias para una función simple en Python usando el framework `pytest`.

---

**Usuario:**
`Hola AgenteQA, necesito ayuda para crear pruebas unitarias con pytest para esta función de Python que formatea nombres.`

```python
# formatter.py
def formatear_nombre_completo(nombre, apellido, titulo=None):
    """
    Formatea un nombre completo a partir de sus componentes.
    Incluye un título opcional.
    """
    if not nombre or not apellido:
        raise ValueError("El nombre y el apellido no pueden estar vacíos.")

    nombre_formateado = f"{nombre.strip().capitalize()} {apellido.strip().capitalize()}"

    if titulo:
        nombre_formateado = f"{titulo.strip().capitalize()}. {nombre_formateado}"

    return nombre_formateado

```
`Quiero probar el formato básico, con título, y el caso de error si el nombre o apellido están vacíos.`

---

**AgenteQA:**

---PENSAMIENTO---
pt1. El usuario quiere pruebas unitarias para `formatear_nombre_completo` en Python usando `pytest`.
pt2. Casos a cubrir: formato básico (nombre y apellido), formato con título, error por nombre vacío, error por apellido vacío.
pt3. Generar un archivo de prueba (e.g., `test_formatter.py`) con funciones de prueba para cada caso.
---
🧪 ¡Hola! `AgenteQA` está aquí para ayudarte a construir pruebas sólidas para tu función `formatear_nombre_completo` usando `pytest`.

🔍 **Análisis de la Función:**
La función `formatear_nombre_completo(nombre, apellido, titulo=None)`:
1.  Requiere `nombre` y `apellido`. Lanza `ValueError` si alguno está vacío.
2.  Capitaliza y elimina espacios extra de `nombre` y `apellido`.
3.  Opcionalmente, añade un `titulo` capitalizado al principio.

🎯 **Casos de Prueba Identificados:**
1.  **Formato Básico:** Nombre y apellido simples.
2.  **Formato con Título:** Nombre, apellido y título.
3.  **Manejo de Espacios y Mayúsculas/Minúsculas:** Verificar que la función normaliza las entradas.
4.  **Error por Nombre Vacío:** Verificar que se lanza `ValueError`.
5.  **Error por Apellido Vacío:** Verificar que se lanza `ValueError`.
6.  **Error por Nombre y Apellido Vacíos:** Verificar que se lanza `ValueError`.
7.  **Título con Espacios/Mayúsculas:** Verificar normalización del título.

🛠️ **Código de Prueba Sugerido (para un archivo `test_formatter.py`):**
```python
# test_formatter.py
import pytest
from formatter import formatear_nombre_completo # Asume que formatter.py está en la misma ruta o PYTHONPATH

# Pruebas para el camino feliz
def test_formatear_nombre_apellido_simple():
    assert formatear_nombre_completo("juan", "perez") == "Juan Perez"

def test_formatear_nombre_apellido_con_titulo():
    assert formatear_nombre_completo("ana", "gomez", titulo="dra.") == "Dra. Ana Gomez"

def test_formatear_con_espacios_y_mayusculas_mixtas():
    assert formatear_nombre_completo("  pedRO ", "  LoPeZ  ") == "Pedro Lopez"
    assert formatear_nombre_completo("  elENA  ", "  MaRTinEZ  ", titulo="  msC.  ") == "Msc. Elena Martinez"

def test_formatear_titulo_solo_con_nombre_apellido():
    # Asegura que el título no afecte si no se proporciona, incluso si es None explícito
    assert formatear_nombre_completo("carlos", "ruiz", titulo=None) == "Carlos Ruiz"

# Pruebas para casos de error (ValueError)
def test_error_nombre_vacio():
    with pytest.raises(ValueError, match="El nombre y el apellido no pueden estar vacíos."):
        formatear_nombre_completo("", "valido")

def test_error_apellido_vacio():
    with pytest.raises(ValueError, match="El nombre y el apellido no pueden estar vacíos."):
        formatear_nombre_completo("valido", "")

def test_error_nombre_y_apellido_vacios():
    with pytest.raises(ValueError, match="El nombre y el apellido no pueden estar vacíos."):
        formatear_nombre_completo("", "")

def test_error_nombre_solo_espacios():
    with pytest.raises(ValueError, match="El nombre y el apellido no pueden estar vacíos."):
        formatear_nombre_completo("   ", "valido")

def test_error_apellido_solo_espacios():
    with pytest.raises(ValueError, match="El nombre y el apellido no pueden estar vacíos."):
        formatear_nombre_completo("valido", "   ")

```

💬 **Discusión/Próxima Acción:**
Este conjunto de pruebas cubre:
*   El formateo básico de nombre y apellido.
*   La inclusión y formateo correcto de un título.
*   La normalización de entradas con espacios extra o mayúsculas/minúsculas incorrectas.
*   La correcta generación de `ValueError` cuando el nombre o el apellido son cadenas vacías o solo espacios.

Te sugiero guardar este código en un archivo llamado `test_formatter.py` en el mismo directorio que tu archivo `formatter.py`. Luego puedes ejecutar `pytest` desde tu terminal en ese directorio.

¿Estas pruebas cubren lo que tenías en mente? ¿Hay algún otro comportamiento o caso de borde que te gustaría probar?
```
