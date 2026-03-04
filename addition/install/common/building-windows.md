# Сборка под Windows

&nbsp;

Для компиляции Parser 3 под Windows используется Microsoft Visual Studio.NET (2003 или новее) и заранее подготовленные нами файлы проектов (.sln). Все модули нужно распаковывать в один каталог, например parser3project.

Для сборки Parser 3 также необходимы каталоги:
**win32/tools**
**win32/gc**
**win32/pcre**
**win32/gnome/libxml2-x.x.x**
**win32/gnome/libxslt-x.x.x**

Для сборки SQL-драйверов необходим каталог:
**win32/sql**

Для сборки варианта Parser 3 без поддержки XML, в файле **parser3/src/include/pa_config_fixed.h** необходимо закомментировать директиву: `#define XML`.

*[XML]: eXtensible Markup Language
