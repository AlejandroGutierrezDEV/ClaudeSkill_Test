# test-estudio

Skill para Claude que crea **tests tipo test para estudiar** a partir de tus apuntes, PDFs, capítulos o simplemente un tema. Cada pregunta incluye una explicación, y al terminar corrige, da la nota y te indica qué repasar.

## Qué hace

- Genera cuestionarios de opción múltiple (4 opciones, una correcta) con distractores plausibles.
- Explica por qué cada respuesta es correcta o incorrecta.
- Corrige tus respuestas, calcula la nota y agrupa los fallos por tema.
- Crea tests de repaso centrados en tus puntos débiles.
- Ofrece varios modos y flashcards.

## Modos

| Modo | Uso | Preguntas |
|---|---|---|
| Rápido | Repaso con poco tiempo | 5 |
| Estándar | Valor por defecto | 10 |
| Simulacro | Práctica tipo examen | 20-40 |
| Repaso de fallos | Tras corregir un test | Solo temas fallados |
| Flashcards | Memorizar | A tu elección |

## Instalación

### En Claude (claude.ai)
1. Comprime la carpeta `test-estudio` en un `.zip` (o usa el archivo `.skill` si lo tienes).
2. Ve a **Configuración → Capacidades → Skills** y sube el archivo.

### En Claude Code
Copia la carpeta en el directorio de skills:

```bash
# Para todos tus proyectos
cp -r test-estudio ~/.claude/skills/

# Solo para un proyecto
cp -r test-estudio .claude/skills/
```

## Uso

Basta con pedirlo con naturalidad:

- «Hazme un test de 10 preguntas sobre el tema 3 de estos apuntes.»
- «Ponme a prueba sobre normalización de bases de datos.»
- «Quiero un simulacro de examen de 30 preguntas.»
- «Corrige mi test y hazme otro con lo que he fallado.»

Si adjuntas apuntes, el test se basa solo en ese contenido.

## Estructura

```
test-estudio/
├── SKILL.md              # Instrucciones y reglas de calidad
├── references/
│   └── formatos.md       # Formatos de salida en Markdown
├── LICENSE
└── README.md
```

## Licencia

Distribuida bajo licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.

© 2026 Alejandro Gutiérrez
