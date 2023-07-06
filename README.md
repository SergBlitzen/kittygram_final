# Kittygram
### Социальная сеть для размещения котиков

Kittygram — простой сервис для того, чтобы кто угодно мог поделиться своими котиками. Всё, что нужно пользователю для этого — создать учётную запись из логина и пароля без дополнительных данных.

### Возможности сервиса

В проекте реализованы две основные модели: Cat и Achievement, где основной является Cat. Каждая запись модели Cat сопровождается именем и возрастом питомца, также опционально фотографией, цветом и достижениями.

### Стэк технологий
<br>— Python;
<br>— Django REST;
<br>— React;
<br>— nginx;
<br>— Docker.

### Установка и деплой приложения

Для работы приложения требуются данные из внешнего окружения.

<br>База данных:
<br><b>POSTGRES_USER</b>=user
<br><b>POSTGRES_PASSWORD</b>=password
<br><b>POSTGRES_DB</b>=django
<br><b>DB_HOST</b>=host
<br><b>DB_PORT</b>=1234

<br>Бэкенд:
<br><b>SECRET_KEY</b>=django_key
<br><b>DEBUG</b>=bool False

CI/CD приложения автоматизирован и работает при помощи GitHub Actions через воркфлоу "main.yml".

При необходимости развернуть проект вручную требуется разместить файл "docker-compose.production.yml" в нужной директории и выполнить следующие команды:
<br>— загрузить образы контейнеров из Docker Hub;
<br>```sudo docker compose -f docker-compose.production.yml pull```
<br>— остановить контейнеры;
<br>```sudo docker compose -f docker-compose.production.yml down```
<br>— запустить контейнеры в фоновом режиме;
<br>```sudo docker compose -f docker-compose.production.yml up -d```
<br>— выполнить миграции в контейнере бэкенда;
<br>```sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate```
<br>— собрать статику;
<br>```sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic```
<br>— скопировать статику.
<br>```sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/```

### Об авторе
Backend and assembly by Serg Blitzen
Assets by Yandex.Practicum
