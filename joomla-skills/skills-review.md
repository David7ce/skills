# skills-review.md

## 1. Objetivo

Reglas para revisar código y detectar errores o inconsistencias.

---

## 2. Principios

* ✅ Seguir `skills-architecture.md` y `skills-js.md`
* ✅ Revisar:
    * modularidad
    * seguridad
    * integridad de datos
    * consistencia de nombres
* ❌ NO aprobar código que rompe reglas críticas

---

## 3. Checklist obligatorio

* [ ] Variables y funciones modularizadas
* [ ] JS vanilla y ES Modules
* [ ] JSON solo lectura
* [ ] Uso correcto de APIs Joomla
* [ ] Override seguro
* [ ] CSS BEM
* [ ] SEO básico aplicado
* [ ] ACL respetado
* [ ] Sin librerías externas no permitidas

---

## 4. Anti-patrones

* ❌ Mezcla de responsabilidades
* ❌ Variables globales
* ❌ Datos inline innecesarios
* ❌ SQL directo sin necesidad

---

## 5. Ejemplo de revisión

> Archivo JS que mezcla UI y mapa → ❌
> Archivo JS modular, import/export, fetch correcto → ✅
