# Метод `append`

Добавление строки в таблицу.

```parser3
^таблица.append{табличные_данные}
```
```parser3
^таблица.append[табличные_данные]
```
```parser3
^таблица.append[хеш]
```

Метод добавляет строку в конец таблицы. Формат представления **данных** — tab-delimited или хеш ***[3.4.4]***. Табличные данные должны иметь такую же структуру, как и таблица, в которую добавляются данные.

#### Пример
```parser3
$stuff[^table::create{name	pos
Alexander	boss
Sergey	coder
}]

^stuff.append{Nikolay	designer}
^stuff.append[
	$.name[Michael]
	$.pos[visitor]
]

^stuff.save[stuff.txt]
```
Пример добавит в таблицу `$stuff` новые строки и сохранит таблицу в файл **stuff.txt**. 
