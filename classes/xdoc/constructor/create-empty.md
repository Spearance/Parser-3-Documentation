# Конструктор `create`

Создание нового пустого документа.

```parser3
^xdoc::create[имя_тега]
```
```parser3
^xdoc::create[базовый_путь;имя_тега]
```

Конструктор создает объект класса `xdoc`, состоящий из единственного тега **имя_тега**. Возможно задание [базового пути](/class/xdoc/options/base-path/), относительно которого указываются имена подключаемых файлов.

#### Пример
```parser3
$document[^xdoc::create[document]]
$paraNode[^document.createElement[para]]
$addedNode[^document.documentElement.appendChild[$paraNode]]

$response:body[^document.string[]]
```
