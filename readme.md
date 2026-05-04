# 🛠️ Полезные шпаргалки

> Личная шпаргалка с полезными командами для разработки и администрирования.

## 📑 Содержание
1. [Linux Basics](#linux-basics)
2. [Git Commands](#git-commands)
3. [Docker & Compose](#docker--compose)

---

## Linux Basics
```bash
# Список файлов с правами и скрытыми
ls -la

# Перейти в директорию
cd ..

# Удалить файл (флаг -rf для удаления директорий)
rm ./file.txt

# Скопировать рекурсивно
cp -r /source /destination

# Установка программ
sudo apt install btop

# Мониторинг сервера
btop
```
---

## Git Commands
```bash
# Клонировать репозиторий
git clone ...

# Добавить в локальный git
git add .

# Быстрый коммит всех изменённых файлов
git commit -am "fix: update config"

# Откатить изменения в файле
git restore file.txt

# Отправить ветку и привязать к удалённой
git push origin main

# Подтянуть коммиты
git pull origin main
```
---

## Docker & Compose
```bash
# Все контейнеры (включая остановленные)
docker ps -a

# Собрать контейнер
docker build -t my-tg-bot .

# Запустить контейнер
docker run -d --name tg-bot --restart unless-stopped -e BOT_TOKEN="ВАШ_ТОКЕН_ОТ_BOTFATHER" my-tg-bot

# Зайти внутрь запущенного контейнера
docker exec -it myapp /bin/bash   # или /bin/sh

# Посмотреть логи в реальном времени
docker logs -f tg-bot

# Остановить контейнер
docker stop tg-bot

# Запустить контейнер
docker start tg-bot

# Удалить контейнер
docker rm -f tg-bot

# Удалить образ
docker rmi my-tg-bot

# Скопировать файл из/в контейнер
docker cp myapp:/etc/nginx/nginx.conf ./nginx.conf
docker cp ./config.conf myapp:/etc/nginx/conf.d/


# Билд docker-compose
docker compose up -d --build

# Удаляет старый контейнер
docker compose down

# Удалить все остановленные контейнеры
docker container prune

# Удалить неиспользуемые образы
docker image prune -a
```

```Dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "bot.py"]
```

```docker-compose.yml
services:
  bot:
    build: .
    container_name: tg-bot
    restart: unless-stopped
    env_file: .env
```
