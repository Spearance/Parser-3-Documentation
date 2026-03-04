## Краткое описание

Класс предназначен для работы с древовидными структурами данных в паре с xdoc, поддерживает XPath-запросы ([w3.org/TR/xpath](https://www.w3.org/TR/xpath/)).

Класс реализует DOM-интерфейсы Node и Element и их производные. Класс не создается напрямую, используются [соответствующие методы](/class/xdoc/method/dom/) класса `xdoc`.

Вместо DOM-интерфейса NamedNodeMap в Parser используется класс `[hash](/class/hash/)`.

***

## DOM. nodeType

DOM-элементы бывают разных типов, тип элемента хранится в [integer](/class/double-int/) поле [nodeType](https://www.w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html#attribute-nodeType).

В классе `xdoc` имеются следующие константы, удобные для проверки значения этого поля:

| Константа                         | Значение |
|-----------------------------------|----------|
| $xdoc:ELEMENT_NODE                | 1        |
| $xdoc:ATTRIBUTE_NODE              | 2        |
| $xdoc:TEXT_NODE                   | 3        |
| $xdoc:CDATA_SECTION_NODE          | 4        |
| $xdoc:ENTITY_REFERENCE_NODE       | 5        |
| $xdoc:ENTITY_NODE                 | 6        |
| $xdoc:PROCESSING_INSTRUCTION_NODE | 7        |
| $xdoc:COMMENT_NODE                | 8        |
| $xdoc:DOCUMENT_NODE               | 9        |
| $xdoc:DOCUMENT_TYPE_NODE          | 10       |
| $xdoc:DOCUMENT_FRAGMENT_NODE      | 11       |
| $xdoc:NOTATION_NODE               | 12       |

#### Пример
```parser3
^if($node.nodeType == $xnode:ELEMENT_NODE){
	<$node.tagName />
}
```
