# Конструктор `::measure`

Создание объекта на основе существующего графического файла.

```parser3
^image::measure[файл]
```
```parser3
^image::measure[имя_файла]
```
```parser3
^image::measure[файл;опции]
```
```parser3
^image::measure[имя_файла;опции]
```

Создает объект класса `image`, измеряя размеры существующего графического файла или объекта класса `file` в поддерживаемом формате. Поддерживаются **GIF**, **JPEG** и **PNG**, а начиная с версии ***[3.4.6]*** дополнительно поддерживаются **TIFF**, **BMP**, **WEBP** и при указании опции `$.video(true)` — еще и **MP4** (MOV).

Сама картинка не считывается, основное назначение метода — определение размеров и, например, последующий вызов для созданного объекта метода `html`.

Параметры конструктора:

**Файл** — объект класса `file`;
**Имя файла** — имя файла с путем.

Можно задать хеш опций: ***[3.4.6]***

| Опция                      | По умолчанию | Описание |
|----------------------------|--------------|----------|
| `$.video(false\|true)`     | false        | Определять размеры у видеофайлов в формате MP4 (MOV) |
| `$.exif(false\|true)`      | false        | Считывать EXIF-информацию из JPEG-файлов; до версии ***[3.4.6]*** EXIF-информация считывалась всегда; |
| `$.xmp(false\|true)`       | false        | Считывать [XMP](https://en.wikipedia.org/wiki/Extensible_Metadata_Platform)-информацию из JPEG-файлов; |
| `$.xmp-charset[кодировка]` | UTF-8        | Кодировка XMP-информации. |


> Поддерживается EXIF 1.0, считываются теги из IFD0 и SubIFD.

#### Пример создания тега IMG с указанием размеров изображения

```parser3
$photo[^image::measure[photo.png]]
^photo.html[]
```
Будет создан объект `photo` класса `image` на основе готового графического изображения в формате **PNG** и выдан тег `<img ...>`, ссылающийся на данный файл, с указанием `width` и `height`.

#### Пример работы с EXIF-информацией

```parser3
$image[^image::measure[jpg/DSC00003.JPG;
	$.exif(true)
]]

$exif[$image.exif]

^if($exif){
	Производитель фотоаппарата, модель: $exif.Make $exif.Model<br>
	Время съемки: ^exif.DateTimeOriginal.sql-string[]<br>
	Выдержка: $exif.ExposureTime секунды<br>
	Диафрагма: F$exif.FNumber<br>
	Использовалась вспышка: ^if(def $exif.Flash){^if($exif.Flash){да;нет};неизвестно}<br>
}{
	нет EXIF-информации<br>
}
```
*[EXIF]: Exchangeable image file format
*[JPEG]: Joint Photographic Experts Group
*[XMP]: Extensible Metadata Platform
*[GIF]: Graphics Interchange Format
*[PNG]: Portable Network Graphics
*[TIFF]: Tagged Image File Format
*[BMP]: Bitmap Picture
