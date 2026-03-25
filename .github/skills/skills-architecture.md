---
name: architecture
description: Reglas arquitectónicas globales, prioridades y restricciones obligatorias del proyecto.
---

# skills-architecture.md

## 1. Objetivo

Definir las **reglas globales, restricciones y decisiones arquitectónicas** del proyecto.
Este documento tiene **prioridad máxima** sobre cualquier otro `skills.md`.

---

## 2. Principios obligatorios

* El sistema se basa en Joomla como núcleo arquitectónico.

* El agente debe **adaptarse al sistema existente antes de modificarlo**.

* Se prioriza:

  1. Seguridad
  2. Consistencia
  3. Mantenibilidad
  4. Rendimiento

* El agente **NO toma decisiones estructurales grandes**.

* Cualquier cambio estructural requiere redefinir los `skills.md`.

---

## 3. Jerarquía de decisiones

En caso de conflicto, el agente debe seguir este orden:

1. `skills-architecture.md`
2. Reglas específicas del proyecto
3. APIs de Joomla
4. Buenas prácticas generales

---

## 4. Reglas globales obligatorias

### 4.1 Joomla

* ✅ Usar siempre APIs internas de Joomla

* ✅ Respetar MVC

* ✅ Usar overrides correctamente

* ❌ NO acceder directamente a la base de datos si existe API

* ❌ NO romper el flujo de renderizado de Joomla

* ❌ NO crear lógica fuera del sistema (hacks)

---

### 4.2 Base de datos

#### Uso permitido:

* Lectura de datos
* Inserción:

  * artículos
  * menús
  * ítems de menú

#### Reglas:

* ✅ Priorizar APIs Joomla SIEMPRE
* ⚠️ Usar SQL solo si la API no es viable

#### Eliminación:

* ❌ NO usar DELETE en SQL
* ✅ Usar backend de Joomla (papelera)

#### Riesgos conocidos:

* SQL directo:

  * no respeta integridad
  * puede generar datos huérfanos
  * no ejecuta lógica interna

---

### 4.3 JSON (datos geográficos)

* ✅ Solo lectura

* ✅ Ubicación: `/data/`

* ✅ Generados desde CSV

* ❌ NO modificar en tiempo de ejecución

* ❌ NO convertir en sistema dinámico

* ❌ NO tratar como base de datos relacional

---

### 4.4 JavaScript

* ✅ Vanilla JS obligatorio
* ✅ Uso de ES Modules permitido
* ✅ Estructura modular obligatoria

```plaintext
/js/
  core/
  map/
  ui/
```

* ❌ NO usar frameworks
* ❌ NO usar librerías externas (excepto mapas)
* ❌ NO scripts globales sin estructura

---

### 4.5 Carga de datos

Estrategia obligatoria:

| Caso                    | Método |
| ----------------------- | ------ |
| Datos críticos pequeños | Inline |
| Datos grandes           | AJAX   |

Umbrales operativos:

* Inline: hasta 30 KB por payload y solo si es crítico para primer render.
* AJAX: obligatorio para payloads mayores a 30 KB o datos no críticos de primer render.

* ❌ NO cargar JSON grandes inline sin justificación
* ❌ NO duplicar datos innecesariamente

---

### 4.6 CSS

* ✅ BEM obligatorio

* ✅ Mobile-first

* ✅ Uso de variables CSS

* ❌ NO usar frameworks CSS salvo autorización explícita del proyecto

* ❌ NO clases ambiguas o genéricas

* El sistema debe evolucionar hacia un **design system formal**

---

### 4.7 Librerías externas

Permitidas:

* Leaflet
* OpenStreetMap

Prohibidas:

* Google Maps
* frameworks JS
* librerías adicionales sin autorización

---

### 4.8 Build tools

* ❌ NO usar bundlers
* ❌ NO pipelines de build
* ❌ NO herramientas externas de compilación

---

## 5. Seguridad (CRÍTICO)

El agente debe actuar como si el código fuera producción.

### Obligatorio:

* Sanitización de datos
* Escape de salida
* Validación de entradas
* Protección contra XSS y CSRF

### Prohibido:

* SQL sin sanitizar
* HTML sin escapar
* confiar en datos del usuario

---

## 6. Adaptación al código existente

El agente debe:

* ✅ analizar estructura actual
* ✅ respetar patrones existentes
* ✅ mejorar sin romper

Prohibido:

* ❌ reestructurar todo
* ❌ imponer arquitectura sin contexto

---

## 7. Anti-patrones (PROHIBIDOS)

### ❌ Uso de librerías no permitidas

```js
import axios from 'axios'
```

---

### ❌ SQL directo innecesario

```php
$db->setQuery("SELECT * FROM #__content");
```

(Si existe método Joomla → usarlo)

---

### ❌ JSON como base de datos

```js
data.push(newItem)
saveToFile(data)
```

---

### ❌ JS sin estructura

```html
<script>
var data = ...
</script>
```

---

### ❌ CSS no estructurado

```css
.red-box {
  color: red;
}
```

---

## 8. Ejemplos correctos

### ✅ PHP seguro

```php
$data = json_decode(file_get_contents($path), true);
```

---

### ✅ JSON embebido seguro

```php
<script type="application/json" id="map-data">
<?= json_encode($data, JSON_HEX_TAG | JSON_HEX_AMP) ?>
</script>
```

---

### ✅ JS modular

```js
import { loadMap } from './map/map.js';
```

---

### ✅ CSS BEM

```css
.card__title--highlight {
  color: var(--color-primary);
}
```

---

## 9. Comportamiento esperado del agente

El agente debe:

* seguir reglas estrictas
* justificar excepciones
* priorizar seguridad
* evitar decisiones implícitas

El agente NO debe:

* improvisar arquitectura
* introducir dependencias
* romper el sistema existente

---

## 10. Regla final

Si una acción:

* rompe Joomla
* rompe seguridad
* rompe consistencia

→ está prohibida, aunque funcione técnicamente.
