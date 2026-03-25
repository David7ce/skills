---
name: testing
description: Estrategia y checklist de pruebas funcionales y de seguridad para funcionalidades críticas.
---

# skills-testing.md

## 1. Objetivo

Definir pruebas obligatorias y revisión de funcionalidades críticas.

---

## 2. Principios

* ✅ Probar formularios (validación, envío)
* ✅ Probar mapa (filtros, búsqueda, clustering)
* ✅ Probar generación de PDFs
* ✅ Validar integridad de JSON y datos
* ❌ NO ignorar errores de render

---

## 3. Estrategia

* Manual con pruebas predefinidas
* Automatizado en JS donde sea crítico
* Documentar fallos en Markdown
* ❌ NO asumir que todo funciona sin prueba

---

## 4. Checklist

* [ ] Formularios funcionan (JS y validación en servidor)
* [ ] Mapas renderizan correctamente
* [ ] Filtros aplican correctamente
* [ ] PDF generado correctamente
* [ ] Seguridad validada (XSS, CSRF)
* [ ] Integración Joomla respetada

---

## 5. Cierre de testing

* ✅ Confirmar `skills-definition-of-done.md` antes de marcar tarea como finalizada

---

## 6. Anti-patrones

* ❌ Saltarse validaciones
* ❌ Modificar datos sin comprobación
* ❌ Ignorar errores en la consola
