# Конструктор `::base64`

Декодирование из Base64.

```parser3
^file::base64[закодированное]
```
```parser3
^file::base64[text|binary;имя_файла;закодированное;опции]
```

Декодирует файл из Base64-представления. Для кодирования файла следует использовать `^файл.base64[]`.

Можно задать хеш опций: ***[3.4.1]***
| Опция                     | Описание |
|---------------------------|----------|
| `$.strict(true)`          | будет выдаваться исключение при невозможности декодирования всех символов. Без указания данной опции файл будет создан из того, что было успешно декодировано. ***[3.4.2]*** |
| `$.url-safe(false\|true)` | использовать модифицированный алфавит, все символы которого не преобразовывались в `%XX` в URL (вместо «+» и «/» используются «\-» и «_»). По умолчанию не использовать. ***[3.4.6]*** |
| `$.pad(true\|false)`      | при кодировании были добавлены символы [паддинга](https://en.wikipedia.org/wiki/Base64) (=), по умолчанию. ***[3.4.6]*** |
| `$.content-type[...]`     | задать **content-type** создаваемого файла |

Подробная информация о Base64 доступна по ссылке: [ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt) и [wikipedia.org/wiki/Base64](https://en.wikipedia.org/wiki/Base64).

#### Пример
```parser3
$encoded[
R0lGODdhyAAyANUAAP////j88fLz8O/v7+v21uns4uTyyd/f397vu9vf1NfsrtDpoM/Pz8rmk8Tj
hr+/v73geK+vr6nWUJ+fn52jkJzQNZXNJ4+Pj39/f3BwcGBgYFBQUEBAQDAwMCAgIBAQEAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACwAAAAAyAAyAAAG/0CAcEgsChkRjHIZ
ORif0Kh0Sq1ar9isdkudaD6gsHj80US46LR6zW5zBxjweE73YAbuvH7P71/kdIFzHxN9hoeIiUQH
HIKOgRx4ipOUlVgPgHQcGUsYGY2CHwyWpKWlE4IbZ1ADE6CDo6ays3wRkE5VD69iorS+v2gMmSAf
q1h/g7jAy8ysHnMdylnC0M3W1wAZ0JJvz2MY2OG+DIPcwcPS4uqUuyAPbbZjGuv0kwdzGXkbc+n1
/nnaeJkzQqCBwQYIDASQcm/MhSmdIkrE8HDKgAcYM2rE2M8Ig40gNw68GLJkxwEXJqoE96SkSwDe
wrCEQqCChZs4JSyMomFMh/8pjwLNizKgQ1BisaCgOjrm3ZCiTMXMfGo0apgnPa2CIDemo5CaOMNa
0BmFqxivQrSGGepxmKNeT5ZqdQqAQcyoUwFAVWskq9YLPqOAFRuWLJS7haKoXdtWK1wicucecXt0
6l6+RPxq1ZzvyWDChXf2/SZlcZjOk00bAxBZ8gHKlYlUXSzbNIhdq4d8xglBAWHDRQCL4SCFg/Hj
yJPfJT4Ew5zkyTNN3eUBunXjox48vw49cVp5KyUSgcbdelOCNsVCEOJbLPAh2oezcS6/+ZzipIfs
ykslvhguc9CFRYBXEEjEbjetN0R7oRXh323zjcGcEPT9F8V+RGB4yX1bGJj/hYdUZCIgghYoSASD
OYkGwIMTplEhhPZ9s9Jd0+V3xYMghIdBbkOQVx5y451nxS50kagAFCjeBByLEdZHoW01SpXFa5s9
YRsIQYoh4BS4fZVeWEdGkeRYOwkXRotovNjii1pFKZMW1FjFVo+2ZRnGllJoBo6RVIxZAQEA6Nnk
mUSwaZWbOW4RZ1RzAnClne5cYSYIPy1AWJh9EuYATGN456KEhUKZoY1ZXMZURd+ZBimeZc1RAAAo
YloFiuslwM+gMD4po0o0jirlGy5hNFuidIpxQbAbrYpFJhSwd5OsVrSnYEBheNCGmqGOgd+vQmjI
h7eOCvmhuFVo9oEA7EF7/wUBm+qVCWpqYBujhVCAC64e4IJYILlUmPWmG9SGgRaFOi6xy5oc1kvq
vf3+iJx0kHbg8HHKYtFOUmrg2KiVpsHL5rb/dktqLqY9Fmidxd6ZBY4eDLTFAOhQYVqjH1+48Mj9
LWayEJpZVTEWPXfgMhamggCvYmptXLPC3ALA8BQ4HrXzED0z9fMVMG/DxQHDUjq0EUk/sfQT9uIM
tWMYGxGw1SlHCicdH7A6RQTDTA3FHBqEh2oRByRblkbSfJTRwE+QhOzg/R6uEREicdHaWoQPccA+
dPCItJb/ZJ7F42ulXUQEVYfhqcz8am56FBPA9sEGGEyA0QQYbKC65aWVflL67UUw0LVpHXhOOua4
B1+4oVZ9wJ8V+gqvPAAHhP7IBxl8XUXyyyuPUjuBbDCB9FY0Xv33Dqa0gXF5Hwv++einr/767Lfv
/vvwxy///PTXj0YQADs=
]

$original[^file::base64[$encoded]]
$filespec[/p2.gif]
^original.save[binary;$filespec]

<img src="$filespec">
```

Выведет:
![Paresr 3](./../../../assets/logo.png)
