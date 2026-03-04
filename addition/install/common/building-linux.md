# Сборка под Linux и другие Unix-подобные системы

&nbsp;

Для сборки Parser 3 под Linux и другие Unix-подобные системы необходимо использовать специально созданный скрипт **buildall**.

Т. е. в общем случае процесс скачивания исходных кодов и сборки Parser 3 будет выглядеть примерно так:

```
cd ~
mkdir parser3project
cd parser3project
wget https://www.parser.ru/off-line/download/src/parser-3.5.0.tar.gz
tar -xzf parser-3.5.0.tar.gz
mv parser-3.5.0 parser3
cd parser3
./buildall
```

Скрипт сборки поддерживает следующие параметры:

`--disable-safe-mode` — не проверять принадлежность открываемых Parser 3 файлов текущему пользователю;
`--without-xml` — собрать Parser 3 без поддержки XML;
`--with-mailreceive` — при запуске Parser 3 с ключом -m переданное на stdin письмо доступно в $mail:receive;
`--with-apache` — собирать модуль Apache (DSO, поддерживаются Apache 1.X и 2.X);
`--strip` — удалить отладочную информацию.


Сборка SQL-драйвера (на примере MySQL) будет выглядеть примерно так:

```
cd ~/parser3project
mkdir sql
cd sql
wget https://www.parser.ru/off-line/download/src/parser3mysql-10.9.tar.gz
tar -xzf parser3mysql-10.9.tar.gz
cd parser3mysql-10.9
./configure
make
```
