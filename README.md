# ai-copilot-config

Repositorio para documentar y versionar la configuración de GitHub Copilot en VS Code, orientado a integrar modelos de IA en flujos reales de desarrollo.

## Objetivo

Definir una base reutilizable para que los agentes y modelos de IA:

- entiendan las convenciones del proyecto,
- usen las herramientas adecuadas,
- y produzcan resultados consistentes desde el primer intento.

Los agentes funcionan mejor cuando comprenden las convenciones de tu proyecto, cuentan con las herramientas adecuadas y utilizan un modelo apropiado para la tarea. VS Code te ofrece varias maneras de personalizar la IA para que genere código que se ajuste a tu base de código desde el principio, evitando así correcciones manuales posteriores.

- **[Instrucciones personalizadas](https://code.visualstudio.com/docs/copilot/customization/custom-instructions)**: Define convenciones de codificación para todo el proyecto, de modo que la IA genere código que se ajuste a tu estilo.
- **[Habilidades del agente](https://code.visualstudio.com/docs/copilot/customization/agent-skills)**: Enseña a Copilot capacidades especializadas que funcionan en VS Code, GitHub Copilot CLI y el agente de codificación de GitHub Copilot.
- **[Agentes personalizados](https://code.visualstudio.com/docs/copilot/customization/custom-agents)**: Crea agentes que asuman un rol específico, como revisor de código o redactor de documentación, con sus propias herramientas e instrucciones.
- **[Servidores MCP](https://code.visualstudio.com/docs/copilot/customization/mcp-servers)**: Amplía las funcionalidades de los agentes con herramientas de servidores MCP o extensiones de Marketplace.
- **[Ganchos](https://code.visualstudio.com/docs/copilot/customization/hooks)**: Ejecuta comandos personalizados en eventos específicos para la automatización y la aplicación de políticas.

## Estructura base sugerida

- `.github/instructions/`: instrucciones globales y por dominio.
- `.github/skills/`: skills en Markdown con frontmatter YAML (core + por proyecto).
- `.github/agents/`: agentes personalizados con rol, herramientas e instrucciones.
- `.vscode/mcp.json`: configuración de servidores MCP.
- `.github/hooks/`: hooks para validaciones y automatización.

## Agrupación de skills por proyecto (sin conflictos)

Puedes agrupar skills por tipo y por proyecto sin duplicar reglas:

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

### Reglas para evitar conflicto de skills

1. Define reglas comunes solo en `core` (HTML, CSS, JS, testing, review, seguridad).
2. Usa `projects/*` solo para decisiones específicas del framework.
3. Mantén una única fuente de verdad por tema (no duplicar el mismo estándar en dos skills).
4. Declara precedencia explícita: `architecture` → `core técnico` → `project` → `task`.
5. Si dos reglas chocan, prevalece la más específica del proyecto, documentando la excepción.

## Formato de cada herramienta (instrucciones, habilidades, agentes, mcp, ganchos)

### Formato de instrucciones

Archivo de ejemplo (`.github/instructions/general.instructions.md`):

```md
---
applyTo: "**/*"
---

## Convenciones del proyecto
- Usa nombres descriptivos en funciones y variables.
- Prioriza cambios pequeños y reversibles.
- Si hay dudas de alcance, pide confirmación antes de refactorizar.
```

### Formato de habilidades

Cada skill debe comenzar con frontmatter YAML:

```yaml
---
name: nombre-corto-del-skill
description: Descripción breve y accionable del propósito del skill.
---
```

Ejemplo (`.github/skills/core/review.md`):

```md
---
name: review-checklist
description: Checklist breve para revisar calidad, seguridad y mantenibilidad.
---

# Cuándo usar
- Antes de crear PR.

# Pasos
1. Verificar alcance y regresiones.
2. Revisar errores y edge cases.
3. Confirmar pruebas mínimas.
```

### Formato de agentes

Archivo de ejemplo (`.github/agents/code-reviewer.agent.md`):

```md
---
name: code-reviewer
description: Agente orientado a revisar calidad y riesgos antes de merge.
tools: ["read_file", "grep_search", "get_errors"]
---

## Rol
Revisar cambios y reportar hallazgos accionables, priorizados por severidad.

## Criterios
- Seguridad y validación de entrada.
- Legibilidad y consistencia.
- Cobertura mínima de pruebas para cambios críticos.
```

### Formato de MCP

Archivo de ejemplo (`.vscode/mcp.json`):

```json
{
	"servers": {
		"filesystem": {
			"command": "npx",
			"args": ["-y", "@modelcontextprotocol/server-filesystem", "."]
		}
	}
}
```

### Formato de ganchos/hooks

Archivo de ejemplo (`.github/hooks/format.json`):

```json
{
	"name": "format-check",
	"event": "beforeCommit",
	"run": "npm run lint && npm run format:check"
}
```

## Flujo recomendado

1. Define instrucciones globales en `.github/instructions/`.
2. Carga primero skills `core` y luego skills `projects/<framework>` según el repositorio (Joomla, Astro, etc.).
3. Crea agentes por rol y por stack en `.github/agents/`.
4. Conecta herramientas externas con `.vscode/mcp.json`.
5. Refuerza políticas con hooks en `.github/hooks/`.

## Modelos sugeridos

> Catálogo de modelos: [Modelos de Openrouter](https://openrouter.ai/models?fmt=cards&categories=programming). El catálogo cambia con frecuencia; valida disponibilidad y precios antes de estandarizar.

| Compañía  | Modelo (ejemplo)            | Tipo recomendado                           |
|-----------|-----------------------------|--------------------------------------------|
| Anthropic | Claude (familia)            | Arquitectura, revisión y redacción técnica |
| Alibaba   | Qwen (familia)              | Tareas generales de código                 |
| DeepSeek  | DeepSeek (familia)          | Programación y depuración                  |
| Google    | Gemini (familia)            | Análisis multimodal y documentación        |
| Kimi      | Kimi (familia)              | Contexto largo y síntesis                  |
| MiniMax   | MiniMax (familia)           | Asistencia general                         |
| OpenAI    | GPT-Codex / GPT-5 (familia) | Implementación y refactorización guiada    |
| Xiaomi    | MiMo (familia)              | Soporte general                            |
| Z.ai      | GLM (familia)               | Automatización y tareas mixtas             |

## Referencias

- [GitHub Copilot - Documentación de VS Code](https://code.visualstudio.com/docs/copilot/overview)
- [Habilidades de Agentes (Estándar abierto)](https://agentskills.io/home)
- [Repositorio de Habilidades de Anthropics · GitHub](https://github.com/anthropics/skills)
- [Repositorio de Habilidades de OpenAI · GitHub](https://github.com/openai/skills)
