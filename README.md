# Проект API для Yatube (api_yatube)

REST API для социальной сети Yatube. Проект позволяет взаимодействовать с приложением через API: получать списки постов и групп, публиковать новые записи, оставлять комментарии и управлять собственным контентом. 

Реализована аутентификация по токену (TokenAuthentication). Чтение данных доступно всем пользователям, а создание, изменение и удаление контента — только авторизованным авторам.

## Технологии
* Python 3.9
* Django 3.2
* Django REST Framework (DRF)
* SQLite3

## Как запустить проект:

1. Клонировать репозиторий и перейти в него в командной строке:
```
git clone [https://github.com/Ваш-Логин/api_yatube.git](https://github.com/Ваш-Логин/api_yatube.git)
```
```
cd api_yatube
```
Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```
```
source venv/bin/activate
```
Установить зависимости из файла requirements.txt:

```
python -m pip install --upgrade pip
```
```
pip install -r requirements.txt
```

Выполнить миграции:

```
cd yatube_api
```
```
python manage.py migrate
```

Запустить локальный сервер:

```
python manage.py runserver
```
Примеры запросов к API
Получение токена (POST):
http://127.0.0.1:8000/api/v1/api-token-auth/

```JSON
{
    "username": "test_user",
    "password": "test_password"
}
```
Получение списка всех постов (GET):
http://127.0.0.1:8000/api/v1/posts/

Создание нового поста (POST, требуется токен):
http://127.0.0.1:8000/api/v1/posts/
В заголовке запроса необходимо передать: Authorization: Token <ваш_токен>

```JSON
{
    "text": "Мой первый пост через API!",
    "group": 1
}
```
Получение списка групп (GET):
http://127.0.0.1:8000/api/v1/groups/

Добавление комментария к посту (POST, требуется токен):
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/

```JSON
{
    "text": "Отличный пост!"
}
```