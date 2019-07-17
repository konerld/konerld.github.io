Mikrotik

Синтаксис
Каждая команда заканчивается символом ";" или концом строки. В некоторых случаях эти символы не нужны для окончания команды. Команда внутри (), [] или {} не нуждается в таких символах.

Операторы
!=		не равно

DEFAULT FIREWALL
forward 				pasthrough (dynamic)
input icmp				accept
input establ;related	accept
input in ether1			drop

forward establ;related	pasthrough
forward establ;related	accept
forward	invalid			drop
forward	in eth1 new 	drop


Переменные
:local		действуют до выполнения скрипта
:local vova "192.168.147.1"

:global		действуют до перезагрузки

Условие
:if ( true ) do={ :put "lala" }

:if ( $a = true \
	and $b=false) do={ :put “$a $b”;

:put [/ip route get [find dst-address=0.0.0.0/0]];




#поменять адрес сети
:local dhcppoolrange "192.168.88.150-192.168.88.254"
/ip pool set default-dhcp ranges=$dhcppoolrange

#изменить диапазон dncp

dns


#поменять адрес роутера
:local routerip "192.168.88.10/24"
/ip address remove [find where interfac=bridge]
/ip address add address=$routerip interface=bridge


поменять порт winbox на 8191
/ip service set winbox port "8191"

отключить telnet
/ip service set telnet disabled=yes

открыть 8191 на вход
/ip firewall filter add chain=input protocol=tcp dst-port=8191 action=accept

установить пароль админу
/user set password=1qsx2waz

поменять имя устройства
:local rbhostname "mikAlpha"
/system identity set name=$rbhostname

	добавить l2tp клиент
:local l2tpintname "skl"
:local l2tpuser "_minePoole_"
:local l2tppass "ZZsswwqq22"
:local l2tpsrv "192.168.147.1"
:local l2tpipseckey "in314ih824"
/interface l2tp-client add name=$l2tpintname user=$l2tpuser password=$l2tppass connect-to=$l2tpsrv use-ipsec=yes ipsec-secret=$l2tpipseckey disabled=no

добавить маршруты


добавить настройки email
/tool e-mail set address=77.88.21.38 port=25 start-tls=yes from=MainMonitoring@yandex.ru user=MainMonitoring
@yandex.ru password=TGCzD7bFEWoRYBMMH4yA

добавить правила netwatch уведомлений
/tool netwatch add host=8.8.4.4 interval=1m timeout=3000 \
up-script={:local newIP [/ip address get [find interface="ether1"] address];
/tool e-mail send from="mainmonitoring@yandex.ru" server=213.180.193.38 to= mainmonitoring@yandex.ru body="MineSklad WAN is UP. RouterIP-192.168.145.1 ether1 ip = $newIP" subject="MineSklad WAN is UP. routerIP-192.168.145.1"}\
down-script={/tool e-mail send from="mainmonitoring@yandex.ru" server=213.180.193.38 to= mainmonitoring@yandex.ru body="MineSklad WAN is DOWN. RouterIP-192.168.145.1" subject="MineSklad WAN is DOWN. routerIP-192.168.145.1"};


/tool netwatch add host=8.8.4.4 interval=1m timeout=3000 \
up-script={:local newIP [/ip address get [find interface="ether1"] address];
:local rbhostname "mikOmega";
:local routerip "192.168.140.1";
/tool e-mail send from="mainmonitoring@yandex.ru" server=213.180.193.38 to= mainmonitoring@yandex.ru body="$rbhostname WAN is UP. RouterIP-$routerip ether1 ip = $newIP" subject="MineSklad WAN is UP. routerIP-$routerip"}\
down-script={:local rbhostname "mikOmega";
:local routerip "192.168.140.1";
/tool e-mail send from="mainmonitoring@yandex.ru" server=213.180.193.38 to= mainmonitoring@yandex.ru body="$rbhostname WAN is DOWN. RouterIP-$routerip" subject="MineSklad WAN is DOWN. routerIP-$routerip"};


настройка времени
/system ntp client set primary-ntp=91.226.136.155 secondary-ntp=109.195.19.73 enabled=yes

создание нового пользователя
задание ему пароля
удаления admin
настройка wifi




stratum+tcp://x11.eu.nicehash.com:3336#xnsub
stratum+tcp://x11.usa.nicehash.com:3336#xnsub
1L1XzqEbaS1dUrRSxBmdADK3AnPDnoNjm7.ibel11v01

1L1XzqEbaS1dUrRSxBmdADK3AnPDnoNjm7.ibel1102
1L1XzqEbaS1dUrRSxBmdADK3AnPDnoNjm7.ibel11v03
x




/interface l2tp-client>add name=l2tp-hm user=l2tp-hm password=123 \
\... connect-to=10.1.101.100 disabled=no
[admin@dzeltenais_burkaans] /interface l2tp-client> print detail   
Flags: X - disabled, R - running 
 0    name="l2tp-hm" max-mtu=1460 max-mru=1460 mrru=disabled 
      connect-to=10.1.101.100 user="l2tp-hm" password="123" 
      profile=default-encryption add-default-route=no dial-on-demand=no 
      allow=pap,chap,mschap1,mschap2 




:put " ENTO $[ :find [/tool sms inbox find .id=1] ] tak to";
/tool fetch host="mysite.ru" keep-result=no mode=http address="mysite.ru" src-path="/sms.php?msg=testmessage&amp;num=79123456789";


Инженер 2ой категории отдела тестирования
управления тестирования и тех документирования департамента исследования и разработки
Мютель

Узнать баланс
AT+CUSD=1,*100#,15


Вариант отправки AT команды через создание интерфейса
/interface ppp-client add name="scripttemp" port=serial0 modem-init="I am the string" null-modem=yes disabled=no
:delay 1
/interface ppp-client remove [/interface ppp-client find name="scripttemp"]



:local messageSMS "needdisableinterface";
:local phoneSMS "+79999999999";
:local defNameInterface "ether9";

:local countMSG [/tool sms inbox print count-only where message=$messageSMS phone=$phoneSMS];
:if ($countMSG = 0) do={
	/tool sms inbox remove [find];
} else={
	/interface ethernet disable [find default-name=$defNameInterface];
}


/tool sms send usb1 phone-number=+79017821420 message="hello i am mikrotik"

/system serial-terminal port=usb1
delay delay-time=3 
ATD+79104445691;
ATD+79017821420;


/interface ppp-client add name="scripttemp" dial-on-demand=no port=usb1 dial-command="ATD+79104445691;" modem-init="ATD+79104445691;" null-modem=yes disabled=no
:delay 1
/interface ppp-client remove [/interface ppp-client find name="scripttemp"]

/interface ppp-client set modem-init="ATD+79101234567"

/interface ppp-client add name="scripttemp" set modem-init="ATD+79104445691;"
interface ppp-client add name="scripttemp" set modem-init="ATD+79104445691;"

