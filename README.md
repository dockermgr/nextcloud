## 👋 Welcome to nextcloud 🚀  

nextcloud README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update nextcloud
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/nextcloud/rootfs"
git clone "https://github.com/dockermgr/nextcloud" "$HOME/.local/share/CasjaysDev/dockermgr/nextcloud"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/nextcloud/rootfs/." "$HOME/.local/share/srv/docker/nextcloud/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-nextcloud \
--hostname nextcloud \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-nextcloud/rootfs/data:/data:z" \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-nextcloud/rootfs/config:/config:z" \
-p 80:80 \
casjaysdevdocker/nextcloud:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/nextcloud
    container_name: casjaysdevdocker-nextcloud
    environment:
      - TZ=America/New_York
      - HOSTNAME=nextcloud
    volumes:
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-nextcloud/rootfs/data:/data:z"
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-nextcloud/rootfs/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/nextcloud
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/nextcloud" "$HOME/Projects/github/casjaysdevdocker/nextcloud"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/nextcloud"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
