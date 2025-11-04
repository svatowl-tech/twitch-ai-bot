# 🚀 Руководство по развертыванию Twitch AI Bot

Этот документ содержит подробные инструкции по развертыванию Twitch AI Bot в различных средах.

## 📋 Содержание

1. [Требования](#требования)
2. [Локальное развертывание](#локальное-развертывание)
3. [Docker развертывание](#docker-развертывание)
4. [Production развертывание](#production-развертывание)
5. [AWS развертывание](#aws-развертывание)
6. [Настройка API](#настройка-api)
7. [Мониторинг](#мониторинг)
8. [Безопасность](#безопасность)
9. [Troubleshooting](#troubleshooting)

## 📋 Требования

### Минимальные требования:
- Node.js 18.0+
- PostgreSQL 15+
- Redis 7+
- 2GB RAM
- 10GB дискового пространства

### Рекомендуемые требования:
- Node.js 18.17+
- PostgreSQL 15+
- Redis 7+
- 4GB RAM
- 20GB SSD дискового пространства
- Docker 20.10+

## 🏠 Локальное развертывание

### 1. Клонирование репозитория
```bash
git clone https://github.com/svatowl-tech/twitch-ai-bot.git
cd twitch-ai-bot
```

### 2. Установка зависимостей
```bash
# Backend зависимости
npm install

# Frontend зависимости
cd frontend && npm install && cd ..
```

### 3. Настройка переменных окружения
```bash
cp .env.example .env
```

Отредактируйте файл `.env` и добавьте ваши API ключи:
- Twitch Bot credentials
- Polza.ai API ключ
- Google Sheets Service Account
- База данных credentials

### 4. Настройка базы данных
```bash
# Создание базы данных
createdb twitch_bot

# Запуск миграций
npm run db:migrate

# Заполнение тестовыми данными (опционально)
npm run db:seed
```

### 5. Запуск в режиме разработки
```bash
# Запуск backend и frontend одновременно
npm run dev
```

Или отдельно:
```bash
# Backend
npm run dev:backend

# Frontend (в отдельном терминале)
npm run dev:frontend
```

Приложение будет доступно:
- Frontend: http://localhost:3000
- Backend API: http://localhost:3000/api
- WebSocket: ws://localhost:3001

## 🐳 Docker развертывание

### Development среда
```bash
# Запуск всех сервисов
docker-compose up -d

# Просмотр логов
docker-compose logs -f

# Остановка
docker-compose down
```

### Production среда
```bash
# Сборка production образов
docker-compose -f docker-compose.prod.yml build

# Запуск production сервисов
docker-compose -f docker-compose.prod.yml up -d

# Мониторинг логов
docker-compose -f docker-compose.prod.yml logs -f
```

### Сервисы в Docker:
- **twitch-bot**: Основное приложение
- **postgres**: База данных PostgreSQL
- **redis**: Кэш и сессии
- **nginx**: Reverse proxy
- **prometheus**: Сбор метрик
- **grafana**: Визуализация метрик

### Доступ к сервисам:
- Frontend: http://localhost
- Backend API: http://localhost/api
- Adminer (DB UI): http://localhost:8080
- Grafana: http://localhost:3001 (admin/admin)
- Prometheus: http://localhost:9090

## 🚀 Production развертывание

### 1. Подготовка сервера
```bash
# Обновление системы
sudo apt update && sudo apt upgrade -y

# Установка Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Установка PM2
sudo npm install -g pm2

# Установка PostgreSQL
sudo apt install postgresql postgresql-contrib -y

# Установка Redis
sudo apt install redis-server -y

# Установка Nginx
sudo apt install nginx -y

# Установка Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
```

### 2. Настройка базы данных
```bash
# Подключение к PostgreSQL
sudo -u postgres psql

# Создание пользователя и базы данных
CREATE USER twitch_bot WITH PASSWORD 'secure_password';
CREATE DATABASE twitch_bot OWNER twitch_bot;
GRANT ALL PRIVILEGES ON DATABASE twitch_bot TO twitch_bot;
\q
```

## 🔧 Настройка API

### Twitch Bot API

1. Перейдите в [Twitch Developer Console](https://dev.twitch.tv/console)
2. Создайте новое приложение
3. Заполните поля:
   - Name: Twitch AI Bot
   - OAuth Redirect URLs: http://localhost:3000/auth/callback
   - Category: Chat Bot
4. Сохраните Client ID и Client Secret

### Polza.ai API

1. Зарегистрируйтесь на [polza.ai](https://polza.ai)
2. Перейдите в личный кабинет
3. Создайте новый API ключ
4. Скопируйте ключ в `.env` файл

### Google Sheets API

1. Создайте проект в [Google Cloud Console](https://console.cloud.google.com/)
2. Включите Google Sheets API
3. Создайте Service Account
4. Скачайте JSON ключ
5. Поделитесь Google Sheets документом с сервисным аккаунтом

## 📞 Контакты

- **GitHub**: https://github.com/svatowl-tech/twitch-ai-bot
- **Issues**: https://github.com/svatowl-tech/twitch-ai-bot/issues
- **Documentation**: https://github.com/svatowl-tech/twitch-ai-bot/wiki