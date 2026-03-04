# ClientCharset

Параметр подключения — кодировка общения с SQL-сервером

Параметр **ClientCharset** определяет кодировку, в которой необходимо общаться с SQL-сервером. Если параметр не указан, Parser 3 считает, что общение с SQL-сервером идет в кодировке `$[request](/class/request/):[charset](/class/request/field/charset/)`.

Список допустимых кодировок определяется в [Конфигурационном файле](/addition/install/common/config-file/). 
