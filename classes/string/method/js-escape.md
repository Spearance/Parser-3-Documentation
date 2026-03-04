# Метод `js-escape`

Кодирование, аналогичное функции escape в JavaScript ***[3.3.0]***

```parser3
^строка.js-escape[]
```

Метод выполняет преобразование строки, аналогичное методу escape, описанному в ECMA-262. Чтобы выполнить обратное преобразование, необходимо воспользоваться `^string:[js-unescape](/class/string/method/js-unescape/)[закодированное]`

Строки, закодированные данным методом, могут быть раскодированы в браузере с помощью функции `unescape`.

Подробная информация о ECMA-262 доступна по ссылке: [ecma-international.org/publications/standards/Ecma-262.htm](https://ecma-international.org/publications-and-standards/standards/ecma-262/) (B.2.1)

#### Пример
```parser3
$value[abcd \`+-=~!@#%&*()_ []{}<>:'",./?абвгд]
^value.js-escape[]
```
Выведет: 
**abcd%20%60+-%3D%7E%21@%23%25%26*%28%29_%20%5B%5D%7B%7D%3C%3E%3A%27%22%2C./%3F%u0430%u0431%u0432%u0433%u0434**
