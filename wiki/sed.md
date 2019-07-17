# SED

sed 's/test/another test' file.txt

-f file		-	взять команды из файла
-e 's/test/another test/ s/this/that'	-	несколько замен


флаги замены:
/2	-	номер вхождения для замены (в каждой стоке)
	sed 's/test/another test/2' myfile
/g	-	заменять все вхождения в строке (поумолчанию заменяется только 1ое)
	sed 's/test/another test/g' myfile
/p	-	вывести 8содержимое исходной строки после измененной
	sed 's/test/another test/g' myfile
	-n не выводить исходную строку и не измененные строки (только имененную)
/w file	-	указывает, что нужно записать результат обработки в файл
	sed 's/test/another test/w output' myfile

Заменить /bin/bash на /bin/csh в файле /etc/passwd
	sed 's/\/bin\/bash/\/bin\/csh/' /etc/passwd
	или
	sed 's!/bin/bash!/bin/csh!' /etc/passwd
	Разделителем будет считаться первый символ после "s"
применить изменения только для 2ой строки (отсчет начинается с 1ой)
	sed '2s/test/another test/' myfile
применить для диапазона строк
	sed '2,3s/test/another test/' myfile
со 2ой строки и до конца
	sed '2,$s/test/another test/' myfile
для строки в которой содержится "likegeek"
	sed '/likegeeks/s/bash/csh/' /etc/passwd

УДАЛЕНИЕ
удалить 3тью строку
	sed '2d' test.txt
удалить диапазон строк
	sed '2,3d'
удалить со 2ой строки и до конца файла
	sed '2,$d' myfile
удалить строки в которых есть слово 'test'
	sed '/test/d' myfile
удалить строки начиная со строки в которое встетилось слово 'second' до строки в которой встретилось слово 'fourth'
	sed '/second/,/fourth/d' myfile

ВСТАВКА
	i	- вставка перед
	a  	- вставка после
	echo "Another test" | sed 'i\First test '
Another test
First test

	sed '2i\This is the inserted line.' myfile
вставить 'This is the inserted line.' перед 2ой строкой
	sed '2a\This is the appended line.' myfile
вставить 'This is the appended line.' после 2ой строки файла
	sed '3c\This is a modified line.' myfile
заменить 3тью строку в файле на 'This is a modified line.'
	sed '/This is/c This is a changed line of text.' myfile
заменить все строчки в которых встречется 'This is' на 'This is a changed line of text.' (строка полностью перезаписывается заменяемой фразой)
	sed 'y/123/567/' myfile
заменяет все вхождения 1 на 4, 2 на 5, 3 на 6
	sed '='
выведет номера строк
	sed -n '/test/=' myfile
вывести номера строк в которых встречается фраза 'test'
	sed '3r newfile' myfile
содержимое файла newfile вставится после третьей строки файла myfile
	sed '/test/r newfile' myfile
Содержимое файла newfile будет вставлено после каждой строки файла myfile в которой встречается 'test'

