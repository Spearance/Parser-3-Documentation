# Метод `idna`
Кодирование в IDNA ***[3.4.4]***

```parser3
^строка.idna[]
```

Метод позволяет преобразовать строку в формат IDNA (может потребоваться для работы с кириллическими доменами). Для обратного преобразования строки из IDNA в исходный вид необходимо воспользоваться `^string:[idna](/class/string/method/idna/)[закодированное]`.

Подробная информация о IDNA доступна по ссылкам: [tools.ietf.org/html/rfc3490](https://datatracker.ietf.org/doc/html/rfc3490) и [en.wikipedia.org/wiki/Internationalized_domain_name](https://en.wikipedia.org/wiki/Internationalized_domain_name).

#### Пример
```parser3
$original[пример.испытание]
<pre>^original.idna[]</pre>
```
Выведет: **xn--e1afmkfd.xn--80akhbyknj4f**

*[IDNA]: Internationalized Domain Names in Applications
