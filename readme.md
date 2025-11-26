# Документация Parser 3.5.0

## Содержание документации

### Классы
- array
  - [Информация о классе](./classes/array/common.md)
  - Конструкторы
    - [create — создание массива с заданными значениями или пустого массива](./classes/array/constructor/create.md)
    - [copy — копирование массива или хеша](./classes/array/constructor/copy.md)
    - [sql — cоздание массива на основе выборки из базы данных](./classes/array/constructor/sql.md)
  - Методы
    - [add — добавление элементов из другого массива или хеша с перезаписью](./classes/array/method/add.md)
    - [append — добавление элементов в конец массива](./classes/array/method/append.md)
    - [at, _at — доступ к элементу массива по порядковому номеру](./classes/array/method/at.md)
    - [compact — удаление неиници­ализированных элементов](./classes/array/method/compact.md)
    - [contains — проверка существования элемента по индексу](./classes/array/method/contains.md)
    - [count — количество элементов массива](./classes/array/method/count.md)
    - [delete — удаление элемента массива](./classes/array/method/delete.md)
    - [insert — вставка элементов в указанную позицию массива](./classes/array/method/insert.md)
    - [join — добавление элементов другого массива или хеша](./classes/array/method/join.md)
    - [keys — список индексов массива](./classes/array/method/keys.md)
    - [left — получение первых n элементов массива](./classes/array/method/left.md)
    - [mid — получение диапазона элементов массива](./classes/array/method/mid.md)
    - [pop — удаление и возврат последнего элемента массива](./classes/array/method/pop.md)
    - [push — добавление элемента в конец массива](./classes/array/method/push.md)
    - [remove — удаление элемента со сдвигом](./classes/array/method/remove.md)
    - [reverse — обратный порядок элементов](./classes/array/method/reverse.md)
    - [right — получение последних n элементов массива](./classes/array/method/right.md)
    - [select — отбор элементов массива](./classes/array/method/select.md)
    - [set — установка значения элемента массива](./classes/array/method/set.md)
    - [sort — сортировка массива](./classes/array/method/sort.md)
  - Поля
    - [поля объекта класса](./classes/array/field/common.md)
- bool
  - [Информация о классе](./classes/bool/common.md)
- console
  - [Информация о классе](./classes/console/common.md)
  - Статические поля
    - [чтение — строки консоли](./classes/console/field/read.md)
    - [запись — строки консоли](./classes/console/field/write.md)
- cookie
  - [Информация о классе](./classes/cookie/common.md)
  - Статические поля
    - [чтение — значения существующего cookie](./classes/cookie/field/read.md)
    - [запись — нового или перезапись значения cookie](./classes/cookie/field/write.md)
    - [fields — получить все cookie в виде хеша](./classes/cookie/field/fields.md)
- curl
  - [Информация о классе](./classes/curl/common.md)
  - Статические методы
    - [info — информация о последнем запросе](./classes/curl/method/info.md)
    - [load — загрузка файла с удаленного сервера](./classes/curl/method/load.md)
    - [options — задание опций для сессии](./classes/curl/method/options.md)
    - [session — создание сессии](./classes/curl/method/session.md)
    - [version — возвращает текущую версию cURL.](./classes/curl/method/version.md)
- date
  - [Информация о классе](./classes/date/common.md)
  - Конструкторы
    - [create — дата/время в стандартном формате для СУБД](./classes/date/constructor/create-db.md)
    - [create — дата в формате ISO 8601](./classes/date/constructor/create-iso.md)
    - [create — копирование даты](./classes/date/constructor/copy.md)
    - [create — относительная дата](./classes/date/constructor/create-relative.md)
    - [create — произвольная дата](./classes/date/constructor/create-arbitrary.md)
    - [now — текущая дата](./classes/date/constructor/now.md)
    - [today — дата на начало текущего дня](./classes/date/constructor/today.md)
    - [unix-timestamp — дата и время в формате UNIX](./classes/date/constructor/unix-timestamp.md)
  - Методы
    - [int, double — преобразование даты в число](./classes/date/method/int-double.md)
    - [gmt-string — вывод даты в виде строки в формате RFC 822](./classes/date/method/gmt-string.md)
    - [iso-string — вывод даты в виде строки в формате ISO 8601](./classes/date/method/iso-string.md)
    - [last-day — получение последнего дня месяца](./classes/date/method/last-day.md)
    - [roll — cдвиг даты](./classes/date/method/roll.md)
    - [sql-string — преобразование даты в вид, стандартный для СУБД](./classes/date/method/sql-string.md)
    - [unix-timestamp — преобразование даты и времени в UNIX формат](./classes/date/method/unix-timestamp.md)
  - Статические методы
    - [calendar — создание календаря на заданную неделю месяца](./classes/date/method/calendar-week.md)
    - [calendar — создание календаря на заданный месяц](./classes/date/method/calendar-month.md)
    - [last-day — получение последнего дня указанного месяца](./classes/date/method/last-day-static.md)
    - [roll — установка временной зоны по умолчанию](./classes/date/method/roll-static.md)
  - Поля
    - [поля объекта класса](./classes/date/field/common.md)
- double-int
  - [Информация о классе](./classes/double-int/common.md)
  - Методы
    - [format — вывод числа в заданном формате](./classes/double-int/method/format.md)
    - [inc, dec, mul, div, mod — простые операции над числами](./classes/double-int/method/inc-dec-mul-div-mod.md)
    - [int, double, bool — преобразование объектов в числа или bool](./classes/double-int/method/int-double-bool.md)
  - Статические методы
    - [sql — получение числа из базы данных](./classes/double-int/method/sql.md)
- env
  - [Информация о классе](./classes/env/common.md)
  - Статические поля
    - [fields — все переменные окружения](./classes/env/field/fields.md)
    - [PARSER_VERSION — получение версии Parser](./classes/env/field/parser-version.md)
    - [переменные окружения — получение значений](./classes/env/field/variables.md)
    - [поля запроса — получение значений](./classes/env/field/request-field.md)
- file
  - [Информация о классе](./classes/file/common.md)
  - Конструкторы
    - [base64 — декодирование из Base64](./classes/file/constructor/base64.md)
    - [cgi и exec — исполнение программы](./classes/file/constructor/cgi-exec.md)
    - [create — создание файла](./classes/file/constructor/create.md)
    - [load — загрузка файла с диска или HTTP-сервера](./classes/file/constructor/load.md)
    - [sql — загрузка файла с SQL-сервера](./classes/file/constructor/sql.md)
    - [stat — получение информации о файле](./classes/file/constructor/stat.md)
  - Методы
    - [base64 — кодирование в Base64](./classes/file/method/base64.md)
    - [crc32 — подсчет контрольной суммы файла](./classes/file/method/crc32.md)
    - [md5 — MD5-отпечаток файла](./classes/file/method/md5.md)
    - [save — сохранение файла на диске](./classes/file/method/save.md)
    - [sql-string — сохранение файла на SQL-сервере](./classes/file/method/sql-string.md)
  - Статические методы
    - [base64 — кодирование в Base64](./classes/file/method/base64-static.md)
    - [basename — имя файла без пути](./classes/file/method/basename.md)
    - [copy — копирование файла](./classes/file/method/copy.md)
    - [crc32 — подсчет контрольной суммы файла](./classes/file/method/crc32-static.md)
    - [delete — удаление файла с диска](./classes/file/method/delete.md)
    - [dirname — путь к файлу](./classes/file/method/dirname.md)
    - [find — поиск файла на диске](./classes/file/method/find.md)
    - [fullpath — полное имя файла от корня веб-пространства](./classes/file/method/fullpath.md)
    - [justext — расширение имени файла](./classes/file/method/justext.md)
    - [justname — имя файла без расширения](./classes/file/method/justname.md)
    - [list — получение оглавления каталога](./classes/file/method/list.md)
    - [lock — эксклюзивное выполнение кода](./classes/file/method/lock.md)
    - [md5 — MD5-отпечаток файла](./classes/file/method/md5-static.md)
    - [move — перемещение или переименование файла](./classes/file/method/move.md)
  - Поля
    - [поля объекта класса](./classes/file/field/common.md)
- form
  - [Информация о классе](./classes/form/common.md)
  - Статические поля
    - [получение значения поля формы — ](./classes/form/field/get-value.md)
    - [elements — массивы всех полей формы](./classes/form/field/elements.md)
    - [fields — все поля формы](./classes/form/field/fields.md)
    - [files — получение множества файлов](./classes/form/field/files.md)
    - [imap — получение координат нажатия в ISMAP](./classes/form/field/imap.md)
    - [qtail — получение остатка строки запроса](./classes/form/field/qtail.md)
    - [tables — получение множества значений поля](./classes/form/field/tables.md)
- main


## Авторы

![](./assets/logo.png)

Язык скриптования сайтов Parser 3

![](./assets/ptic.png)

Автор технологий Parser и Parser 3:

- Константин Моршнев

Авторы Parser 3:

- Александр Петросян (PAF)
- Михаил Петрушин (Misha v.3)

Авторы документации:

- Константин Моршнев
- Алексей Сорокин
- Владимир Муров
- Александр Петросян (PAF)

Адаптация для markdown:
- Евгений Лепешкин (Spearance)