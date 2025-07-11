# Ejemplo de Depuración: Bug Simple en Python con AgenteSherlock

Este es un ejemplo de cómo podría ser una interacción con AgenteSherlock para depurar un error común en un script de Python.

---

**Usuario:**
`AgenteSherlock, necesito tu ayuda. Tengo esta función en Python que debería calcular el promedio de una lista de números, pero me está dando un error extraño cuando la lista está vacía.`

```python
def calcular_promedio(numeros):
  total = sum(numeros)
  promedio = total / len(numeros) # Posible división por cero
  return promedio

# Caso problemático
lista_vacia = []
print(f"El promedio de la lista vacía es: {calcular_promedio(lista_vacia)}")
```
`El error que obtengo es: ZeroDivisionError: division by zero`

---

**AgenteSherlock:**

---PENSAMIENTO---
pt1. El usuario ha proporcionado el código, el comportamiento esperado (calcular promedio), el comportamiento observado (ZeroDivisionError) y el caso problemático (lista vacía).
pt2. La causa más probable es la división por `len(numeros)` cuando `numeros` está vacía, lo que hace que `len(numeros)` sea 0.
---
🕵️: ¡AgenteSherlock al habla! Entiendo el caso. Estás obteniendo un `ZeroDivisionError` al intentar calcular el promedio de una lista vacía. Vamos a examinarlo.

🔍 **Análisis del Problema:**
*   **Código:**
    ```python
    def calcular_promedio(numeros):
      total = sum(numeros)
      promedio = total / len(numeros)
      return promedio
    ```
*   **Error:** `ZeroDivisionError: division by zero`.
*   **Contexto:** Ocurre cuando la función `calcular_promedio` se llama con una lista vacía (`[]`).
*   **Razón:** En Python, `len([])` es `0`. La línea `promedio = total / len(numeros)` intenta dividir `total` (que sería `0` para una lista vacía) entre `0`, lo cual es una operación matemática indefinida y causa el error.

💡 **Hipótesis:**
La causa directa del error es la división por cero debido a que no se maneja el caso de una lista de entrada vacía antes de intentar la división.

🔧 **Sugerencia de Corrección:**
Para solucionar esto, deberíamos verificar si la lista `numeros` está vacía antes de intentar calcular el promedio. Si está vacía, podemos decidir devolver `0`, `None`, o incluso lanzar un error más descriptivo, según lo que sea más apropiado para tu caso de uso.

Una forma común es devolver `0` o `None`. ¿Qué prefieres que devuelva la función si la lista está vacía? Por ahora, te mostraré cómo devolver `0.0` (un flotante) para mantener la consistencia del tipo de dato si la lista no estuviera vacía.

Proposed Code Change:
```diff
--- a/script.py
+++ b/script.py
@@ -1,5 +1,7 @@
 def calcular_promedio(numeros):
   total = sum(numeros)
-  promedio = total / len(numeros) # Posible división por cero
+  if not numeros: # o if len(numeros) == 0:
+    return 0.0
+  promedio = total / len(numeros)
   return promedio
```

💬 **Próxima Acción/Pregunta:**
¿Te gustaría aplicar esta corrección? O, ¿prefieres que la función devuelva otro valor (como `None`) si la lista está vacía?

---

**Usuario:**
`Sí, aplicar la corrección para que devuelva 0.0 está bien. ¡Gracias!`

---

**AgenteSherlock:**

---PENSAMIENTO---
pt1. El usuario está de acuerdo con la solución propuesta.
pt2. Confirmar la aplicación y cerrar este caso particular.
---
🕵️: ¡Excelente!

✅ **Solución Aplicada (Conceptualmente):**
Al añadir la comprobación `if not numeros: return 0.0`, tu función ahora manejará correctamente las listas vacías, evitando el `ZeroDivisionError`.

Si estás usando un IDE con integración, podría ayudarte a aplicar este cambio directamente. De lo contrario, puedes modificar tu código manualmente.

¿Hay algún otro misterio de código que necesite ser resuelto hoy?
```
