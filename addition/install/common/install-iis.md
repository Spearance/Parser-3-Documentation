# Установка Parser на веб-сервер IIS 8.0 или новее

&nbsp;

Нужно поместить файлы с исполняемым кодом Parser в произвольный каталог. Если используется версия Parser с поддержкой XML, то в каталог, указанный в переменной окружения PATH (например, `C:\WinNT`), следует распаковать XML-библиотеки.

Затем назначить Parser обработчиком .html-страниц:

1) Запустить **Management Console**, кликнув правой кнопкой мыши на названии созданного веб-сервера, и выбрать **Properties**.
2) На вкладке **Home directory** и в разделе **Application settings** нажать на кнопку **Configuration…**
3) В появившемся окне нажать кнопку **Add**.
4) В поле **Executable** ввести полный путь к файлу **parser3.exe** или **parser3isapi.dll**.
5) В поле **Extension** ввести строку `.html`.
6) Включить опцию **Check that file exists**.
7) Нажать на кнопку **OK**.

## Подобие mod_rewrite

Для веб-сервера IIS встроенного подобия Apache-модуля **mod_rewrite** (см. также [egoroff.spb.ru/portfolio/apache/mod_rewrite.html](https://www.egoroff.spb.ru/portfolio/mod_rewrite.html)) нет, есть только модули, разработанные сторонними компаниями.

Однако можно назначить произвольную страницу **handler.html** в качестве обработчика ошибки 404 (рекомендуется ее же назначить обработчиком ошибок 403.14 и 405).

Оригинальный запрос при этом будет доступен в `$[request](/class/request/):[uri](/class/request/field/uri/)`.

К сожалению, при обработке POST-запросов к адресам, в которых не указано имя документа (…/), IIS не передает тело POST-запроса CGI-скриптам. Возможный вариант выхода из ситуации, задавать для таких страниц:
```html
<form action="form.html"…></form>
```
и перехватывать неизбежную ошибку отсутствия файла **form.html** в `[@unhandled_exception](/common/operators/common/unhandled-exception/)`, и подавляя ее запись в журнал ошибок. 

*[XML]: eXtensible Markup Language
*[IIS]: Internet Information Services
