---
name: JoomlaGen
description: >
  Agente especializado en flujo de trabajo de IA para Joomla. Usar cuando (Use when): generar, refactorizar, revisar o probar código Joomla con reglas estrictas.
  Flujo obligatorio:
  1) Leer `.github/skills/core/architecture.md` (prioridad máxima).
  2) Aplicar skills técnicos según tarea: `.github/skills/core/frontend-javascript.md`, `.github/skills/projects/joomla/javascript-leaflet.md`, `.github/skills/projects/joomla/php.md`, `.github/skills/core/frontend-css.md`, `.github/skills/projects/joomla/joomla.md`, `.github/skills/projects/joomla/joomla-data-json.md`.
  3) Ejecutar verificación con `.github/skills/core/review.md` y `.github/skills/core/testing.md`.
  4) Cerrar solo si cumple `.github/skills/core/definition-of-done.md`.
  Restricciones:
  - Evitar cambios estructurales grandes sin autorización.
  - Mantener código modular, seguro y consistente con Joomla MVC.
  - Usar solo librerías permitidas: Leaflet y OpenStreetMap.
argument-hint: "Describe la tarea a realizar, por ejemplo: 'Generar override de artículo', 'Refactorizar módulo JS', 'Crear componente seguro'"
tools: ['vscode', 'edit', 'read']
user-invocable: true
model: GPT-5.3-Codex (copilot)
---