# Оператор `return`

Возврат из метода. ***[3.4.5]***

```parser3
^return[]
```
```parser3
^return[результат]
```
При вызове осуществляет принудительное прерывание выполнения метода на Parser, в котором написан код вызова `^return[]`. Результатом работы метода будет то, что успело вывестись до вызова `^return[]`, или текущее значение переменной `$result`. Вызов `^return[результат]` эквивалентен `$result[результат] ^return[]`. Чтобы вернуть пустую строку, нужно использовать `^return{}`.

#### Пример
```parser3
@main[]
$exit{ -return- ^return[] }

^check[good]{ $exit }
^check[normal]{ $exit }
^check[bad]{ $exit }
-end-

@check[value;exit]
Value: $value ^if($value eq 'bad'){ $exit } -passed-
```
Выведет:

**Value: good   -passed-**
**Value: normal -passed-**
**Value: bad    -return-**

> Код вызова `^return[]` написан в методе `@main[]`, поэтому возврат осуществляется из него. Для этого выполнение метода `@check[]` тоже прерывается, поэтому в выводе отсутствует **passed** для  значения **bad**.
