# Статическое поле `fields`

Все `cookie` в виде хеша.

```parser3
$cookie:fields
```

Такая конструкция возвращает хеш со всеми `cookie`.

#### Пример

```parser3
^cookie:fields.foreach[name;value]{
	$name - ^if($value is "hash"){$value.value}{$value}
}[<br>]
```

Пример выведет на экран все доступные `cookie` и соответствующие им значения c новой строки. 
