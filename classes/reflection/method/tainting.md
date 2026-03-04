# Статический метод `:tainting`

Преобразования строки. ***[3.4.5]***

```parser3
^reflection:tainting[строка]
```
```parser3
^reflection:tainting[вид_преобразования;строка]
```

Метод позволяет узнать, в каких преобразованиях нуждается **строка**. Результатом является строка, в которой каждому символу исходной строки соответствует символ с кодом преобразования. При указании **вида преобразования** с помощью `+` выделяются символы, подлежащие преобразованию указанного вида. Кроме имени преобразования, можно указать значение **tainted** для показа неопределенно грязных символов и **optimized** для показа символов, нуждающихся в оптимизации при выводе.


### Коды преобразований

| clean       | 0 |
|-------------|---|
| as-is       | A |
| tainted     | T |
| file-spec   | F |
| uri         | U |
| http-header | h |
| mail-header | m |
| sql         | Q |
| js          | J |
| json        | S |
| parser-code | p |
| regex       | R |
| xml         | X |
| html        | H |
| cookie      | C |

#### Пример

```parser3
$s[clean ^taint[<tainted>] ^taint[uri;&] ^taint[json;"json"]]

^taint[as-is;$s]
^reflection:tainting[$s]
^reflection:tainting[tainted;$s]

Applied: $s
```

Выведет:

**clean <tainted> & "json"**
**000000TTTTTTTTT0U0SSSSSS**
**------+++++++++---------**

**Applied: clean &lt;tainted&gt; %26 \"json\"**
