# Оператор `apply-taint`

Применение преобразований данных. ***[3.4.1]***

```parser3
^apply-taint[текст]
```
```parser3
^apply-taint[вид преобразования][текст]
```

Оператор `apply-taint` выполняет сиюминутное преобразование всех фрагментов в строке. Неопределенно «грязные» фрагменты преобразуются в указанный вид преобразования (по умолчанию **as-is**).

#### Пример
Пример, иллюстрирующий разницу между `taint` и `untaint`:
```parser3
$s[?	^taint[?]	^taint[uri][?]	^taint[file-spec][?]]
<pre>
^apply-taint[uri][$s]
^apply-taint[uri][^taint[as-is][$s]]
^apply-taint[uri][^untaint{$s}]
^apply-taint[uri][^untaint[uri]{$s}]
</pre>
```
Выведет:
**?	%3F	%3F	_3F**
**?	?	?	?**
**?	?	%3F	_3F**
**?	%3F	%3F	_3F** 
