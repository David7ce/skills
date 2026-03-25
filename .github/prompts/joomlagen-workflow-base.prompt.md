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
1. Leer `joomla-skills/skills-architecture.md` y respetar prioridad máxima.
2. Aplicar los skills técnicos necesarios según la tarea:
   - JS: `joomla-skills/skills-js.md`
   - Leaflet (si aplica): `joomla-skills/skills-js-leaflet.md`
   - PHP: `joomla-skills/skills-php.md`
   - CSS: `joomla-skills/skills-css.md`
   - Joomla: `joomla-skills/skills-joomla.md`
   - JSON: `joomla-skills/skills-joomla-data-json.md`
3. Verificar con:
   - `joomla-skills/skills-review.md`
   - `joomla-skills/skills-testing.md`
4. Cerrar solo si cumple `joomla-skills/skills-definition-of-done.md`.

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
