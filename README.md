��#   h a b i t 
     Курсовая работа 7 - DRF
Для работы с проектом необходимо выполнить следующие действия:
Клонировать репозиторий. Активировать виртуальное окружение venv/Scripts/activate Установить зависимости pip install -r requirements.txt Создать файл .env, заполнить его данными из файла env.sample Создать базу данных в PostreSQL  Создать python manage.py makemigrations и применить миграции python manage.py migrate Создать пользователя командой python manage.py csu Создать пользователя командой python manage.py user_create Установить и запустить Redis локально (на Windows) В терминале набрать команду celery -A config worker --loglevel info -P eventlet В терминале набрать команду celery -A config beat -l info -S django Запустить проект python manage.py runserver Откройте браузер и перейдите по адресу http://127.0.0.1:8000 для доступа к приложению.

Решены следующие задачи:
Настроено CORS Настроена интеграция с Telegram Реализована пагинация Использованы переменные окружения Все необходимые модели описаны или переопределены Все необходимые эндпоинты реализовали Настроены все необходимые валидаторы Описанные права доступа заложены Настроена отложенная задача через Celery Проект покрыт тестами как минимум на 80%  Имеется список зависимостей Решение выложено на GitHub

Описание задач
Добавлены необходимые модели привычек Реализованы эндпоинты для работы с фронтендом Создано приложение для работы с Telegram и рассылками напоминаний.

      ИТОГОВОЕ ЗАДАНИЕ.
Все сервисы проекта выделены в отдельные контейнеры: Django, PostgreSQL, Redis, Celery, nginx .
Для управления контейнерами используется docker-compose.
Созданы необходимые Dockerfile для сервисов проекта.
 CI/CD
Настроен процесс CI/CD с использованием GitHub Actions.
Включены этапы тестирования, линтинга, проверки Docker-сборки.
 Деплой на сервер
Проект автоматически развертывается на удаленном сервере через Docker Compose.
Настроено управление контейнерами для обновления сервиса при деплое.
Конфигурация деплоя описана в workflow GitHub Actions.
Создайны отдельные контейнеры:
для Django,
PostgreSQL, Redis, Celery, Nginx.
Настроен запуск всех сервисов проекта через Docker Compose.
Добавлена в репозиторий GitHub конфигурацию GitHub Actions, которая будет:
запускать тесты и линтинг кода, проверять возможность сборки Docker-образов,
при успешных проверках автоматически деплоить проект на сервер.
Настроен удаленный сервер:
Убедитесь, что сервер готов к работе с Docker и Docker Compose.
Настроен SSH-доступ к серверу для деплоя через GitHub Actions.
    Запуск проекта локально
    Предварительные требования

1. Установите [Docker](https://docs.docker.com/get-docker/) и [Docker Compose](https://docs.docker.com/compose/install/).
2. Склонируйте репозиторий:
   git clone https://github.com/VasiliiKuptsov/habit.git
   cd habit
Настройка окружения
Создайте файл .env в корне проекта и заполните необходимые переменные окружения.
Запуск контейнеров
Запустите проект с помощью Docker Compose:
docker-compose up -d --build
После сборки контейнеров выполните миграции:
docker-compose exec web python manage.py migrate
Доступ к приложению
Django-приложение будет доступно по адресу: http://localhost:8000
Админка: http://localhost:8000/admin
Развертывание на сервере
Настройка сервера
Установите на сервер:
Docker, Docker Compose.
Настройте SSH-доступ для GitHub Actions:
Добавьте публичный ключ в ~/.ssh/authorized_keys
Добавьте приватный ключ в Secrets GitHub как SSH_PRIVATE_KEY
Настройка CI/CD
В репозитории GitHub перейдите в Settings > Secrets и добавьте:
SSH_PRIVATE_KEY — приватный SSH-ключ для доступа к серверу
SERVER_IP — IP-адрес сервера
SSH_USERNAME — имя пользователя для SSH (обычно root)
Другие необходимые переменные окружения (как в .env)

При пуше в ветку main/master или создании PR GitHub Actions автоматически:
Запустит тесты и линтинг
Соберет Docker-образы
При успешных проверках — задеплоит на сервер

Деплой вручную
Склонируйте репозиторий на сервер:
git clone https://github.com/VasiliiKuptsov/habit.git
cd habit
Создайте .env файл и заполните переменные
Запустите:
docker-compose -f docker-compose.prod.yml up -d --build
docker-compose -f docker-compose.prod.yml exec web python manage.py migrate
Производственный адрес
Приложение доступно по адресу: http://130.193.58.114
docker-compose down
Просмотр логов:
docker-compose logs -f
Запуск тестов:
docker-compose exec web python manage.py test



      
 
 
