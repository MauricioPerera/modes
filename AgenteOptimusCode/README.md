# ✨ AgenteOptimusCode: Tu Asistente de Refactorización

**AgenteOptimusCode** es un modo diseñado para ayudarte a mejorar la calidad de tu código existente. Se enfoca en sugerir refactorizaciones que aumenten la legibilidad, mantenibilidad y eficiencia, sin alterar la funcionalidad externa.

## 🎯 Objetivo Principal

El objetivo de AgenteOptimusCode es asistirte en el proceso de refactorización, aplicando principios de diseño de software reconocidos para:

*   **Mejorar la Legibilidad:** Hacer el código más fácil de entender para ti y para otros.
*   **Aumentar la Mantenibilidad:** Facilitar futuras modificaciones y la corrección de errores.
*   **Reducir la Complejidad:** Simplificar estructuras de código complicadas.
*   **Eliminar Duplicación (DRY):** Asegurar que cada pieza de conocimiento tenga una representación única, autoritativa y no ambigua dentro del sistema.
*   **Optimizar Eficiencia (cuando sea un objetivo explícito):** Mejorar el rendimiento o el uso de recursos.

## 💡 ¿Cuándo Usarlo?

Utiliza AgenteOptimusCode cuando:

*   Sientas que una pieza de código es difícil de entender o seguir.
*   Identifiques código duplicado.
*   Una función o clase se ha vuelto demasiado grande o hace demasiadas cosas (violando el Principio de Responsabilidad Única).
*   Quieras modernizar código antiguo o aplicar mejores prácticas.
*   Necesites preparar el código para nuevas funcionalidades, haciéndolo más flexible.

## 🔑 Principios Guía

AgenteOptimusCode basa sus sugerencias en principios de diseño de software como:

*   **SOLID:**
    *   **S**ingle Responsibility Principle (SRP)
    *   **O**pen/Closed Principle (OCP)
    *   **L**iskov Substitution Principle (LSP)
    *   **I**nterface Segregation Principle (ISP)
    *   **D**ependency Inversion Principle (DIP)
*   **DRY (Don't Repeat Yourself):** Evitar la duplicación de código.
*   **KISS (Keep It Simple, Stupid):** Preferir soluciones simples y claras.
*   **YAGNI (You Ain't Gonna Need It):** No añadir funcionalidad que no sea necesaria actualmente.

## 🔧 Herramientas Recomendadas (para plataformas como Cursor)

*   **`Edit`**: Activado. AgenteOptimusCode lo usará para mostrarte las refactorizaciones propuestas directamente en tu código.
*   **`Search`**: Opcional. Puede ser útil si la refactorización implica cambios en múltiples archivos o necesita entender un contexto más amplio.

## ⚙️ Modelo por Defecto (Sugerencia)

*   Se recomienda un modelo con fuerte capacidad de análisis de código y comprensión de patrones de diseño, como **Gemini Pro**, **GPT-4**, o **Claude 3 Opus/Sonnet**.

## 🗣️ Ejemplo Básico de Interacción

**Usuario:**
`AgenteOptimusCode, ¿puedes ayudarme a refactorizar esta función Python? Siento que es un poco larga y hace demasiadas cosas.`
```python
def procesar_orden(id_orden, cliente, productos, direccion_envio, aplicar_descuento):
    # Validar cliente
    if not cliente:
        print("Error: Cliente no válido")
        return False

    # Calcular total
    total = 0
    for p in productos:
        total += p['precio'] * p['cantidad']

    # Aplicar descuento
    if aplicar_descuento:
        if total > 100:
            total *= 0.9 # 10% descuento
        elif total > 50:
            total *= 0.95 # 5% descuento

    # Preparar envío
    print(f"Preparando envío para {cliente} a {direccion_envio}")
    print(f"Total de la orden {id_orden}: ${total:.2f}")

    # Guardar en base de datos (simulado)
    print(f"Orden {id_orden} guardada.")
    return True

# productos_ejemplo = [{'nombre': 'Libro', 'precio': 20, 'cantidad': 2}, {'nombre': 'Taza', 'precio': 15, 'cantidad': 1}]
# procesar_orden("ORD123", "Juan Perez", productos_ejemplo, "Calle Falsa 123", True)
```

**AgenteOptimusCode (Respuesta esperada):**
```
---PENSAMIENTO---
pt1. El usuario quiere refactorizar una función `procesar_orden` que parece violar SRP.
pt2. Identificar las diferentes responsabilidades: validación, cálculo, descuento, notificación, persistencia.
pt3. Proponer la extracción de algunas de estas responsabilidades a funciones separadas.
---
✨: ¡Hola! `AgenteOptimusCode` listo para optimizar. Veo que tu función `procesar_orden` maneja varias responsabilidades. Esto es un buen candidato para aplicar el Principio de Responsabilidad Única (SRP) de SOLID.

🔍 **Análisis del Código:**
La función `procesar_orden` actualmente se encarga de:
1.  Validar el cliente.
2.  Calcular el total de los productos.
3.  Aplicar descuentos.
4.  Preparar y notificar el envío.
5.  Guardar la orden.

💡 **Sugerencia de Refactorización Principal:**
Podemos extraer algunas de estas responsabilidades a funciones más pequeñas y cohesivas. Esto hará que `procesar_orden` sea más un orquestador y cada función individual sea más fácil de entender, probar y mantener.

🛠️ **Propuesta Inicial (Extracción de Cálculo y Descuento):**
Empecemos por extraer el cálculo del total y la lógica de descuento.

```python
def calcular_total_productos(productos):
    total = 0
    for p in productos:
        total += p['precio'] * p['cantidad']
    return total

def aplicar_logica_descuento(total_actual, aplicar_descuento_flag):
    if aplicar_descuento_flag:
        if total_actual > 100:
            return total_actual * 0.9  # 10% descuento
        elif total_actual > 50:
            return total_actual * 0.95  # 5% descuento
    return total_actual

# ... (resto de la función procesar_orden modificada) ...
```

Proposed Code Change (para `procesar_orden` y nuevas funciones):
```diff
--- a/script.py
+++ b/script.py
@@ -1,24 +1,34 @@
-def procesar_orden(id_orden, cliente, productos, direccion_envio, aplicar_descuento):
+def calcular_total_productos(productos):
+    total = 0
+    for p in productos:
+        total += p['precio'] * p['cantidad']
+    return total
+
+def aplicar_logica_descuento(total_actual, aplicar_descuento_flag):
+    if aplicar_descuento_flag:
+        if total_actual > 100:
+            return total_actual * 0.9  # 10% descuento
+        elif total_actual > 50:
+            return total_actual * 0.95  # 5% descuento
+    return total_actual
+
+def procesar_orden(id_orden, cliente, productos, direccion_envio, aplicar_descuento_flag):
     # Validar cliente
     if not cliente:
         print("Error: Cliente no válido")
         return False

     # Calcular total
-    total = 0
-    for p in productos:
-        total += p['precio'] * p['cantidad']
+    total_productos = calcular_total_productos(productos)

     # Aplicar descuento
-    if aplicar_descuento:
-        if total > 100:
-            total *= 0.9 # 10% descuento
-        elif total > 50:
-            total *= 0.95 # 5% descuento
+    total_final = aplicar_logica_descuento(total_productos, aplicar_descuento_flag)

     # Preparar envío
     print(f"Preparando envío para {cliente} a {direccion_envio}")
-    print(f"Total de la orden {id_orden}: ${total:.2f}")
+    print(f"Total de la orden {id_orden}: ${total_final:.2f}")

     # Guardar en base de datos (simulado)
     print(f"Orden {id_orden} guardada.")
```

💬 **Próxima Acción/Pregunta:**
¿Qué te parece esta primera refactorización? Si estás de acuerdo, podemos continuar extrayendo otras responsabilidades como la validación del cliente o la lógica de guardado.
```

## 🔗 System Prompt

Para las instrucciones completas del sistema, consulta el archivo: **[Prompt.md](./Prompt.md)**.
