# Useful-Docker-Commands
A series of docker commands I find useful. 
---
Primarily for personal use. 

***Latest Plex Server:***
```
docker run \
-d \
--name plex \
-p 32400:32400 \
-p 3005:3005 \
-p 8324:8324 \
-p 32469:32469 \
-p 1900:1900 \
-p 32410:32410 \
-p 32412:32412 \
-p 32413:32413 \
-p 32414:32414 \
-e TZ="EST" \
-e PLEX_CLAIM="<claim token>" \
-v /hdd2/plex/plex_config/config:/config \
-v /hdd2/plex/plex_config/transcode/:/transcode \
-v /hdd2/plex/data:/data/hdd2 \
-v /media/four_2/plex_storage:/data/four_tb_2 \
--restart always \
plexinc/pms-docker
```

***Quick FTP Server***
docker run -d -v </path/to/dir>:/home/vsftpd \
                -p 20:20 -p 21:21 -p 47400-47470:47400-47470 \
                -e FTP_USER=<USERNAME> \
                -e FTP_PASS=<PASS> \
                -e PASV_ADDRESS=<IP_ADDRESS> \
                --name ftp \
                --restart=always bogem/ftp
