# 🧪 AgenteQA: Tu Especialista en Generación de Pruebas

**AgenteQA** es un modo diseñado para asistirte en la creación de pruebas de software. Te ayuda a identificar casos de prueba, generar código para pruebas unitarias, de integración (conceptualmente) y a definir escenarios para pruebas de comportamiento, asegurando que tu código funcione como se espera.

## 🎯 Objetivo Principal

El objetivo de AgenteQA es ayudarte a:

*   **Identificar Casos de Prueba:** Descubrir escenarios relevantes para probar tu código, incluyendo el camino feliz, casos borde, entradas inválidas y condiciones de error.
*   **Generar Código de Pruebas Unitarias:** Escribir el código necesario para probar unidades aisladas de tu software (funciones, métodos, clases pequeñas).
*   **Definir Pruebas de Integración:** Ayudar a conceptualizar cómo probar la interacción entre diferentes componentes o módulos.
*   **Esbozar Pruebas de Comportamiento (BDD):** Ayudar a escribir escenarios en formato Gherkin (Given-When-Then) si es necesario.
*   **Promover Buenas Prácticas de Testing:** Fomentar la creación de pruebas claras, mantenibles y efectivas.

## 💡 ¿Cuándo Usarlo?

Utiliza AgenteQA cuando:

*   Estás desarrollando nuevas funcionalidades y quieres asegurar su calidad desde el inicio (TDD o BDD).
*   Necesitas aumentar la cobertura de pruebas de un código existente.
*   Quieres verificar que una refactorización no ha introducido regresiones.
*   No estás seguro de qué casos de prueba son importantes para una pieza de código específica.
*   Necesitas ayuda para escribir el "boilerplate" o estructura de tus archivos de prueba.

## ✅ Consideraciones Clave

*   **Frameworks de Pruebas:** AgenteQA intentará adaptarse al framework de pruebas que especifiques (e.g., `pytest` para Python, `JUnit` para Java, `Jest` o `Mocha` for JavaScript/TypeScript, etc.). Si no especificas uno, podría preguntar o usar uno común para el lenguaje.
*   **Tipos de Pruebas:**
    *   **Unitarias:** Foco principal. Prueban la unidad más pequeña de código de forma aislada.
    *   **Integración:** AgenteQA puede ayudar a definir qué interacciones probar y cómo podrían estructurarse estas pruebas, pero la implementación completa puede requerir más contexto del sistema.
    *   **E2E/Comportamiento:** Puede ayudar a escribir los escenarios (e.g., en Gherkin), pero la automatización de estas pruebas suele depender de herramientas específicas fuera del alcance directo de generación de código simple.
*   **Cobertura vs. Calidad:** AgenteQA te ayudará a generar pruebas, pero recuerda que el objetivo no es solo el 100% de cobertura, sino tener pruebas significativas que realmente validen el comportamiento esperado y los casos críticos.

## 🔧 Herramientas Recomendadas (para plataformas como Cursor)

*   **`Edit`**: Activado. Esencial para que AgenteQA escriba el código de las pruebas en tus archivos.
*   **`Search`**: Opcional. Podría ser útil para entender dependencias si se están generando pruebas para código que interactúa con otras partes del sistema.

## ⚙️ Modelo por Defecto (Sugerencia)

*   Un modelo con buena comprensión de código y conocimiento de diversos frameworks de pruebas es ideal. **Gemini Pro**, **GPT-4**, o **Claude 3 Opus/Sonnet** son buenas opciones.

## 🗣️ Ejemplo Básico de Interacción (Prueba Unitaria Python con Pytest)

**Usuario:**
`AgenteQA, necesito generar pruebas unitarias para esta función en Python. Estoy usando pytest.`
```python
# utils.py
def dividir(a, b):
    if b == 0:
        raise ValueError("No se puede dividir por cero")
    return a / b
```
`Quiero probar el caso normal y la división por cero.`

**AgenteQA (Respuesta esperada):**
```
---PENSAMIENTO---
pt1. El usuario quiere pruebas unitarias para la función `dividir` en Python usando `pytest`.
pt2. Casos a cubrir: división normal y `ValueError` en división por cero.
pt3. Generar un archivo de prueba `test_utils.py` con dos funciones de prueba.
---
🧪 ¡Entendido! `AgenteQA` listo para asegurar la calidad de tu función `dividir`. Vamos a crear algunas pruebas con `pytest`.

🔍 **Análisis de la Función:**
La función `dividir(a, b)`:
1.  Realiza la división `a / b`.
2.  Lanza un `ValueError` si `b` es cero.

🎯 **Casos de Prueba Identificados:**
1.  **División Exitosa:** Probar con valores válidos para `a` y `b`.
2.  **División por Cero:** Verificar que se lanza `ValueError` cuando `b` es `0`.

🛠️ **Código de Prueba Sugerido (para un archivo `test_utils.py`):**
```python
# test_utils.py
import pytest
from utils import dividir # Asegúrate que utils.py esté en el mismo directorio o en el PYTHONPATH

def test_dividir_exitosamente():
    """Prueba la división con números válidos."""
    assert dividir(10, 2) == 5
    assert dividir(9, 3) == 3
    assert dividir(5, 2) == 2.5
    assert dividir(-10, 2) == -5
    assert dividir(0, 5) == 0

def test_dividir_por_cero_lanza_excepcion():
    """Prueba que dividir por cero lanza ValueError."""
    with pytest.raises(ValueError) as excinfo:
        dividir(10, 0)
    assert "No se puede dividir por cero" in str(excinfo.value)

# Opcional: prueba con otro valor para asegurar que la excepción se lanza correctamente
def test_dividir_por_cero_otro_caso():
    """Prueba otro caso de división por cero."""
    with pytest.raises(ValueError, match="No se puede dividir por cero"):
        dividir(0, 0)
```

💬 **Próxima Acción/Pregunta:**
Este código de prueba cubre los dos escenarios que mencionaste.
1.  `test_dividir_exitosamente`: Verifica varios casos de división normal.
2.  `test_dividir_por_cero_lanza_excepcion` y `test_dividir_por_cero_otro_caso`: Verifican que se lanza `ValueError` correctamente cuando se intenta dividir por cero, y que el mensaje de error es el esperado.

¿Te gustaría que genere estas pruebas en un archivo `test_utils.py`? ¿Hay otros casos o comportamientos de esta función que te gustaría probar?
```

## 🔗 System Prompt

Para las instrucciones completas del sistema, consulta el archivo: **[Prompt.md](./Prompt.md)**.
