# Конструктор `::open`

Открытие.

```parser3
^memcached::open[параметры_соединения]
```
```parser3
^memcached::open[параметры_соединения](время_хранения_записей_по_умолчанию_в_секундах)
```

#### Пример
```parser3
$memcached[^memcached::open[server1:port1,server2]]
```

#### Пример
```parser3
$memcached[^memcached::open[
	$.server[server1:port1]
	$.binary-protocol(true)
	$.connect-timeout(5)
]]
```

## Параметры соединения

Параметры соединения с серверами memcached могут быть заданы как в виде **строки**, так и в виде **хеша**.

Если параметры соединения заданы в виде строки, то они передаются функции **memcached_servers_parse** библиотеки libmemcached «как есть». Данная функция ожидает строку соединения в следующем формате:

`server1:port1,server2,server3,server4:port4`

Чуть подробнее прочитать о ее параметрах можно в [документации](http://docs.libmemcached.org/memcached_servers_parse.html) библиотеки libmemcached.

Если параметры соединения указаны в виде хеша, то они обрабатываются более новой и универсальной функцией memcached (которая тем не менее может отсутствовать у библиотеки, установленной в системе). Ключами хеша с параметрами соединения могут быть любые опции, доступные у установленной в конкретной системе библиотеки libmemcached (см. [документацию](http://docs.libmemcached.org/libmemcached_configuration.html#memcached)). Имена опций нужно писать без префикса `--`.

Список наиболее востребованных опций:

```parser3
$.server[<servername>:<port>]
$.binary-protocol(true)
$.connect-timeout(N)
$.tcp-keepalive(true)
```
