# Guía para Contribuir y Gestionar Modos en este Repositorio

Este documento describe el estándar para agregar y mantener "modos" en este repositorio. Un modo define la configuración y el comportamiento de un agente de IA (como los utilizados en plataformas como Cursor) para optimizar los resultados en tareas específicas.

## Estructura de un Modo

Cada modo debe residir en su propio directorio dentro del repositorio. El nombre del directorio debe ser descriptivo y utilizar `PascalCase` (por ejemplo, `MiNuevoModo/`).

Dentro del directorio de cada modo, se deben incluir los siguientes archivos:

### 1. `README.md` (Requerido)

Este archivo es la tarjeta de presentación del modo. Debe contener la siguiente información:

*   **Nombre del Modo:** Claro y conciso.
*   **Descripción:**
    *   ¿Cuál es el propósito principal del modo?
    *   ¿Para qué tipo de tareas, proyectos o plataformas es más útil?
    *   ¿Qué beneficios clave ofrece (e.g., mayor precisión, código más limpio, mejor planificación)?
*   **Ícono (Opcional pero Recomendado):**
    *   Un emoji o carácter que represente visualmente el modo (e.g., 🤖, 💡, 🛠️).
*   **Instrucciones Personalizadas / System Prompt (Resumen):**
    *   Un breve resumen de las instrucciones principales del agente.
    *   Se debe enlazar al archivo `Prompt.md` para la versión completa.
*   **Modelo por Defecto (Si Aplica):**
    *   Recomendación sobre el modelo de IA a utilizar (e.g., "Auto (Gemini)", "Claude 3 Opus", "GPT-4 Turbo").
*   **Herramientas Recomendadas (Para Plataformas como Cursor):**
    *   Listar las herramientas que se recomienda activar o desactivar:
        *   Ej: `Search: Activado`, `Edit: Activado`, `Run: Desactivado`, `Auto-execute: Precaución/Desactivado`.
*   **Atajo de Teclado Sugerido (Opcional):**
    *   Si la plataforma lo permite, sugerir un atajo para activar rápidamente el modo (e.g., `Cmd + Shift + M`).
*   **Ejemplo de Uso (Opcional):**
    *   Un pequeño bloque de código o descripción mostrando cómo iniciar una interacción típica con el modo.

### 2. `Prompt.md` (o `SystemPrompt.md`) (Requerido)

Este archivo contiene el texto completo y exacto del "system prompt" o las instrucciones personalizadas que se deben configurar en la plataforma (e.g., Cursor, ChatGPT con instrucciones personalizadas) para activar el modo.

Debe estar bien estructurado y puede incluir secciones como:

*   `OBJETIVO`: La meta principal del agente.
*   `CONTEXTO`: Información relevante que el agente debe conocer.
*   `ESTRUCTURA DE SALIDA`: Cómo deben formatearse las respuestas.
*   `FLUJO DE INTERACCIÓN`: Cómo debe proceder la conversación.
*   `COMANDOS`: Comandos especiales que el agente debe reconocer (e.g., `/plan`, `/debug`).
*   `PERSONALIDAD Y ESTILO`: Tono y forma de comunicación del agente.
*   `RESTRICCIONES`: Cosas que el agente no debe hacer.

**Ejemplo:** El modo `Nexus/` en este repositorio sirve como una excelente referencia para la estructura de `README.md` y `Prompt.md`.

### Archivos Opcionales

*   **`Examples/` (Directorio):**
    *   Puede contener subdirectorios o archivos (e.g., en formato `.md` o `.txt`) que muestren ejemplos de interacciones completas con el modo. Esto ayuda a entender su comportamiento y resultados esperados.
*   **`Config/` (Directorio):**
    *   Para archivos de configuración adicionales, scripts de apoyo o recursos que el modo pueda necesitar.
*   **`AGENTS.md` (Específico del Modo):**
    *   Si un modo es particularmente complejo, involucra múltiples sub-agentes, o tiene un flujo de trabajo interno que requiere documentación detallada para su mantenimiento o extensión.

## Proceso para Agregar un Nuevo Modo

1.  **Crea un nuevo directorio:** Usa `PascalCase` para el nombre (e.g., `ModoRevisionCodigo/`).
2.  **Añade `README.md`:** Documenta tu modo siguiendo la estructura detallada arriba.
3.  **Añade `Prompt.md`:** Incluye el system prompt completo.
4.  **Añade archivos opcionales:** Si son necesarios (ejemplos, configuraciones).
5.  **Verifica:** Asegúrate de que la estructura y el contenido sean claros y sigan las pautas.
6.  **Envía un Pull Request:** Para que tu modo sea revisado e incorporado al repositorio.

## Manteniendo la Calidad

*   **Claridad:** Los prompts y las descripciones deben ser fáciles de entender.
*   **Consistencia:** Sigue la estructura de archivos y la nomenclatura definidas.
*   **Pruebas:** Antes de proponer un modo, pruébalo exhaustivamente en la plataforma de destino para asegurar que funciona como se espera.
*   **Feedback:** Está abierto a recibir feedback para mejorar los modos existentes.

Al seguir estas directrices, podemos construir una colección valiosa y bien organizada de modos para mejorar nuestra interacción con las herramientas de IA.
