# Переменная CLASS_PATH

&nbsp;

В [конфигурационном методе](/addition/install/common/config-method/) может быть задана переменная или таблица `CLASS_PATH`, в которой задается путь (пути) к каталогу с файлами классов. Если имя подключаемого модуля указано относительно, то файл ищется по `CLASS_PATH` (если `CLASS_PATH` — таблица, то каталоги в ней перебираются снизу вверх).

#### Пример таблицы CLASS_PATH:

```parser3
$CLASS_PATH[^table::create{path
/classes/common
/classes/specific
}]
```
Теперь по относительному пути **my/class.p** поиск файла будет происходить в таком порядке:
**/classes/specific/my/class.p**
**/classes/common/my/class.p**
