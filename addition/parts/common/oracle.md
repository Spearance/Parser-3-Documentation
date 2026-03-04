# Для Oracle

&nbsp;

```
oracle://user:password@service?
	ClientCharset=кодировка&
	LowerCaseColumnNames=0&
	DisableQueryModification=0& [3.3.0]
	NLS_LANG=RUSSIAN_AMERICA.CL8MSWIN1251&
	NLS_DATE_FORMAT=YYYY-MM-DD HH24:MI:SS&
	NLS_LANGUAGE=language-dependent conventions&
	NLS_TERRITORY=territory-dependent conventions&
	NLS_DATE_LANGUAGE=language for day and month names&
	NLS_NUMERIC_CHARACTERS=decimal character and group separator&
	NLS_CURRENCY=local currency symbol&
	NLS_ISO_CURRENCY=ISO currency symbol&
	NLS_SORT=sort sequence&
	ORA_ENCRYPT_LOGIN=TRUE
```
**[ClientCharset](/addition/parts/common/client-charset/)** — задает кодировку, в которой необходимо общаться с SQL-сервером, перекодированием занимается драйвер.

Если имена колонок в запросе `select` не взять в кавычки, Oracle преобразует их в ВЕРХНИЙ регистр. Parser 3 же по умолчанию преобразует их в нижний регистр. Указав параметр *LowerCaseColumnNames=0*, можно отключить преобразование в нижний регистр.

При выполнении запроса с *limit/offset* драйвер модифицирует текст запроса для отсечения ненужных данных средствами SQL-сервера. Однако в случае возникновения проблем это поведение можно отключить с помощью параметра *DisableQueryModification=1*.

Информацию по остальным параметрам можно найти в документации по Environment variables для Oracle. Однако, мы рекомендуем всегда задавать параметры **NLS_LANG** и **NLS_DATE_FORMAT** так, как указано выше.

#### Пример
Допустим, данные в базе хранятся в кодировке windows-1251, строку подключения стоит написать так:

```
oracle://user:password@service?ClientCharset=windows-1251&NLS_LANG=RUSSIAN_AMERICA.CL8MSWIN1251&NLS_DATE_FORMAT=YYYY-MM-DD HH24:MI:SS
```

> Существует специальная конструкция для записи больших строковых литералов. Oracle не умеет работать с большими строковыми литералами. Если передаваемая, например, из формы строка будет содержать больше 2000 [Oracle 7.x] или 4000 [Oracle 8.x] букв, сервер выдаст ошибку «Слишком длинный литерал». Если пытаться хитрить, комбинируя «2000 букв» + «2000 букв», то также будет выдана ошибка «Слишком длинная сумма». Для хранения таких конструкций используется тип данных CLOB[Oracle] и OID[Postgres], а для того чтобы SQL-команды были максимально просты, при записи таких строк необходимо лишь добавить управляющий комментарий, который драйвер соответствующего SQL-сервера обработает нужным образом:

```
insert into news text values (/**text**/'$form:text')
```

Слово **text** в записи `/\*\*text\*\*/` — это имя колонки, в которую предназначен следующий за этой конструкцией строковый литерал. Пробелы здесь недопустимы. 
