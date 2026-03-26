
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
