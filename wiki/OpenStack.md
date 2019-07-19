# OpenStack Centos

* Добавить репозиторий:

		yum -у install epel-release

* Устанавливаем: 

		yum install -у https://rdo.fedorapeople.org/rdo-release.rpm
	



Q > Проверить кластер
A > rabbitmqctl cluster_status


Q > Как поменять vr_id ?
A > На deploy сервере в файле:
	 	/opt/rustack-installer/installer/12.module.vrrp.sh
	 Параметр:
	 	virtual_router_id 51