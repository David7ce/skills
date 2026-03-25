# skills-testing.md

## 1. Objetivo

Definir pruebas obligatorias y revisión de funcionalidades críticas.

---

## 2. Principios

* ✅ Testear formularios (validación, envío)
* ✅ Testear mapa (filtros, búsqueda, clustering)
* ✅ Testear generación de PDFs
* ✅ Validar integridad de JSON y data
* ❌ NO ignorar errores de render

---

## 3. Estrategia

* Manual con pruebas predefinidas
* Automatizado en JS donde sea crítico
* Documentar fallos en Markdown
* ❌ NO asumir que todo funciona sin prueba

---

## 4. Checklist

* [ ] Formularios funcionan (JS y server-side)
* [ ] Mapas renderizan correctamente
* [ ] Filtros aplican correctamente
* [ ] PDF generado correctamente
* [ ] Seguridad validada (XSS, CSRF)
* [ ] Integración Joomla respetada

---

## 5. Anti-patrones

* ❌ Saltarse validaciones
* ❌ Modificar data sin comprobación
* ❌ Ignorar errores en la consola
