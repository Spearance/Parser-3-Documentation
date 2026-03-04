# Статическое поле `uri`

Получение URI запроса.

```parser3
$request:uri
```

Возвращает URI запрошенного документа.

#### Пример

Предположим, пользователь запросил такую страницу:

*`http://www.mysite.ru/some%20news/articles.html?year=2000&month=05&day=27`*

Тогда:
```parser3
$request:uri
```

вернет: **/some%20news/articles.html?year=2000&month=05&day=27**
