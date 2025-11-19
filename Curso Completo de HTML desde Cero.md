=================================
Tabla de Contenidos
-------------------

*   [Introducción](#introduction)
*   [¿Qué es HTML?](#what-is-html)
*   [Requisitos](#requirements)
*   [Creando Carpeta + Extensión](#creating-folder)
*   [¿De qué se encarga y no HTML?](#html-responsibilities)
*   [Primer Archivo HTML](#first-html-file)
*   [¿Qué son las etiquetas?](#tags)
*   [Semántica](#semantics)
*   [Cómo usar la extensión](#using-extension)
*   [Headings (h1-h6)](#headings)
*   [Párrafos](#paragraphs)
*   [Elementos Anidados (strong)](#nested-elements)
*   [Lista Desordenada](#unordered-lists)
*   [Mala Práctica](#bad-practices)
*   [Elementos de Reemplazo (img, input, br…)](#replacement-elements)
*   [Atributos](#attributes)
*   [Detalle Importante de los Atributos](#important-attribute-details)
*   [Atributos Booleanos](#boolean-attributes)
*   [No Usar Mayúsculas](#avoid-uppercase)
*   [Atributo ID](#id-attribute)
*   [Atributo Class](#class-attribute)
*   [MDN](#mdn)
*   [Etiqueta Center](#center-tag)
*   [Etiqueta Em](#em-tag)
*   [Estilos por Defecto](#default-styles)
*   [Estructura Básica](#basic-structure)
*   [¿Para qué sirve el Head y el Body?](#head-body)
*   [Metadato UTF-8](#utf8-metadata)
*   [Metadato ViewPort](#viewport-metadata)
*   [Etiqueta Title](#title-tag)
*   [Metadato Robots y Theme Color](#robots-theme-color)
*   [Favicon](#favicon)
*   [Etiquetas para el SEO](#seo-tags)
*   [Etiqueta Style](#style-tag)
*   [HTML Semántico](#semantic-html)
*   [Ejemplo de HTML Semántico](#example-semantic-html)
*   [Etiqueta Article](#article-tag)
*   [Etiqueta Small](#small-tag)
*   [Continuando Semántica](#continuing-semantics)
*   [Etiqueta Aside](#aside-tag)
*   [¿Por qué tantos headers, qué es section, aside, article?](#headers-section)
*   [Etiqueta Main y Anchor](#main-anchor)
*   [Atributo rel="noreferer"](#rel-noreferer-attribute)
*   [Div y Span](#div-span)
*   [Atributo Role](#role-attribute)
*   [Enlaces Especiales](#special-links)
*   [Atributos de Listas (ol, ul)](#list-attributes)
*   [Etiquetas de Formulario](#form-tags)
*   [Fieldset, Label, Input](#fieldset-label-input)
*   [Elementos en Línea y de Bloque](#inline-block-elements)
*   [Continuando con el Formulario](#continuing-form)
*   [Validaciones de Formularios](#form-validation)
*   [Datalist](#datalist)
*   [Etiqueta Details](#details-tag)
*   [Input Submit vs Button Submit](#input-submit-vs-button-submit)
*   [Etiqueta de Video](#video-tag)
*   [Etiqueta Audio](#audio-tag)
*   [Atributo loading lazy](#loading-lazy-attribute)
*   [Iframes](#iframes)
*   [Etiqueta Dialog (para Modales)](#dialog-tag)
*   [Despedida](#farewell)

Introducción
------------

Hoy vamos a hacer un curso de HTML desde cero. HTML es el lenguaje más importante que existe en internet. Todo lo que veis en cualquier página web que estáis viendo a día de hoy, casi el 99.9% tiene HTML. Sin HTML, no veríais absolutamente nada. Es el lenguaje de marcado que se está utilizando para elaborar páginas web desde 1993.

¿Qué es HTML?
-------------

HTML son las siglas de Hypertext Markup Language, que significa lenguaje de marcado de hipertexto. Es un lenguaje de marcado que se enfoca en cómo se marca nuestro contenido, describiendo la estructura y el contenido de nuestra página web.

Requisitos
----------

Para seguir el curso necesitáis un editor de código. Podéis utilizar el que queráis, pero se recomienda Visual Studio Code, que es totalmente gratuito y disponible para Windows, Linux y macOS.

Creando Carpeta + Extensión
---------------------------

Vamos a crear una carpeta llamada "curso HTML" y abriremos nuestro editor favorito. Si utilizáis Visual Studio Code, hay una extensión llamada Live Preview que facilitará la visualización de cambios en tiempo real.

¿De qué se encarga y no HTML?
-----------------------------

HTML no se encarga de la presentación; eso es tarea de CSS. HTML describe el contenido y la estructura, mientras que CSS se encarga de cómo se ve visualmente.

Primer Archivo HTML
-------------------

Para crear un archivo HTML, debemos usar la extensión .html. Normalmente, este archivo se llama "index.html" porque es el archivo que se busca por defecto al entrar en una página web.

¿Qué son las etiquetas?
-----------------------

Las etiquetas en HTML son los elementos que crean el contenido. Por ejemplo, para un título principal se utiliza la etiqueta `h1`.

Semántica
---------

La semántica en HTML es crucial. Describe el significado de los elementos en la página web. Por ejemplo, un `h1` es un encabezado principal, mientras que un `p` es un párrafo.

Cómo usar la extensión
----------------------

La extensión Live Preview permite ver en tiempo real los cambios que realizamos en el código HTML sin necesidad de refrescar la página manualmente.

Headings (h1-h6)
----------------

Los headings van de `h1` a `h6`, donde `h1` es el más importante y `h6` es el menos importante.

Párrafos
--------

Los párrafos se crean con la etiqueta `p`, que permite separar el texto en bloques.

Elementos Anidados (strong)
---------------------------

HTML permite anidar elementos. Por ejemplo, dentro de un párrafo podemos tener un elemento `strong` para destacar texto importante.

Lista Desordenada
-----------------

Las listas desordenadas se crean con la etiqueta `ul` y cada elemento de la lista se define con `li`.

Mala Práctica
-------------

HTML permite obviar algunas etiquetas, pero no es recomendable hacerlo, ya que puede causar problemas en el futuro.

Elementos de Reemplazo (img, input, br…)
----------------------------------------

Los elementos de reemplazo como `img` y `input` no necesitan etiquetas de cierre y se utilizan para insertar contenido multimedia.

Atributos
---------

Los atributos en HTML proporcionan información adicional a los elementos. Por ejemplo, el atributo `src` en las imágenes indica la fuente de la imagen.

Detalle Importante de los Atributos
-----------------------------------

Algunos atributos son globales y pueden utilizarse en cualquier etiqueta, como `class` e `id`.

Atributos Booleanos
-------------------

Existen atributos booleanos que no necesitan un valor. Por ejemplo, el atributo `hidden` se utiliza para ocultar elementos.

No Usar Mayúsculas
------------------

HTML no es sensible a mayúsculas y minúsculas, pero se recomienda utilizar siempre minúsculas para mantener la consistencia.

Atributo ID
-----------

El atributo `id` se utiliza para identificar de manera única un elemento en el documento.

Atributo Class
--------------

El atributo `class` se utiliza para clasificar varios elementos y aplicar estilos a ellos.

MDN
---

MDN es una excelente fuente de información para consultar todos los elementos y atributos de HTML.

Etiqueta Center
---------------

La etiqueta `center` está obsoleta y no se recomienda su uso. Se deben utilizar CSS para centrar contenido.

Etiqueta Em
-----------

La etiqueta `em` se utiliza para enfatizar texto, pero no debe confundirse con `strong`.

Estilos por Defecto
-------------------

Los navegadores aplican estilos por defecto a las etiquetas HTML, lo que puede afectar cómo se ve el contenido.

Estructura Básica
-----------------

La estructura básica de un documento HTML incluye el doctype, las etiquetas `html`, `head` y `body`.

¿Para qué sirve el Head y el Body?
----------------------------------

El `head` contiene metadatos y enlaces a estilos, mientras que el `body` contiene el contenido visible de la página.

Metadato UTF-8
--------------

El metadato `charset="UTF-8"` se utiliza para especificar la codificación de caracteres.

Metadato ViewPort
-----------------

El metadato `viewport` se utiliza para controlar el diseño en dispositivos móviles.

Etiqueta Title
--------------

La etiqueta `title` define el título de la página que aparece en la pestaña del navegador.

Metadato Robots y Theme Color
-----------------------------

El metadato `robots` indica a los motores de búsqueda si deben indexar la página, y el `theme-color` establece el color de la barra de herramientas del navegador.

Favicon
-------

El favicon es el icono que aparece en la pestaña del navegador y se define con la etiqueta `link rel="icon"`.

Etiquetas para el SEO
---------------------

Las etiquetas para SEO, como `meta description`, son importantes para mejorar la visibilidad en buscadores.

Etiqueta Style
--------------

La etiqueta `style` se utiliza para definir estilos CSS en línea.

HTML Semántico
--------------

El HTML semántico utiliza etiquetas que tienen significado y describen el contenido de manera adecuada.

Ejemplo de HTML Semántico
-------------------------

Un ejemplo de HTML semántico podría ser el uso de `article` para definir un artículo de blog.

Etiqueta Article
----------------

La etiqueta `article` se utiliza para encapsular contenido que tiene sentido por sí mismo.

Etiqueta Small
--------------

La etiqueta `small` se utiliza para textos que deben ser menos prominentes.

Continuando Semántica
---------------------

Es importante seguir usando etiquetas semánticas para mejorar la accesibilidad y la comprensión del contenido.

Etiqueta Aside
--------------

La etiqueta `aside` se utiliza para contenido relacionado, pero no esencial al contenido principal.

¿Por qué tantos headers, qué es section, aside, article?
--------------------------------------------------------

Los headers pueden aparecer en diferentes niveles y se utilizan para definir secciones de contenido.

Etiqueta Main y Anchor
----------------------

La etiqueta `main` define el contenido principal de un documento, mientras que `anchor` se utiliza para crear enlaces.

Atributo rel="noreferer"
------------------------

El atributo `rel="noreferer"` se utiliza para mejorar la seguridad al evitar que se envíen datos de referencia al hacer clic en un enlace externo.

Div y Span
----------

Las etiquetas `div` y `span` se utilizan para agrupar contenido, pero no tienen significado semántico.

Atributo Role
-------------

El atributo `role` se utiliza para definir el propósito de un elemento y mejorar la accesibilidad.

Enlaces Especiales
------------------

Hay enlaces especiales que utilizan protocolos diferentes al de HTTP, como `mailto:` para correos electrónicos.

Atributos de Listas (ol, ul)
----------------------------

Las listas se pueden crear con `ul` (lista desordenada) o `ol` (lista ordenada), y cada uno de sus elementos se define con `li`.

Etiquetas de Formulario
-----------------------

Los formularios se crean con la etiqueta `form` y pueden incluir varios tipos de inputs.

Fieldset, Label, Input
----------------------

La etiqueta `fieldset` agrupa elementos de un formulario, mientras que `label` se utiliza para etiquetar inputs.

Elementos en Línea y de Bloque
------------------------------

Los elementos en línea, como `span`, no inician una nueva línea, mientras que los elementos de bloque, como `div`, sí lo hacen.

Continuando con el Formulario
-----------------------------

Los formularios pueden incluir opciones como `select` para listas desplegables y `input` para entradas de texto.

Validaciones de Formularios
---------------------------

HTML permite realizar validaciones básicas en formularios a través de atributos como `required`.

Datalist
--------

La etiqueta `datalist` permite crear listas de opciones autocompletables para inputs.

Etiqueta Details
----------------

La etiqueta `details` permite crear contenido que se puede mostrar u ocultar, como un acordeón.

Input Submit vs Button Submit
-----------------------------

El elemento `button` puede ser utilizado como un botón de envío, y se prefiere por su semántica.

Etiqueta de Video
-----------------

La etiqueta `video` se utiliza para insertar vídeos y puede incluir atributos como `controls` y `autoplay`.

Etiqueta Audio
--------------

La etiqueta `audio` se utiliza para insertar archivos de audio y también puede incluir atributos similares a la etiqueta de vídeo.

Atributo loading lazy
---------------------

El atributo `loading="lazy"` se utiliza en imágenes para cargarlas solo cuando son visibles en el viewport.

Iframes
-------

La etiqueta `iframe` permite incrustar otra página web dentro de la actual.

Etiqueta Dialog (para Modales)
------------------------------

La etiqueta `dialog` se utiliza para crear modales y puede abrirse y cerrarse mediante JavaScript.

Despedida
---------

Espero que hayáis aprendido sobre HTML y su importancia. La semana que viene, profundizaremos en CSS para estilizar nuestras páginas web.

Made with [VideoToBlog](https://www.videoToBlog.ai)