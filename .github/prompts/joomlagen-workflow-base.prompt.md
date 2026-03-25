---
agent: JoomlaGen
description: "Prompt base para ejecutar tareas de Joomla con flujo de skills y cierre por Definition of Done."
---

# Prompt base JoomlaGen (workflow)

Usa el agente JoomlaGen para la siguiente tarea:

[TAREA]

Contexto funcional:
- [OBJETIVO DE NEGOCIO]
- [ALCANCE EXACTO]
- [RESTRICCIONES ADICIONALES]

Flujo obligatorio a seguir:
1. Leer `.github/skills/core/architecture.md` y respetar prioridad máxima.
2. Aplicar los skills técnicos necesarios según la tarea:
   - JS: `.github/skills/core/frontend-javascript.md`
   - Leaflet (si aplica): `.github/skills/projects/joomla/javascript-leaflet.md`
   - PHP: `.github/skills/projects/joomla/php.md`
   - CSS: `.github/skills/core/frontend-css.md`
   - Joomla: `.github/skills/projects/joomla/joomla.md`
   - JSON: `.github/skills/projects/joomla/joomla-data-json.md`
3. Verificar con:
   - `.github/skills/core/review.md`
   - `.github/skills/core/testing.md`
4. Cerrar solo si cumple `.github/skills/core/definition-of-done.md`.

Criterios de implementación:
- Cambios mínimos, seguros y consistentes con Joomla MVC.
- Sin cambios estructurales grandes sin autorización.
- Solo librerías permitidas (Leaflet y OpenStreetMap).
- Sin frameworks de JS/CSS salvo autorización explícita.

Entregable esperado:
- Resumen breve de cambios.
- Lista de archivos modificados.
- Riesgos/limitaciones detectadas.
- Validación final de DoD (cumple / no cumple + motivo).
