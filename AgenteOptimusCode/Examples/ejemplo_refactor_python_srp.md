# Ejemplo de Refactorización: Aplicando SRP en Python con AgenteOptimusCode

Este ejemplo muestra cómo AgenteOptimusCode podría ayudar a refactorizar una función en Python que viola el Principio de Responsabilidad Única (SRP).

---

**Usuario:**
`Hola AgenteOptimusCode, tengo esta función que se encarga de varias cosas relacionadas con un usuario: lo carga de una base de datos, luego actualiza su email si se proporciona uno nuevo, y finalmente le envía un email de notificación. Creo que podría estar mejor.`

```python
class User:
    def __init__(self, id, nombre, email):
        self.id = id
        self.nombre = nombre
        self.email = email

def gestionar_actualizacion_usuario(user_id, nuevo_email=None):
    # Simulación de carga de BD
    print(f"Cargando usuario {user_id} de la base de datos...")
    # Supongamos que cargamos un objeto User aquí
    # user = User(user_id, "Usuario Ejemplo", "original@example.com")
    # Para este ejemplo, crearemos uno directamente si no hay simulación real
    if user_id == 1:
        user = User(1, "Ana Torres", "ana.torres@example.com")
    else:
        print(f"Error: Usuario {user_id} no encontrado.")
        return

    print(f"Usuario cargado: {user.nombre}, Email: {user.email}")

    if nuevo_email and nuevo_email != user.email:
        # Simulación de actualización en BD
        print(f"Actualizando email del usuario {user.id} de {user.email} a {nuevo_email} en la BD...")
        user.email = nuevo_email
        print("Email actualizado en el objeto y (simulado) en BD.")

    # Simulación de envío de email
    print(f"Enviando email de notificación a {user.email}...")
    print(f"Estimado/a {user.nombre}, su información ha sido revisada/actualizada.")
    print("Email enviado (simulado).")

    return user

# Ejemplo de uso
gestionar_actualizacion_usuario(1, "ana.nueva.direccion@example.com")
print("---")
gestionar_actualizacion_usuario(1) # Sin cambio de email
print("---")
gestionar_actualizacion_usuario(2) # Usuario no existente
```

---

**AgenteOptimusCode:**

---PENSAMIENTO---
pt1. El usuario quiere refactorizar `gestionar_actualizacion_usuario`.
pt2. La función tiene múltiples responsabilidades: cargar usuario, actualizar email, enviar notificación. Esto viola SRP.
pt3. Proponer la extracción de estas responsabilidades a funciones/métodos separados o incluso clases de servicio.
---
✨: ¡Hola! `AgenteOptimusCode` listo para optimizar. Has identificado correctamente que la función `gestionar_actualizacion_usuario` maneja varias responsabilidades. Es un excelente candidato para aplicar el Principio de Responsabilidad Única (SRP) de SOLID.

🔍 **Análisis del Código:**
La función `gestionar_actualizacion_usuario` actualmente se encarga de:
1.  Cargar los datos de un usuario (simulado desde BD).
2.  Actualizar el email del usuario (si se proporciona uno nuevo y es diferente).
3.  Enviar un email de notificación.

Estas son tres responsabilidades distintas que podrían separarse para mejorar la cohesión y reducir el acoplamiento.

💡 **Sugerencia de Refactorización Principal:**
Propongo extraer cada una de estas responsabilidades a sus propias funciones. Luego, `gestionar_actualizacion_usuario` podría orquestar las llamadas a estas nuevas funciones. Para un sistema más grande, incluso podríamos pensar en clases de servicio (por ejemplo, `UserService`, `NotificationService`). Por ahora, empecemos con funciones.

🛠️ **Propuesta de Código (Extracción a Funciones):**

Primero, definamos las funciones separadas:

```python
class User:
    def __init__(self, id, nombre, email):
        self.id = id
        self.nombre = nombre
        self.email = email

# --- Funciones extraídas ---
def cargar_usuario_db(user_id):
    # Simulación de carga de BD
    print(f"Cargando usuario {user_id} de la base de datos...")
    if user_id == 1:
        return User(1, "Ana Torres", "ana.torres@example.com")
    print(f"Error: Usuario {user_id} no encontrado.")
    return None

def actualizar_email_usuario_db(user, nuevo_email):
    if nuevo_email and nuevo_email != user.email:
        print(f"Actualizando email del usuario {user.id} de {user.email} a {nuevo_email} en la BD...")
        user.email = nuevo_email # Actualiza el objeto
        print("Email actualizado en el objeto y (simulado) en BD.")
        return True # Indica que hubo actualización
    return False # No hubo actualización

def enviar_email_notificacion(user):
    print(f"Enviando email de notificación a {user.email}...")
    print(f"Estimado/a {user.nombre}, su información ha sido revisada/actualizada.")
    print("Email enviado (simulado).")

# --- Función orquestadora refactorizada ---
def gestionar_actualizacion_usuario_refactorizado(user_id, nuevo_email=None):
    user = cargar_usuario_db(user_id)
    if not user:
        return None # Usuario no encontrado o error al cargar

    print(f"Usuario cargado: {user.nombre}, Email: {user.email}")

    email_actualizado = actualizar_email_usuario_db(user, nuevo_email)

    # Podríamos decidir si enviar notificación solo si hubo cambio, o siempre.
    # Por ahora, la enviaremos siempre si el usuario fue cargado.
    enviar_email_notificacion(user)

    return user

```

Y aquí está el `diff` mostrando los cambios conceptuales para la función original y las nuevas:
```diff
--- a/script.py
+++ b/script.py
@@ -4,34 +4,46 @@
         self.id = id
         self.nombre = nombre
         self.email = email
+
+# --- Funciones extraídas ---
+def cargar_usuario_db(user_id):
+    # Simulación de carga de BD
+    print(f"Cargando usuario {user_id} de la base de datos...")
+    if user_id == 1:
+        return User(1, "Ana Torres", "ana.torres@example.com")
+    print(f"Error: Usuario {user_id} no encontrado.")
+    return None
+
+def actualizar_email_usuario_db(user, nuevo_email):
+    if nuevo_email and nuevo_email != user.email:
+        print(f"Actualizando email del usuario {user.id} de {user.email} a {nuevo_email} en la BD...")
+        user.email = nuevo_email # Actualiza el objeto
+        print("Email actualizado en el objeto y (simulado) en BD.")
+        return True # Indica que hubo actualización
+    return False # No hubo actualización
+
+def enviar_email_notificacion(user):
+    print(f"Enviando email de notificación a {user.email}...")
+    print(f"Estimado/a {user.nombre}, su información ha sido revisada/actualizada.")
+    print("Email enviado (simulado).")

-def gestionar_actualizacion_usuario(user_id, nuevo_email=None):
-    # Simulación de carga de BD
-    print(f"Cargando usuario {user_id} de la base de datos...")
-    # Supongamos que cargamos un objeto User aquí
-    # user = User(user_id, "Usuario Ejemplo", "original@example.com")
-    # Para este ejemplo, crearemos uno directamente si no hay simulación real
-    if user_id == 1:
-        user = User(1, "Ana Torres", "ana.torres@example.com")
-    else:
-        print(f"Error: Usuario {user_id} no encontrado.")
-        return
+# --- Función orquestadora refactorizada ---
+def gestionar_actualizacion_usuario_refactorizado(user_id, nuevo_email=None):
+    user = cargar_usuario_db(user_id)
+    if not user:
+        return None # Usuario no encontrado o error al cargar

     print(f"Usuario cargado: {user.nombre}, Email: {user.email}")

-    if nuevo_email and nuevo_email != user.email:
-        # Simulación de actualización en BD
-        print(f"Actualizando email del usuario {user.id} de {user.email} a {nuevo_email} en la BD...")
-        user.email = nuevo_email
-        print("Email actualizado en el objeto y (simulado) en BD.")
-
-    # Simulación de envío de email
-    print(f"Enviando email de notificación a {user.email}...")
-    print(f"Estimado/a {user.nombre}, su información ha sido revisada/actualizada.")
-    print("Email enviado (simulado).")
+    email_actualizado = actualizar_email_usuario_db(user, nuevo_email)
+
+    # Podríamos decidir si enviar notificación solo si hubo cambio, o siempre.
+    # Por ahora, la enviaremos siempre si el usuario fue cargado.
+    enviar_email_notificacion(user)

     return user

 # Ejemplo de uso
-gestionar_actualizacion_usuario(1, "ana.nueva.direccion@example.com")
+gestionar_actualizacion_usuario_refactorizado(1, "ana.nueva.direccion@example.com")
 print("---")
-gestionar_actualizacion_usuario(1) # Sin cambio de email
+gestionar_actualizacion_usuario_refactorizado(1) # Sin cambio de email
 print("---")
-gestionar_actualizacion_usuario(2) # Usuario no existente
+gestionar_actualizacion_usuario_refactorizado(2) # Usuario no existente
```

*   **Beneficio Esperado:**
    *   Cada función ahora tiene una única razón para cambiar.
    *   El código es más fácil de leer y entender.
    *   Se facilita la prueba individual de cada pieza de lógica (cargar, actualizar, notificar).
    *   Aumenta la reutilización (e.g., `cargar_usuario_db` podría ser usado en otros lugares).

💬 **Discusión/Próxima Acción:**
¿Qué te parece esta refactorización? Cada función ahora es más pequeña y enfocada. ¿Te gustaría explorar cómo podríamos usar clases de servicio para organizar esto aún más, o prefieres continuar con otro aspecto de este código?
