# Skills para ai-copilot-config

## 1. Propósito

Este directorio define skills reutilizables para agentes de IA en VS Code, organizados para evitar conflicto entre reglas compartidas y reglas por framework.

Objetivos:

- mantener consistencia técnica,
- reducir duplicación de reglas,
- soportar varios proyectos (ej. Joomla y Astro) con una misma base.

## 2. Organización recomendada (core + proyecto)

```plaintext
.github/skills/
├── core/
│   ├── architecture.md
│   ├── workflow.md
│   ├── review.md
│   ├── testing.md
│   ├── definition-of-done.md
│   ├── frontend-html.md
│   ├── frontend-css.md
│   ├── frontend-javascript.md
│   └── backend-data.md
└── projects/
	├── joomla/
	│   ├── joomla.md
	│   ├── joomla-data-json.md
	│   └── javascript-leaflet.md
	└── astro/
		├── astro.md
		├── astro-content.md
		└── astro-routing.md
```

## 3. Reglas de precedencia (anti-conflicto)

Orden obligatorio de aplicación:

1. `core/architecture.md`
2. skill técnico de `core` (frontend/backend)
3. skill de `projects/<framework>`
4. skill de tarea puntual (si existe)

Si hay conflicto, prevalece la regla más específica del proyecto. La excepción debe documentarse en el skill del proyecto para que no se replique en otros repositorios.

## 4. Flujo de uso recomendado

1. Cargar arquitectura y workflow desde `core`.
2. Cargar skills comunes de frontend/backend desde `core`.
3. Seleccionar el paquete de proyecto (`projects/joomla` o `projects/astro`).
4. Ejecutar checklist de `core/review.md` y `core/testing.md`.
5. Cerrar con `core/definition-of-done.md`.

## 5. Mapeo de nombres aplicados

La migración ya fue aplicada con esta equivalencia:

| Actual                         | Propuesto                               |
|--------------------------------|-----------------------------------------|
| `skills-architecture.md`       | `core/architecture.md`                  |
| `skills-workflow.md`           | `core/workflow.md`                      |
| `skills-review.md`             | `core/review.md`                        |
| `skills-testing.md`            | `core/testing.md`                       |
| `skills-definition-of-done.md` | `core/definition-of-done.md`            |
| `skills-js.md`                 | `core/frontend-javascript.md`           |
| `skills-css.md`                | `core/frontend-css.md`                  |
| `skills-php.md`                | `projects/joomla/php.md`                |
| `skills-js-leaflet.md`         | `projects/joomla/javascript-leaflet.md` |
| `skills-joomla.md`             | `projects/joomla/joomla.md`             |
| `skills-joomla-data-json.md`   | `projects/joomla/joomla-data-json.md`   |

## 6. Estado

Referencias internas de skills, prompts y agentes Joomla ya actualizadas al nuevo árbol `core/projects`.

## 7. Detección de Copilot (/skills y /create-skill)

Para que VS Code detecte una skill como Agent Skill, debe existir un directorio dentro de `.github/skills/` que contenga un archivo `SKILL.md` con frontmatter YAML válido.

Skill registrada en este repositorio:

- `.github/skills/joomlagen-workflow/SKILL.md`

Nota importante:

- Los archivos `.md` sueltos dentro de `core/` o `projects/` son recursos/documentación, pero no se indexan como skill invocable mientras no estén empaquetados en un directorio con `SKILL.md`.
