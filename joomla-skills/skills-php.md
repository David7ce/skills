# skills-php.md

## 1. Objetivo

Definir las reglas de desarrollo en PHP para Joomla y el proyecto, asegurando:

* uso correcto de APIs
* seguridad
* compatibilidad con JS y JSON
* integridad de datos

---

## 2. Principios obligatorios

* ✅ PHP solo para backend Joomla
* ✅ Integración con JS mediante JSON seguro o inline controlado
* ✅ Validación de todas las entradas
* ✅ Sanitización de salidas
* ❌ NO modificar core de Joomla
* ❌ NO saltarse MVC
* ❌ NO SQL directo innecesario

---

## 3. Interacción con Joomla

* ✅ Crear artículos, menús e ítems de menú usando APIs Joomla
* ✅ Overrides mediante APIs modernas de Joomla (`Table`, `Factory`)
* ✅ Evitar consultas directas cuando exista API
* ✅ Validar integridad de datos antes de guardar

---

## 4. Seguridad

* ✅ Escape de salida
* ✅ Validación de formularios
* ✅ Prevención de XSS, CSRF
* ✅ Sanitización de datos JSON antes de enviarlos a JS
* ❌ NO usar `$_GET`/`$_POST` sin sanitizar

---

## 5. Anti-patrones

* ❌ Mezclar lógica JS/HTML/PHP sin estructura
* ❌ SQL directo innecesario
* ❌ Manipulación de archivos JSON desde PHP sin control
* ❌ Variables globales

---

## 6. Ejemplos correctos

### 6.1 Creación segura de artículo

```php id="php1"
use Joomla\CMS\Table\Table;

$article = Table::getInstance('Content');
$article->bind([
     'title' => 'Título seguro',
     'state' => 1,
]);
$article->check();
$article->store();
```

### 6.2 Generación de JSON seguro para JS

```php id="php2"
$data = json_decode(file_get_contents(JPATH_ROOT . '/data/file.json'), true);
echo '<script type="application/json" id="data-json">'
     . json_encode($data, JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT)
     . '</script>';
```
