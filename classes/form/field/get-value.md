# Поля формы

Получение значения поля формы.

```parser3
$form:поле_формы
```

Такая конструкция возвращает значение поля формы. Возвращаемый объект может принадлежать либо классу `file`, если поле формы имеет тип `file`, либо классу `string`. Дальнейшая работа с объектом возможна только методами, определенными для соответствующих классов.

Поле без имени считается имеющим имя `nameless`. Координаты нажатия пользователем на картинку с атрибутом **ISMAP** доступны через `$form:imap`.

Необходимо помнить, что если в HTML используется `<input type="image" name="fieldname">`, то при нажатии пользователем на эту кнопку мышью, браузером на сервер передаются координаты места произошедшего события в полях `fieldname.x` и `fieldname.y`.

#### Пример: текстовое поле, поле типа **image** и загрузка файла

```parser3
^if(def $form:photo){
	^form:photo.save[binary;/upload/photos/beauty.^file:justext[$form:photo.name]]
	Файл $form:photo.name загружен на сервер.
}

^if(def $form:user){
	Пользователь: $form:user<br>
}

^if(def $form:[action.x]){
	Координаты:<br>
	X: $form:[action.x]<br>
	Y: $form:[action.y]<br>
}

<form method="post" enctype="multipart/form-data">
	<input type="file" name="photo">
	<input type="text" name="user">
	<input type="image" name="action" src="/i/button.gif" width="75" height="25">
</form>
```
Этот код сохранит картинку, выбранную пользователем в поле формы и присланную на сервер, в заданном файле.


#### Пример: безымянное поле

<img src="/show.html?123&a=b">

Внутри `show.html` строка **123** доступна как `$form:nameless`.
