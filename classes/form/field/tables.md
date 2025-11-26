# Статическое поле `tables`

Получение множества значений поля.

```parser3
$form:tables
```

Поле возвращает редактируемый хеш со всеми элементами формы или параметрами, переданными через URL. Имена ключей хеша — это названия элементов формы, значениями же являются таблицы, см. ниже.

```parser3
$form:tables.поле_формы
```

Если поле формы имеет хотя бы одно значение, такая конструкция возвращает таблицу (объект класса `table`) с одним столбцом **field**, содержащим все значения поля. Используется для получения множества значений поля.

> Перед использованием таблицы нужно проверить ее определенность.

#### Пример

```parser3
Выберите, чем вы увлекаетесь в свободное время:
<form method="post">
	<fieldset>
		<input type="checkbox" name="hobby" value="Театр" id="theatre"> <label for="theatre">Театром</label>
		<input type="checkbox" name="hobby" value="Кино" id="movies"> <label for="movies">Кино</label>
		<input type="checkbox" name="hobby" value="Книги" id="books"> <label for="books">Книгами</label>
	</fieldset>
	<input type=submit value="OK">
</form>

$hobby[$form:tables.hobby]

^if($hobby){
	Ваши хобби:
	<ul>
		^hobby.menu{
			<li>$hobby.field</li>
		}
	</ul>
}{
	Ничего не выбрано
}
```

Пример выведет на экран выбранные варианты или напишет, что ничего не выбрано. 
