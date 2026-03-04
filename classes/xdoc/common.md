## Краткое описание

Класс рботает в паре с [xnode](/class/xnode/) и поддерживает считывание файлов в формате XML, запись в XML [w3.org/XML](https://www.w3.org/XML/) и HTML, а также XSLT-трансформацию [w3.org/TR/xslt](https://www.w3.org/TR/xslt/).

Работа с деревом производится в [DOM-модели](https://dom.spec.whatwg.org/), доступен DOM1 и ряд возможностей DOM2.

Класс реализует DOM-интерфейс Document и является наследником класса [xnode](/class/xnode/).

Ошибки DOM-операций (интерфейс DOMException) преобразуются в исключения XML-типа. 

*[XML]: eXtensible Markup Language
*[HTML]: HyperText Markap Language
