# Статический метод `:basename`

Имя файла без пути.

```parser3
^file:basename[filespec]
```

Из полного пути к файлу `filespec` метод получает имя файла с расширением имени, но без пути.

#### Пример
```parser3
^file:basename[/a/some.tar.gz]
```

Выдаст: **some.tar.gz**
