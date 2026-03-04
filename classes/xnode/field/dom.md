DOM

Интерфейсы Document моделей.

## DOM1-интерфейс Node

```parser3
$узел.nodeName
```
```parser3
$узел.nodeValue
```
```parser3
$узел.nodeValue[новое значение]
```
```parser3
^if($узел.nodeType == $xnode:ELEMENT_NODE){…}
```
```parser3
$Node[$узел.parentNode]
```
```parser3
$NodeList[$узел.childNodes]
```
```parser3
$Node[$узел.firstChild]
```
```parser3
$Node[$узел.lastChild]
```
```parser3
$Node[$узел.previousSibling]
```
```parser3
$Node[$узел.nextSibling]
```
```parser3
$NamedNodeMap[$узел_типа_ELEMENT.attributes]
```
```parser3
$Document[$node.ownerDocument]
```

## DOM2-интерфейс Node

```parser3
$узел.prefix
```
```parser3
$узел.namespaceURI
```

## DOM1-интерфейс Element

```parser3
$узел_типа_ELEMENT.tagName
```

## DOM1-интерфейс Attr

```parser3
$узел_типа_ATTRIBUTE.name
```
```parser3
^if($узел_типа_ATTRIBUTE.specified){…}
```
```parser3
$узел_типа_ATTRIBUTE.value
```

## DOM1-интерфейс ProcessingInstruction

```parser3
$узел_типа_PROCESSING_INSTRUCTION.target
```
```parser3
$узел_типа_PROCESSING_INSTRUCTION.data
```

## DOM1-интерфейс DocumentType

```parser3
$узел_типа_DOCUMENT_TYPE.name
```

## DOM1-интерфейс Notation

```parser3
$узел_типа_NOTATION.publicId
```
```parser3
$узел_типа_NOTATION.systemId
```

В Parser:

-	DOM-интерфейс — класс `hash` с ключами 0, 1, …;  
-	DOM-интерфейс — класс `hash`, где в качестве ключей выступают имена атрибутов;  
-	DOM-тип [DOMString](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html#ID-C74D1578) — класс `string`;  
-	DOM-тип boolean — логическое значение (0 = «ложь», 1 = «истина»).  
	

Подробная спецификация DOM1 доступна по ссылке: [w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html](https://www.w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html)

Подробная спецификация DOM2 доступна по ссылке: [w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html)
