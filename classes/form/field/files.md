# Статическое поле `files`

Получение множества файлов.

```parser3
$form:files
```

Поле возвращает редактируемый хеш со всеми файлами формы. Имена ключей — это названия файловых элементов формы, значениями же являются хеши, см. ниже.

```parser3
$form:files.поле_формы
```

Если поле формы имеет хотя бы одно значение типа файл, такая конструкция возвращает хеш (объект класса `hash`) с ключами 0, 1, 2... (по количеству переданных файлов), содержащий все файлы с указанным именем. Используется для получения множества файлов с одинаковым именем формы.

> Перед использованием хеша нужно проверить его определенность.

#### Пример
```parser3
^if($form:files.picture){
	<p>Загружены изображения (^form:files.picture._count[]):
	^form:files.picture.foreach[sNum;fValue]{
		$fValue.name
		^fValue.save[binary;/upload/pictures/${sNum}.^file:justext[$fValue.name]]
	}[, ]
	</p>
}
<form method="post" enctype="multipart/form-data">
	<fieldset>
		<legend>Выберите несколько изображений для загрузки:</legend>

		<input type="file" name="picture"><br>
		<input type="file" name="picture"><br>
		<input type="file" name="picture"><br>
	</fieldset>
	<button type="submit">Загрузить</button>
</form>
```
