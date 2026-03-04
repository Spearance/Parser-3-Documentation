# Параметры преобразования 

Преобразование документа в текст.

В ряде методов можно задать хеш `Параметры_преобразования_в_текст`. Они идентичны атрибутам элемента `<xsl:output … />`. Исключениями являются атрибуты **doctype-public** и **doctype-system**, которые так задать нельзя. Пока также является исключением **cdata-section-elements**.

По умолчанию текст создается в кодировке `$[request:charset](/class/request/field/charset/)`, однако в XML-заголовке или в элементе **meta** для HTML-метода Parser указывает кодировку `$[response:charset](/class/response/field/charset/)`. Такое поведение можно изменить, явно указав кодировку в `<xsl:output … />` или соответствующем параметре преобразования.

При создании объекта класса `file` можно задать параметр **media-type**, при задании нового тела ответа заголовок ответа **content-type** получит значение этого параметра.

#### Пример
```parser3
^document.string[
	$.method[html]
	$.indent[no]
	$.omit-xml-declaration[yes]
	$.encoding[windows-1251]
# $.charset[windows-1251]		[3.4.2] опция не может быть использована совместно с опцией $.encoding[]
]
```
Будет выдан документ в HTML-представлении без отступов и XML-декларации.

______


## Выдача XHTML

Если необходимо выдать [XHTML](https://www.w3.org/TR/xhtml1/), следует использовать следующие атрибуты элемента `<xsl:stylesheet … />`:

```xsl
<xsl:stylesheet version="1.0"
	xmlns="http://www.w3.org/1999/xhtml"
	xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
>
```
Xmlns указывается без префикса: так необходимо делать, чтобы все создаваемые в шаблоне элементы без префикса попадали в пространство имен xhtml. Необходимо задавать xmlns без префикса в каждом XSL-файле, этот параметр не распространяется на включаемые файлы.

Помимо этого, требуется задать следующие атрибуты элемента `<xsl:output … />`:
```xsl
<xsl:output 
	doctype-public="-//W3C//DTD XHTML 1.0 Strict//EN"
	doctype-system="DTD/xhtml1-strict.dtd"
/>
```
> Атрибут method не задается. XHTML — это разновидность метода xml, включающаяся при использовании следующих doctype:
> — `—//W3C//DTD XHTML 1.0 Strict//EN`
> — `—//W3C//DTD XHTML 1.0 Frameset//EN`
> — `—//W3C//DTD XHTML 1.0 Transitional//EN`

*[XHTML]: eXtensible HyperText Markup Language
