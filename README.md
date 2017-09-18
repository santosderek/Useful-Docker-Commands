# Useful-Docker-Commands
A series of docker commands I find useful. 
---
Primarily for personal use. 

***Latest Plex Server:***
```
docker run \
-d \
--name plex \
-p 80:32400 \
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
-v /media/four_1/plex_storage:/data/four_tb_one \
plexinc/pms-docker
```
