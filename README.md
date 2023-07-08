# Curse_work_6_-SkyStore-
## Проект SkyDiv
___
### Для работы с данным сервисом нужно провести следующие операции:

1) Клонирование репозитория
2) Установка зависимостей
3) Установка и настройка Redis
4) Установка и настройка PostgreSQL
5) Настройка окружения
6) Запуск миграций и закгрузка данных
7) Запуск celery и celery-beat
8) Запуск сервера Django
___
### 1) Клонирование репозитория

Для клонирования репозитория нужно запустить консоль git и вней пропилать команду:
```
git clone https://github.com/IngAivar/Curse_work_6_-SkyStore-
```
Тут подробная информация по этому вопросу: https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository
___
### 2) Установка зависимостей

Когда вы уже будите в виртуальном окружении команда:
```
pip install -r requirements.txt
```

Можно это сделать через консоль, подробно об этом тут: https://docs.python.org/3/tutorial/venv.html

Если вы работаете в IDE и уже зашли в проект просто инсталируйте все библиотеки из файла: <requirements.txt>
___
### 3) Установка и настройка Redis

По поводу установки на windows можно прочитать здесь: https://redis.io/docs/getting-started/installation/install-redis-on-windows/
___
### 4) Установка и настройка PostgreSQL

Подробно про установку на windows: https://winitpro.ru/index.php/2019/10/25/ustanovka-nastrojka-postgresql-v-windows/

Также нужно будет создать базу данных: <newsletter> для коректной работы программы

Для этого можно воспользоватся pgAdmin или создать через консоль

Для создания через консоль нужно зайти в вертулаьное окружение проекта и прописать данную строку
```
CREATE DATABASE newsletter;
```
___
### 5) Настройка окружения

Также вам нужно будет настроиль файл .env под себя
```
DB_NAME=название_бд (newsletter)
DB_USER=имя_пользователя_бд (postgres)
DB_PASSWORD=пароь_пользователя_бд
DB_HOST=localhost
DB_PORT=5432

EMAIL_HOST_USER=адрес_электронной_почты_для_аутенфикации_на_почтовом_сервере
EMAIL_HOST_PASSWORD=пароль_для_для_аутенфикации_на_почтовом_сервере
```
___
### 6) Запуск миграций и закгрузка данных

Для начала воспльзуемся комманодой <migrate>
```
python manage.py migrate
```
А после успешно прошедшей миграции нужно загрузить данные в базу прописав эти команды по очериди
```
python manage.py loaddata user_data.json
python manage.py loaddata post_data.json
python manage.py loaddata client_data.json
python manage.py loaddata message_data.json
python manage.py loaddata newsletter_data.json
```
___
### 7) Запуск celery и celery-beat

В виртуальном окружении прописываем команду:
```
celery -A config worker --loglevel=info
```
Поле того как запустили <celery>, нужно открыть новый терминал и в нём прописать эту команду:
```
celery -A config beat --loglevel=info
```
Тем самым запуская <celery-beat>
___
### 8) Запуск сервера Django

Отлично! Осталось только запустить проект
```
python manage.py runserver
```
