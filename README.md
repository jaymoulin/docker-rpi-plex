![logo](logo.png)

Raspberry PI - Plex Media Server - Docker Image
===

[![latest release](https://img.shields.io/github/release/jaymoulin/docker-rpi-plex.svg "latest release")](http://github.com/jaymoulin/docker-rpi-plex/releases)
[![Follow on twitter](https://img.shields.io/twitter/follow/DockerRpiPlex.svg?style=social&label=Follow "Follow on twitter")](https://twitter.com/DockerRpiPlex)


This image allows you to configure a Plex Media Server easily thanks to Docker.

Installation
---

First, you have to mount your USB drive.
```
sudo mount /dev/sda1 /mnt/usbdrive
```

This will start Plex using your mounted drive
```
docker run -d --restart=always --name plex -v /mnt/usbdrive:/media --net=host jaymoulin/rpi-plex
```

Configuration
---

Go to http://__raspberry_ip__:32400 to configure it

You can change the Plex Library directory by plugin your local folder to `/root/Library` folder 

Example :

```
docker run -d --restart=always --name plex -v /mnt/usbdrive:/media --net=host -v /mnt/usbdrive:/root/Library jaymoulin/rpi-plex
```

Updating
---

When Plex Media Server new version is released, you will be able to update your running version with this command:
 
```
docker exec plex apt-get update && docker exec plex apt-get upgrade -y
```

Appendixes
---

### Install RaspberryPi Docker

If you don't have Docker installed yet, you can do it easily in one line using this command
 
```
curl -sSL "https://gist.githubusercontent.com/jaymoulin/e749a189511cd965f45919f2f99e45f3/raw/0e650b38fde684c4ac534b254099d6d5543375f1/ARM%2520(Raspberry%2520PI)%2520Docker%2520Install" | sudo sh && sudo usermod -aG docker $USER
```

### Unkonwn file formats / "This server is not powerful enough to convert video"

Plex for Raspberry PI cannot read some video file format like AVI, WMV or OGM, either due to codec or due to RPI powerness. You can convert them to make them compatible by usign my docker image `jaymoulin/rpi-plex-video-converter` : https://github.com/jaymoulin/docker-rpi-plex-video-converter

### New versions

Follow [@DockerRpiPlex](https://twitter.com/DockerRpiPlex) on Twitter to be alerted of updates!

