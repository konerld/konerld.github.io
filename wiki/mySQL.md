# SQL
apt-get install mysql-server

Язык SQL подрязделяется на 4 категории:
DDL - Data Definition Language (язык описания данных)
	CREATE - создание новой таблицы, СУБД, схемы
	ALTER - изменение существующей таблицы, колонки
		
		sqlite> ALTER table switch ADD COLUMN mngmt_ip text;
		sqlite> ALTER table switch ADD COLUMN mngmt_vid integer;
	
	DROP - удаление существующих объектов из СУБД
	
		DROP table table_name;
	
DML - Data Manipulation Language (язык манипулирования данными)
	
	SELECT - выбор данных
	
		SELECT * from switch;
	
	INSERT - добавление новых данных

		INSERT into switch (mac, model, location, hostname)
		values ('0020.A2AA.C2CC', 'Cisco 3850', 'London, Green Str', 'sw2');
	
	UPDATE - обновление существующих данных
		UPDATE switch set mngmt_ip = '10.255.1.1' WHERE hostname = 'sw1';
		UPDATE switch set mngmt_vid = 255 WHERE hostname = 'sw1';
		UPDATE switch set mngmt_ip = '10.255.1.2', mngmt_vid = 255 WHERE hostname = 'sw2';
		UPDATE switch set model = 'Cisco 3850', mac = '0010.D1DD.E1EE' WHERE hostname = 'sw1';
	DELETE - удаление данных
		DELETE from switch where hostname = 'sw8';
	REPLACE - используется для добавления или замены данных в таблице.
		REPLACE INTO switch VALUES ('0030.A3AA.C1CC', 'sw3', 'Cisco 3850', 'London, Green Str', '10.255.1.3', 255);
DCL - Data Control Language (язык определения доступа к данным)
	GRANT - предоставление пользователям разрешения на чтение/запись определенных объектов в СУБД
	REVOKE - отзыв ранее предоставленных разрешений
TCL - Transaction Control Language (язык определения транзакций)
	COMMIT Transaction - применение транзакции
	ROLLBACK Transaction - откат всех изменений, сделанных в текущей транзакции


Типы данных:
INT
TEXT
YEAR
VARCHAR

(N) - кол-во символов
not NULL

SELECT
INSERT


CREATE DATABASE cars;
USE cars;
CREATE TABLE new (brand VARCHAR(10), model VARCHAR(10), year YEAR, price INT);
CREATE TABLE used (brand VARCHAR(10), model VARCHAR(10), year YEAR, price INT);
CREATE TABLE new (id INT NOT NULL AUTO_INCREMENT, brand VARCHAR(10), model VARCHAR(10), year YEAR, price INT, PRIMARY KEY(id))
# Показать все таблицы в БД
SHOW TABLES;
# Показать описание столбцов таблицы new
DESCRIBE new;

# Запустить mysql в режиме импорта 
sudo mysql --local-infile=1 -u root
LOAD DATA LOCAL INFILE 'new.txt' INTO TABLE new;
INSERT INTO new (brand, model, year) VALUES ('Daewoo', 'Nexia', '2015');
DELETE * FROM used WHERE model='Murano';
SELECT * new;
UPDATE new SET model='Kuga' model='Focus';
SELECT * FROM new JOIN used ON new.brand = used.brand;
SELECT * FROM new ORDER BY price;
# Получить уникальный список брендов (без повторов)
SELECT * FROM new GROUP BY brand;

метакоманд:
.help - подсказка со списком всех метакоманд
.exit или .quit - выход из сессии sqlite3
.databases - показывает присоединенные БД
.tables - показывает доступные таблицы
.schema table_name - показать структуру таблицы table_name
.headers ON - 
.mode column
.width 20 10 8 - установить ширину колонки (для 1ого 2ого и 3его столбца)
.read file.txt

HOMEDIR/.sqliterc

_ - обозначает один символ или число
% - обозначает ноль, один или много символов

SELECT * from switch WHERE model LIKE '%3750';
SELECT * from switch WHERE model = 'C3750' or model = 'Cisco';

SELECT count(*) from swith where model = 'Cisco';
SELECT count(*) from swith where netmask betweem 14 and 17;
SELECT * from swith where netmask betweem 14 and 17 LIMIT 10;
ORDER BY hostname ASC;
ORDER BY hostname DESC;
AND
	select * from switch where model = 'Cisco 3750' and ip LIKE '10.0.%';
OR
	select * from switch where model = 'Cisco 3750' or model = 'Cisco 3850';
IN
	select * from switch where model in ('Cisco 3750', 'C3750');
NOT
	select * from switch where model not in ('Cisco 3750', 'C3750');






CREATE table switch (
mac text not NULL primary key,
hostname text,
model text,
location text);

INSERT into switch (mac, model, location, hostname)
values ('0020.A2AA.C2CC', 'Cisco 3850', 'London, Green Str', 'sw2');




 
SQLite

Добавить в таблицу "dhcp" столбуц "action" тип данных integer
ALTER TABLE dhcp ADD COLUMN last_active text;
 




