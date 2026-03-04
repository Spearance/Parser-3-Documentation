# Статическое поле `headers`

Заданные заголовки HTTP-ответа.

```parser3
$response:headers
```

Возвращает хеш со всеми заголовками HTTP-ответа, которые были заданы в коде на данный момент. Заголовки имеют имена в верхнем регистре. ***[3.4.4]***

#### Пример
```parser3
$response:expires[^date::now(+1)]

^response:headers.foreach[header;value]{
   $header - ^if($value is "string" || $value is "int" || $value is "double"){$value}{not printable}
}[<br>]
```

Пример выведет на экран все заданные ранее заголовки HTTP-ответа. 
