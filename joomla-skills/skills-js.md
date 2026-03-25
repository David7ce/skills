# skills-js.md

## 1. Objetivo

Definir las reglas obligatorias para el desarrollo en JavaScript dentro del proyecto.

Este documento regula:

* estructura del código
* organización de módulos
* carga de datos
* interacción con Joomla y JSON

---

## 2. Principios obligatorios

* JavaScript debe ser:

  * modular
  * predecible
  * mantenible

* El código debe:

  * evitar duplicación
  * evitar lógica global
  * ser desacoplado

---

## 3. Reglas globales

### 3.1 Base tecnológica

* ✅ Usar JavaScript nativo (vanilla)
* ✅ Usar ES Modules (`import/export`)
* ❌ NO usar frameworks (React, Vue, etc.)
* ❌ NO usar librerías externas (excepto Leaflet)

---

### 3.2 Estructura obligatoria

Todo el JS debe seguir esta estructura:

```plaintext
/js/
  core/
  map/
  ui/
```

#### core/

Responsabilidad:

* utilidades
* helpers
* acceso a datos
* lógica común

#### map/

Responsabilidad:

* inicialización del mapa
* capas
* markers
* clustering

#### ui/

Responsabilidad:

* interacción usuario
* formularios
* filtros
* búsqueda

---

### 3.3 Modularidad

* ✅ Cada archivo debe tener una única responsabilidad
* ✅ Usar `export` / `import`
* ❌ NO usar variables globales
* ❌ NO duplicar lógica entre módulos

---

## 4. Carga de datos (CRÍTICO)

### Estrategia obligatoria

| Caso                   | Método |
| ---------------------- | ------ |
| JSON pequeño o crítico | Inline |
| JSON grande            | AJAX   |

Umbrales operativos:

* Inline: hasta 30 KB por payload y solo si afecta la primera renderización.
* AJAX: obligatorio para payloads mayores a 30 KB o cuando no sea crítico para la primera renderización.

---

### 4.1 Inline (PHP → JS)

Uso permitido solo si:

* datos pequeños
* necesarios al inicio

Ejemplo correcto:

```html
<script type="application/json" id="map-data">
{...}
</script>
```

---

### 4.2 AJAX (recomendado para JSON grandes)

* ✅ Usar `fetch`
* ✅ Manejar errores
* ✅ Evitar múltiples cargas innecesarias

Ejemplo:

```js
export async function loadData(url) {
  const response = await fetch(url);
  if (!response.ok) throw new Error('Error loading data');
  return response.json();
}
```

---

### 4.3 Reglas críticas

* ❌ NO cargar múltiples veces el mismo JSON
* ❌ NO bloquear el render inicial con JSON grandes
* ❌ NO mezclar inline + AJAX sin motivo

---

## 5. Integración con PHP / Joomla

### 5.1 Datos desde PHP

* ✅ usar JSON embebido seguro
* ❌ NO concatenar strings manualmente

---

### 5.2 Interacción dinámica

* Preferencia:

  * AJAX sobre manipulación inline

---

## 6. Arquitectura del mapa (Leaflet)

### Obligatorio:

* separar responsabilidades

#### Ejemplo:

```plaintext
/map/
  map.js        → inicialización
  markers.js    → gestión de markers
  filters.js    → lógica de filtros
  layers.js     → capas base
```

---

### Reglas:

* ❌ NO mezclar lógica de mapa con UI
* ❌ NO cargar datos directamente en map.js
* ✅ usar funciones reutilizables

---

## 7. Filtros y búsqueda

* deben ser:

  * independientes del mapa
  * reutilizables

* ❌ NO acoplar filtros a Leaflet directamente

---

## 8. Manejo de estado

* usar variables locales en módulos
* evitar estado global

### Permitido:

```js
let currentFilters = {};
```

### Prohibido:

```js
window.filters = {};
```

---

## 9. Rendimiento (CRÍTICO)

### JSON grandes:

* ✅ cargar bajo demanda
* ✅ procesar una vez
* ✅ reutilizar resultados

### Mapa:

* ✅ usar clustering
* ✅ evitar re-render completo

---

## 10. Eventos

* usar `addEventListener`
* separar lógica de evento y acción

❌ Prohibido:

```js
element.onclick = function() {}
```

---

## 11. Anti-patrones

### ❌ Código global

```js
var data = [];
```

---

### ❌ Mezcla de responsabilidades

```js
// map + UI + fetch todo junto
```

---

### ❌ Duplicación de fetch

```js
fetch('/data/file.json');
fetch('/data/file.json');
```

---

### ❌ DOM acoplado

```js
document.querySelector('.btn').onclick = ...
```

(sin control ni estructura)

---

## 12. Ejemplos correctos

### ✅ Módulo limpio

```js
export function initMap(containerId) {
  return L.map(containerId);
}
```

---

### ✅ Separación de datos

```js
import { loadData } from '../core/api.js';
```

---

### ✅ UI desacoplada

```js
button.addEventListener('click', handleClick);
```

---

## 13. Adaptación al proyecto

El agente debe:

* analizar estructura existente
* respetarla
* mejorar sin romperla

---

## 14. Regla final

Si el código:

* mezcla responsabilidades
* rompe modularidad
* introduce dependencias

→ es incorrecto, aunque funcione.
