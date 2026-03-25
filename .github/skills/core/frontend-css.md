---
name: css
description: Estándares CSS del proyecto con BEM, mobile-first y organización por componentes.
---

# frontend-css.md

## 1. Objetivo

Definir reglas de desarrollo de CSS para plantillas y overrides, asegurando:

* consistencia
* mantenibilidad
* compatibilidad con BEM y diseño móvil

---

## 2. Principios obligatorios

* ✅ BEM obligatorio (`block__element--modifier`)
* ✅ Mobile-first
* ✅ Uso de variables CSS (`--color-primary`, `--spacing-lg`)
* ✅ Anidación simple y lógica
* ❌ NO usar frameworks CSS salvo autorización explícita del proyecto
* ❌ NO clases genéricas o ambiguas

---

## 3. Organización de CSS

* Archivos separados por componente o funcionalidad
* Plantilla principal:

```plaintext id="css1"
/css/
  core/
  layout/
  components/
  pages/
```

* ❌ NO mezclar estilos globales con específicos de componente
* ❌ NO duplicar estilos innecesariamente

---

## 4. Estilo y nomenclatura

* ✅ Nombres de clase claros y descriptivos
* ✅ Evitar abreviaturas confusas
* ✅ Variables para colores, tamaños y espaciado
* ✅ Media queries definidas con nombres claros

---

## 5. Anti-patrones

* ❌ Uso de !important indiscriminado
* ❌ Clases duplicadas
* ❌ Mezcla de BEM con clases genéricas
* ❌ Estilos en línea en HTML salvo casos críticos

---

## 6. Ejemplos correctos

### 6.1 BEM simple

```css id="css2"
.card__title--highlight {
  color: var(--color-primary);
  font-size: var(--font-lg);
}
```

### 6.2 Media query

```css id="css3"
@media (max-width: 768px) {
  .card__title {
    font-size: var(--font-md);
  }
}
```

---

## 7. Adaptación al proyecto

* ✅ Revisar CSS existente antes de añadir
* ✅ Seguir jerarquía de carpetas
* ✅ Mantener consistencia con JS y HTML
