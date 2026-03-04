# Оператор `throw`

Сообщение об ошибке.

```parser3
^throw[type]
```
```parser3
^throw[type;source]
```
```parser3
^throw[type;source;comment]
```
```parser3
^throw[хеш]
```

Оператор `throw` сообщает об ошибке типа **type**, произошедшей по вине **source**, с комментарием **comment**.

Эта ошибка может быть перехвачена и обработана при помощи оператора `[try](/common/operators/common/try/)`.

Не нужно перехватывать ошибки только для их красивого вывода, пусть этим централизованно займется метод `[unhandled_exception](/common/operators/common/unhandled-exception/)`, вызываемый Parser, если ни одного обработчика ошибки так и не будет найдено. Кроме прочего, произойдет запись в журнал ошибок веб-сервера, который можно регулярно просматривать на предмет имевших место проблем.

#### Пример
```parser3
@method[command]
^switch[$command]{
	^case[add]{
		добавляем…
	}
	^case[delete]{
		удаляем…
	}
	^case[DEFAULT]{
		^throw[bad.command;$command;Wrong command $command, good are add&delete]
		^rem{
			допустим также следующий формат вызова оператора throw
			^throw[
				$.type[bad.command]
				$.source[$command]
				$.comment[Wrong command $command, good are add&delete]
			]
		}
	}
}

@main[]
$action[format c:]
^try{
	^method[$action]
}{
	^if($exception.type eq bad.command){
		$exception.handled(true)
		Неправильная команда '$exception.source', задана
		в файле $exception.file, в строке $exception.lineno.
	}
}
```
Результатом работы примера будет
**Неправильная команда 'format c:', задана **
**в файле c:/parser3tests/www/htdocs/throw.html, в строке 15.**

Обращаем внимание на то, что посетители сайтов не должны видеть технические подробности в сообщениях об ошибках, тем более содержащие пути к файлам, это некрасиво и ненадежно.

Вывод `$exception.file` дан в качестве примера и настоятельно не рекомендуется к использованию на промышленных серверах — только для отладки.
