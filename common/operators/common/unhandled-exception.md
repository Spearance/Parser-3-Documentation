# Метод `@unhandled_exception`

Вывод необработанных ошибок.

Если ошибка так и не была обработана ни одним обработчиком (см. оператор `[try](/common/operators/common/try/)`), Parser вызывает метод `unhandled_exception`, ему передается информация об ошибке и стек вызовов, приведших к ошибке, а также выдаются результаты работы метода. Помимо этого, ошибка записывается в журнал ошибок.

Хорошим тоном является оформление сообщения об ошибке в общем дизайне сайта, а также проверка и скрытие технических подробностей от посетителей.

Рекомендуем поместить этот метод в Конфигурационный файл сайта.

Имеется возможность предотвратить запись ошибки в журнал ошибок, для чего только для нужных ошибок можно зажечь флаг: ***[3.1.4]***
```parser3
$exception.handled(true)
```

#### Пример
```parser3
@unhandled_exception[exception;stack]
$response:content-type[
	$.value[text/html]
	$.charset[$response:charset]
]

<title>UNHANDLED EXCEPTION (root)</title>
<body bgcolor=white>
<font color=black>
<pre>^untaint[html]{$exception.comment}</pre>
^if(def $exception.source){
	<b>$exception.source</b><br />
	<pre>^untaint[html]{$exception.file^($exception.lineno^)}</pre>
}
^if(def $exception.type){exception.type=$exception.type}
^if($stack){
	<hr>
	^stack.menu{
		<tt>$stack.name</tt> $stack.file^($stack.lineno^)<br>
	}
}
```
