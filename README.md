# AI Skills

Repositorio de skills para guiar agentes de IA en proyectos de programación, con reglas de arquitectura, seguridad, calidad y flujo de trabajo.

## Objetivo

Estandarizar cómo los agentes:

- analizan el contexto del proyecto,
- implementan cambios con seguridad,
- validan calidad y criterios de cierre (DoD).

## Estructura del repositorio

- `.github/agents/`: agentes personalizados del repositorio.
- `.github/skills/`: skills por dominio en Markdown con frontmatter YAML (`name`, `description`).
- `.claude/skills/`, `.agents/skills/`: ubicaciones compatibles para otros entornos.

## Skills disponibles

- `skills-architecture.md`: reglas globales y jerarquía de decisiones.
- `skills-workflow.md`: flujo de trabajo recomendado.
- `skills-definition-of-done.md`: criterio de cierre obligatorio.
- `skills-review.md`: checklist de revisión.
- `skills-testing.md`: checklist de pruebas.
- `skills-js.md`: estándares JavaScript.
- `skills-js-leaflet.md`: reglas para Leaflet/OpenStreetMap.
- `skills-css.md`: convenciones CSS (BEM, mobile-first).
- `skills-php.md`: prácticas PHP/Joomla y seguridad.
- `skills-joomla.md`: arquitectura y buenas prácticas Joomla.
- `skills-joomla-data-json.md`: manejo de datos JSON geográficos.

## Formato de cada skill

Cada archivo debe comenzar con frontmatter YAML:

```yaml
---
name: nombre-corto-del-skill
description: Descripción breve y accionable del propósito del skill.
---
```

## Modelos recomendados

- GPT Codex
- Claude
- Listado de modelos: https://openrouter.ai/models?fmt=cards&categories=programming

## Referencias

- [Agent Skills (Open Standard)](https://agentskills.io/home)
- [Anthropics Skills · GitHub](https://github.com/anthropics/skills)
- [OpenAI Skills · GitHub](https://github.com/openai/skills)
- [Cypher Skills · GitHub](https://github.com/dkyazzentwatwa/chatgpt-skills)
- [GitHub Copilot - VSCode Docs](https://code.visualstudio.com/docs/copilot/overview)
- [GitHub Copilot Agent Skills - VSCode Docs](https://code.visualstudio.com/docs/copilot/customization/agent-skills)