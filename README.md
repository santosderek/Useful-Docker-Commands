# Useful-Docker-Commands
A series of docker commands I find useful. 
---
Primarily for personal use. 

*Latest Plex Server:*
```
docker run \
-d \
--name plex_latest \
-e TZ="EST" \
-v /hdd2/plex/config_for_latest_plex/config:/config \
-v /hdd2/plex/config_for_latest_plex/transcode/:/transcode \
-v /hdd2/plex/data:/data/hdd2 \
-v /media/four_1/plex_storage:/data/four_tb_one \
-p 0.0.0.0:80:32400/tcp \
-e PLEX_CLAIM="<plex.tv/claim>" \
--restart always \
plexinc/pms-docker
```
