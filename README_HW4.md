
# Задача 1

## Dockerfile
```dockerfile
FROM nginx:1.29.0
COPY index.html /usr/share/nginx/html/index.html

файл index.html содержит следующее:
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I will be DevOps Engineer!</h1>
</body>
</html>

Сборка образа -docker build -t irina/custom-nginx:1.0.0 .
Ретег образа, т.к. имеется разница в никнейме юзера - docker tag irina/custom-nginx:1.0.0 irinakau/custom-nginx:1.0.0
Публикация - docker push irinakau/custom-nginx:1.0.0
Ссылка на DockerHub - https://hub.docker.com/repository/docker/irinakau/custom-nginx/general


# Задача 2

irina@ubuntuVB:~$ date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080 ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html
29-03-2026 13:21:07.208775748 +07
CONTAINER ID   IMAGE                         COMMAND                  CREATED         STATUS         PORTS                    NAMES
fae573bedd14   irinakau/custom-nginx:1.0.0   "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   127.0.0.1:8080->80/tcp   custom-nginx-t2
LISTEN 0      4096       127.0.0.1:8080       0.0.0.0:*          
2026/03/29 06:19:00 [notice] 1#1: start worker process 29
PGh0bWw+CjxoZWFkPgpIZXksIE5ldG9sb2d5CjwvaGVhZD4KPGJvZHk+CjxoMT5JIHdpbGwgYmUg
RGV2T3BzIEVuZ2luZWVyITwvaDE+CjwvYm9keT4KPC9odG1sPgo=

вывод запроса показывает: 
статус Up 2 minutes - контейнер работает
порт 8080 прослушивается
index.html реально внутри контейнера - я получила base64-код страницы
nginx запустился

проверка, что страница реально доступна извне:
irina@ubuntuVB:~$ curl http://127.0.0.1:8080
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I will be DevOps Engineer!</h1>
</body>
</html>




