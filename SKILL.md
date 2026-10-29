---
name: test-estudio
description: Crea tests (cuestionarios tipo test) para estudiar a partir de apuntes, temarios, PDFs, capítulos o simplemente un tema. Úsala siempre que el usuario pida un test, cuestionario, quiz, preguntas de examen, preguntas tipo test, flashcards, repasar, autoevaluarse, practicar para un examen o "ponme a prueba", aunque no mencione la palabra "test". También cuando quiera corregir un test que ha hecho, repasar sus fallos o generar un simulacro de examen.
---

# Test de estudio

Genera tests que ayuden a **aprender**, no solo a puntuar. Un buen test detecta lagunas, obliga a recordar y explica el porqué de cada respuesta.

## Flujo

1. **Identifica el material.** Si el usuario adjunta apuntes o un archivo, básate solo en ese contenido (si el archivo no está en contexto, léelo desde `/mnt/user-data/uploads`). Si solo da un tema, usa conocimiento general y dilo en una línea.
2. **Fija los parámetros con lo que ya sepas.** Pregunta como máximo una vez y solo lo imprescindible. Si el usuario no lo indica, usa estos valores por defecto:
   - Nº de preguntas: 10
   - Formato: opción múltiple, 4 opciones, una correcta
   - Dificultad: mixta (30 % fácil, 50 % media, 20 % difícil)
   - Idioma: el del usuario
3. **Genera el test** siguiendo las reglas de calidad de abajo.
4. **Entrega el test** según lo que esté disponible:
   - Si existe la herramienta `quiz_display_v0`, úsala (modo `quiz`, o `flashcards` si piden tarjetas de repaso).
   - Si no, usa el formato en Markdown de `references/formatos.md`.
5. **Tras responder el usuario**, corrige, da la nota y ofrece repasar los fallos o generar otro test centrado en los temas débiles.

## Reglas de calidad

- **Una sola respuesta correcta** e inequívoca. Evita "todas las anteriores" y "ninguna de las anteriores".
- **Distractores plausibles**: errores típicos, conceptos parecidos o medias verdades. Si un distractor se descarta sin saber la materia, está mal hecho.
- **Opciones de longitud parecida** y correcta repartida al azar entre A, B, C y D; no la pongas siempre en la misma posición.
- **Enunciados claros**, sin dobles negaciones ni trampas de redacción. Mide comprensión, no atención lectora.
- **Variedad cognitiva**: mezcla definiciones, aplicación a casos prácticos, comparación de conceptos y detección de errores, en lugar de pura memorización.
- **Cobertura equilibrada** del material; no concentres todas las preguntas en una sección.
- **Explicación breve de cada respuesta**: por qué la correcta lo es y, si ayuda, por qué falla el distractor más tentador.
- **No inventes datos.** Si el material no permite una pregunta fiable, no la hagas.

## Modos de test

Elige el modo según lo que pida el usuario:

| Modo | Cuándo | Particularidades |
|---|---|---|
| Rápido | "repaso rápido", poco tiempo | 5 preguntas, dificultad baja-media |
| Estándar | por defecto | 10 preguntas, dificultad mixta |
| Simulacro | "simulacro", "como el examen" | 20-40 preguntas, sin pistas, nota al final; si dice que penalizan los fallos, aplica la regla que indique |
| Repaso de fallos | tras corregir un test | Solo temas fallados, preguntas nuevas con enfoque distinto |
| Flashcards | "tarjetas", memorizar | Pregunta delante, respuesta y explicación detrás |

## Corrección

Al corregir:

1. Indica aciertos, fallos y nota sobre 10 (y sobre el total de preguntas).
2. Agrupa los fallos por tema para que el usuario vea dónde flojea.
3. Explica cada fallo en una o dos frases, sin sermones.
4. Cierra con una recomendación concreta: qué repasar y si conviene hacer otro test.

## Ejemplo de pregunta bien formada

**Tema:** bases de datos relacionales

**¿Qué garantiza la clave foránea?**
- A) Que los valores de una columna no se repitan
- B) Que el valor referenciado exista en la tabla relacionada ✅
- C) Que la tabla esté en tercera forma normal
- D) Que la columna se indexe automáticamente en todos los motores

**Explicación:** la clave foránea impone integridad referencial. A describe una restricción `UNIQUE`; C es una propiedad del diseño, no de la clave; D depende del motor y no es su garantía.
