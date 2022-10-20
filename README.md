# API for checking comments
Задание: Реализовать REST API для системы комментариев блога.


### Документация API (автодокументирование на swagger (drf-yasg) доступно по адресу http://127.0.0.1:8000/swagger/ )

## Описание ТЗ:

### Функциональные требования:
У системы должны быть методы API, которые обеспечивают
- Добавление статьи (Можно чисто номинально, как сущность, к которой крепятся комментарии).
- Добавление комментария к статье.
- Добавление коментария в ответ на другой комментарий (возможна любая вложенность).
- Получение всех комментариев к статье вплоть до 3 уровня вложенности.
- Получение всех вложенных комментариев для комментария 3 уровня.
- По ответу API комментариев можно воссоздать древовидную структуру.

### Нефункциональные требования:
- Использование Django ORM.
- Следование принципам REST.
- Число запросов к базе данных не должно напрямую зависеть от количества комментариев, уровня вложенности.
- Решение в виде репозитория на Github, Gitlab или Bitbucket.
- readme, в котором указано, как собирать и запускать проект. Зависимости указать в requirements.txt либо использовать poetry/pipenv.
- Использование свежих версий python и Django.

## Окружение проекта:
  * python 3.8
  * Django 4.0.3
  * djangorestframework

Склонируйте репозиторий с помощью git

    https://github.com/Strijyury/comments_api.git
Перейти в папку:
```bash
cd comments_api
```
Создать и активировать виртуальное окружение Python.

Установить зависимости из файла **requirements.txt**:
```bash
pip install -r requirements.txt
```

# Выполнить следующие команды:

* Команда для создания миграций приложения для базы данных
```bash
python manage.py makemigrations
python manage.py migrate
```
* Создание суперпользователя
```bash
python manage.py createsuperuser
```
Будут выведены следующие выходные данные. Введите требуемое имя пользователя, электронную почту и пароль:

```bash
Username (leave blank to use 'admin'): admin
Email address: admin@admin.com
Password: ********
Password (again): ********
Superuser created successfully.
```
* Команда для запуска приложения
```bash
python manage.py runserver
```
* Приложение будет доступно по адресу: http://127.0.0.1:8000/


### Просмотр существующих статей или создание новой:
* Request method: GET, POST
* URL: http://127.0.0.1:8000/api/articles/
* Body:
    * article_name: Название статьи
    * pub_date: Дата и время публикации статьи, format: YYYY-MM-DD HH:MM:SS
    * article_description: Содержание статьи


### Просмотр существующих комментариев с ответами (если есть) или создание нового:
* Request method: GET, POST
* URL: http://127.0.0.1:8000/api/comments/
* Body:
    * article: id статьи
    * comment_text: Текст комментария
    * pub_date: Дата и время публикации комментария, format: YYYY-MM-DD HH:MM:SS
    * reply: Ответ на комментарий
