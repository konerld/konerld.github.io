
torrent_wait_dir=/data/torrents/wait
torrent_download_dir=/data/torrents/download
tvshow_dir=/data/media/tvshows
movies_dir=/data/media/movies

DOCKER

DOCKER COMPOSE
sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version



FILEBOT
apt-get install openjdk-8-jdk mediainfo openjfx
wget -O filebot_4.7.5_amd64.deb http://downloads.sourceforge.net/project/filebot/filebot/FileBot_4.7.5/filebot_4.7.5_amd64.deb?r=http%3A%2F%2Fwww.filebot.net%2F&ts=1482609251&use_mirror=heanet
dpkg -i filebot_4.7.5_amd64.deb

cat .bash_aliases
```
alias anime-test='filebot --action test --conflict skip --format "{plex}" --db AniDB -r -non-strict --output /data/Media -rename'
alias series-test='filebot --action test --conflict skip --format "{plex}" --db TheTVDB -r -non-strict --output /data/Media -rename'
alias movie-test='filebot --action test --conflict skip --format "{plex}" --db TheMovieDB -r -non-strict --output /data/Media -rename'
alias music-test='filebot --action test --conflict skip --format "{plex}" --db AcoustID -r -non-strict --output /data/Media -rename'
alias anime-hardlink='filebot --action hardlink --conflict skip --format "{plex}" --db AniDB -r -non-strict --output /data/Media -rename'
alias series-hardlink='filebot --action hardlink --conflict skip --format "{plex}" --db TheTVDB -r -non-strict --output /data/Media -rename'
alias movie-hardlink='filebot --action hardlink --conflict skip --format "{plex}" --db TheMovieDB -r -non-strict --output /data/Media -rename'
alias anime-move='filebot --action move --conflict skip --format "{plex}" --db AniDB -r -non-strict --output /data/Media -rename'
alias series-move='filebot --action move --conflict skip --format "{plex}" --db TheTVDB -r -non-strict --output /data/Media -rename'
alias movie-move='filebot --action move --conflict skip --format "{plex}" --db TheMovieDB -r -non-strict --output /data/Media -rename'
alias music-move='filebot --action move --conflict skip --format "{plex}" --db AcoustID -r -non-strict --output /data/Media -rename'
```

PLEX

docker run \
-d \
--name plexmedia \
--net=host \
--restart=always \
-e TZ=Europe/Moscow \
-v /home/docker/plex/config:/config \
-v /home/docker/plex/tvshows:/data/tvshows \
-v /home/docker/plex/movies:/data/movies \
-v /home/docker/plex/transcode:/transcode \
-p 32400:32400/tcp \
-p 3005:3005/tcp \
-p 8324:8324/tcp \
-p 32469:32469/tcp \
-p 1900:1900/udp \
-p 32410:32410/udp \
-p 32412:32412/udp \
-p 32413:32413/udp \
-p 32414:32414/udp \
plexinc/pms-docker


TRANSMISSION
	https://www.smarthomebeginner.com/install-transmission-using-docker/
	https://www.maketecheasier.com/how-to-download-torrents-from-the-command-line-in-ubuntu/
	
# /watch - при попадании .torrent файла - начинается его скачивание
	# если торрент начался закачиваться к файлу добавляется .added
	# после завершения закачки - файл удаляется
# /downloads/complete - папка с завершенными закачками


docker create --name=transmission \
--restart=always \
-v /home/docker/transmission/config:/config \
-v /home/docker/transmission/downloads:/downloads \
-v /home/docker/transmission/watch:/watch \
-e PGID=1001 \
-e PUID=1001 \
-e TZ=Europe/Moscow \
-p 9091:9091 \
-p 51413:51413 \
-p 51413:51413/udp \
linuxserver/transmission

docker run transmission


TORRENT MONITORING
docker run \
-d \
--name torrentmonitor \
--restart=always \
-p 8080:80 \
-v /home/rsp/data/htdocs/torrents:/data/htdocs/torrents \
-v /home/rsp/data/htdocs/db:/data/htdocs/db \
nawa/torrentmonitor

далее http://192.168.148.90:8080
passwd: torrentmonitor


mkdir -p /opt/mediacenter/{mariadb-data,monitorrent-db,owncloud-apps,owncloud-config,plex-config,plex-transcode,torrentmonitor-db,torrentmonitor-torrents,transmission-config}
mkdir -p /data/Media/{Books,Documents,Downloads,Games,Home\ Videos,Movies,Music,ownCloud,Photos,Torrents,TVshows}


Plex: http://<YOUR_IP>:32400
Transmission: http://<YOUR_IP>:9091
TorrentMonitor: http://<YOUR_IP>:8080
Monitorrent: http://<YOUR_IP>:6687
ownCloud: http://<YOUR_IP>:8081



	





