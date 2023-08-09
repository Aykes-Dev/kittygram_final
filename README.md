[![Kittygramm workflow](https://github.com/Aykes-Dev/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/Aykes-Dev/kittygram_final/actions/workflows/main.yml)
#  Kittygram - социальная сеть
Kittygram - социальная сеть, специально созданная для любителей кошек. Здесь вы сможете делиться фотографиями своих питомцев. Это идеальная платформа для всех кошачьих ценителей, которые хотят поделиться своими кошачьими моментами и находить новых друзей со схожими интересами.


## Технологии
#### 1. Frontend:
- Node.js
- Next.js
- React

\* Полный список библиотек в файле packeje.json

#### 2. Backend:
- Django
- DRF
- Gunicorn
- Pillow

\* Полный список библиотек в файле requirements.txt

#### 3. Сервер:
nginx

#### 4. Деплой
- Docker
- Docker compose

## Развертывание
1. Скачиваем файл docker-compose.yml из репозитория https://github.com/Aykes-Dev/kittygram_final/blob/main/

2. Создает файл .env
```
touch .env
```
3. Записываем в файл переменные окружения
```
POSTGRES_DB=<имя БД>
POSTGRES_USER=<имя пользователя>
POSTGRES_PASSWORD=<пароль>
DB_NAME=<имя БД>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<секретный ключ Django>
DEBUG=<режим DEBUG True/False>
ALLOWED_HOSTS=<разрешенные хосты>
TEST_BASE=<Использование SQLite - True, Postgres - False>
```

4. Запускаем Docker compose
```
sudo docker compose -f docker-compose.yml pull
sudo docker compose -f docker-compose.yml down
sudo docker compose -f docker-compose.yml up -d
```
5. Собираеми уопируем статику, делаем миграции
```
sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/ 
```

## Автодеплой с помощью Git Hub Action 
1. Скачиваем репозиторий
```
git@github.com:Aykes-Dev/kittygram_final.git
```
2. Добавляем перменные в Secrets
```
ALLOWED_HOSTS - разрешенные хосты
DB_HOST - имя БД
DB_NAME - db
DB_PORT - 5432
DEBUG - True/False режим DEBUG Django
DOCKER_PASSWORD - пароль от Docker Hub
DOCKER_USERNAME - имя пользователя Docker Hub
HOST - ip сервера
POSTGRES_DB - имя БД
POSTGRES_PASSWORD - пароль БД
POSTGRES_USER - имя пользователя БД
SECRET_KEY - секретный ключ Django
SSH_KEY - ключ ssh для доступа к удаленному серверу
SSH_PASSPHRASE - пароль ssh
TELEGRAM_TO - id пользователя TELEGRAM
TELEGRAM_TOKEN - TELEGRAM токен
USER - имя пользователя сервера
```

### Автор: [Андрей Савостьянов](https://github.com/Aykes-Dev)