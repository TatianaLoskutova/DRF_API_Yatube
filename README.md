# api_final_yatube

### Разработчик проекта: Лоскутова Татьяна (Loskutova Tatiana)

### Назначение проекта
Данный проект представляет собой API для работы с web приложение API_YATUBE.
Он предоставляет возможность пользователям публиковать посты, подписываться на других пользователей, получать информацию о подписках и подписчиках.
Оставлять комментарии под своими и чужими постами. Редактировать свои публикации и комментарии. 
Просмотр информации доступен всем пользователям, но манипулировать публикациями и комментариями может только их автор.
Создание групп не доступно пользователям, их может создать только admin.

### Технологический стек
- Python - основной язык программирования.
- Django - фреймворк для разработки веб-приложений.
- Django REST framework - инструмент для создания веб-API на основе Django.
- GIT - система контроля версий проекта
- Pytest - инструмент для тестирования проекта
  
### Как запустить проект:

**1)** Клонировать репозиторий и перейти в него в командной строке:

    git clone https://github.com/TatianaLoskutova/api_final_yatube.git

    cd api_finale_yatube

**2)** Создать и активировать виртуальное окружение:
    
    python -m venv venv

    venv/Scripts/activate

**3)** Установить зависимости из файла requirements.txt:
    
    python -m pip install --upgrade pip

    pip install -r requirements.txt

**4)** Выполнить миграции:
    
    cd yatube_api

    python manage.py migrate
    
**5)** Запустить проект:

    python manage.py runserver


   ### Описание API:

**Posts**
Создание новых публикаций с группой и без. Редактирование публикаций, частичное редактирование, удаление публикаций. Пагинация, сериализация.

**Groups**
Создание новых групп только суперюзером

**Comments**
Создание комментариев к посту Редактирование, частичное редактирование, удаление, получение комментария по id. Сериализация.

**Follows**
Получение подписчиков и подписок

**JWT** Аутентификация и авторизация

 ### Примеры:

**GET запрос на публикации на эндпоинт**
http://127.0.0.1:8000/api/v1/posts/
Response: код 200
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}

**POST запрос на комментарий**
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
Payload:
{
  "text": "string"
}
Response: 201
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
