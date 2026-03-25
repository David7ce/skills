# skills-data-json.md

## 1. Objetivo

Reglas para manejar JSON estáticos de datos geográficos dentro del proyecto. Garantiza:

* eficiencia
* solo lectura
* compatibilidad con mapa
* seguridad

---

## 2. Reglas generales

* ✅ JSON ubicados en `/data/`
* ✅ Fragmentados (≈13 archivos)
* ✅ Solo lectura
* ❌ NO convertir en base de datos dinámica
* ❌ NO modificar en runtime

---

## 3. Carga de JSON

* Estrategia híbrida:

| Tamaño / importancia | Método         |
|----------------------|----------------|
| Pequeño / crítico    | Inline         |
| Grande               | AJAX (`fetch`) |

* ✅ Evitar múltiples cargas
* ✅ Manejar errores
* ❌ NO duplicar datos

---

## 4. Validación

* ✅ JSON debe ser parseable (`JSON.parse`)
* ✅ Sanitizar contenido antes de usar en JS
* ✅ Revisar consistencia con estructura definida
* ❌ NO asumir integridad de datos

---

## 5. Anti-patrones

* ❌ Mezclar múltiples datasets en un solo archivo
* ❌ Modificar JSON desde frontend
* ❌ Cargar JSON gigantes inline

---

## 6. Ejemplo correcto

```js id="json1"
import { loadData } from '../core/data.js';

const municipios = await loadData('/data/municipios.json');
```
