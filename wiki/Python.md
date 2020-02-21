# Python

## Системы исчисления

### Как записать число в N-ой системе исчисления

| 10-ая система | Целевая система   | Запись   |
| ------------- | ----------------- | -------- |
| 128           | Десятичная        | 128      |
| 43            | Двоичная          | 0b101011 |
| 143           | Восьмиричная      | 0o217    |
| 425           | Шестнадцатиричная | 0x1A9    |

### Как вывести число digit в определенной системе исчисления

| INPUT система | OUTPUT            | Запись        |
| ------------- | ----------------- | ------------- |
| Любая         | Десятичная        | print(digit)        |
| Любая         | Двоичная          | print( bin(digit) ) |
| Любая         | Восьмиричная      | print( oct(digit) ) |
| Любая         | Шестнадцатиричная | print( hex(digit) ) |

+=
a = a + b тоже самое что a += b

PIPE
просмотр установленных модулей
pip freeze
sudo pip install -r requirements.txt




вирт окружение
workon pyneng-py3

sudo pip install virtualenv

sudo pip install virtualenvwrapper
vi .bashrc
	# virtualenvwrapper
	export WORKON_HOME=$HOME/python_enviroments
	source /usr/local/bin/virtualenvwrapper.sh
source .bashrc
mkvirtualenv --python=/usr/local/bin/python3.6 $env_name
deactivate
workon <virtualenv_name>

добавить и активировать вирт окружение
virtualenv <virtualenv_name>
source <virtualenv_name>/bun/activate

выйти из окружения
deactivate

pip freeze проверить что никакие пакеты не установлены (мы в новом окружении)



Типы данных:
numbers числа
	int
	float
string
list
dictionary
tuples
sets		множества
booleans

Что бы были разные id элементов:
a1 = a2.copy()

Переменные

>>>>>>>>>>>>>>>>>>>>>>>>>>
Операторы>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>
**int (возведение в степень)>>>
>>>3**2
<<<9

and>>>
>>>"str1" and "str2" and "str3"
<<<str3 # последний элемент

>>>"" and [] and "str3"
<<<"" # первое ложное значение


%>>>
% - остаток отделения
Функции
Классы
методы  .copy() .clear() .del()
аргумент (фунции и методов)
Литерал dict()
	r1 = dict(model='4451', ios='15.4')

>>>>>>>>>>>>>>>>>>>>>>>>>>
ФУНКЦИИ>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>

print>>>
>>>mode ='access'
>>>access = 'sw port mode access'
>>>trunk = "sw port mode trunk"
>>>print(mode=='access' and access or mode=='trunk' and trunk)
<<<sw port mode access




from sys import argv




Списки list>>>

>>>in

пример присвоения
list1 = '1 2 3 4'
e1, e2, e3, e4 = list1.split()

set>>>

in>>>
l = [1,1,1,3,3,3,2]
set(l)
out>>>
{1, 2, 3}
in>>>
l.add(4)
l
out>>>
{1, 2, 3, 4}


кортеж
a = ('one', 'two', 'three')
b = ('monkey',) обязательно должна быть запятая в конце (даже если один элемент в кортеже)
без запятой это будет строка

a+b
>> ('one', 'two', 'three', 'monkey	')

Словари:
d1 = {1:100,2:200,3:300}
a = d1.keys() - получить все ключи словаря (a будет меняться вместе со словарем)
a = list(d1.keys())

d1.values() - значения
d1.items() - возвращает пару (ключ и значение)
len(d1.values()) - кол-во значений

# Создание словаря
for i in "one", "two", "three"
	dic[i] = 2
{'one':2, 'two':2, 'three':2}

# словать в словаре
dic[1st_lvl][2nd_lvl] = value

# sorted dictionary
from collections import OrderedDict
d = OrderedDict()


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
mat>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
выравнивание:
по леву		{0:<5}
по праву	{0:>5}
по центру	{0:^5}

in>>>
print('''
{0:<5} {0:08b}
{1:<5} {0:08b}
'''.format(2, 255))
out<<<
2     00000010
255   00000010
in>>>
'{:10}{:10}'.format(100,5)
out>>>
'       100         5'

in>>>
print('{:10}{:10}\n{:10}{:10}'.format(100,5,7,55))
out>>>
       100         5
         7        55

in>>>
print('{:10}{:10}\n{:10}{:10}'.format('on','table','a','word'))
out>>>
on        table 
a         word 



london = {'name': 'London1', 'location': 'London Str', 'vendor': 'Cisco', 'model': '4451', 'ios': '15.4'}

циклы:

for>>>

for i in [1,2,3]:
for i in rande(10):
for 'word' in 'text':


методы
.join>>>
in>>>
','.join(['1','2','3'])
out>>>
'1,2,3'

.get>>>
d1 = {'1':'100','2':'200','3':'300'}
d1.get(2, 'No element')
>>>200
d1.get(7, 'No element')
>>>'No element'
 
.setdefault>>>
Ищет ключ в словаре и возаращает значение
Если значение или ключ отсутствует - создает ключ и присваивает значение 'None'
d1.setdefault(1)
100
d1.setdefault(6)
None
d1 = {'1':'100','2':'200','3':'300','7':'None'}

.update>>>
d2.update(d1) - содержимае словаря d1 перезапишет идентичные значени в d2 
		или создаст новые в случае отсутствия значений

.dict>>>
var1:
r1 = dict(model='4451', ios='15.4')
r1
{'ios': '15.4', 'model': '4451'}
var2:
r1 = dict([('model','4451'), ('ios','15.4')])
r1
{'ios': '15.4', 'model': '4451'}

.fromkeys>>>
d_keys = ['hostname', 'location', 'vendor', 'model', 'ios', 'ip']
r1 = dict.fromkeys(d_keys)
r1
{'ios': None,
'ip': None,
'hostname': None,
'location': None,
'model': None,
'vendor': None}

.append>>> - добавляет в конец списка элемент
vlans = ['10', '20', '30', '100-200']
vlans.append('300')
vlans
['10', '20', '30', '100-200', '300']

list.pop([i]) 
Удаляет i-ый элемент и возвращает его. 
Если индекс не указан, удаляется последний элемент

.rstrip()
Убирает пустые строки при выводе и символы переноса строки '\n', tab 
for line in f:
	print(line.rstrip())

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Очистка строки от мусора>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
исходник:
line(str) = 'O        10.0.24.0/24 [110/41] via 10.0.13.3, 3d18h, FastEthernet0/0'
должный вид:
value(list) = ['OSPF', '10.0.24.0/24', '110/41', '10.0.13.3', '3d18h', 'FastEthernet0/0']
line = line.replace('O', 'OSPF')
line = line.replace('[','').replace(']','').replace(',','')
values = line.split()
values.remove('via')

Область видимости Пространство имен
L (local) - в локальной (внутри функции)
	переменные, которые определены внутри функции
	эти переменные становятся недоступными после выхода из функции
E (enclosing) - в локальной области объемлющих функций (это те функции, внутри
которых находится наша функция)
G (global) - в глобальной (в скрипте)
	переменные, которые определены вне функции
	эти переменные 'глобальны' только в пределах модуля
		например, чтобы они были доступны в другом модуле, их надо импортировать
B (built-in) - в встроенной (зарезервированные значения Python)



*args
**kwargs

string = 'apple, book, cam, door, earth, zombie'
a, b *args, z = string.split()
print(a)	apple
print(b)	book
print(args)	['cam', 'door', 'earth']
print(z)	zombie 

all

IP = '10.0.1.1'
all( i.isdigit() for i in IP.split('.'))
	True
all( i.isdigit() for i in '10.1.1.a'.split('.'))
	False
all([i.isdigit() and 1 <= int(i) < 255 for i in IP.splt('.') ])


print
print(1, 2, 3, 4, sep='|')
1|2|3|4


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Регулярные выражения>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
import re
match = re.search(regex, string)
	regex	- регулярное выражение
	string	- строка, в которой ищется совпадение
		Если совпадение было найдено, функция вернет специальный объект Match. 
		Если же совпадения не было, функция вернет None.

методы для re
re.search
re.match 	ищет только с начала строки
re.finditer
	result = re.finditer('(\S+) +'
						'([\d.]+), str_text)
re.findall
re.compile
Флаги
re.split
re.sub

методы для рузультатов поиска
	match.group показывает, что в строке совпало с описанным выражением (совпало с regex)
		Если совпало - возращает значение regex
		Если не совпало - None

tricks:
	match = re.finditer(regex_string, f.read())
	result = [m.group() for m in match]

	result = [m.groups() for m in re.finditer(regex, f.read())]
	result = {m.group('intf'): m.group('ip','mask') for m in matches}

Символы regex
"""
.		-	любой символ
\.		-	точка
_		-	пробел
[1-3]	-	с 1ого до 3ех
[13]	-	1ый и 3ий
[a-z]	-	от a до z

\d		- цифра 
\D		- любое не числовое значение
\s		- whitespace (\t\n\r\f\v)
\S		- любой символ кроме whitespace
\w		- любая буква, цифра или нижнее подчеркивание
\W		- все кроме буквы цифры или нижнего подчеркивания
+		- повторение предыдущего символа не менее одного или более раз
\d+		- одна или более цифр

regex+ - одно или более повторений предшествующего элемента
regex* - ноль или более повторений предшествующего элемента
regex? - ноль или одно повторение предшествующего элемента
regex{n} - ровно n повторений предшествующего элемента
regex{n,m} - от n до m повторений предшествующего элемента
regex{n, } - n или более повторений предшествующего элемента

{1,4}		 - диапазон повторений

.		- любой символ, кроме символа новой строки
^		- начало строки
$		- конец строки
[abc]	- любой символ в скобках
[^abc]	- любой символ, кроме тех, что в скобках
a|b		- элемент a или b
(regex)	- выражение рассматривается как один элемент. Кроме того, подстрока,
			которая совпала с выражением, запоминается
[^ab]	- любой символ кроме 'a' и 'b'

Группирование результатов:
match = re.search('(BW)\s+(\d+)', line)
print(match.group(1))
print(match[1])
print(match[2])
?:		- отключить захват в группе

Синтаксис именованной группы:
match = re.

\b		- граница слова ставится или вначале или вконце слова или и там и там
\B		-  Не граница слова: либо и слева, и справа буквы,
либо и слева, и справа НЕ буквы

[-+]? 	— либо -, либо +, либо пусто


"""
???
match = re.search(r'(\d\w', line)
\1


методы
>>>>>>>><<<<<<<<<
>>>groupdict()<<<
>>>>>>>>><<<<<<<<
In [19]: line = "FastEthernet0/1 10.0.12.1 YES manual up up"
In [20]: match = re.search('(?P<intf>\S+)\s+(?P<address>[\d.]+)\s+', line)
In [23]: match.groupdict()
Out[23]: {'address': '10.0.12.1', 'intf': 'FastEthernet0/1'}

match() - ищет последовательность в начале строки
search() - ищет первое совпадение с шаблоном
findall() - ищет все совпадения с шаблоном. Выдает результирующие строки в
виде списка
finditer() - ищет все совпадения с шаблоном. Выдает итератор
compile() - компилирует регулярное выражение. К этому объекту затем можно
применять все перечисленные функции
fullmatch() - вся строка должна соответствовать описанному регулярному
выражению
re.sub - для замены в строках
re.split - для разделения строки на части
start()
end()




примеры
In [2]: match = re.search('(([0-9a-fA-F]{4}\.){2}[0-9a-fA-F]{4}).+vlan (\d+).+port (\S
+).+port (\S+)', log)
In [3]: match.groups()
Out[3]: ('f03a.b216.7ad7', 'b216.', '10', 'Gi0/5', 'Gi0/15')
а если добавим ?: - то отключим захват в группе и тогда не будет лишнего 'b216.'
In [4]: match = re.search('((?:[0-9a-fA-F]{4}\.){2}[0-9a-fA-F]{4}).+vlan (\d+).+port (
\S+).+port (\S+)', log)
In [5]: match.groups()
Out[5]: ('f03a.b216.7ad7', '10', 'Gi0/5', 'Gi0/15')

In [9]: int_line = ' MTU 1500 bytes, BW 10000 Kbit, DLY 1000 usec,'
In [10]: match = re.search('BW \d+', int_line)
In [11]: match.group()
Out[11]: 'BW 10000'

In [1]: log = '*Jul 7 06:15:18.695: %LINEPROTO-5-UPDOWN: Line protocol on Interface '
				'Ethernet0/3, changed state to down'
In [2]: re.search('\d\d:\d\d:\d\d', log).group()
Out[2]: '06:15:18'

In [3]: log2 = 'Jun 3 14:39:05.941: %SW_MATM-4-MACFLAP_NOTIF: Host '
				'f03a.b216.7ad7 in vlan 10 is flapping between port Gi0/5 and port Gi0/15'
In [4]: re.search('\w\w\w\w\.\w\w\w\w\.\w\w\w\w', log2).group()
Out[4]: 'f03a.b216.7ad7'

In [3]: line = '100 aab1.a1a1.a5d3 FastEthernet0/1'
In [4]: re.search('(a1)+', line).group()
Out[4]: 'a1a1'

IP адрес можно описать выражением:
\d+\.\d+\.\d+\.\d+


email:
\w+@\w+\.\w+		# если до @ нет точек
\w+\.\w+@\w+\.\w+	# если до @ есть точки
\w+\.*\w+@\w+\.\w+	# для обоих вариантов
\w+\.?\w+@\w+\.\w+ 	# для обоих более правильный вариант


In [7]: line = '1500 aab1.a1a1.a5d3 FastEthernet0/1'
In [8]: re.search('\d+\s+\S+', line).group()
Out[8]: '1500 aab1.a1a1.a5d3'

In [9]: line = '100 a011.baaa.a5d3 FastEthernet0/1'
In [10]: re.search('ba*', line).group()
Out[10]: 'baaa'

In [24]: line = '100 aab1.a1a1.a5d3 FastEthernet0/1'
In [25]: re.search('\w{4}\.\w{4}\.\w{4}', line).group()
Out[25]: 'aab1.a1a1.a5d3'
	
In [26]: mac_table = '''
...: sw1#sh mac address-table
...: Mac Address Table
...: -------------------------------------------
...:
...: Vlan Mac Address Type Ports
...: ---- ----------- -------- -----
...: 100 a1b2.ac10.7000 DYNAMIC Gi0/1
...: 200 a0d4.cb20.7000 DYNAMIC Gi0/2
...: 300 acb4.cd30.7000 DYNAMIC Gi0/3
...: 1100 a2bb.ec40.7000 DYNAMIC Gi0/4
...: 500 aa4b.c550.7000 DYNAMIC Gi0/5
...: 1200 a1bb.1c60.7000 DYNAMIC Gi0/6
...: 1300 aa0b.cc70.7000 DYNAMIC Gi0/7
...: '''
In [27]: for line in mac_table.split('\n'):
...: match = re.search('\d{1,4}', line)
...: if match:
...: print('VLAN: ', match.group())
...:
VLAN: 1		# цифра в имени коммутатора
VLAN: 100
VLAN: 200
VLAN: 300
VLAN: 1100
VLAN: 500
VLAN: 1200
VLAN: 1300

заменить via или любой элемент из квадратных скобок на пробел
re.sub('(via|[,\[\]])', ' ', ospf_route)

match = re.search('\d{1,4} +', line) # правильный вариент

In [19]: line = "FastEthernet0/1 10.0.12.1 YES manual up up"
In [20]: match = re.search('(?P<intf>\S+)\s+(?P<address>[\d.]+)\s+', line)
Теперь к этим группам можно обращаться по имени:
In [21]: match.group('intf')
Out[21]: 'FastEthernet0/1'

исключить DYNAMIC и заменить . на :
In : mac_table = ''
..: 100 aabb.cc10.7000 DYNAMIC Gi0/1
..: 200 aabb.cc20.7000 DYNAMIC Gi0/2
..: 300 aabb.cc30.7000 DYNAMIC Gi0/3
.: 100 aabb.cc40.7000 DYNAMIC Gi0/4
..: 500 aabb.cc50.7000 DYNAMIC Gi0/5
..: 200 aabb.cc60.7000 DYNAMIC Gi0/6
..: 300 aabb.cc70.7000 DYNAMIC Gi0/7
In : print(re.sub(' *(\d+) +'
...: '([a-f0-9]+)\.'
...: '([a-f0-9]+)\.'
...: '([a-f0-9]+) +\w+ +'
...: '(\S+)',
...: r'\1 \2:\3:\4 \5',
...: mac_table))
...:
100 aabb:cc10:7000 Gi0/1
200 aabb:cc20:7000 Gi0/2
300 aabb:cc30:7000 Gi0/3
100 aabb:cc40:7000 Gi0/4
500 aabb:cc50:7000 Gi0/5
200 aabb:cc60:7000 Gi0/6
300 aabb:cc70:7000 Gi0/7

if match:
	if match.lastgroup == 'intf':
		interface = match.group(match.lastgroup)




>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Работа с CSV
>>>>>>>>>>>>>>>>>>>>>>>>>>>>
import csv

# чтение из файла csv
in : with open('sw_data.csv') as f:
		reader = csv.reader(f)
		print(reader)
out : <_csv.reader object at 0x10385b050>
in : print(list(reader))
	[['hostname', 'vendor', 'model', 'location'], ['sw1', 'Cisco', '3750', 'London'], ['sw
2', 'Cisco', '3850', 'Liverpool'], ['sw3', 'Cisco', '3650', 'Liverpool'], ['sw4', 'Cis
co', '3650', 'London']]
Чаще

in : with open('sw_data.csv') as f:
		reader = csv.DictReader(f)
		for row in reader:
			print(row)
			print(row['hostname'], row['model'])
out :
	OrderedDict([('hostname', 'sw1'), ('vendor', 'Cisco'), ('model', '3750'), ('location',
	'London')])
	sw1 3750
	OrderedDict([('hostname', 'sw2'), ('vendor', 'Cisco'), ('model', '3850'), ('location',
	'Liverpool')])
	sw2 3850

# Запись
data = [['hostname', 'vendor', 'model', 'location'],
	['sw1', 'Cisco', '3750', 'London, Best str'],
	['sw2', 'Cisco', '3850', 'Liverpool, Better str'],
	['sw3', 'Cisco', '3650', 'Liverpool, Better str'],
	['sw4', 'Cisco', '3650', 'London, Best str']]
with open('sw_data_new.csv', 'w') as f:		
	writer = csv.writer(f)
	for row in data:
		writer.writerow(row)

with open('sw_data_new.csv') as f:
	print(f.read())
hostname,vendor,model,location
sw1,Cisco,3750,"London, Best str"
sw2,Cisco,3850,"Liverpool, Better str"
sw3,Cisco,3650,"Liverpool, Better str"
sw4,Cisco,3650,"London, Best str"

# запись с кавычками
with open('sw_data_new.csv', 'w') as f:
	writer = csv.writer(f, quoting=csv.QUOTE_NONNUMERIC)
	for row in data:
		writer.writerow(row)
with open('sw_data_new.csv') as f:
	print(f.read())
"hostname","vendor","model","location"
"sw1","Cisco","3750","London, Best str"
"sw2","Cisco","3850","Liverpool, Better str"
"sw3","Cisco","3650","Liverpool, Better str"
"sw4","Cisco","3650","London, Best str"

# запись из словаря в файл csv
with open('csv_write_dictwriter.csv', 'w') as f:
	writer = csv.DictWriter(f, fieldnames=list(data[0].keys()),
								quoting=csv.QUOTE_NONNUMERIC)
	writer.writeheader()
	for d in data:
		writer.writerow(d)

# указание разделителя
reader = csv.reader(f, delimiter=';')

>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Работа с JSON
>>>>>>>>>>>>>>>>>>>>>>>>>>>>
import json
with open('sw_templates.json') as f:
	file_content = f.read()
	templates = json.loads(file_content)
print(templates)
for section, commands in templates.items():
print(section)
print('\n'.join(commands))
Результат


>>>>>>>>>>>>>>>>>>>>>>>>>>>>
sqlite3 >>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>

.execute() - метод для выполнения одного выражения SQL
	.executemany() - метод позволяет выполнить одно выражение SQL 
		для последовательности параметров (или для итератора)
	.executescript() - метод позволяет выполнить несколько выражений SQL за один раз
cursor.fetchall()
cursor.fetchmany(3)
cursor.fetchone()

connection.commit()
connection.close()

МЕТОД .execute

import sqlite3
connection = sqlite3.connect('test.db')
cursor = connection.cursor()
data = [
	('0000.AAAA.CCCC', 'sw1', 'Cisco 3750', 'London, Green Str'),
	('0000.BBBB.CCCC', 'sw2', 'Cisco 3780', 'London, Green Str'),
	('0000.AAAA.DDDD', 'sw3', 'Cisco 2960', 'London, Green Str'),
	('0011.AAAA.CCCC', 'sw4', 'Cisco 3750', 'London, Green Str')]
query = "INSERT into switch values (?, ?, ?, ?)"
for row in data:
	cursor.execute(query, row)
		Второй аргумент, который передается методу execute, должен быть кортежем. 
		Если нужно передать кортеж с одним элементом, используется запись (value, ) .
	
	Чтобы изменения были применены, нужно выполнить commit (обратите внимание, что 
	метод commit вызывается у соединения):
connection.commit()


МЕТОД .executemany
Метод executemany позволяет выполнить одну команду SQL для последовательности
параметров (или для итератора).
С помощью метода executemany в таблицу switch можно добавить аналогичный список
данных одной командой.

data2 = [
...: ('0000.1111.0001', 'sw5', 'Cisco 3750', 'London, Green Str'),
...: ('0000.1111.0002', 'sw6', 'Cisco 3750', 'London, Green Str'),
...: ('0000.1111.0003', 'sw7', 'Cisco 3750', 'London, Green Str'),
...: ('0000.1111.0004', 'sw8', 'Cisco 3750', 'London, Green Str')]
	
cursor.executemany(query, data2)
connection.commit()
	Второй аргумент, который передается методу executemany, должен быть списком кортежей. 

МЕТОД .executescript
Метод executescript позволяет выполнить несколько выражений SQL за один раз.
Особенно удобно использовать этот метод при создании таблиц:
connection = sqlite3.connect('new_db.db')
cursor = connection.cursor()
cursor.executescript('''
	create table switches(
	hostname text not NULL primary key,
	location text
	);

	create table dhcp(
	mac text not NULL primary key,
	ip text,
	vlan text,
	interface text,
	switch text not null references switches(hostname)
	);
	''')

Обработка исключений
In [37]: con = sqlite3.connect('sw_inventory2.db')
In [38]: query = "INSERT into switch values ('0000.AAAA.DDDD', 'sw7', 'Cisco 2960', 'London, Green Str')"
In [39]: con.execute(query)
IntegrityError Traceback (most recent call last)
<ipython-input-56-ad34d83a8a84> in <module>()
----> 1 con.execute(query)
IntegrityError: UNIQUE constraint failed: switch.mac

try:
    con.execute(query)
except sqlite3.IntegrityError as e:
    print("Error occured: ", e)
Error occured: UNIQUE constraint failed: switch.mac

метод enumerate для просмотра номера строки
for idx, line in enumerate(cursor.execute('select * from switch')):
	print(dx, line)
0 (mac1, host1, ...)
1 (mac2, host2, ...)






>>>>>>>>>>>>>>>>>>>>>>>>>>>>
выполнение bash команд>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
import subprocess
subprocess.run(['ls', '-la'])
или		
subprocess.run('ls -la', shell=True)

изменить место вывода
result = subprocess.run(['ls -la'], shell=True, stdout=subprocess.PIPE, encoding='utf-8')



почитать
sting.capitalize()
append()
argv[]


/ip route add distance=1 dst-address=10.0.0.1/32 gateway=<primary_chanel>
/ip route add distance=1 dst-address=77.88.8.1/32 gateway=<primary_chanel>

/ip route add comment=Overrided disabled=yes distance=2 gateway=<reserve_gateway>


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
COPMREHENSIONS>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
b = tuple([i,j] for i, j in topology_dict[dev][port].items())

Вопросы по автотестам
###################################
В common.py функция test_wrapper
	try:
		yield
###################################




TESTS
>>>>>assert<<<<<
assert type(a) == int, 'Зачение должно быть целым числом'

pytest
Создать функцию с "test_..." в названии
	def test_check_ip(id_addr):
		 assert check_ip(10.1.1.1/24) == True, 'ip ok'







