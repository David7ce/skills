---
name: review
description: Checklist de revisión técnica para validar arquitectura, seguridad y calidad antes de aprobar.
---

# review.md

## 1. Objetivo

Reglas para revisar código y detectar errores o inconsistencias.

---

## 2. Principios

* ✅ Seguir `architecture.md` y `frontend-javascript.md`
* ✅ Revisar:
    * modularidad
    * seguridad
    * integridad de datos
    * consistencia de nombres
* ❌ NO aprobar código que rompe reglas críticas

---

## 3. Checklist obligatorio

* [ ] Variables y funciones modularizadas
* [ ] JS nativo (vanilla) y ES Modules
* [ ] JSON solo lectura
* [ ] Uso correcto de APIs Joomla
* [ ] Override seguro
* [ ] CSS BEM
* [ ] SEO básico aplicado
* [ ] ACL respetado
* [ ] Sin librerías externas no permitidas

---

## 4. Cierre de revisión

* ✅ Confirmar `definition-of-done.md` antes de aprobar

---

## 5. Anti-patrones

* ❌ Mezcla de responsabilidades
* ❌ Variables globales
* ❌ Datos inline innecesarios
* ❌ SQL directo sin necesidad

---

## 6. Ejemplo de revisión

> Archivo JS que mezcla UI y mapa → ❌
> Archivo JS modular, import/export, fetch correcto → ✅
