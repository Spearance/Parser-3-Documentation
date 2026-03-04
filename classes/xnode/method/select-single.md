# Метод `selectSingle`

XPath-поиск одного узла.

```parser3
^узел.selectSingle[XPath-запрос]
```

Метод выдает **узел**, найденный в контексте узла по заданному **XPath-запросу**. Если запрос не нашел подходящего узла, выдается `[void](/class/void/)`. Если запрос выдал больше чем один узел, выдается ошибка.

Для использования в **запросе** префиксов пространств имен необходимо их заранее определить, см. `[$xdoc.search-namespaces](/class/xdoc/field/search-namespaces/)`.

#### Пример
```parser3
$d[^xdoc::create{<?xml version="1.0" encoding="windows-1251" ?>
<t attr="привет" n="123"/>}]

# результат=один элемент "t"
$element[^d.selectSingle[t]]

# результат=2 (количество атрибутов <t>)
Количество атрибутов: ^element.attributes._count[]<br />
```
