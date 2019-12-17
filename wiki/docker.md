# Docker

## What is Docer ?
- Container Image spec
	how to package
- Cont

## What is Kubernetes role ?
Kubernetes is orchestrator for docker containers:
- Deploy
- Scale
- Manage

## What including in Kubernetes master ?
- API server
- Scheduler
- COntroller
- etcd

## What including in Kuber nodes ?
- Pods
- Docker
- kube proxy
- kubelet
- Fluentd
- Optional
	- DNS
	- UI
	- etc



Docker file -build-> Docker image -run-> Docker container

Изоляция достигается за счет использования таких Linux-механизмов, как:
namespaces	-	обеспечивают изоляцию в рамках ОС
control groups - устанавливают лимиты на потребление контейнером ресурсов хоста

docker pull image_name	-	загрузить образ image_name
docker images	-	посмотреть список загруженных образов (образы в системе)
docker ps	-	вывести список запущенных
docker ps -a	-	список запущенных ранее контейнеров
docker rm id_контейнера	-	удалить контейнер с указанным id

Удалить все контейнеры:
	docker rm $(docker ps -a -q -f status=exited)
docker rmi	-	удалить образ


docker run image_name	-	запустить образ image_name
docker run busybox echo "hello from busybox"	-	запустить образ busybox и выполнить команду из запущенного контейнера (echo "hello from busybox")


docker exec -i -t container_name /bin/bash
 Перейти в консоль контейнера



Запуск нескольких команд из контейнера:
docker run -it busybox sh
/ # ls
bin   dev   etc   home  proc  root  sys   tmp   usr   var
/ # uptime
 05:45:21 up  5:58,  0 users,  load average: 0.00, 0.01, 0.04

	Команда run с флагом -it подключает интерактивный tty в контейнер. Теперь можно запускать сколько угодно много команд внутри. Попробуйте.




UMPUTUN VPN

CID=$(docker run -d --restart=always --privileged -p 1194:1194/udp -p 443:443/tcp umputun/dockvpn)

docker run -t -i -p 8080:8080 --volumes-from $CID umputun/dockvpn serveconfig
docker run -t -i -p 8181:8080 --volumes-from $CID umputun/dockvpn serveconfig

https://178.62.200.139:8080/
	


docker ps
docker exec -i -t 115d0e4f665e bash

docker run -d -p11443:443 --name=mtproto-proxy --restart=always -v proxy-config:/data telegrammessenger/proxy:latest

docker run --restart always -d --name socs5 -e SOCKS_USER=_us@r_sAcs5_ -e SOCKS_PASSWORD=d_Sw3Ge7r#a% -p 1080:1080 ex3ndr/telegram-proxy
export http_proxy="http://user:password@host:port"
export http_proxy="http://_us@r_sAcs5_:d_Sw3Ge7r#a%@178.62.200.139:1080"
export http_proxy="https://_us$r_sAcs5_:d_Sw3Ge7r#a%@178.62.200.139:1080"


git clone https://github.com/mobilejazz/docker-ipsec-vpn-server.git
cd docker-ipsec-vpn-server
./start.sh
./adduser.sh _us$r_sAcs5_
Shared secret: eVzCL7RZYZsZVBWrAyrqHtHL4WsFxn
Password for user is: 7WovgTzTfmAAMvTndbHj

adduser.sh dwooklarmana
Shared secret: eVzCL7RZYZsZVBWrAyrqHtHL4WsFxn
Password for user is: C6w8dnhNupahEXkq3psn

docker run --restart=always -d -p 5867:5867 -e PROXY_USER=SET_USER -e PROXY_PASSWORD=SET_PASSWORD -e PROXY_SERVER=0.0.0.0:5867 xkuma/socks5





### Whar is CNCF?
Answer:







# Questions

## Block 1

### Question 1 of 3

### Question 2 of 3
What is the CNCF?
- Container Networking CLoud Fundation
- Cloud Native Computing Fundation
- Cloud 