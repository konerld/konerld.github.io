# GIT

## Состояния файлов

**Рабочая директория/каталог** - текущее состояние всех файлов их изменений и история изменений Иначе говоря - комбинация всех ниже описанных статусов

### Виды состояний:
1. **Untracked** (не отслеживаемый) - не добавленный в репозиторий файл (новый или игнорируемый пользователем)
git: видит текущее состояние файла, но не хранит информацию об истории изменений

2. **Indexed / commited** (зафиксирован / закоммичен) - файл ранее уже добавлен в репозиторий и не изменялся со времен последнего коммита
git: не видит изменений между текущим состоянием и последним коммитом(их нет) и хранит всю историю коммитов(изменений)

3. **Modified** (измененный) - файл уже добавленный в репозиторий и имеющий изменения относительно последнего коммита
git: видит разницу между текущим состоянием и последним коммитом и хранит всю историю коммитов(изменений)

4. **Staged** (подготовленный) - файл отмеченный для добавления в следующий коммит
git: git хранит разницу помеченную на добавление в коммит и хранит всю историю коммитов(изменений) если она есть


## F.A.Q.
### Q: Как получить URL проекта откуда был слонирован репозиторий?
	
	git config --get remote.origin.url
	git remote show origin
	git remote -v

### Q: Разница между merge и rebase
**merge** - копирует изменения из одной ветки и добавляет в текущую в результате остаются две ветки объедеяются в одну (коммиты до слияния остаются в разных ветках)

**rebase** - переносит изменения из одной ветки в текущую удаляя ветку, из которой были перенесены изменеия

Ссылки по теме:
[Подробное описание на stackoverflow](https://stackoverflow.com/questions/16666089/whats-the-difference-between-git-merge-and-git-rebase)

### Q: Как переместить указатель ветки на другой коммит?
Перенести указатель ветки new_feature_branch в HEAD

	git branch -f new_feature_branch

### Как изменить последний коммит?

	git commit --amend

## Установка
### Установка на Debian

	sudo apt-get install git

## Настройка
### Прописать в настройках имя и почту:

	git config --global user.name 'ivanov'
	git config --global user.email 'ivan@ivanov.ru'

### Просмотреть настройки

	git config --list

## Работа
### Quick Start
Инициализировать (создать) репозиторий в текущей директории

	git init 

Посмотреть статус

	git status

Добавить файлы в stage (подготовить к коммиту)
	git add <file_name>

	git add *

Сделать коммит (сохранить текущее состояние с комментарием)

	git commit -m 'commit descriprion about change'

Добавить удаленный репозиторий в бренч с именем branch_name

	git remote add [branch_name] [url]

 ### Создать ветку
Создать ветку с именем branch_name можно командой:

	git branch branch_name

Создать ветку branch_name и переключиться на нее:

	git checkout -b branch_name
	

### Переключиться на ветку

### git merge
Добавить изменения из ветки master в текущую ветку (в которой сейчас находитесь). Обе ветки останутся существовать.

	git merge master

### git rebase
Слить изменения из ветки feature в текущую ветку master.
(коммиты из ветки )
 
	git rebase feature


## git diff
Увидеть, что вы изменили, но пока не проиндексировали:

	git diff

Посмотреть, что вы проиндексировали и что войдёт в следующий коммит:

	git diff --cached

Посмотреть, разницу между индексированными изменениями и последним коммитом:

	git diff --staged








git status --untracked-files=normal
	normal
	all
	nope

git add file.txt			# добавить на коммит
git rm --cached file.txt	# отменить добавление на коммит



git diff	-	показывает разницу между :
	a) рабочей директрорией и индексированными файлами (staged)
	b) между unmodified и modified
	НЕ ПОКАЗЫВЕТ между:
		если изменения в staged или уже unmodified
git diff --cached (или --staged) - посмотреть
	разницу между staged и unmodified (до попдания в staged)

git commit --amend 	-	дополнить последний коммит




git checkout -b hotfix	-	создать и перейти в branch hotfix

git branch -d hotfix	-	удалить branch 'horfix'

git checkout -- index.html
	Два дефиса '--' показывают, что мы имеем ввиду файл а не branch

git checkout {перые символы хэша} -- file.txt	- вернуть файл file.txt из коммита с указанным хэшом в текущем branch ('--' - указывает что нам нужен файл а не branch целиком)



проверить ключ
ssh-add -l

fix
ssh-add ~/.ssh/pykey

проверить подключение к github.com
ssh -T git@github.com


remote$ [ -d ~/.ssh ] || (mkdir ~/.ssh; chmod 711 ~/.ssh) # создаем директорию и даём права
remote$ cat ~/id_rsa.pub >> ~/.ssh/authorized_keys        # добавляем открытый ключ
remote$ chmod 600 ~/.ssh/authorized_keys                  # делаем правильные права 
remote$ rm ~/id_rsa.pub                                   # удаляем не нужное

После этого полностью копируем публичный ключ из области, выделенной красным цветом (на слайде выше), в консоли пишем cat >> .ssh/authorized_keys << EOF, нажимаем Enter, затем вставляем публичный ключ, еще раз нажимаем Enter, пишем EOF и еще раз жмем Enter

File Ccannot be lo
get-help about_signing" for more details.



sel 4977e2 0 1 2 3 4 5 6 7 8 9 10


git branch newbranch - создать новую ветку с именем newbranch
git branch -b newbranch - создать и перейти

git checkout newbranch - перейти в ветку с именем newbranch

git merge master

git rebase master
	-i - интерактивный режим

git log - посмотреть хэш коммитов
	^ - перемещение на 1 коммит назад
		git checkout HEAD^
	~N - перемещение на N коммитов назад

git branch -f master HEAD~3 - переносит ветку master на 3 родителя назад
-f (branch forcing)



git reset - отменяет изменения, перенося ссылку на ветку назад, на более старый коммит
	git reset HEAD~1
git revert - отменить изменения и поделиться отменёнными изменениями с остальными
	git revert HEAD


git cherry-pick <commit1> <commit2> - копировать несколько коммитов на место, где старый сейчаснаходишься (HEAD)

git rebase 



git log
	--author='Dima'
	--since=2018-12-30
	--until=2018=12-30
	--grep='init'
	-n 0

HEAD
	при checkout на другой branch - HEAD указывает на последний коммит в этом branch



git mergetool --tool=<tool>
merge tools
	deltawalker
	diffmerge
	tkdiff
have
	diffuse
	emerge
	opendiff
	vimdiff
	vimdiff2
	vimdiff3


## Полезные ссылки:
Игра для изучения веток:

	https://learngitbranching.js.org/


