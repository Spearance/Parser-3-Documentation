# Опции 

Копирование и поиск.

При копировании записей из одной таблицы в другую:

`[table::create](/class/table/constructor/create/)`
`[table.join](/class/table/method/join/)`

и при поиске:

`[table.locate](/class/table/method/locate/)`

Можно задать хеш опций:

`$.offset(количество строк)` — пропустить указанное количество строк таблицы;
`$.offset[cur]` — с текущей строки таблицы;
`$.limit(максимум)` — максимум строк, которые можно обработать;
`$.reverse(true|false)` — true = в обратном порядке. 
