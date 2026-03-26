---
name: joomlagen-workflow
description: Flujo reutilizable para tareas Joomla en este repositorio. Cargar arquitectura base, skills tecnicos por tipo de cambio, validacion de calidad y criterio de cierre (Definition of Done).
argument-hint: Describe la tarea Joomla a ejecutar (ej: "crear vista de componente", "refactor JS de mapa", "ajustar estilos del template")
user-invocable: true
---

# JoomlaGen Workflow Skill

Usa este skill cuando una tarea requiera desarrollo, refactor, revision o pruebas en Joomla dentro de este workspace.

## Objetivo

Aplicar un flujo consistente, seguro y verificable, reutilizando los documentos ya definidos en [.github/skills/core](../core) y [.github/skills/projects/joomla](../projects/joomla).

## Flujo obligatorio

1. Leer [architecture.md](../core/architecture.md) y respetar sus restricciones.
2. Seleccionar skills tecnicos segun la tarea:
   - JavaScript: [frontend-javascript.md](../core/frontend-javascript.md)
   - CSS: [frontend-css.md](../core/frontend-css.md)
   - Joomla general: [joomla.md](../projects/joomla/joomla.md)
   - PHP: [php.md](../projects/joomla/php.md)
   - Leaflet/OpenStreetMap (si aplica): [javascript-leaflet.md](../projects/joomla/javascript-leaflet.md)
   - JSON de datos (si aplica): [joomla-data-json.md](../projects/joomla/joomla-data-json.md)
3. Implementar cambios minimos y modulares, evitando cambios estructurales grandes sin autorizacion.
4. Ejecutar verificacion con:
   - [review.md](../core/review.md)
   - [testing.md](../core/testing.md)
5. Cerrar solo si cumple [definition-of-done.md](../core/definition-of-done.md).

## Reglas de seguridad y consistencia

- Mantener coherencia con MVC de Joomla y convenciones del repositorio.
- No introducir dependencias nuevas sin necesidad explicita.
- Para mapas, usar solo Leaflet y OpenStreetMap.
- Priorizar cambios pequenos, verificables y faciles de revertir.

## Entrada esperada

Describe siempre:
- objetivo de negocio/funcional
- alcance del cambio (archivo, modulo, componente)
- restricciones (performance, seguridad, UI, compatibilidad)

## Resultado esperado

- Cambios implementados en archivos correctos
- Validacion tecnica y funcional completada
- Riesgos y siguientes pasos documentados si aplica
