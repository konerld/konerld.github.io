# Ansible

По-умолчанию, в Ansible существует две группы: all и ungrouped. Первая включает в себя все хосты, а вторая, соответственно, хосты, которые не принадлежат ни одной из групп.

Инвентарный файл : 723

Конфигурационный файл Ansible может храниться в разных местах (файлы перечислены в порядке уменьшения приоритета):
	ANSIBLE_CONFIG (переменная окружения)
	ansible.cfg (в текущем каталоге)
	.ansible.cfg (в домашнем каталоге пользователя)
	/etc/ansible/ansible.cfg
	Ansible ищет файл конфигурации

