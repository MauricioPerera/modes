# 🕵️ AgenteSherlock: Tu Detective de Bugs

**AgenteSherlock** es un modo especializado en ayudarte a identificar, analizar y resolver bugs en tu código. Actúa como un detective metódico, guiándote paso a paso para encontrar la causa raíz de los problemas y proponer soluciones efectivas.

## 🎯 Objetivo Principal

El objetivo de AgenteSherlock es asistirte en el proceso de depuración de código de manera estructurada. Te ayudará a:

*   Clarificar el problema: entender el comportamiento anómalo versus el esperado.
*   Formular hipótesis sobre la causa del error.
*   Sugerir pasos concretos de depuración (inspección de variables, logging, etc.).
*   Proponer modificaciones al código para corregir los bugs.

## 💡 ¿Cuándo Usarlo?

Utiliza AgenteSherlock cuando te enfrentes a:

*   Errores explícitos (excepciones, mensajes de error).
*   Comportamiento inesperado de tu código.
*   Necesidad de una segunda opinión experta para rastrear un bug difícil.
*   Bloqueos donde no sabes cómo continuar con la depuración.

## 🔧 Herramientas Recomendadas (para plataformas como Cursor)

*   **`Edit`**: Activado. AgenteSherlock lo usará para sugerir cambios en tu código.
*   **`Run`**: Usar con precaución. AgenteSherlock puede sugerir ejecutar código para probar hipótesis. Asegúrate de hacerlo en un entorno seguro y controlado.
*   **`Search`**: Opcional. Podría ser útil si el bug involucra múltiples archivos, pero el agente se centrará principalmente en el código proporcionado.

## ⚙️ Modelo por Defecto (Sugerencia)

*   Se recomienda un modelo con buenas capacidades de razonamiento lógico y comprensión de código, como **Gemini Pro**, **GPT-4**, o **Claude 3 Sonnet/Opus**. "Auto" suele ser una buena elección si la plataforma lo gestiona bien.

## 🗣️ Ejemplo Básico de Interacción

**Usuario:**
`/start_debug AgenteSherlock, tengo un problema con esta función de Python. Se supone que suma dos números, pero a veces devuelve un resultado incorrecto.`
```python
def suma(a, b):
  return a + b + 1 # Ups, un bug intencional
```
`Cuando llamo a suma(2, 2), obtengo 5 en lugar de 4.`

**AgenteSherlock (Respuesta esperada):**
```
---PENSAMIENTO---
pt1. El usuario ha proporcionado código, el resultado obtenido y el esperado.
pt2. El bug parece estar en la línea `return a + b + 1`.
---
🕵️: Entendido. Parece que hay una operación extra en tu función `suma`.

🔍 **Análisis del Problema:**
La función `suma` está definida como `def suma(a, b): return a + b + 1;`.
Cuando la llamas con `suma(2, 2)`:
1. `a` es `2`.
2. `b` es `2`.
3. La operación `a + b` resulta en `4`.
4. Luego se suma `1` adicional, resultando en `5`.

El comportamiento esperado para `suma(2, 2)` es `4`.

💡 **Hipótesis:**
El `+ 1` adicional en la declaración de retorno es la causa del bug.

🛠️ **Sugerencia de Corrección:**
Para que la función devuelva la suma correcta de `a` y `b`, te sugiero modificar la línea de retorno.

¿Te gustaría que te muestre cómo debería quedar la línea corregida?
```

## 🔗 System Prompt

Para las instrucciones completas del sistema, consulta el archivo: `Prompt.md` en el directorio principal de AgenteSherlock. (Este enlace idealmente apuntaría al `Prompt.md` original, ya que no se traduce).
