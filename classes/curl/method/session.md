# Статический метод `:session`

Создание сессии.

```parser3
^curl:session{код}
```

Метод создает cURL-сессию. Код метода обрабатывается Parser, позволяя работать с удаленным сервером. Внутри сессии могут быть установлены общие опции и сделано несколько вызовов метода загрузки файла. Если удаленный сервер поддерживает **keep-alive**, то все запросы к нему будут сделаны в рамках одной установленной HTTP-сессии.

#### Пример

```parser3
^curl:session{
	^curl:options[
		$.url[https://store.artlebedev.ru/]
		$.charset[UTF-8]
		$.timeout(10)
		$.ssl_verifypeer(0)
	]

	$file1[^curl:load[
		$.url[https://store.artlebedev.ru/login/]
		$.postfields[Username=^taint[uri][$form:login]&Password=^taint[uri][$form:password]&btnSubmit=^taint[uri][Войти]]
	]]

	$file2[^curl:load[]]
}
```
