# Статическое поле `query`

Получение параметров строки запроса.

```parser3
$request:query
```

Возвращает строку после `?` в URI (значение переменной окружения QUERY_STRING). 

> Для работы с полями форм (**<form>**) и строкой после второго `?` (/?a=b?thisText) используется класс `[form](/class/form/)`.

#### Пример

Предположим, пользователь запросил такую страницу:

*`http://www.mysite.ru/some%20news/articles.html?year=2000&month=05&day=27`*

Тогда:
```parser3
$request:query
```

вернет: **year=2000&month=05&day=27**
