# parser://метод/параметр

Чтение XML из произвольного источника.

Parser может считать XML из произвольного источника. Везде, где можно считать XML, можно задать адрес документа в виде `parser://метод/параметр`.

Считывание документа по такому адресу приводит к чтению результата работы метода Parser:` ^метод[/параметр]`.

#### Пример хранения XSL-шаблонов в базе данных
```parser3
@main[]
…
# к этому моменту в $xdoc находится документ, который хотим преобразовать
^xdoc.transform[parser://xsl_database/main.xsl]

@xsl_database[name]
^string:sql{SELECT text FROM xsl WHERE name='$name'}
```
Причем относительные ссылки будут обработаны точно так же, как если бы файлы читались с диска. Скажем, если **parser://xsl_database/main.xsl** ссылается на **utils/common.xsl**, то будет загружен документ **parser://xsl_database/utils/common.xsl**, для чего будет вызван метод `^xsl_database[/utils/common.xsl]`. 

*[XML]: eXtensible Markup Language
