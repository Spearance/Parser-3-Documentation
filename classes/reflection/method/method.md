# Статический метод `:method`

Получение метода объекта. ***[3.4.2]***

```parser3
^reflection:method[объект;имя_метода]
```
```parser3
^reflection:method[класс;имя_метода]
```

Метод возвращает метод **объекта** или **класса**. Может быть использован в пользовательских классах, где приоритет доступа к полям выше, чем к методам с тем же именем.

```parser3
^reflection:method[метод]
```
```parser3
^reflection:method[метод;объект]
```

Привязывает **метод** к вызывавшему его объекту или классу либо к переданному вторым параметром **объекту** или классу. ***[3.4.5]*** В Parser все методы привязаны к контексту исполнения (self), и таким образом можно поменять эту привязку.


#### Пример

```parser3
@main[]
$a[^A::create[]]

# ^a.m[] - метод m не может использоваться напрямую, т. к. одноименное поле m имеет больший приоритет
# поэтому используем ^reflection:method[], чтобы добраться до метода m

$method[^reflection:method[$a;m]]
^method[]

$b[^B::create[]]

# подменяем self, чтобы вызвать метод m в контексте другого объекта, сохраняем результат в объекте b
$b.m[^reflection:method[$method;$b]]

# теперь в объекте b тоже есть метод m
^b.m[]

@CLASS
A

@create[]
$name[object of class A]
$m[object field]

@m[]
method of class A, called on $name

@CLASS
B

@create[]
$name[object of class B]
```

Выведет:

`method of class A, called on object of class A`
`method of class A, called on object of class B`
