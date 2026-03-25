# Skills para agente IA - Proyecto Joomla

## 1. Propósito

Estos archivos de skills definen **reglas, normas y buenas prácticas** para el agente de IA que trabajará en este proyecto Joomla.

Su objetivo:

- Mantener consistencia
- Evitar errores de arquitectura, seguridad y rendimiento
- Guiar generación de código, refactorización y pruebas

---

## 2. Instrucciones de uso

1. Abrir VS Code en la raíz del repositorio y trabajar con `joomla-skills/`.
2. Mantener abiertos **los archivos principales** mientras se trabaja en código:
   - `skills-architecture.md`
   - `skills-js.md`
   - `skills-joomla.md`
3. Para nuevas tareas, consultar siempre las reglas de:
   - arquitectura
   - JS
   - PHP
   - CSS
4. Usar como **guía de contexto para Copilot Chat / Claude / GPT-Codex**:
   - Al generar código, copiar la sección relevante en el prompt o mantener el archivo abierto.
   - Nunca ignorar reglas críticas de `skills-architecture.md`.

---

## 3. Jerarquía y dependencias

```plaintext
skills-architecture.md (PRIORIDAD MÁXIMA)
|
├── skills-js.md
|     └── skills-js-leaflet.md
|
├── skills-joomla.md
|     └── skills-joomla-data-json.md
|
├── skills-php.md
|
├── skills-css.md
|
├── skills-workflow.md
|
├── skills-review.md
|
├── skills-testing.md
|
└── skills-definition-of-done.md
```

---

## 4. Flujo recomendado para IA

1. Leer `skills-architecture.md`.
2. Aplicar el skill técnico principal según tarea (JS, Joomla, PHP, CSS, JSON, Leaflet).
3. Ejecutar validación con `skills-review.md` y `skills-testing.md`.
4. Confirmar cierre de tarea con `skills-definition-of-done.md`.