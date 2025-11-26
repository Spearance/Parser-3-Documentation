# Статическое поле `qtail`

Получение остатка строки запроса.

```parser3
$form:qtail
```

Поле возвращает часть `$request:query` после второго «?».

#### Пример
Предположим, пользователь запросил такую страницу: `http://www.mysite.ru/news/article.html?year=2000&month=05&day=27?thisText`

Тогда:

```parser3
$form:qtail
```

вернет: **thisText**
