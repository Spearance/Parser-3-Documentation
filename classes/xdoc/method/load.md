# Метод `load`

Загрузка XML с диска, HTTP-сервера или иного источника.

```parser3
^xdoc::load[имя_файла]
```

Метод загружает XML-код из некоторого файла или адреса на HTTP-сервере и создает на его основе объект класса `xdoc`. Parser способен считать XML из произвольного источника, см. раздел «[Чтение XML из произвольного источника](/class/xdoc/options/read-xml/)».

**имя файла** — имя файла с путем или URL файла на HTTP-сервере.


#### Пример загрузки XML-документа с диска
```parser3
$xdoc[^xdoc::load[article.xml]]
$response:body[^xdoc.string[]]
```
#### Пример загрузки XML-документа с HTTP-сервера
```parser3
$xdoc[^xdoc::load[http://www.cbr.ru/scripts/XML_daily.asp]]
На
	^xdoc.selectString[string(/ValCurs/@Date)]
курс валюты
	$node[^xdoc.selectSingle[/ValCurs/Valute[CharCode='USD']]]
	"^node.selectString[string(Name)]"
равен
	^node.selectString[string(Value)]
<hr />
<pre>^taint[^xdoc.string[]]</pre>
```
> Чтобы пример корректно работал, необходимо чтобы в основном **auto.p** была раскомментирована строка `$.windows-1251[$charsetsdir/windows-1251.cfg]` хеша `$CHARSETS`.

*[XML]: eXtensible Markup Language
*[URL]: Uniform Resource Locator
