# Docker certificates

Если docker pull требует сертификат, необходимо сделать следующее:

1. подключится через docker-machine - 
```
docker-machine ssh machinename
```

2. Создать директорию в /etc/docker/certs.d/url.requires.cert.com/
3. Положить сертификат в директорию которую создали выше.

