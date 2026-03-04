# Метод `select`

XPath-поиск узлов.

```parser3
$NodeList[^узел.select[XPath-запрос]]
```

Метод выдает список узлов, найденных в контексте **узла** по заданному **XPath-запросу**. Если запрос не вернул подходящих узлов, выдается пустой список.

Для использования в **запросе** префиксов пространств имен необходимо их заранее определить, см. `[$xdoc.search-namespaces](/class/xdoc/field/search-namespaces/)`.

#### Пример
```parser3
$d[^xdoc::create{<?xml version="1.0" encoding="windows-1251" ?>
<document>
	<t/><t/>
</document>}]

# результат=список из двух элементов "t"
$list[^d.select[/document/t]]

# перебираем найденные листы:
#	этот код будет работать
#	даже если запрос не найдет ни одного листа 
^for[i](0;$list-1){
	$node[$list.$i]
	Имя: $node.nodeName<br />
	Тип: $node.nodeType<br />
}
```
В Parser DOM-интерфейс NodeList — класс `hash` с ключами 0, 1, …

Подробная спецификация XPath доступна по ссылке: [w3.org/TR/xpath](https://www.w3.org/TR/xpath/).
