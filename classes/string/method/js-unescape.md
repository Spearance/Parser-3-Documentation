# Статический метод `:js-unescape`

Декодирование, аналогичное функции `unescape` в JavaScript. ***[3.3.0]***

```parser3
^string:js-unescape[закодированное]
```

> Примечание: именно статический метод, не конструктор!

Метод выполняет преобразование строки, аналогичное методу `unescape`, описанному в ECMA-262. Для кодирования следует использовать 
`^строка.[js-escape](/class/string/method/js-escape/)[]`

С помощью данного метода возможно декодировать строки, закодированные в браузере с помощью функции `escape`.

Подробная информация о ECMA-262 доступна по ссылке: [ecma-international.org/publications/standards/Ecma-262.htm](https://ecma-international.org/publications-and-standards/standards/ecma-262/) (B.2.2)

> Метод также декодирует символы, закодированные в виде \uXXXX. ***[3.4.1]***

#### Пример
```parser3
$escaped[abcd%20%60+-%3D%7E%21@%23%25%26*%28%29_%20%5B%5D%7B%7D%3C%3E%3A%27%22%2C./%3F%u0430%u0431%u0432%u0433%u0434]
$original[^string:js-unescape[$escaped]]
$original
```
Выведет: 
**abcd `+-=~!@#%&*()_ []{}<>:'",./?абвгд**
