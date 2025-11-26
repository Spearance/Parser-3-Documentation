# Опции 

Работа с библиотекой cURL.

В качестве опций у методов `^curl:options[]` и `^curl:load[]` можно указывать любую из опций, доступную в библиотеке `libcurl`, установленной в системе (см. документацию). Имена опций нужно писать в нижнем регистре и без префикса **CURLOPT_**.

Кроме этого, поддерживаются следующие опции Parser:   

| Опция | По умолчанию | Значение |
|-------|--------------|----------|
| `$.library[/путь/к/libcurl.so]` | libcurl.so для Unix; libcurl.dll для Windows | Имя или полный дисковый путь динамической библиотеки libcurl в системе. Задается вызовом `^curl:options[]` до начала использования curl. |
| `$.charset[кодировка]` | Соответствует $request:charset | Кодировка документов на удаленном сервере. В эту кодировку перекодируется строка запроса. Из этой кодировки перекодируется ответ сервера, если в HTTP-ответе не указана кодировка. |
| `$.response-charset[кодировка]` | Берется из заголовка HTTP-ответа | Принудительно указывает, в какой кодировке был получен ответ от сервера |
| `$.name[имя файла]` | NONAME.DAT | Имя файла создаваемого объекта класса **file**. |
| `$.mode[text\|binary]` | text | Тип создаваемого объекта класса **file**. |
| `$.content-type[CONTENT-TYPE]` | Берется из заголовка HTTP-ответа | Поле `content-type` создаваемого объекта класса **file**. |


Поддерживаемые опции libcurl в алфавитном порядке:

| Название | Тип | Аналог в libcurl | Описание |
|----------|-----|------------------|----------|
| `accept_encoding` | string | CURLOPT_ACCEPT_ENCODING | Метод упаковки ответа: gzip или deflate. (Старое название параметра: encoding — тоже поддерживается). |
| `autoreferer` | int | CURLOPT_AUTOREFERER | Автоматическое создание заголовка Referer. |
| `cainfo` | string | CURLOPT_CAINFO | См. документацию по libcurl. |
| `capath` | string | CURLOPT_CAPATH | См. документацию по libcurl. |
| `connecttimeout` | int | CURLOPT_CONNECTTIMEOUT | Тай-маут ожидания соединения в секундах. |
| `connecttimeout_ms` | int | CURLOPT_CONNECTTIMEOUT_MS | Тайм-аут ожидания соединения в миллисекундах. |
| `cookie` | string | CURLOPT_COOKIE | Строка с cookies. |
| `cookielist` | string | CURLOPT_COOKIELIST | Строка с cookies в формате, соответствующем документации libcurl (отличном от формата cookie в Parser). |
| `cookiesession` | int | CURLOPT_COOKIESESSION | Поставить cookies на всю сессию. |
| `copypostfields` | string, file | CURLOPT_COPYPOSTFIELDS | Тело пост-запроса (с копированием). |
| `crlfile` | string | CURLOPT_CRLFILE | См. документацию по libcurl. |
| `customrequest` | string | CURLOPT_CUSTOMREQUEST | Другой HTTP-метод. |
| `failonerror` | int | CURLOPT_FAILONERROR | Выдавать ошибку, если HTTP-статус больше или равен 400. |
| `followlocation` | int | CURLOPT_FOLLOWLOCATION | Обрабатывать редиректы в ответе сервера. |
| `forbid_reuse` | int | CURLOPT_FORBID_REUSE | См. документацию по libcurl. |
| `fresh_connect` | int | CURLOPT_FRESH_CONNECT | Создавать новое соединение при каждом запросе в сессии. |
| `http_version` | string | CURLOPT_HTTP_VERSION | Версия HTTP-протокола. Допустимые значения: 1.0, 1.1, 2, 2.0, 2TLS, 2ONLY. |
| `http_content_decoding` | int | CURLOPT_HTTP_CONTENT_DECODING | См. документацию по libcurl. |
| `http_transfer_decoding` | int | CURLOPT_HTTP_TRANSFER_DECODING | См. документацию по libcurl. |
| `httpauth` | int | CURLOPT_HTTPAUTH | Тип HTTP-авторизации: |
|||| CURLAUTH_NONE = 0  |
|||| CURLAUTH_BASIC = (1<<0) |
|||| CURLAUTH_DIGEST = (1<<1) |
|||| CURLAUTH_GSSNEGOTIATE = (1<<2) |
|||| CURLAUTH_NTLM = (1<<3) |
|||| CURLAUTH_DIGEST_IE = (1<<4) |
|||| CURLAUTH_NTLM_WB = (1<<5) |
|||| CURLAUTH_ONLY = (1<<31) |
|||| CURLAUTH_ANY = (~CURLAUTH_DIGEST_IE) |
|||| CURLAUTH_ANYSAFE = (~(CURLAUTH_BASIC\|CURLAUTH_DIGEST_IE)) |
| `httpget` | int | CURLOPT_HTTPGET | Передать запрос методом GET. |
| `httpheader` | hash | CURLOPT_HTTPHEADER | HTTP-заголовки запроса. |
| `httppost` | hash | CURLOPT_HTTPPOST | Поля пост-запроса, заданные аналогично полю form для file::load. |
| `httpproxytunnel` | int | CURLOPT_HTTPPROXYTUNNEL | Включить тунелирование запросов через прокси. |
| `ignore_content_length` | int | CURLOPT_IGNORE_CONTENT_LENGTH | Игнорировать заголовок Content-Length ответа сервера. |
| `interface` | string | CURLOPT_INTERFACE | Имя сетевого интерфейса. |
| `ipresolve` | int | CURLOPT_IPRESOLVE | 1 — использовать IPv4 (по умолчанию), 2 — использовать IPv6. |
| `issuercert` | string | CURLOPT_ISSUERCERT | Имя файла с сертификатом CA. |
| `keypasswd` | string | CURLOPT_KEYPASSWD | Пароль для ключа (passphrase). |
| `localport` | int | CURLOPT_LOCALPORT | Локальный порт. |
| `low_speed_limit` | int | CURLOPT_LOW_SPEED_LIMIT | Минимальная скорость передачи, Б/сек. |
| `low_speed_time` | int | CURLOPT_LOW_SPEED_TIME | Максимальное время, когда скорость передачи может быть меньше low_speed_limit. |
| `maxconnects` | int | CURLOPT_MAXCONNECTS | Максимальное количество постоянных соединений в рамках сессии. |
| `maxfilesize` | int | CURLOPT_MAXFILESIZE | Максимальный размер ответа в байтах. |
| `maxredirs` | int | CURLOPT_MAXREDIRS | Максимальное число редиректов. |
| `nobody` | int | CURLOPT_NOBODY | Передать запрос методом HEAD. |
| `password` | string | CURLOPT_PASSWORD | Пароль. |
| `port` | int | CURLOPT_PORT | Порт. |
| `post` | int | CURLOPT_POST | Передать запрос методом POST. |
| `postfields` | string, file | CURLOPT_POSTFIELDS | Тело пост-запроса. |
| `postredir` | int | CURLOPT_POSTREDIR | См. документацию по libcurl. |
| `proxy` | string | CURLOPT_PROXY | Адрес прокси-сервера. |
| `proxyauth` | int | CURLOPT_PROXYAUTH | Тип авторизации (см. параметр httpauth). |
| `proxyport` | int | CURLOPT_PROXYPORT | Порт прокси-сервера. |
| `proxytype` | int | CURLOPT_PROXYTYPE | Тип прокси: |
|||| 0 — HTTP |
|||| 1 — HTTP_1_0 |
|||| 4 — SOCKS4 |
|||| 5 — SOCKS5 |
|||| 6 — SOCKS4A |
|||| 7 — SOCKS5_HOSTNAME |
| `proxyuserpwd` | string | CURLOPT_PROXYUSERPWD | Имя пользователя и пароль для прокси. |
| `range` | string | CURLOPT_RANGE | Вернуть части ответа, находящиеся в указанном диапазоне. |
| `referer` | string | CURLOPT_REFERER | Заголовок Referer. |
| `ssl_cipher_list` | string | CURLOPT_SSL_CIPHER_LIST | См. документацию по libcurl. |
| `ssl_sessionid_cache` | int | CURLOPT_SSL_SESSIONID_CACHE | Включить SSL session-ID кеш. |
| `ssl_verifyhost` | int | CURLOPT_SSL_VERIFYHOST | Проверять сертификат хоста. |
| `ssl_verifypeer` | int | CURLOPT_SSL_VERIFYPEER | Проверять сертификат пира. |
| `sslcert` | string | CURLOPT_SSLCERT | Имя файла с SSL-сертификатом. |
| `sslcerttype` | string | CURLOPT_SSLCERTTYPE | Тип SSL-сертификата. |
| `sslengine` | string | CURLOPT_SSLENGINE | См. документацию по libcurl. |
| `sslengine_default` | string | CURLOPT_SSLENGINE_DEFAULT | См. документацию по libcurl. |
| `sslkey` | string | CURLOPT_SSLKEY | Имя файла с SSL-ключом. |
| `sslkeytype` | string | CURLOPT_SSLKEYTYPE | Тип SSL-ключа. |
| `sslversion` | int | CURLOPT_SSLVERSION | Версия протокола SSL/TLS-соединения: |
|||| 0 — по умолчанию |
|||| 1 — TLSv1 (TLS 1.x) |
|||| 2 — SSLv2 |
|||| 3 — SSLv3 |
|||| 4 — TLSv1_0 |
|||| 5 — TLSv1_1 |
|||| 6 — TLSv1_2 |
| `stderr` | string | CURLOPT_STDERR | Имя файла, в который будет переадресован вывод из stderr. |
| `timeout` | int | CURLOPT_TIMEOUT | Таймаут с секундах. |
| `timeout_ms` | int | CURLOPT_TIMEOUT_MS | Таймаут в миллисекундах. |
| `unrestricted_auth` | int | CURLOPT_UNRESTRICTED_AUTH | Повторно отсылать параметры HTTP-авторизации, если при редиректе сменилось имя сервера. |
| `url` | string | CURLOPT_URL | URL-адрес. |
| `useragent` | string | CURLOPT_USERAGENT | Заголовок User-Agent. |
| `username` | string | CURLOPT_USERNAME | Имя пользователя. |
| `userpwd` | string | CURLOPT_USERPWD | Имя пользователя и пароль. |
| `verbose` | int | CURLOPT_VERBOSE | Выводить подробную информацию в процессе обработки запроса в stderr.  |
