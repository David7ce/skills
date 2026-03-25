# skills-joomla.md

## 1. Objetivo

Definir las reglas y buenas prácticas para el desarrollo de **plantillas, overrides, componentes y gestión de contenido** en Joomla dentro de este proyecto.

Este archivo garantiza que:

* el agente respete la arquitectura del CMS
* evite manipulaciones peligrosas de la base de datos
* siga el flujo de creación de artículos, menús y contenido
* mantenga seguridad, SEO y ACL

---

## 2. Principios obligatorios

* Joomla es **el núcleo del sistema**, todo código PHP o interacción debe respetar MVC.
* Los overrides de plantillas deben seguir la estructura estándar:

  ```plaintext id="ov1"
  /templates/custom/
    html/
      com_content/
        article/
          default.php
  ```

* Las modificaciones deben ser **mínimas y documentadas** en Markdown separado.
* ❌ NO modificar core de Joomla.
* ❌ NO alterar flujo de render sin override oficial.

---

## 3. Uso de PHP y APIs

### 3.1 Lectura de datos

* ✅ Usar APIs de Joomla con namespaces (`Factory`, `Table`)
* ✅ Evitar SQL directo si existe método Joomla
* ✅ Sanitizar resultados
* Ejemplo correcto:

```php id="pjc23"
use Joomla\CMS\Factory;

$db = Factory::getContainer()->get('DatabaseDriver');
$query = $db->getQuery(true)
            ->select('*')
            ->from($db->quoteName('#__content'))
            ->where($db->quoteName('state') . ' = 1');
$db->setQuery($query);
$articles = $db->loadObjectList();
```

### 3.2 Inserción de contenido

* ✅ Priorizar API de Joomla para crear artículos, menús e ítems de menú
* ✅ SQL solo si la API falla
* ✅ Validar todos los campos antes de insertar

---

### 3.3 Eliminación de contenido

* ❌ NO usar SQL DELETE salvo emergencia crítica
* ✅ Usar backend Joomla (papelera)
* ⚠️ Nota: eliminación SQL directa **NO pasa por papelera** y puede romper relaciones

---

## 4. Overrides y plantillas

* ✅ Estructura obligatoria de carpetas
* ✅ Evitar mezclar PHP, HTML y JS innecesariamente
* ✅ Mantener BEM en CSS
* ❌ NO copiar/pegar core
* ✅ Documentar cambios en Markdown separado

---

## 5. Componentes custom

* ✅ Deben seguir MVC
* ✅ Evitar lógica global
* ✅ Evitar llamadas directas a DB si existe API
* ❌ NO usar dependencias externas
* ❌ NO manipulación de core directamente

---

## 6. Formularios y PDFs

* ✅ Formularios deben validar en servidor y cliente
* ✅ Usar JForm para estructuras complejas
* ✅ Generación de PDF solo mediante componentes controlados
* ❌ NO mezclar lógica JS global dentro de PHP

---

## 7. ACL y multilenguaje

* ✅ ACL básico aplicado según estándares Joomla
* ✅ Multilenguaje: usar `JText::_()` y campos multilingüe
* ❌ NO bypass de ACL
* ❌ NO hardcodear idioma

---

## 8. SEO

Nivel intermedio:

* ✅ URLs amigables
* ✅ Metatags automáticos en artículos
* ✅ Uso de schema básico si disponible
* ❌ NO duplicar contenido
* ❌ NO ignorar títulos y descripciones

---

## 9. Anti-patrones

* ❌ SQL directo innecesario
* ❌ Mezcla de lógica PHP/JS sin estructura
* ❌ Modificar core de Joomla
* ❌ Código sin documentación mínima

---

## 10. Ejemplos correctos

### 10.1 Override artículo

```php id="ov2"
defined('_JEXEC') or die;

echo '<h1 class="article__title">' . $this->item->title . '</h1>';
```

### 10.2 Creación de artículo con API

```php id="ov3"
use Joomla\CMS\Table\Table;

$article = Table::getInstance('Content');
$article->bind([
  'title' => 'Nuevo artículo',
  'state' => 1,
]);
$article->check();
$article->store();
```

---

## 11. Comportamiento esperado del agente

* Seguir reglas estrictas
* Usar APIs primero
* Evitar improvisación
* Mantener coherencia con `skills-js.md` y `skills-architecture.md`
* Documentar cambios críticos

---

## 12. Regla final

Si una acción:

* rompe MVC
* rompe seguridad
* rompe consistencia
* ignora ACL

→ está prohibida, aunque funcione técnicamente.
