# Статический метод `:info`

Информация о последнем запросе ***[3.4.4]***

```parser3
^curl:info[название]
```
```parser3
^curl:info[]
```

Метод возвращает информацию о последнем запросе. Результатом является либо конкретное значение, либо хеш со всеми значениями.

Поддерживаемые значения параметра название:

| Название          | Тип    | Аналог в libcurl | Описание |
|-------------------|--------|------------------|----------|
| __`appconnect_time`__ | double | CURLINFO_APPCONNECT_TIME | Время до установки SSL-соединения. |
| __`connect_time`__    | double | CURLINFO_CONNECT_TIME | Время до установки соединения. |
| __`content_length_download`__ | double | CURLINFO_CONTENT_LENGTH_DOWNLOAD | Значение заголовка Content-length полученных данных. |
| __`content_length_upload`__ | double | CURLINFO_CONTENT_LENGTH_UPLOAD | Значение заголовка Content-length переданных данных. |
| __`content_type`__    | string | CURLINFO_CONTENT_TYPE | Значение заголовка Content-type. |
| __`effective_url`__   | string | CURLINFO_EFFECTIVE_URL | Последний использованный URL. |
| __`header_size`__     | int    | CURLINFO_HEADER_SIZE | Размер всех заголовков в байтах. |
| __`httpauth_avail`__  | int    | CURLINFO_HTTPAUTH_AVAIL | Доступные методы HTTP-аутентификации. |
| __`namelookup_time`__ | double | CURLINFO_NAMELOOKUP_TIME | Время от начала до завершения определения IP-адреса по имени. |
| __`num_connects`__    | int    | CURLINFO_NUM_CONNECTS | Число успешных соединений, потребовавшихся для предыдущего запроса. |
| __`os_errno`__        | int    | CURLINFO_OS_ERRNO | Код errno последней ошибки соединения. |
| __`pretransfer_time`__ | double | CURLINFO_PRETRANSFER_TIME | Время от начала запроса до начала передачи данных. |
| __`primary_ip`__      | string | CURLINFO_PRIMARY_IP | IP-адрес последнего соединения. |
| __`proxyauth_avail`__ | int    | CURLINFO_PROXYAUTH_AVAIL | Доступные методы HTTP-аутентификации прокси-сервера. |
| __`redirect_count`__  | string | CURLINFO_REDIRECT_COUNT | Общее число совершенных переходов по редиректам. |
| __`redirect_time`__   | double | CURLINFO_REDIRECT_TIME | Время, потребовавшееся для совершения редиректов до финального соединения. |
| __`redirect_url`__    | string | CURLINFO_REDIRECT_URL | URL, по которому был бы совершен переход, если бы был включен переход по редиректам. |
| __`request_size`__    | int    | CURLINFO_REQUEST_SIZE | Размер совершенных HTTP-запросов в байтах. |
| __`response_code`__   | int    | CURLINFO_RESPONSE_CODE | Последний полученный код HTTP-ответа. |
| __`size_download`__   | double | CURLINFO_SIZE_DOWNLOAD | Размер полученных данных. |
| __`size_upload`__     | double | CURLINFO_SIZE_UPLOAD | Размер переданных данных. |
| __`speed_download`__  | double | CURLINFO_SPEED_DOWNLOAD | Средняя скорость получения данных. |
| __`speed_upload`__    | double | CURLINFO_SPEED_UPLOAD | Средняя скорость передачи данных. |
| __`ssl_verifyresult`__ | int    | CURLINFO_SSL_VERIFYRESULT | Результат проверки SSL-сертификата. | 
| __`starttransfer_time`__ | double | CURLINFO_STARTTRANSFER_TIME | Время от начала запроса до начала получения данных. |
| __`total_time`__      | double | CURLINFO_TOTAL_TIME | Общее время последнего запроса. |
