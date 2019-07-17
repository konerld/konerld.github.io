GIT
# установка
sudo apt-git install git

Q > Как получить URL проекта откуда был слонирован репозиторий
A > git config --get remote.origin.url
	git remote show origin
	git remote -v



# настройка
git congig --global user.name 'volkov.d'
	
Q > Как поменять vr_id ?
A > На deploy сервере в файле:
	 	/opt/rustack-installer/installer/12.module.vrrp.sh
	 Параметр:
	 	virtual_router_id 51


git config --list

git status --untracked-files=normal
	normal
	all
	nope

git add file.txt			# добавить на коммит
git rm --cashed file.txt	# отменить добавление на коммит



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


