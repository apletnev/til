# Docker authorization

Если при docker pull необходима авторизация необходимо на локальной машине добавить в ~/.docker/config.json **auths** секцию:

```
{
    "auths": {
                “hostname.com": {
                 "auth”:”YW11cmRhY2E6c3VwZXJzZWNyZXRwYXNzd29yZA==”,
                "email": “test@test.com"
             }
    }
}
```

```
$ echo YW11cmRhY2E6c3VwZXJzZWNyZXRwYXNzd29yZA== | base64 -D -
amurdaca:supersecretpassword
```

Как альтернатива рекомендуют воспользоваться [docker-credential-helpers](https://github.com/docker/docker-credential-helpers)