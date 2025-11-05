# 🤖 Twitch AI Bot - Полнофункциональный ИИ бот для Twitch

![Twitch Bot](https://img.shields.io/badge/Twitch-Bot-9146FF?style=for-the-badge&logo=twitch&logoColor=white)
![AI Powered](https://img.shields.io/badge/AI-Powered-FF6B35?style=for-the-badge&logo=openai&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

> **Современный ИИ бот для Twitch** с системами гадания, броска кубиков, рекомендаций игр, заказов и профессиональным веб-интерфейсом управления.

## 🚀 Быстрый старт

[![Deploy to Railway](https://railway.app/button.svg)](https://railway.app/template/github/svatowl-tech/twitch-ai-bot)
[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)
[![Run in Docker](https://img.shields.io/badge/Docker-Run-blue?logo=docker&logoColor=white)](./DOCKER_README.md)

```bash
# Быстрый запуск через Docker
git clone https://github.com/svatowl-tech/twitch-ai-bot.git
cd twitch-ai-bot
cp .env.example .env
docker-compose up -d

# Откройте http://localhost:3000 для веб-интерфейса
```

## 🎯 Основные возможности

### 🎲 Игровые функции
- **Бросок кубиков** - D&D, Pathfinder, любые комбинации с критическими результатами
- **Рекомендации игр** - персонализированные рекомендации с интеграцией Steam/Epic Games
- **Гадание и предсказания** - карты Таро, гороскопы, нумерология через ИИ

### 🧠 ИИ возможности
- **Ответы на вопросы** - интеграция с Polza.ai для умных ответов
- **Персонализация** - адаптация под стиль каждого пользователя
- **Модерация контента** - автоматическая фильтрация нежелательных сообщений

### 🛒 Система заказов
- **Заказ игр** - автоматическое создание и отслеживание заказов
- **Google Sheets интеграция** - выгрузка всех заказов в таблицы
- **Уведомления** - автоматические сообщения в чат о статусе

### 💻 Веб-интерфейс
- **Дашборд управления** - полный мониторинг и контроль
- **Real-time обновления** - WebSocket соединение
- **Управление пользователями** - роли, права доступа, безопасность
- **Аналитика и метрики** - детальная статистика использования

### 🎮 Расширенные возможности
- **Discord интеграция** - синхронизация с Discord серверами
- **Голосовые команды** - распознавание и обработка голоса
- **Музыкальный плеер** - интеграция с Spotify, YouTube Music, SoundCloud
- **Мини-игры** - казино, угадывание, командные игры
- **Twitch Extensions** - официальные расширения для стримов
- **Мобильное приложение** - управление ботом со смартфона

## 📋 Команды бота

### Игровые команды
| Команда | Описание | Пример |
|---------|----------|---------|
| `!roll [dice]` | Бросок кубиков | `!roll 1d20+5` |
| `!dice [count]d[sides]` | Несколько кубиков | `!dice 3d6` |
| `!adv [dice]` | Бросок с преимуществом | `!adv 1d20` |
| `!crit` | Критический успех | `!crit` |

### Игровые рекомендации
| Команда | Описание | Пример |
|---------|----------|---------|
| `!игра [жанр]` | Поиск игр | `!игра rpg` |
| `!порекомендуй [жанр]` | Персонализированные рекомендации | `!порекомендуй action` |
| `!оцени [игра] [оценка]` | Оценка игры | `!оцени Elden Ring 10` |
| `!отзыв [игра] [текст]` | Оставить отзыв | `!отзыв Cyberpunk 2077 Отличная игра` |

### Гадания
| Команда | Описание | Пример |
|---------|----------|---------|
| `!карта [вопрос]` | Карты Таро | `!карта Когда я найду любовь?` |
| `!предсказание [тема]` | Предсказание | `!предсказание карьера` |
| `!гороскоп [знак]` | Гороскоп | `!гороскоп лев` |

### Система заказов
| Команда | Описание | Пример |
|---------|----------|---------|
| `!заказать [игра]` | Создать заказ | `!заказать Baldur's Gate 3` |
| `!статус [номер]` | Проверить статус | `!статус 12345` |
| `!отменить [номер]` | Отменить заказ | `!отменить 12345` |

### Музыкальные команды
| Команда | Описание | Пример |
|---------|----------|---------|
| `!play [песня]` | Воспроизвести музыку | `!play Never Gonna Give You Up` |
| `!pause` | Пауза | `!pause` |
| `!resume` | Продолжить | `!resume` |
| `!queue` | Очередь | `!queue` |
| `!skip` | Пропустить | `!skip` |

### Discord интеграция
| Команда | Описание | Пример |
|---------|----------|---------|
| `!discord connect` | Подключить Discord | `!discord connect` |
| `!sync` | Синхронизировать команды | `!sync` |
| `!voice [команда]` | Голосовые команды | `!voice join` |

### Общие команды
| Команда | Описание | Пример |
|---------|----------|---------|
| `!ai [вопрос]` | Спросить ИИ | `!ai Что такое квантовая физика?` |
| `!help` | Список всех команд | `!help` |
| `!ping` | Проверка работы бота | `!ping` |
| `!stats` | Статистика бота | `!stats` |

## 🏗️ Архитектура системы

```mermaid
graph TB
    subgraph "Frontend Layer"
        WEB[Веб-интерфейс<br/>React + TypeScript]
        MOB[Мобильное приложение<br/>React Native]
        EXT[Twitch Extensions<br/>HTML + JavaScript]
    end
    
    subgraph "API Layer"
        GW[API Gateway<br/>Express + JWT]
        WS[WebSocket Server<br/>Real-time updates]
        AUTH[Auth Service<br/>JWT + OAuth]
    end
    
    subgraph "Bot Core"
        BOT[Twitch Bot<br/>TwitchIO]
        DISCORD[Discord Bot<br/>Discord.js]
        VOICE[Voice Commands<br/>Web Speech API]
    end
    
    subgraph "AI Layer"
        AI[Polza.ai Integration]
        SAFETY[Safety Filter]
        PERSONAL[Personalization Engine]
    end
    
    subgraph "Game Systems"
        DICE[Dice System]
        GAMES[Game Recommendations]
        DIVINATION[Divination System]
        CASINO[Casino Games]
    end
    
    subgraph "Services"
        ORDERS[Orders System]
        MUSIC[Music Player]
        NOTIFY[Notification System]
        ANALYTICS[Analytics Engine]
    end
    
    subgraph "Data Layer"
        DB[(PostgreSQL)]
        REDIS[(Redis Cache)]
        SHEETS[Google Sheets]
        FILES[File Storage]
    end
    
    WEB --> GW
    MOB --> GW
    EXT --> GW
    GW --> WS
    GW --> AUTH
    GW --> BOT
    GW --> DISCORD
    GW --> VOICE
    BOT --> AI
    BOT --> DICE
    BOT --> GAMES
    BOT --> DIVINATION
    BOT --> CASINO
    DISCORD --> MUSIC
    BOT --> ORDERS
    BOT --> NOTIFY
    BOT --> ANALYTICS
    AI --> SAFETY
    AI --> PERSONAL
    GW --> DB
    GW --> REDIS
    ORDERS --> SHEETS
    ANALYTICS --> FILES
```

## 🔧 Настройка окружения

### Переменные окружения

Скопируйте `.env.example` и настройте следующие переменные:

```env
# === BOT CONFIGURATION ===
BOT_NAME=YourBotName
TWITCH_CLIENT_ID=your_twitch_client_id
TWITCH_CLIENT_SECRET=your_twitch_client_secret
TWITCH_OAUTH_TOKEN=your_oauth_token
TWITCH_CHANNEL=your_channel_name

# === AI CONFIGURATION ===
POLZA_API_KEY=your_polza_api_key
POLZA_BASE_URL=https://api.polza.ai/v1

# === DATABASE CONFIGURATION ===
DATABASE_URL=postgresql://user:password@localhost:5432/twitch_bot
REDIS_URL=redis://localhost:6379

# === API KEYS ===
GOOGLE_SHEETS_API_KEY=your_google_sheets_key
GOOGLE_SERVICE_ACCOUNT_EMAIL=your_service_account@project.iam.gserviceaccount.com
GOOGLE_SERVICE_ACCOUNT_KEY=your_private_key

# === WEB INTERFACE ===
JWT_SECRET=your_jwt_secret_key
WEB_PORT=3000
ADMIN_USERNAME=admin
ADMIN_PASSWORD=your_secure_password

# === INTEGRATIONS ===
DISCORD_BOT_TOKEN=your_discord_bot_token
SPOTIFY_CLIENT_ID=your_spotify_client_id
SPOTIFY_CLIENT_SECRET=your_spotify_client_secret

# === EXTERNAL APIs ===
STEAM_API_KEY=your_steam_api_key
EPIC_GAMES_API_KEY=your_epic_games_key

# === SECURITY ===
ENCRYPTION_KEY=your_encryption_key
RATE_LIMIT_WINDOW=15
RATE_LIMIT_MAX_REQUESTS=100

# === LOGGING ===
LOG_LEVEL=info
LOG_FILE=logs/bot.log
```

### Настройка API сервисов

#### Twitch API
1. Перейдите в [Twitch Developer Console](https://dev.twitch.tv/console)
2. Создайте новое приложение
3. Настройте OAuth redirect URI: `http://localhost:3000/auth/twitch/callback`
4. Скопируйте Client ID и Client Secret

#### Polza.ai API
1. Зарегистрируйтесь на [polza.ai](https://polza.ai)
2. Пополните баланс
3. Получите API ключ в разделе "API Keys"

#### Google Sheets API
1. Создайте проект в [Google Cloud Console](https://console.cloud.google.com/)
2. Включите Google Sheets API
3. Создайте Service Account и скачайте JSON ключ
4. Поделитесь таблицей с email сервисного аккаунта

#### Discord Bot
1. Перейдите в [Discord Developer Portal](https://discord.com/developers/applications)
2. Создайте новое приложение
3. В разделе Bot настройте права и скопируйте токен

## 🐳 Развертывание

### Docker (Рекомендуется)

```bash
# Клонирование репозитория
git clone https://github.com/svatowl-tech/twitch-ai-bot.git
cd twitch-ai-bot

# Настройка окружения
cp .env.example .env
# Отредактируйте .env файл

# Запуск в development режиме
docker-compose -f docker-compose.dev.yml up -d

# Запуск в production режиме
docker-compose -f docker-compose.prod.yml up -d

# Просмотр логов
docker-compose logs -f

# Остановка
docker-compose down
```

### Railway развертывание

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/github/svatowl-tech/twitch-ai-bot)

1. Нажмите кнопку "Deploy on Railway" выше
2. Подключите GitHub аккаунт
3. Выберите репозиторий
4. Настройте переменные окружения
5. Дождитесь завершения развертывания

### Heroku развертывание

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

1. Нажмите кнопку "Deploy to Heroku" выше
2. Введите имя приложения
3. Выберите регион
4. Настройте переменные окружения в настройках приложения
5. Разверните приложение

### AWS развертывание

Подробные инструкции в [`AWS_DEPLOYMENT.md`](./AWS_DEPLOYMENT.md)

### Локальное развертывание

```bash
# Установка зависимостей
npm install
cd frontend && npm install
cd ..

# Настройка базы данных
npm run db:migrate
npm run db:seed

# Компиляция TypeScript
npm run build

# Запуск в development режиме
npm run dev

# Запуск в production режиме
npm run start
```

## 📊 Мониторинг и веб-интерфейс

Веб-интерфейс доступен по адресу: `http://localhost:3000`

### Основные разделы:

| Раздел | Описание | Функции |
|--------|----------|---------|
| **Dashboard** | Главная панель управления | Общий статус, метрики, быстрые действия |
| **Bot Management** | Управление ботом | Запуск/остановка, настройки, команды |
| **Orders** | Система заказов | Управление заказами, статистика, отчеты |
| **Users** | Управление пользователями | Роли, права доступа, блокировки |
| **Analytics** | Аналитика и отчеты | Детальная статистика, графики, экспорт |
| **Games** | Игровые системы | Настройка игр, результаты, лидерборд |
| **Music** | Музыкальный плеер | Управление очередью, плейлисты |
| **Security** | Безопасность | Логи, аудит, настройки безопасности |
| **Monitoring** | Системный мониторинг | Производительность, алерты, метрики |
| **Settings** | Настройки | Конфигурация, интеграции, экспорт |

### Мониторинг в реальном времени:

- **WebSocket соединения** - мгновенные обновления
- **Push уведомления** - важные события
- **Дашборд метрик** - производительность и использование
- **Логи в реальном времени** - отладка и мониторинг

## 🔐 Безопасность

### Аутентификация и авторизация
- **JWT токены** с refresh механизмом
- **RBAC система ролей**: Owner → Admin → Streamer → Moderator → Viewer
- **OAuth интеграция** с Twitch и Discord
- **Двухфакторная аутентификация** для администраторов

### Защита данных
- **Шифрование** чувствительных данных
- **Rate limiting** для API endpoints
- **Input валидация** и sanitization
- **SQL injection защита** через parameterized queries
- **XSS защита** через Content Security Policy

### Безопасность развертывания
- **Docker security** - непривилегированные контейнеры
- **HTTPS обязательно** в production
- **Переменные окружения** для секретных ключей
- **Регулярные обновления** зависимостей
- **Security headers** для веб-интерфейса

### Политика безопасности
Смотрите [SECURITY.md](./SECURITY.md) для подробной информации о политике безопасности и сообщении об уязвимостях.

## 🧪 Тестирование

### Тестовые команды
```bash
# Unit тесты
npm test

# Integration тесты
npm run test:integration

# E2E тесты
npm run test:e2e

# Покрытие кода
npm run test:coverage

# Тестирование в watch режиме
npm run test:watch
```

### Качество кода
```bash
# Линтинг
npm run lint

# Форматирование
npm run format

# TypeScript проверка
npm run type-check

# Pre-commit хуки
npm run prepare
```

## 📈 Производительность

### Оптимизации
- **Redis кэширование** - экономия API вызовов до 90%
- **Connection pooling** для базы данных
- **Асинхронная обработка** - неблокирующие операции
- **Batch операции** - групповая обработка данных
- **CDN интеграция** для статических ресурсов

### Масштабирование
- **Horizontal scaling** - поддержка множественных инстансов
- **Load balancing** - распределение нагрузки
- **Microservices архитектура** - модульная структура
- **Event-driven архитектура** - асинхронная обработка событий

### Мониторинг производительности
- **Prometheus метрики** - сбор метрик
- **Grafana дашборды** - визуализация
- **Alertmanager** - уведомления о проблемах
- **Health checks** - проверка состояния сервисов

## 🌟 Новые возможности в последней версии

### v2.0.0 (Текущая версия)
- ✅ **Enhanced README** с подробной документацией
- ✅ **Complete Documentation** - полная документация проекта
- ✅ **Updated GitHub Actions** - новые CI/CD пайплайны
- ✅ **Release Notes Generation** - автогенерация release notes
- ✅ **Community Guidelines** - правила для сообщества
- ✅ **Contribution Workflow** - рабочий процесс для контрибьюторов
- ✅ **Security Policy** - политика безопасности
- ✅ **License Updater** - обновление лицензии
- ✅ **Archive Creation** - создание архивов для старых версий

### v1.x.x (Предыдущие версии)
- ✅ Базовая функциональность бота
- ✅ Веб-интерфейс управления
- ✅ Система заказов
- ✅ Интеграция с ИИ (Polza.ai)
- ✅ Докеризация

## 🤝 Контрибьюция

Мы приветствуем вклад сообщества! Подробности в [CONTRIBUTING.md](./CONTRIBUTING.md)

### Быстрый старт для контрибьюторов:

```bash
# Fork и клонирование репозитория
git clone https://github.com/your-username/twitch-ai-bot.git
cd twitch-ai-bot

# Создание ветки для фичи
git checkout -b feature/amazing-feature

# Установка зависимостей
npm install

# Запуск в development режиме
npm run dev

# После внесения изменений
npm run test
npm run lint
git commit -m "Add amazing feature"
git push origin feature/amazing-feature

# Откройте Pull Request
```

### Руководства для контрибьюторов:

- [Code Style Guide](./docs/CODE_STYLE.md)
- [API Documentation](./docs/API.md)
- [Architecture Guide](./docs/ARCHITECTURE.md)
- [Testing Guide](./docs/TESTING.md)
- [Deployment Guide](./docs/DEPLOYMENT.md)

## 📋 Roadmap

### v2.1.0 (Планируется)
- [ ] **Discord Voice Integration** - голосовые команды в Discord
- [ ] **Advanced Analytics** - детальная аналитика пользователей
- [ ] **Plugin System** - система плагинов для расширений
- [ ] **Multi-language Support** - поддержка множественных языков

### v2.2.0 (Планируется)
- [ ] **Twitch Extensions Store** - публикация в официальном магазине
- [ ] **Advanced AI Features** - улучшенные ИИ возможности
- [ ] **Community Hub** - социальные функции для сообщества
- [ ] **Mobile App Improvements** - улучшения мобильного приложения

### v3.0.0 (Будущие планы)
- [ ] **Microservices Architecture** - микросервисная архитектура
- [ ] **AI Training Pipeline** - обучение ИИ на данных пользователей
- [ ] **Enterprise Features** - функции для корпоративного использования
- [ ] **API Marketplace** - маркетплейс ботов и расширений

## 📄 Лицензия

Этот проект лицензирован под MIT License - подробности в [LICENSE](./LICENSE)

```
MIT License

Copyright (c) 2025 SvatOwl Tech

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🆘 Поддержка

### Документация
- [Установка и настройка](./INSTALLATION.md)
- [Docker развертывание](./DOCKER_README.md)
- [AWS развертывание](./AWS_DEPLOYMENT.md)
- [API документация](./docs/API.md)
- [Архитектура системы](./docs/ARCHITECTURE.md)

### Сообщество
- **GitHub Issues**: [Сообщить об ошибке](https://github.com/svatowl-tech/twitch-ai-bot/issues)
- **GitHub Discussions**: [Обсуждения](https://github.com/svatowl-tech/twitch-ai-bot/discussions)
- **Wiki**: [Подробная документация](https://github.com/svatowl-tech/twitch-ai-bot/wiki)

### Контакты
- **Email**: support@svatowl-tech.com
- **Discord**: [Присоединиться к серверу](https://discord.gg/svatowl-tech)
- **Twitch**: [Стримы и демо](https://twitch.tv/svatowl_tech)

### FAQ
Смотрите [FAQ.md](./docs/FAQ.md) для ответов на часто задаваемые вопросы.

## 📊 Статистика проекта

![GitHub stars](https://img.shields.io/github/stars/svatowl-tech/twitch-ai-bot?style=social)
![GitHub forks](https://img.shields.io/github/forks/svatowl-tech/twitch-ai-bot?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/svatowl-tech/twitch-ai-bot?style=social)
![GitHub issues](https://img.shields.io/github/issues/svatowl-tech/twitch-ai-bot)
![GitHub pull requests](https://img.shields.io/github/issues-pr/svatowl-tech/twitch-ai-bot)
![GitHub license](https://img.shields.io/github/license/svatowl-tech/twitch-ai-bot)
![GitHub last commit](https://img.shields.io/github/last-commit/svatowl-tech/twitch-ai-bot)

### Метрики проекта
- **Строк кода**: 25,000+
- **Компонентов**: 150+
- **API endpoints**: 50+
- **Тестов**: 300+
- **Документации**: 30+ файлов
- **Контрибьюторов**: 15+

### Покрытие тестами
- **Unit тесты**: 85%
- **Integration тесты**: 90%
- **E2E тесты**: 80%
- **Общее покрытие**: 87%

## 🎉 Благодарности

- **MiniMax AI** - предоставление ИИ технологий
- **Twitch** - платформа для стриминга
- **Discord** - коммуникационная платформа
- **Open Source Community** - вклад в развитие проекта

## ⭐ Поддержать проект

Если проект оказался полезным, поставьте звездочку ⭐ и поделитесь с друзьями!

[![GitHub stars](https://img.shields.io/github/stars/svatowl-tech/twitch-ai-bot?style=social)](https://github.com/svatowl-tech/twitch-ai-bot)
[![GitHub forks](https://img.shields.io/github/forks/svatowl-tech/twitch-ai-bot?style=social)](https://github.com/svatowl-tech/twitch-ai-bot/fork)
[![Tweet](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fgithub.com%2Fsvatowl-tech%2Ftwitch-ai-bot)](https://twitter.com/intent/tweet?text=Check%20out%20this%20awesome%20Twitch%20AI%20Bot!&url=https%3A%2F%2Fgithub.com%2Fsvatowl-tech%2Ftwitch-ai-bot)

---

<div align="center">

**Made with ❤️ by [SvatOwl Tech](https://svatowl-tech.com)**

[![Sponsor](https://img.shields.io/badge/Sponsor-Patreon-FF424D?style=for-the-badge&logo=patreon&logoColor=white)](https://patreon.com/svatowl_tech)
[![Sponsor](https://img.shields.io/badge/Sponsor-Buy%20Me%20a%20Coffee-FFDD00?style=for-the-badge&logo=buymeacoffee&logoColor=black)](https://buymeacoffee.com/svatowl_tech)

</div>