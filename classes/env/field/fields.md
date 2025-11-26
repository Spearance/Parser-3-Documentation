# Статическое поле `fields`

Все переменные окружения ***[3.4.3]***

```parser3
$env:fields
```

Такая конструкция возвращает хеш со всеми полями переменных окружения сервера.

#### Пример

```parser3
^env:fields.foreach[field;value]{
	$field — $value
}[<br>]
```

Пример выведет на экран все переменные окружения сервера и соответствующие им значения:

`SERVER_SOFTWARE — Apache/2.2.22 (Win32)`
`SCRIPT_NAME — /cgi-bin/parser3.cgi`
`PATH_INFO — /env.html`
...
