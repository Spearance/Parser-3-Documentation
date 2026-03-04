# Поля

Объекта класса `image`.

`$картинка.src` — имя файла
`$картинка.width` — ширина
`$картинка.height` — высота
`$картинка.exif` — хеш с EXIF-информацией
`$картинка.xmp` — строка с XMP-информацией (в формате XML)



Ключами `$картинка.exif` являются названия EXIF-тегов (см. спецификацию [exiftool.org/TagNames/EXIF.html](https://exiftool.org/TagNames/EXIF.html)).

Значения имеют тип **string**, **int**, **double**, **date**. Когда тег имеет несколько значений, они считываются в хеш, ключами которого являются цифры `(0…[количество_значений-1])`.

Часто используемые EXIF-теги (см. подробности в спецификации):
| Тег | Тип | Описание |
|-----|-----|----------|
| Make | string | Производитель фотоаппарата |
| Model | string | Модель фотоаппарата |
| DateTimeOriginal | date | Дата и время съемки |
| ExposureTime | double | Выдержка в секундах |
| FNumber | double | Диафрагменное число F |
| Flash | int | `0` = не использовалась |
||| другие значения = использовалась |


> Ключами нестандартных EXIF-тегов являются их значения в десятичной системе счисления.

#### Пример
```parser3
$photo[^image::measure[photo.jpg]]

Имя файла: $photo.src<br>
Ширина изображения в пикселях: $photo.width<br>
Высота изображения в пикселях: $photo.height<br>

$date_time_original[$photo.exif.DateTimeOriginal]

^if(def $date_time_original){
	Снимок сделан ^date_time_original.sql-string[]<br>
}
```
Будет выведено имя файла, а также ширина и высота изображения, хранящегося в этом файле. Если снимок был сделан цифровым фотоаппаратом, вероятно, будет выведена дата и время съемки.

*[EXIF]: Exchangeable image file format
*[XMP]: Extensible Metadata Platform
*[XML]: eXtensible Markup Language
