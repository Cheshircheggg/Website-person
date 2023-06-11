![main](https://github.com/Cheshircheggg/kittygram_final/actions)

<h1 align="center">Kittygram</h1>

<h1 align="center">https://kittygramru.ddns.net/</h1>

# Описание проекта

Данный учебный проект является финальным результатом изучения Docker и технологий Cl и CD.

### Main features

* Separated dev and production settings

* Example app with custom user model

* Bootstrap static files included

* User registration and logging in as demo

* Procfile for easy deployments

* Separated requirements files

* Postgres 13.10



### Как запустить проект:

Установить программу контейнеризации Docker (версия 4.19.0), так же необходимо зарегистрироваться на DockerHub.

Клонировать репозиторий:
```
git clone https://github.com/
https://github.com/Cheshircheggg/kittygram_final/
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
## Автор 

Трубачева Екатерина (Cheshircheggg) 

## Обратная связь 

Электронная почта - mikuo.jovi@yandex.ru 