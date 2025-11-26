# Метод `sql-string`

Сохранение файла на SQL-сервере.

```parser3
^file.sql-string[]
```

Метод выдает строку, которую можно использовать в SQL-запросе. Позволяет сохранить файл в базе данных.

> На данный момент реализована поддержка только MySQL-сервера.

#### Пример
```parser3
$name[image.gif]
$file[^file::load[$name]]

^connect[строка соединения]{
	^void:sql{
		INSERT INTO images (name, bytes)
		VALUES ('$name', '^file.sql-string[]')
	}
} 
```
*[SQL]: Structured Query Language
