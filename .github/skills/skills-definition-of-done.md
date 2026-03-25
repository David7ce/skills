---
name: definition-of-done
description: Criterios obligatorios para considerar una tarea como terminada y aprobable.
---

# skills-definition-of-done.md

## 1. Objetivo

Definir un criterio único de cierre para tareas implementadas por IA en este proyecto Joomla.

---

## 2. Definition of Done (obligatoria)

Una tarea se considera terminada solo si cumple todo lo siguiente:

1. Arquitectura respetada
   - Sigue `skills-architecture.md`
   - No introduce cambios estructurales no autorizados

2. Seguridad validada
   - Entradas validadas y salidas escapadas
   - Sin SQL inseguro
   - Riesgos XSS y CSRF cubiertos

3. Integración Joomla correcta
   - Uso de APIs internas priorizado
   - MVC y overrides respetados
   - ACL y multilenguaje no degradados

4. Frontend consistente
   - JS modular (sin globales)
   - CSS con BEM y mobile-first
   - Sin librerías externas no permitidas

5. Datos y rendimiento
   - JSON en modo solo lectura
   - Estrategia inline/AJAX aplicada con umbrales definidos
   - Sin cargas duplicadas ni bloqueo evitable de render

6. Calidad verificable
   - Checklist de `skills-review.md` completado
   - Checklist de `skills-testing.md` ejecutado
   - Cambios críticos documentados en Markdown

---

## 3. Regla final

Si cualquier punto de esta DoD falla, la tarea no se considera cerrada.
