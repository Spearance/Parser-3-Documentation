# Оператор `continue`

Переход к следующей итерации цикла.

```parser3
^continue[]
```
```parser3
^continue(условие)
```

Оператор continue может быть использован внутри циклов (`[for](/common/operators/common/for/)`, `[while](/common/operators/common/while/)`, `[menu](/class/table/method/menu/)`, `[foreach](/class/hash/method/foreach/)`) для их принудительного прерывания текущей итерации цикла и переходу к следующей. Использование оператора вне цикла недопустимо и приводит к ошибке **parser.continue**.

Вызов `^continue(условие)` эквивалентен `^if(условие){ ^continue[] }`. ***[3.4.5]***
