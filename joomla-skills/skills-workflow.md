# skills-workflow.md

## 1. Objetivo

Reglas de flujo de trabajo para que el agente genere, refactorice y revise código.

---

## 2. Principios

* ✅ Seguir reglas de `skills-architecture.md` primero
* ✅ Adaptar código existente
* ✅ Validar seguridad y coherencia
* ❌ NO improvisar cambios estructurales grandes

---

## 3. Proceso recomendado

1. Analizar estructura
2. Aplicar módulo correspondiente
3. Cargar datos de forma eficiente
4. Revisar seguridad y SEO
5. Documentar cambios mínimos en Markdown
6. Probar funcionalidad
7. Validar cierre con `skills-definition-of-done.md`

---

## 4. Versionado

* ✅ Mantener todo en Git
* ✅ Commits claros y atómicos
* ❌ NO mezclar múltiples funcionalidades en un commit

---

## 5. Buenas prácticas

* ✅ Revisar consistencia de nombres (BEM, JS modules)
* ✅ Reusar funciones comunes
* ✅ Revisar duplicación de datos o lógica
* ❌ NO modificar core sin autorización
