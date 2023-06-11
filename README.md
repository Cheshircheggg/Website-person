![main](https://github.com/Cheshircheggg/kittygram_final/actions/workflows/main.yml/badge.svg)

<h1 align="center">Kittygram</h1>

<h1 align="center">https://kittygramru.ddns.net/</h1>

## Технологии

 - Python 3.9
 - Django==3.2.3
 - Docker
 - Nginx
 - gunicorn
 - PostgreSQL
 - GitHub Actions

# Описание проекта

Данный учебный проект является финальным результатом изучения Docker и технологий Cl и CD.

### Как запустить проект:

Установить программу контейнеризации Docker (версия 4.19.0), так же необходимо зарегистрироваться на DockerHub.

Клонировать репозиторий:
```
git clone https://github.com/
https://github.com/Cheshircheggg/kittygram_final/
```
Подключиться к удалённому серверу:
```
ssh -i путь_до_файла_с_SSH_ключом/название_файла_с_SSH_ключом имя_пользователя@ip_адрес_сервера 
```
Установить Docker на сервер:
```
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin
```
Скопировать на сервер файл docker-compose.production.yml:
```
 scp -i path_to_SSH/SSH_name docker-compose.production.yml username@server_ip:/home/username/taski/docker-compose.production.yml
 _или сделать это вручную_
```
Создать файл .env:
```
sudo touch .env
```
В файле .env прописать следующие: 
```
SECRET_KEY
POSTGRES_USER
POSTGRES_PASSWORD
POSTGRES_DB
DB_HOST=db
DB_PORT=5432
```
В терминале выполнить команду:

```
docker compose -f docker-compose.production.yml up
```

После последовательно в терминале выполнить команды для миграций и сбора статики:

```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate

sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic

sudo docker compose -f docker-compose.production.yml exec backend cp -r collected_static/. ../backend_static/static/
```
Откоректировать конфиг nginx на сервере:
```
sudo nano /etc/nginx/sites-enabled/default
```
Должно быть так:
```
 location / {
        proxy_set_header Host $http_host;
        proxy_pass http://127.0.0.1:8080;
    }
```
Поздравляю! теперь у вас есть сайт, где вы можете делиться с миром фотографиями своих котов.

## Автор 

Трубачева Екатерина (Cheshircheggg) 

## Обратная связь 

Электронная почта - mikuo.jovi@yandex.ru 
