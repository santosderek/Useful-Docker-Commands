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
-v /StorageDrives/plex/config:/config \
-v /StorageDrives/plex/transcode:/transcode \
-v /StorageDrives/plex/media:/data/ \
--restart always \
plexinc/pms-docker:plexpass
```

***Latest Plex Server w/ Hardware Encoding:***

*Change your device settings to your own hardware*

*Does not work on AMD graphics cards* 

```
docker run \
-d \
--name plex \
--network host \
-e TZ="EST" \
--device=/dev/dri/card0:/dev/dri/card0 \
--device=/dev/dri/renderD128:/dev/dri/renderD128 \
--device=/dev/nvidia0:/dev/nvidia0 \
--device=/dev/nvidiactl:/dev/nvidiactl \
--device="/dev/nvidia-modeset":"/dev/nvidia-modeset" \
--device="/dev/nvidia-uvm":"/dev/nvidia-uvm" \
-v /StorageDrives/plex/config:/config \
-v /StorageDrives/plex/transcode:/transcode \
-v /StorageDrives/plex/media:/data/ \
--restart always \
"plexinc/pms-docker:plexpass"
```


***Start Steam Cache***
```
docker run \
  --restart unless-stopped \
  --name steamcache \
  -p 192.168.75.15:80:80 \
  -v /StorageDrives/steamcache/cache:/data/cache \
  -v /StorageDrives/steamcache/logs:/data/logs \
  -d \
  -e CACHE_MEM_SIZE=6000m \
  -e CACHE_DISK_SIZE=2000g \
  steamcache/monolithic:latest
  
docker run --name steamcache-dns \
    --restart unless-stopped \
    -p 192.168.75.15:53:53/udp \
    -e USE_GENERIC_CACHE=true \
    -e LANCACHE_IP=192.168.75.15 \
    -e UPSTREAM_DNS=192.168.75.1 \
    -d \
    steamcache/steamcache-dns:latest

# Don't need this anymore (keeping just in case)
#docker exec -it steamcache chown -R nginx:nginx /data/

# ***Needs steamcache/sniproxy if images not loading***
docker run --name steamcache-sni --restart unless-stopped -it -d -p 192.168.75.15:443:443 steamcache/sniproxy
```
