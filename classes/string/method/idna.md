# Статический метод `:idna`

Декодирование из IDNA. ***[3.4.4]***

```parser3
^string:idna[закодированное]
```

> Замечание: именно метод, не конструктор!

Метод декодирует строку из IDNA-представления (может потребоваться при работе с кириллическими доменами). Для кодирования строки следует использовать `^строка.[idna](/class/string/method/idna-encode/)[]`.

Подробная информация о IDNA доступна по ссылкам: [tools.ietf.org/html/rfc3490](https://datatracker.ietf.org/doc/html/rfc3490) и [en.wikipedia.org/wiki/Internationalized_domain_name](https://en.wikipedia.org/wiki/Internationalized_domain_name).

#### Пример
```parser3
$encoded[xn--e1afmkfd.xn--80akhbyknj4f]
$original[^string:idna[$encoded]]
$original
```
Выведет: **пример.испытание**

*[IDNA]: Internationalized Domain Names in Applications
