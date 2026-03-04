# Поле `search-namespaces`

Хеш пространств имен для поиска.

```parser3
$документ.search-namespaces
```

Для использования префиксов пространств имен в методах `xnode.select*` необходимо заранее определить эти префиксы в данном хеше.

Здесь:

-	ключи — префиксы пространств имен
-	значения — их URI.  

#### Пример добавления нескольких префиксов
```parser3
$xdoc[^xdoc::create{<?xml version="1.0"?>
<document xmlns:s="urn:special">
	<s:code xmlns:o="urn:other" o:attr="123">давай поиграем в прятки</s:code>
</document>
}]

^xdoc.search-namespaces.add[
   $.s[urn:special]
   $.o[urn:other]
]

^xdoc.selectString[string(//s:code[@o:attr=123])]
```
#### Пример добавления одного префикса
```parser3
$xdoc.search-namespaces.s[urn:special] 
```
*[URI]: Uniform Resource Identifier
