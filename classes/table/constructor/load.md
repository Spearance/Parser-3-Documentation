# Конструктор `load`

Загрузка таблицы с диска или HTTP-сервера.

```parser3
^table::load[имя_файла]
```
```parser3
^table::load[имя_файла;опции_загрузки] 
```
```parser3
^table::load[nameless;имя_файла]
```
```parser3
^table::load[nameless;имя_файла;опции_загрузки]
```

Конструктор создает объект, используя таблицу, определенную в некотором файле или документе на HTTP-сервере. Данные должны быть представлены в формате **tab-delimited** (см. `[table::create](/class/table/constructor/create/)`).

**Имя файла** — Имя файла с путем или URL документа на HTTP-сервере.

**Опции загрузки** — Основные опции описаны в разделе «Приложение 1. Пути к файлам и каталогам, работа с HTTP-серверами», также доступны дополнительные опции, см. «[Опции формата файла](/table/options/table-format/)».

Параметр **nameless** используется так же, как и в конструкторе `[table::create](/class/table/constructor/create/)`.

#### Пример загрузки таблицы с диска
```parser3
$loaded_table[^table::load[/addresses.cfg]]
```
Пример создает объект класса `table`. Он содержит именованную таблицу, определенную в файле **addresses.cfg**, который находится в корневом каталоге сайта.

#### Пример загрузки таблицы с HTTP-сервера
```parser3
$table[^table::load[nameless;http://www.parser.ru/;
	$.headers[
		$.USER-AGENT[table load example]
	]
]]
Количество строк: ^table.count[]
<hr>
<pre>$table.0</pre>
```
