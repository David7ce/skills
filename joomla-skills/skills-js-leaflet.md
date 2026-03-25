# skills-js-leaflet.md

## 1. Objetivo

Establecer reglas para el uso de Leaflet y OpenStreetMap.

---

## 2. Principios

* ✅ Separar mapa de UI
* ✅ Modularizar capas, markers y filtros
* ✅ Usar clustering
* ❌ No mezclar lógica global con DOM
* ❌ No cargar datos directamente dentro del mapa

---

## 3. Estructura recomendada

```plaintext id="leaf1"
/js/map/
  map.js
  markers.js
  layers.js
  filters.js
```

---

## 4. Carga de datos

* ✅ Usar `loadData()` de `core`
* ✅ Manejar errores
* ✅ Evitar render bloqueante

---

## 5. Ejemplo modular

```js id="leaf2"
import { loadData } from '../core/data.js';
import { initMap } from './map.js';
import { addMarkers } from './markers.js';

const map = initMap('map-container');
const data = await loadData('/data/comercios.json');
addMarkers(map, data);
```

---

## 6. Anti-patrones

* ❌ Mezclar UI y mapa
* ❌ Data inline innecesaria
* ❌ Variables globales
