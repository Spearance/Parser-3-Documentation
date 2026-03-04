# Свойства

&nbsp;

```parser3
@GET_имя[]
# код, выдающий значение или метод.
```

```parser3
@SET_имя[value]
# код, обрабатывающий новое значение $value.
```
```parser3
@GET_DEFAULT[]
@GET_DEFAULT[имя]
# код, обрабатывающий обращения к несуществующим полям или вызовы несуществующих методов.
```
```parser3
@SET_DEFAULT[имя;значение]
# код, обрабатывающий запись в несуществующие поля.
```
```parser3
@GET[]   [3.3.0]
@GET[тип_обращения]   [3.4.0]
# код, обрабатывающий обращения к объекту или классу в определенных контекстах вызова.
```

Можно определить default getter (@GET_DEFAULT[] ***[3.3.0]***) — метод, который будет вызываться при обращении к несуществующим полям. Имя поля, к которому пытались обратиться, передается единственным параметром этому методу. ***[3.3.0]***

> С этим методом нельзя работать как с обычным «свойством», при попытке написать `$DEFAULT` будет выдано сообщение об ошибке.

Также можно определить default setter (@SET_DEFAULT[имя;значение] ***[3.4.1]***) — метод, который будет вызываться при попытках записи в несуществующие поля. Имя поля, к которому пытались обратиться, и записываемое значение будут переданы этому методу.

У пользовательских классов можно определить специальное свойство `@GET[]`, которое будет вызываться при обращении к классу или объекту этого класса в определенных контекстах вызова, например: в скалярном контексте, в выражении и т. п. Если у этого свойства определен параметр, то через него будет передан **тип обращения**, который может принимать одно из следующих значений: **def**, **expression**, **bool**, **double**, **hash**, **table** или **file**.

> При обычном присваивании вида `$a[$b]` метод `@GET[]` не вызывается.

Так названные [методы](/common/constructions/common/method/) задают «свойство», которым можно пользоваться как обычной [переменной](/common/constructions/common/variables/):
| Пишем            | Происходит           |
|------------------|----------------------|
| `$имя`           | `^GET_имя[]`         |
| `$имя[значение]` | `^SET_имя\[[значение](/common/constructions/common/parameters/)\]` |


Если не требуется возможность записи или чтения свойства, соответствующий метод можно не определять.

> Нельзя иметь и свойство, и переменную с одним именем.

#### Пример: возраст и эл. почта
Возьмем человека — хранить удобно дату рождения, а выводить часто нужно возраст. Нужна эл. почта, но можно забыть проверить ее на корректность.

Пусть людьми занимается [класс](/common/constructions/common/class/), его свойства «**возраст**» и **email** позволят спрятать ненужные детали, сделав код проще и нагляднее:
```parser3
@USE
/person.p

@main[]
$person[^person::create[
	$.name[Василий Пупкин]
	$.birthday[^date::create(2000;8;5)]
]]

# можно менять, но значение проверят
$person.email[vasya@pupkin.ru]
$person.name ($person.email), возраст: $person.age<br>
```
Выведет:
**Василий Пупкин (vasya@pupkin\.ru), возраст: 5<br>** (с течением времени возраст будет увеличиваться)

При этом менять возраст человека нельзя:
```parser3
# это вызовет ошибку!
$person.age(99)
```
Также нельзя присваивать свойству email некорректные значения:
```parser3
# это вызовет ошибку!
$person.email[vasya#pupkin.ru]
```
#### Определение класса person

Чтобы вышеописанный пример сработал, нужно [определить](/common/constructions/common/class/) класс **person** и его свойства.

В корне веб-пространства в файл person.p поместим следующий код:
```parser3
@CLASS
person

@create[p]
$name[$p.name]
$birthday[$p.birthday]

# свойство «возраст»
@GET_age[][now;today;celebday]
$now[^date::now[]]
$today[^date::create($now.year;$now.month;$now.day)]
$celebday[^date::create($now.year;$birthday.month;$birthday.day)]
# числовое значение логического выражения: истина=1; ложь=0
$result(^if($birthday>$today)(0)($today.year — $birthday.year — ($today<$celebday)))

# свойство «e-mail»
@SET_email[value]
^if(!^Lib:isEmail[$value]){
	^throw[email.invalid;Некорректная эл. почта: '$value']
}
# имя переменной не должно совпадать с именем свойства!
$private_email[$value]

@GET_email[]
$private_email
```
> Метод `isEmail`, как и ряд других полезных методов и операторов, можно скачать по следующему адресу: [www.parser.ru/examples/lib/](https://www.parser.ru/examples/lib/).
> 
> Классы лучше помещать в отдельное удобное место и при подключении не указывать путь, см. `$[CLASS_PATH](/addition/parts/common/class-path/)`.

#### Пример: класс, расширяющий функциональность системного класса table
```parser3
@main[]
$t[^MyTable::create{a	b
0a	0b
1a	1b
2a	2b
3a	3b}]

Значение в выражении: ^eval($t)<br>
^^t.count: ^t.count[]<br>
Выводим содержимое пользовательского объекта: ^print[$t]<br>
<br>
Копируем объект и выводим ^^c.count[]:
$c[^MyTable::create[$t]]
^c.count[]<br>
Удаляем две строки, начиная со строки с offset=1, и выводим содержимое пользовательского объекта:
^c.remove(1;2)
^print[$c]<br>
<br>
Создаем объект системного класса table на основании объекта класса MyTable и выводим ^^z.count[]:
$z[^table::create[$t]]
^z.count[]<br>

@print[t]
^t.menu{$t.a = $t.b}[<br>]
```

#### Определение класса MyTable
```parser3
@CLASS
MyTable

@create[uParam]
^switch[$uParam.CLASS_NAME]{
	^case[string]{$t[^table::create{$uParam}]}
	^case[table;MyTable]{$t[^table::create[$uParam]]}
	^case[DEFAULT]{^throw[MyTable;Unsupported type $uParam.CLASS_NAME]}
}

# метод, возвращающий значение объекта в разных контекстах вызова
@GET[sMode]
^switch[$sMode]{
	^case[table]{$result[$t]}
	^case[bool]{$result($t!=0)}
	^case[def]{$result(true)}
	^case[expression;double]{$result($t)}
	^case[DEFAULT]{^throw[MyTable;Unsupported mode '$sMode']}
}

# метод обрабатывает обращения к «столбцам»
@GET_DEFAULT[sName]
$result[$t.$sName]

# для всех существующих методов нужно написать обертки-wrappers
@count[]
^t.count[]

@menu[jCode;sSeparator]
^t.menu{$jCode}[$sSeparator]

# добавляем новую функциональность
@remove[iOffset;iLimit]
$iLimit(^iLimit.int(0))
$t[^t.select(^t.offset[] < $iOffset || ^t.offset[] >= $iOffset+$iLimit)]
```
