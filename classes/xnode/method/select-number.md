# Метод `selectNumber`

Вычисление числового XPath-запроса.

```parser3
^узел.selectNumber[XPath-запрос]
```

Метод выдает **результат** выполнения **XPath-запроса** в контексте узла, если это [число](/class/double-int/). Если же это не число, выдается ошибка типа **parser.runtime**.

Для использования в **запросе** префиксов пространств имен необходимо их заранее определить, см. `[$xdoc.search-namespaces](/class/xdoc/field/search-namespaces/)`.

#### Пример
```parser3
$d[^xdoc::create{<?xml version="1.0" encoding="windows-1251" ?>
<t attr="привет" n="123"/>}]

# результат = 124
^d.selectNumber[number(/t/@n)+1]<br />

# результат = 4
^d.selectNumber[2*2]<br />
```
