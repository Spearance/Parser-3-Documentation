# DOM

Интерфейсы Document моделей.

## DOM1-интерфейс Node

```parser3
$Node[^узел.insertBefore[$newChild;$refChild]]
```
```parser3
$Node[^узел.replaceChild[$newChild;$oldChild]]
```
```parser3
$Node[^узел.removeChild[$oldChild]]
```
```parser3
$Node[^узел.appendChild[$newChild]]
```
```parser3
^if(^узел.hasChildNodes[]){…}
```
```parser3
$Node[^узел.cloneNode(deep)]
```

## DOM1-интерфейс Element

```parser3
^узел.getAttribute[name]
```
```parser3
^узел.setAttribute[name;value]
```
```parser3
^узел.removeAttribute[name]
```
```parser3
$Attr[^узел.getAttributeNode[name]]
```
```parser3
$Attr[^узел.setAttributeNode[$newAttr]]
```
```parser3
$Attr[^узел.removeAttributeNode[$oldAttr]]
```
```parser3
$NodeList[^узел.getElementsByTagName[name]]
```
```parser3
^узел.normalize[]
```

## DOM2-интерфейс Element

```parser3
$строка[^узел.getAttributeNS[namespaceURI;localName]]
```
```parser3
^узел.setAttributeNS[namespaceURI;qualifiedName;value]
```
```parser3
^узел.removeAttributeNS[namespaceURI;localName]
```
```parser3
$Attr[^узел.getAttributeNodeNS[namespaceURI;localName]]
```
```parser3
$Attr[^узел.setAttributeNodeNS[$newAttr]]
```
```parser3
$NodeList[^узел.getElementsByTagNameNS[namespaceURI;localName]]
```
```parser3
^if(^узел.hasAttribute[name]){…}
```
```parser3
^if(^узел.hasAttributeNS[namespaceURI;localName]){…}
```
```parser3
^if(^узел.hasAttributes[]){…}
```

В Parser:

-	DOM-интерфейс — класс `hash` с ключами 0, 1, …;  
-	DOM-тип — класс `string`;  
-	DOM-тип boolean — логическое значение (0 = «ложь», 1 = «истина»).  
	

Подробная спецификация DOM1 доступна по ссылке: [w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html](https://www.w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html)

Подробная спецификация DOM2 доступна по ссылке: [w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html)
