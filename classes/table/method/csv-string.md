# Метод `csv-string`

Преобразование в строку в формате CSV. ***[3.4.3]***

```parser3
^таблица.csv-string[]
```
```parser3
^таблица.csv-string[опции]
```
```parser3
^таблица.csv-string[nameless]
```
```parser3
^таблица.csv-string[nameless;опции]
```

Метод выводит содержимое таблицы в виде строки в формате CSV. Использование опции **nameless** выводит таблицу без имен столбцов.

#### Пример
```parser3
$table[^table::create{object	action	subject
Маша	"мыла"	раму
Мама	мыла	Машу
}]

^table.csv-string[
	$.encloser["]
	$.separator[,]
]
```
Выведет:
**"object","action","subject"**
**"Маша","""мыла""","раму"**
**"Мама","мыла","Машу"**

*[CSV]: Comma-Separated Values
