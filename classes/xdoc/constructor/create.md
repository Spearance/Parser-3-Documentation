# Конструктор `create`

Создание документа на основе заданного XML.

```parser3
^xdoc::create{XML-код}
```
```parser3
^xdoc::create[базовый_путь]{XML-код}
```

Конструктор создает объект класса `xdoc` из XML-кода. Возможно задание [базового пути](/class/xdoc/options/base-path/), относительно которого указываются имена подключаемых файлов.

#### Пример
```parser3
$document[^xdoc::create{<?xml version="1.0" encoding="windows-1251" ?>
<document>
	текст
</document>}]

$response:body[^document.string[]]
```
