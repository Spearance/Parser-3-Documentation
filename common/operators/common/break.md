# Оператор `break`

Выход из цикла.

```parser3
^break[]
```
```parser3
^break(условие)
```

Оператор `break` может быть использован внутри циклов (`[for](/common/operators/common/for/)`, `[while](/common/operators/common/while/)`, `[menu](/class/table/method/menu/)`, `[foreach](/class/hash/method/foreach/)`) для их принудительного прерывания. Использование оператора вне цикла недопустимо и приводит к ошибке **parser.break**.

Вызов `^break(условие)` эквивалентен `^if(условие){ ^break[] }`. ***[3.4.5]***
