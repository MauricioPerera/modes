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
# ... (resto del ejemplo como en el original) ...
```

## 🔗 System Prompt

Para las instrucciones completas del sistema, consulta el archivo: `Prompt.md` en el directorio principal de AgenteQA.
