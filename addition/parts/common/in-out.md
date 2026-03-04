# SQL-серверы, работа с IN/OUT-переменными

Приложение 7.

При работе с SQL-сервером Oracle поддерживается работа со связанными переменными (bind variables), поддерживаются **IN-**, **OUT-** и **IN/OUT-**переменные, которые связываются с передаваемым в запрос [хешем](/common/constructions/common/hash/).

При прямом использовании конструкций `CALL` и `EXECUTE` в некоторых версиях Oracle имеются известные проблемы, рекомендуется пользоваться PL/SQL-оберткой `begin …; end;`, не забывая экранировать знак `;`.

> Значение типа [void](/class/void/) соответствует **NULL**. Во втором примере `days` имеет начальное значение **NULL**.

#### Пример использования IN-переменных
```parser3
# procedure ban_user(user_id in number, days in number)

^void:sql{begin ban_user(:user_id, :days)^; end^;}[
	$.bind[
		$.user_id(7319)
		$.days(10)
	]
]
```

#### Пример использования IN- и OUT-переменных
```parser3
# procedure read_user_ban_days(user_id in number, days out number)

$variables[
	$.user_id(7319)
# несмотря на то что параметр OUT, все равно необходимо его передать
# его текущее значение будет проигнорировано
	$.days[]
]

^void:sql{begin read_user_ban_days(:user_id, :days)^; end^;}[
	$.bind[$variables]
]

Пользователь выключен на $variables.days!
```
