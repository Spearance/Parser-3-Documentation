# DOM

Интерфейсы Document моделей.

## DOM1-интерфейс Document

```parser3
$Element[^документ.createElement[tagName]]
```
```parser3
$DocumentFragment[^документ.createDocumentFragment[]]
```
```parser3
$Text[^документ.createTextNode[data]]
```
```parser3
$Comment[^документ.createComment[data]]
```
```parser3
$CDATASection[^документ.createCDATASection[data]]
```
```parser3
$ProcessingInstruction[^документ.createProcessingInstruction[target;data]]
```
```parser3
$Attr[^документ.createAttribute[name]]
```
```parser3
$EntityReference[^документ.createEntityReference[name]]
```
```parser3
$NodeList[^документ.getElementsByTagName[tagname]]
```

## DOM2-интерфейс Document

```
$Node[^документ.importNode[importedNode](deep)]
```
```parser3
$Element[^документ.createElementNS[namespaceURI;qualifiedName]]
```
```parser3
$Attr[^документ.createAttributeNS[namespaceURI;qualifiedName]]
```
```parser3
$NodeList[^документ.getElementsByTagNameNS[namespaceURI;localName]]
```
```parser3
$Element[^документ.getElementById[elementId]]
```

В Parser:

-	DOM-интерфейсы Node и Element и их производные реализованы в классе xnode;  
-	DOM-интерфейс NodeList — класс `hash` с ключами 0, 1, …;  
-	DOM-тип DOMString — класс `string`;  
-	DOM-тип boolean — логическое значение (0 = «ложь», 1 = «истина»).  
	
Подробная спецификация DOM1 доступна по ссылке: [w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html](https://www.w3.org/TR/1998/REC-DOM-Level-1-19981001/level-one-core.html)

Подробная спецификация DOM2 доступна по ссылке: [w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html)
