# Week 1 · Notes

> Ejemplo de estructura. Reescribe cada punto con tus palabras: si no puedes explicarlo, aún no lo has entendido.

## Qué construí
- `day1.ipynb`: generador de asuntos de correo. Recibe el texto de un email y devuelve un asunto de máximo 10 palabras en el mismo idioma.

## Conceptos clave
- **Chat Completions API**: se envía una lista de `messages` y el modelo responde con el siguiente mensaje.
- **Roles**:
  - `system`: define el comportamiento y las reglas (qué hacer, formato, límites).
  - `user`: la entrada concreta (en este caso, el email).
  - `assistant`: la respuesta del modelo (también se usa para dar ejemplos o historial).
- **El modelo no tiene memoria**: cada llamada es independiente; si quiero contexto, tengo que reenviar el historial en `messages`.
- **Delimitar la entrada** (`<email>...</email>`): ayuda a que el modelo trate el texto como datos y no como instrucciones (defensa básica contra prompt injection).
- **API key en `.env`**: se carga con `load_dotenv()`; nunca va en el código ni en GitHub.

## Decisiones que tomé
- El modelo es un parámetro de la función → puedo comparar modelos sin tocar la lógica.
- Restricciones explícitas en el system prompt (una línea, sin comillas, sin explicación) → salida fácil de usar en código.

## Pruebas (mini-eval)
| Entrada | Esperado | Resultado | ¿OK? |
| --- | --- | --- | --- |
| Email en español (NovaPay) | 1 línea, español, ≤10 palabras | | |
| Email en inglés (cloud bill) | 1 línea, inglés, ≤10 palabras | | |

## Dudas abiertas
- ¿Cuánto cuesta cada llamada? (tokens de entrada + salida)
- ¿Qué pasa si el email está vacío o es muy largo?

## Para la próxima
- Medir tokens y coste por llamada.
- Probar el mismo ejercicio con un modelo local en Ollama.
