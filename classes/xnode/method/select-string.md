# Метод `selectString`

Вычисление строчного XPath-запроса.

```parser3
^узел.selectString[XPath-запрос]
```

Метод выдает результат выполнения **XPath-запроса** в контексте **узла**, если это [строка](/class/string/). Если не строка, выдается ошибка типа **parser.runtime**.

Для использования в **запросе** префиксов пространств имен необходимо их заранее определить, см. `[$xdoc.search-namespaces](/class/xdoc/field/search-namespaces/)`.

#### Пример
```parser3
$d[^xdoc::create{<?xml version="1.0" encoding="windows-1251" ?>
<t attr="привет" n="123"/>}]

# результат=привет
^d.selectString[string(t/@attr)] 
```
