# BASH

## Русский язык в консоли

	locale-gen ru_RU.UTF-8
	dpkg-reconfigure locales
	sudo apt-get install console-cyrillic
	localectl set-locale LANG=ru_RU.UTF-8

## Комбинации клавиш
	Ctrl + L 	- Очистить экран
	Ctrl + W 	- очистить слева от курсора, до ппробела
	Ctrl + U 	- очистить все слева от курсора
	Ctrl + K 	- очистить все справа от курсора
	Ctrl + R 	- поиск по истории команд
	Ctrl + T 	- меняет соседние символы местами

| cmd     | descriptiom                        |
| ---     | -----------                        |
| cd      | сменить директорию на уровень выше |
| !!      | повторить поледнюю команду         |
| atq     | посмотреть отложенные задания      |
| \`cmd\` | выполнить команду внутри \` `      |

## Массовое переименование
	$ ls
		text_comes_here_1.txt
		text_comes_here_2.txt
		text_comes_here_3.txt
		text_comes_here_4.txt
	

	$ rename 's/comes_here/goes_there/' *.txt
	$ ls
		text_goes_there_1.txt
		text_goes_there_2.txt
		text_goes_there_3.txt

## Юзкейсы

### Проверить открыт ли ssh
	nc -w 2 -zv 10.11.1.200 22

### создание и отправка ключа
	ssh-keygen
	chmod -R 700 ~/.ssh
	ssh-copy-id user@server

### Посмотреть запущенные сервисы
	rc-status

|    command  | descriptiom                                                       |
|      ---    |    ---                                                            |
| ls -lSrh       | сортировать файлы по размеру в обратном порядке                |
| ls -lSrh \*.mp* | --//-- только с расширением  начинающимся на .mp               |
| blkid /dev/sda1 | показать uuid устройства sda1
| `du -kx | egrep -v "\./.+/"` | sort -n | поиск самых больших директорий           |
| while ! [command]; do sleep 1; done | выполнять команду до успешного результата |
| `pv access.log | gzip > access.log.gz` | посмотреть информаци о передаче файла  |
| cat /etc/passwd | column -t   | вывод данных в виде таблицы                     |
| cat /dev/urandom > /dev/null  | загрузить процессор на полную                   |
| perl -pi -e 's/\r//' file.txt | убрать все '\n' из файла
| cp /home/sample.txt{,-old}    | создать в текушей директории копию файла с именем sample.txt-old |
| `echo wget https://sample.site/test.mp4 | at 2:00 PM` | отложенное задание      |
| `ls -al --time-style=+%D | grep $(date +%D)` | измененные сегодня файлы         |


## Текстовый редактор vi / vim
### В командном режиме
| cmd         | descriptiom                                   |
| ---         | -----------                                   |
| a           | в режим редактирования и на символ влево      |
| A           | в режим редактирования и в конец строки       |
| /info       | поиск слова info                              |
| n           | следеющий результат поиска                    |
| N           | предыдущий результат поиска                   |
| h,j,k,l     | влево вниз вверх вправо                       |
| 0           | в начало строки                               |
| `$`         | в конец строки                                |
| D           | удалить все справа от курсора в данной строке |
| dd          | удаляет слева от курсора в данной строке      |
| x           | удаляет символ под курсором                   |
| :syntax off | выключить/включить посветку синтаксиса        |
| :syntax on  | --//--                                        |
| :set background=dark  | сменить фон                         |
| :set background=light | --//--                              |

** чтобы не писать каждый раз, можно добавить в команды в файл: 
	
	~/.vimrc
	

## Работа с сетью

### Посмотреть доступные сетевые интерфейсы
	sudo lshw -C network

### Включить / Выключить интерфейс eth0
	ifup eth0 / ifdown eth0

### настройка статики
	iface eth0 inet static 
	address 192.168.0.1 
	netmask 255.255.255.0 
	gateway 192.168.0.254
	dns-nameservers 192.168.0.254 8.8.8.8
	auto eth0

### настройка dhcp client
	iface eth0 inet dhcp
	auto eth0

### Список открытых портов
	netstat -lnp

### Переименование сетевого интерфейса
	ip link set enp5s0 down
	ip link set enp5s0 name eth0
	ip link set eth0 up


## SYSTEM INFO

### Информация о процессоре
	cat /proc/cpuinfo

### Сколько файлов может быть открыто пользователем
	cat /proc/sys/fs/file-max

### Разрешен ли ip forward (0 - запрешен; 1 - разрешен)
	cat /proc/sys/net/ipv4/ip_forward

### Информация о модулях ядра
	lsmod

### Информация об устройствах pci
	lspci

### информация об устр-вах PCMCIA
	lspcmcia

### Информация о шине USB
	lsusb

### Информация о комплектующих
	lshw

### Все смонтированные устройства
	df -k
	cat /proc/mounts

### посмотреть UUID дисков
	blkid

### Древо загрузки процессов
	pstree



## BOOT

### Показать текущий run level
	runlevel
 
### Поменять уровень загрузки
	telinit (1-5)	/	init (1-5)

### Файл с описанием run level
	/etc/inittab
	
### Скрипты для runlevel'ов
	/etc/rc.d/rc(0-6).d


## SYSTEMCTL
### Показать все запущенные юниты, используемые устр-ва, точки монтирования, службы, сокеты, 
	systemctl list-units

### Юниты, которые не запустились
	systemctl --failed

### Показать запущенные сервисы
	systemctl list-units --type=service

### Посмотреть статус сервиса(службы)
	systemctl status crond

### Узнать запущенные таргеты
	systemctl list-units --type=target

### Переключиться на другой таргет
	systemctl isolate $name.target

### Установить таргет по умолчанию
	systemctl set-default -f $name.target

## Notification/MSGs

### отправка сообщения всем пользователям
	wall 'messages'



## INPUT OUTPUT

### Вывести первые 10 строк текстового файла
	head file.txt

### Вывести первые N строк текстового файла
	head -n N file.txt

### Форматирование все строки в одну строчку
	fmt file.txt

### Форматирование стоки (10 символов в строке)
	fmt -w 10 file.txt

### Заменить таб на несколько пробелов в файле
	expand filename 

### Заменить пробелы на на таб в файле
	unexpand filename

### Вывести указанные символы с каждой строки
	cut -c  2,3,4,10 filename

### Конвертирует файл в другой формат
	od filename # конвертироватьв в 8ричный код
	od -c filename # конвертировать в ASCII

### Объеденяет строчки по общему ключу
	cat 1.txt
		1 red
		2 blue
		3 white
		
	cat 2.txt
		1 apple
		2 sky
		3 board
		
	join 1.txt 2.txt
		1 red apple
		2 blue sky
		3 white board	

### объеденить файлы построчно
	cat 1.txt
		1 red
		2 blue
		3 white
		
	cat 2.txt
		1 apple
		2 sky
		3 board
		
	paste 1.txt 2.txt
		1 red		1 apple
		2 blue		2 sky
		3 white		3 board

### Просмотр файла по страницам
	less filename

### Пронумеровать линии/строки
	nl filename

### предварительны просмотр печати
	pr filename

## xargs
Просмотреть дату на всех хостах из файла /etc/hosts (ssh-ключи уже добавлены)

	awk '/^10/ {print $1}' /etc/hosts | xargs -n1 -I{} ssh '{}' date


## SED

### заменить слово в файле
	cat 1.txt
		1 red
		2 blue
		3 white
	sed -e 's/blue/orange/' 1.txt
		1 red
		2 orange
		3 white

### заменить в файле(ах) определенную строку на другую строку
	sed -i 's/.*ШАБЛОН.*/ЗАМЕНЯЮЩАЯ_СТРОКА/' ФАЙЛ


## TR
### Заменить все буквы на маленькие
		echo Hello | tr -t A-Z a-z
			hello

### Заменить букву 'l' на заглавную 'L'
	echo Hello | tr -t l Ll
		HeLLo

### Объеденить буквы 'l' в одну букву
	echo Hello | tr -s l
		Helo

### Удалить все 'l'
	echo Hello | tr -s l
		Heo

## СИМВОЛЫ
| символ | значение               |
|--------|------------------------|
| *	     | сколько угодно символов |
| ?     | один любой символ       |
| !	     | не                      |
| [ac]  | a или c                 |
| [a-c] | a b c                   |

## ПОИСК

### Найти по имени по всей ФС
	find / -name '*.txt'
	
### Найти файлы больше 5мб
	find / -size +5M
	
### Найти файлы с acces time болше 5 дней назад
	find / -atime +5
### Найти файлы с change time болше 5 дней назад
	find / -ctime +5
### Найти файлы типа (f - файл; d - папка)
	find / -type f 

## АРХИВАТОРЫ

## CPIO
### Архивировать файл
	cpio -o > filename
### Распаковать файл
	cpio -i > filename

## GZIP
### Заархивировать файл и удалить файл
	gzip filname
### Распаковать файл и удалить архив
	gunzip finlema.gz

## BZIP
### Заархивировать файл и удалить файл
	bzip filname
### Распаковать файл и удалить архив
	bunzip finlema.bz2

## XZ
### Заархивировать файл и удалить файл
	xz filname
### Распаковать файл и удалить архив
	unxz finlema.bz2

## TAR
	tar cvf ArchiveFilename SourceFile
	tar cvfg ArchiveFilename SourceFile
	tar xvf ArchiveFilename SourceFile

## ПРОЦЕССЫ

### Запуск процесса в работу даже после выхода пользователя
	nohup

### Активные процессы пользователя в данной сессии
	jobs
	
### открыть процесс в активном режиме (не фоновом)
	fg %номер из команды jobs%

### открыть процесс в фоновом режиме
	bg %номер из команды jobs%

### показать снапшот текущих процессов
	ps aux
	-a (все процессы) -u (все пользователи) -x (процессы во всех терминалах)

### древо процессов
	pstree

### убить процессы
	killall sleep

### запустить процесс не завясящий от текущей открытой сессии
### при завершении сессии - процесс останется выполняться 
	nohup sleep 1000 

## показать информацию о процессах
### показать id процессов sleep
	pgrep sleep
### показать id процессов и имена
	pgrep -l sleep
### показать все процессы пользователя user25
	pgrep -u user25 -l

### показать диспетчер процессов
	top
#### управление top
| команда | результат                                              |
|---------|--------------------------------------------------------|
| h             | help по комбинациям клавиш                       |
| < или >       | менять по какому столюцу будет сортировка        |
| k + pid + sig | процесса | что бы убить соответствующий процесс  |
| а затем тип sig'а
| 	15 - (sigterm) обычное завершение работы
| 	9 - (sigkill) жесткое убитие процесса


## SCREEN

### создать скрин и выполнить в нем команду ping
	screen -s yandex ping ya.ru
	
### посмотреть активные screen'ы
	screel -ls
	
### восстановить screen по названию 'yandex'
	screen -r yandex
	
### Выйти из screen'а не закрывая его
	'ctrl+a' 'D'
	
### Выйти из screen'а с закрытием
	'ctrl+d'

## SCP
	scp file.txt user@remote.host:/some/remote/directory

## SSH

	ssh-copy-id -i ~/.ssh/id_rsa user@remote.org.ua
	scp ~/.ssh/id_rsa.pub  user@remote.org.ua:~ 

remote$ [ -d ~/.ssh ] || (mkdir ~/.ssh; chmod 711 ~/.ssh) # создаем директорию и даём права
remote$ cat ~/id_rsa.pub >> ~/.ssh/authorized_keys        # добавляем открытый ключ
remote$ chmod 600 ~/.ssh/authorized_keys	       # делаем правильные права 
remote$ rm ~/id_rsa.pub			  # удаляем не нужное

### добавить ключ
	ssh-add ./work-key

### переброс порта
	ssh %OpenSshServer -N -L localport:ip:remoteport

	gpg --gen-key
	gpg --export keyname > file.public
	# на удаленном сервере
	gpg --list-key # проверить что нет ключей
	gpg --import  keyfile.public
	gpg --list-key # проверить что есть ключ
	gpg --out filename.encrypted --recipient 'user' --encrypt file.txt
	gpt --out filename.decrypted --decrypt filename.encrypted




## РЕГУЛЯРНЫЕ ВЫРАЖЕНИЯ
| regex   | описания                       |
| -----   | --------                       |
| \<text  | слова начинающиеся с text	   |
| \text>  | слова заканчивающиеся на text  |
| ^       | начало строки                  |
| `$`     | конец строки                   |
| [a-z]   | диапазон от a до z             |
| [^t]    | не буква t                     |
| \[      | воспринять символ [ буквально  |
| .       | любой символ                   |
| `a|z`   | a или z                        |


## RSYNC
### Если надо сделать резервную копию папки и скопировать только изменившиеся файлы, то можно использовать для этого rsync (вам нужен акаунт на удаленном компьютере):
	rsync -vare ssh jono@192.168.0.2:/home/jono/importantfiles/* /home/jono/backup/


## NTP
	ntpdate ntp.blueyonder.co.uk




Удаленный доступ к вашим программ
	X11Forwarding yes
	ssh -X 192.168.0.2 gimp


## СТРУКТУРА /etc/fstab

| устр. | место монтирования | fs (auto) | user | парам. сохран-ия на диск | парам. проверки |
| ---          | ---              | ---  | ---    | ---  | --- |
| /media/cdrom | udd,cdfs,iso9660 | user | noauto | exec | ro  |
 	
 	`/media/cdrom udd,cdfs,iso9660 user,noauto,exec,ro`

	user - можно монтировать пользователем
	noauto - не монтировать пристарте ОС 
	ro - только чтение
	rw - чтение запись
	userquota grpquota c
	парам сохран-ия на диск (dump) сохранять ли файлы при отключении системы
	0 - не записывать
	парам проверки
	1 - для "/" корня фс
	2 - у остальныъ
	0 - у съемных
 

jobs
Crontab
jobs
ps aux
разница kill и pkill
sigterm
fg bg
nohup
ps
pstree
psrep
free


Таргет - группировка юнитов (последовательность их вызова)

## Логические операции сравнения

| выражение | значение                                                   |
| --------- | --------                                                   |
| n1 -eq n2 | Возвращает истинное значение, если n1 равно n2.            |
| n1 -ge n2 | Возвращает истинное значение, если n1 больше или равно n2. |
| n1 -gt n2 | Возвращает истинное значение, если n1 больше n2.           |
| n1 -le n2 | Возвращает истинное значение, если n1 меньше или равно n2. |
| n1 -lt n2 | Возвращает истинное значение, если n1 меньше n2.           |
| n1 -ne n2 | Возвращает истинное значение, если n1 не равно n2.         |
|           |                                                            |
|str1 = str2   | Проверяет строки на равенство, возвращает истину, если строки идентичны.
| str1 != str2 | Возвращает истину, если строки не идентичны.            |
| str1 < str2  | Возвращает истину, если str1меньше, чем str2.           |
| str1 > str2  | Возвращает истину, если str1больше, чем str2.           |
| -n str1      | Возвращает истину, если длина str1больше нуля.          |
| -z str1      | Возвращает истину, если длина str1равна нулю.           |

## ПРИМЕРЫ СКРИПТОВ
## Существует ли пользователь "likegeeks"
	#!/bin/bash
	user=likegeeks
	if grep $user /etc/passwd
		then
		echo "The user $user Exists"
		else
		echo "The user $user doesn’t exist"
	fi

## РАБОТА С ПОЛЬЗОВАТЕЛЯМИ И ГРУППАМИ

### useradd
	useradd -m -G smbusers buh1
	-d # указать домашнюю папку нового пользователя
	-g # указать id группы в которую добавить пользователя
	-G # добавить группо по имени
	-m # создать папку сразу (без логина в систему)
	-u # вручную указать номер id пользователя

### usermod
	-L # Заблокировать уч. запись
	
### chage -l username	# показать свойства уч. запись
| Параметр             | Описание                             |
| --------             | --------                             |
| Last password change | когда менялся пароль                 |
| Password expires     | когда истекает пароль                |
| Password inactive    | когда пароль станет не активным      |
| Account expires      | когда истекает срок уч записи        |
| Minimum number of days between password change | мининимальное кол-во дней между сменами паролей |
| Maximum number of days between password change | максимальное кол-во дней между сменами паролей
| Number of days of warning before password expires | за сколько дней предупреждать об окончании срока действия пароля |

## tmux

	tmux ls 					# Показать активные сессии
	tmux attach-session -t 3 	# подключиться к сессии 3

### удаленный запуск сессии и отправка команды в запущенную сессию
	ssh root@10.11.1.201 tmux new-session -d -s sep
	ssh root@10.11.1.201 tmux send-keys -t 0 C-z 'top' Ente

### Комбинации клавиш для tmux
	Ctrl + b 	# Перейти в командный режим
	C-o		Rotate the panes in the current window forwards.
	C-z		Suspend the tmux client.
	! 		Break the current pane out of the window.
	" 		Split the current pane into two, top and bottom.
	# 		List all paste buffers.
	$	Rename the current session.
	%	Split the current pane into two, left and right.
	&	Kill the current window.
	'	Prompt for a window index to select.
	(	Switch the attached client to the previous session.
	)	Switch the attached client to the next session.
	,	Rename the current window.
	-	Delete the most recently copied buffer of text.
	.	Prompt for an index to move the current window.
	0 to 9      Select windows 0 to 9.
	:	Enter the tmux command prompt.
	;	Move to the previously active pane.
	=	Choose which buffer to paste interactively from a list.
	?	List all key bindings.
	D	Choose a client to detach.
	L	Switch the attached client back to the last session.
	[	Enter copy mode to copy text or view the history.
	]	Paste the most recently copied buffer of text.
	c	Create a new window.
	d	Detach the current client.
	f	Prompt to search for text in open windows.
	i	Display some information about the current window.
	l	Move to the previously selected window.
	n	Change to the next window.
	o	Select the next pane in the current window.
	p	Change to the previous window.
	q	Briefly display pane indexes.
	r	Force redraw of the attached client.
	m	Mark the current pane (see select-pane -m).
	M	Clear the marked pane.
	s	Select a new session for the attached client interactively.
	t	Show the time.
	w	Choose the current window interactively.
	x	Kill the current pane.
	z	Toggle zoom state of the current pane.
	{	Swap the current pane with the previous pane.
	}	Swap the current pane with the next pane.
	~	Show previous messages from tmux, if any.
	Page Up     Enter copy mode and scroll one page up.

userdel

groupadd
groupmod
groupdel

## AT-команды

### Позвонить на номер телефона с модема
	ATD+79109992233;
	echo -e "ATD+79104445691;\n;\r" > /dev/ttyUSB1
	
## /etc/systemd/logind.conf
| Параметр               | Описание                           |
| --------               | --------                           |
| HandleLidSwitch=ignore | Действие при закрытии крышки ноута |

## /etc/sudoers
### Allow members of group sudo to execute any command
	%sudo ALL=(ALL:ALL) ALL
	john ALL = NOPASSWD: /home/john/Documents/script.sh


## grep

	-i - игнорировать различие в больших и маленьких буквах

	grep -r proverka /
	ищет во всех каталогах файл с содержащий текст “proverka”
	
	grep что_ищем где_ищем
	grep CPU: /var/run/dmesg.boot
	или так
	</var/run/dmesg.boot grep CPU:
	
	grep WARNING /var/run/dmesg.boot -c
	найти в файле и подсчитать кол-во слов
	
	grep -w 'seven' test.txt
	поиск слова целиком
	
	grep '\<seven' test.txt
	grep 'seven\>' test.txt
	по началу и по концу слова
	
	grep '^seven' test.txt
	grep 'seven$' test.txt
	по началу и по концу
	
	grep -C 1 twentyseven test.txt
	строки в окрестности
	
	grep -A 1 twentyseven test.txt
	grep -B 1 twentyseven test.txt
	Только снизу или сверху?
	
	grep -v #
	исключить из вывода строку с #
	
	grep -o только слово (не строчка)
	
	-E регулярные выдажения
	
	grep -oE '\b[0-9]{1,3}(\.[0-9]{1,3}){3}\b' /etc/resolv.conf | grep -v '#
	nova flavor-list | grep -o 'm1.tiny' 

## СЕТЬ
### CentOS 
/etc/sysconfig/network-scripts/
								ifcfg-eth0
								ifcfg-enp0s3
								ifcfg-lo
	# пример файла
TYPE=Ethernet
BOOTPROTO=dhcp
DEFROUTE=yes			# через данную карту будут уходить пакеты на dgw
PEERDNS=yes				# файл resolve.conf будет перезаписываться получеными данными с этого интерфейса
PEERROUTES=yes			# аналогично для маршрутов
IPV4_FAILURE_FATAL=no	# не выключать интерфейс при ошибках ipv4 
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_PEERDNS=yes
IPV6_PEERROUTE=yes
IPV6_FAILURE_FATAL=no	# не выключать интерфейс при ошибках ipv4 
NAME=enp0s3
UUID=34145329584-85778657-834523895
DEVICE=enp0s3
ONBOOT=no				# включен или нет
IPADDR=192.168.160.11
NETMASK=255.255.255.0
GATEWAY=192.168.160.1
DNS1=192.168.160.1
DNS2=192.168.160.1


### Ubuntu
/etc/network/interfaces
	# пример файла
auto eth0
iface eth9 inet static
address 192.168.147.111
netmask 255.255.255.0
gateway 192.168.147.1
dns 192.168.147.1 8.8.8.8

auto eth1
iface eth1 inet dhcp

### установить ip адрес
	iconfig eth0 192.168.147.10/24
	ifconfi netmask 255.255.0.0
	iconfig eth0 hw ethernet %MacAddress

	ip -4 address flush eth0 # стереть ipv4 на интерфейсе
	ip address add 192.168.10.11/255.255.255.0 dev eth0



## sudo
### Редактирование прав su
	sudo visudo
### User privelege specification
	root ALL=(ALL:ALL) ALL
### user host=(user:group) cmd
 


### маршруты
route add default gw 192.168.0.1
route del default


### Включение и выключение интерфейсов
	ifup eth0 / ifdown eth0
	ip link set eth0 up / ip link set eth0 down

### Показать все сетевые интерфейсы (и выключенные)
	ifconfig -a

## Удаление драйвера
	lsmod #посмотреть модуля ядра
	rmmod %modname  

## APT полезное
	gpm		# мышь в консоли

## Мониторинг
	uptime # время работы ОС

	cat /proc/uptime # первое число - время работы (в секундах)
				 # второе число - время простоя (в секундах)


## STDIN STDOUT STDERR
	>&	-	перенаправить STDOUT и STDERR
	2>	-	перенаправить только STDERR
	cmd1 || cmd2	-	cmd2 будет выполняться если cmd1 выполнится с ошибкой
	cmd1 && cmd2	-	cmd2 будет выполняться если cmd1 выполнится без ошибки
	
	mail -s "subject1" jhon < message.txt


## WC
### wc - считает кол-во сток, слов и символов
	-l	-	кол-во строк (line)
	-w	-	кол-во слов (word)
	-c	-	кол-во символов (chfrfcter/bytes)
	
## Установка X-ов
	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get install firefox
	sudo apt-get install xorg
	sudo X -configure
	machine halt -h now
	sudo startx
	
	xwin
	xdpyidinfo
	xhost +192.168.147.96
	DISPLAY=192.168.1.n
	DISPLAY=:0.0
	 
	sudo apt-get install gdm kdm xdm
	sudo dpkg-reconfigure kdm
	cat /etc/x11
		/usr/bin/kdm

	
	
Q > Как проверить работоспособность nfs шары?
A > Попробовать примонтировать командой:
```
    mount -t nfs {IP шары}:/{путь/к/директории/на/сервере} {путь/к/локальной/директории}
```
Q > Проверить сколько свободно места на диске
A > 
```
    df -h
```
Q > Как инициализировать жесткий диск в системе без перезагрузки?
A >
```
	#!/bin/bash
	for i in /sys/class/scsi_host/host*; do 
	echo "- - -" > $i/scan; 
	done
```











