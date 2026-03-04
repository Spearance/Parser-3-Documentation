# Конструктор `create`

Создание документа на основе файла.

```parser3
^xdoc::create[файл]
```

Конструктор создает объект класса `xdoc`, который состоит из XML-кода, содержащегося в файле.

#### Пример
```parser3
$file[^file::load[binary;http://server/data.xml;
	$.timeout(10)
]]

$xdoc[^xdoc::create[$file]]
$response:body[^xdoc.string[]]
```
