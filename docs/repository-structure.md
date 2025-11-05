# Руководство по структуре репозитория

Данный документ описывает обновленную структуру репозитория Twitch AI Bot для обеспечения лучшей организации кода и удобства разработки.

## 📁 Структура директорий

```
twitch-ai-bot/
├── 📁 .github/                    # GitHub файлы и workflow
│   ├── 📁 workflows/              # GitHub Actions CI/CD пайплайны
│   │   ├── ci.yml                 # Основной CI пайплайн
│   │   ├── release.yml            # Автогенерация релизов
│   │   ├── security.yml           # Security scanning
│   │   └── deploy.yml             # Deploy пайплайны
│   ├── 📁 ISSUE_TEMPLATE/         # Шаблоны issues
│   │   ├── bug_report.md          # Шаблон багрепорта
│   │   ├── feature_request.md     # Шаблон фич-реквеста
│   │   └── question.md            # Шаблон вопроса
│   ├── 📁 PULL_REQUEST_TEMPLATE/  # Шаблоны PR
│   │   └── pull_request_template.md
│   ├── FUNDING.yml                # Funding информация
│   └── CODEOWNERS                 # Code owners
├── 📁 .archive/                   # Архивы старых версий
│   ├── v1.0.0/                    # Архив первой версии
│   ├── v1.1.0/                    # Архив версии 1.1.0
│   └── README.md                  # Информация об архивах
├── 📁 docs/                       # Документация
│   ├── 📁 api/                    # API документация
│   ├── 📁 architecture/           # Архитектурная документация
│   ├── 📁 deployment/             # Руководства по развертыванию
│   ├── 📁 development/            # Руководства разработчика
│   ├── 📁 security/               # Безопасность
│   ├── CHANGELOG.md               # История изменений
│   ├── CONTRIBUTING.md            # Руководство по контрибьюции
│   └── README.md                  # Документация проекта
├── 📁 frontend/                   # Frontend приложение
│   ├── 📁 src/                    # Исходный код
│   ├── 📁 public/                 # Статические файлы
│   ├── package.json               # Зависимости и скрипты
│   └── README.md                  # Документация frontend
├── 📁 backend/                    # Backend сервер (если вынесен отдельно)
│   ├── 📁 src/                    # Исходный код
│   ├── 📁 config/                 # Конфигурация
│   ├── package.json               # Зависимости
│   └── README.md                  # Документация backend
├── 📁 src/                        # Основной исходный код
│   ├── 📁 api/                    # API сервер
│   ├── 📁 bot/                    # Twitch бот
│   ├── 📁 discord/                # Discord интеграция
│   ├── 📁 database/               # База данных
│   ├── 📁 services/               # Бизнес-логика
│   ├── 📁 utils/                  # Утилиты
│   └── 📁 types/                  # TypeScript типы
├── 📁 tests/                      # Тесты
│   ├── 📁 unit/                   # Unit тесты
│   ├── 📁 integration/            # Integration тесты
│   └── 📁 e2e/                    # End-to-end тесты
├── 📁 scripts/                    # Скрипты для разработки
│   ├── setup.sh                   # Скрипт установки
│   ├── build.sh                   # Скрипт сборки
│   ├── deploy.sh                  # Скрипт развертывания
│   └── utils/                     # Утилитарные скрипты
├── 📁 docker/                     # Docker конфигурация
│   ├── 📁 development/            # Docker for development
│   ├── 📁 production/             # Docker for production
│   ├── docker-compose.dev.yml     # Compose для разработки
│   ├── docker-compose.prod.yml    # Compose для продакшена
│   └── Dockerfile                 # Основной Dockerfile
├── 📁 cloud/                      # Cloud развертывание
│   ├── 📁 aws/                    # AWS конфигурация
│   ├── 📁 heroku/                 # Heroku конфигурация
│   ├── 📁 railway/                # Railway конфигурация
│   └── 📁 docker/                 # Docker конфигурации
├── 📁 .gitignore                  # Git игноры
├── .env.example                   # Пример переменных окружения
├── .gitattributes                 # Git атрибуты
├── .editorconfig                  # Конфигурация редактора
├── .eslintrc.js                   # ESLint конфигурация
├── .prettierrc                    # Prettier конфигурация
├── jest.config.js                 # Jest конфигурация
├── tsconfig.json                  # TypeScript конфигурация
├── package.json                   # Основные зависимости
├── Dockerfile                     # Основной Docker файл
├── docker-compose.yml             # Основной compose
├── Makefile                       # Make команды
├── LICENSE                        # Лицензия
├── README.md                      # Основной README
├── SECURITY.md                    # Политика безопасности
└── CONTRIBUTING.md                # Руководство контрибьюции
```

## 📋 Описание директорий

### `.github/` - GitHub инфраструктура
Содержит все GitHub-специфичные файлы, включая workflow, шаблоны и конфигурации.

**Поддиректории:**
- `workflows/` - GitHub Actions пайплайны для CI/CD
- `ISSUE_TEMPLATE/` - Шаблоны для создания issues
- `PULL_REQUEST_TEMPLATE/` - Шаблоны для pull requests

### `.archive/` - Архивные версии
Хранение архивов старых версий проекта для исторических целей и отката.

### `docs/` - Документация
Полная документация проекта, организованная по тематическим разделам.

### `src/` - Исходный код
Основной исходный код проекта, организованный по функциональным модулям.

### `tests/` - Тестирование
Все виды тестов: unit, integration и e2e тесты.

### `scripts/` - Скрипты разработки
Скрипты для автоматизации разработки, сборки и развертывания.

### `docker/` - Контейнеризация
Конфигурация Docker для различных окружений.

### `cloud/` - Облачное развертывание
Конфигурации для различных облачных платформ.

## 🚀 Workflow разработки

1. **Branch Strategy:**
   - `main` - стабильная версия
   - `develop` - активная разработка
   - `feature/*` - новые функции
   - `hotfix/*` - критические исправления
   - `release/*` - подготовка релизов

2. **Development Flow:**
   - Создание feature ветки от `develop`
   - Разработка и тестирование
   - Pull Request в `develop`
   - Code review и проверки
   - Merge в `develop`
   - Подготовка релиза в `release/*`
   - Merge в `main` и тегирование

3. **CI/CD Pipeline:**
   - Автоматические тесты на PR
   - Security scanning
   - Автоматические релизы
   - Развертывание в staging/production

## 📝 Правила коммитов

Используем [Conventional Commits](https://www.conventionalcommits.org/) формат:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Типы коммитов:**
- `feat:` - новая функциональность
- `fix:` - исправление бага
- `docs:` - изменения в документации
- `style:` - форматирование кода
- `refactor:` - рефакторинг
- `test:` - добавление тестов
- `chore:` - обновление зависимостей, конфигурации

**Примеры:**
```
feat(bot): добавить поддержку Discord команд
fix(api): исправить валидацию в orders endpoint
docs(readme): обновить документацию установки
```

## 🎯 Best Practices

1. **Code Organization:**
   - Модульная архитектура
   - Separation of concerns
   - DRY принцип
   - SOLID принципы

2. **Documentation:**
   - Комментарии в коде для сложной логики
   - README файлы в каждой директории
   - API документация
   - Обновление документации при изменениях

3. **Testing:**
   - Минимальное покрытие 80%
   - Unit тесты для бизнес-логики
   - Integration тесты для API
   - E2E тесты для критических путей

4. **Security:**
   - Валидация всех входных данных
   - Использование переменных окружения для секретов
   - Security scanning в CI
   - Защита от common vulnerabilities

## 🔄 Автоматизация

1. **GitHub Actions:**
   - Автоматическое тестирование
   - Code quality checks
   - Security scanning
   - Автоматические релизы

2. **Pre-commit Hooks:**
   - Линтинг кода
   - Форматирование
   - Проверка коммитов
   - Запуск тестов

3. **Deployment:**
   - Автоматическое развертывание
   - Health checks
   - Rollback механизмы
   - Мониторинг

---

Эта структура обеспечивает масштабируемость, удобство разработки и поддержку проекта.