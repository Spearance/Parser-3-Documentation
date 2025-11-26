# Метод `base64`

Кодирование в Base64.

```parser3
^file.base64[]
```
```parser3
^file.base64[опции]
```

Метод позволяет преобразовать файл в Base64-форму.

Чтобы преобразовать файл из Base64 к исходному виду, нужно воспользоваться конструкцией:

```parser3
^file::base64[закодированное]
```

Можно задать хеш опций: ***[3.4.6]***

`$.wrap(true|false)` — формировать результат с переносами строк (по умолчанию) или в одну строку;  
`$.url-safe(false|true)` — использовать модифицированный алфавит, все символы которого не будут преобразовываться в в `%XX` в URL (вместо «+» и «/» используются «-» и «\_»); по умолчанию не использовать;  
`$.pad(true|false)` — добавлять символы [паддинга](https://en.wikipedia.org/wiki/Base64) (=), если кодируемая длина не кратна трем; по умолчанию добавлять.  
	
Подробная информация о Base64 доступна по ссылкам: [ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt) и [wikipedia.org/wiki/Base64](https://en.wikipedia.org/wiki/Base64).

#### Пример
```parser3
$original[^file::load[binary;HTTP://www.parser.ru/i/p2.gif]]

<pre>^original.base64[]</pre>
```

выведет:
`R0lGODlhCQAJAID/AMDAwAAAACH5BAEAAAAALAAAAAAJAAkAAAINhI8YqXwLQVyMJtscKgA7`
