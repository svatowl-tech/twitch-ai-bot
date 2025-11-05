# Руководство по контрибьюции в Twitch AI Bot

Спасибо за ваш интерес к участию в развитии Twitch AI Bot! Это руководство поможет вам начать работу с проектом и внести свой вклад.

## 📋 Содержание

- [Быстрый старт](#-быстрый-старт)
- [Настройка окружения](#-настройка-окружения)
- [Workflow разработки](#-workflow-разработки)
- [Стандарты кода](#-стандарты-кода)
- [Тестирование](#-тестирование)
- [Документация](#-документация)
- [Сообщения об ошибках](#-сообщения-об-ошибках)
- [Pull Request процесс](#-pull-request-процесс)
- [Release процесс](#-release-процесс)

## 🚀 Быстрый старт

### Предварительные требования

- **Node.js** 18.x или выше
- **npm** или **yarn**
- **Git** (последняя версия)
- **Docker** (для разработки)
- **PostgreSQL** 15.x (для полного функционала)
- **Redis** 7.x (для кэширования)

### Первые шаги

1. **Fork репозитория**
   ```bash
   # На GitHub нажмите "Fork" на странице проекта
   # Затем клонируйте ваш fork:
   git clone https://github.com/YOUR_USERNAME/twitch-ai-bot.git
   cd twitch-ai-bot
   ```

2. **Добавьте upstream remote**
   ```bash
   git remote add upstream https://github.com/svatowl-tech/twitch-ai-bot.git
   ```

3. **Создайте ветку для работы**
   ```bash
   git checkout -b feature/amazing-feature
   ```

## 🔧 Настройка окружения

### Установка зависимостей

```bash
# Установка основных зависимостей
npm install

# Установка зависимостей для frontend
cd frontend
npm install
cd ..

# Установка зависимостей для backend (если вынесен отдельно)
cd backend
npm install
cd ..
```

### Настройка окружения разработки

1. **Копирование конфигурации**
   ```bash
   cp .env.example .env
   cp .env.example .env.development
   ```

2. **Редактирование переменных окружения**
   ```env
   # Обязательные переменные для разработки
   NODE_ENV=development
   BOT_NAME=TwitchAIBot
   TWITCH_CLIENT_ID=your_twitch_client_id
   TWITCH_CLIENT_SECRET=your_twitch_client_secret
   DATABASE_URL=postgresql://postgres:postgres@localhost:5432/twitch_bot_dev
   REDIS_URL=redis://localhost:6379
   JWT_SECRET=your_jwt_secret_for_dev
   ```

3. **Запуск базы данных**
   ```bash
   # Через Docker (рекомендуется)
   docker-compose -f docker-compose.dev.yml up -d postgres redis
   
   # Или локальная установка
   # Установите PostgreSQL и Redis локально
   ```

4. **Инициализация БД**
   ```bash
   npm run db:migrate
   npm run db:seed
   ```

5. **Проверка установки**
   ```bash
   npm run dev
   # Откройте http://localhost:3000
   ```

## 🔄 Workflow разработки

### Branch Strategy

Мы используем GitFlow с некоторыми модификациями:

- **`main`** - стабильная production версия
- **`develop`** - основная ветка разработки
- **`feature/*`** - новые функции
- **`hotfix/*`** - критические исправления
- **`release/*`** - подготовка релизов
- **`security/*`** - исправления безопасности

### Стандартный workflow

1. **Синхронизация с upstream**
   ```bash
   git checkout develop
   git pull upstream develop
   git push origin develop
   ```

2. **Создание feature ветки**
   ```bash
   git checkout -b feature/user-authentication
   # или
   git checkout -b fix/websocket-reconnection
   ```

3. **Разработка**
   - Делайте небольшие, логичные коммиты
   - Следуйте conventional commits стандарту
   - Тестируйте локально

4. **Commit сообщения**
   ```bash
   # Хорошие примеры:
   feat(bot): add Twitch OAuth authentication
   fix(api): resolve database connection timeout
   docs(readme): update installation instructions
   style(frontend): fix ESLint warnings in Dashboard.tsx
   refactor(database): optimize user queries
   test(orders): add integration tests for order processing
   chore(dependencies): update React to v18.2.0
   ```

5. **Push и создание PR**
   ```bash
   git push origin feature/user-authentication
   # Затем создайте PR через GitHub UI
   ```

### Conventional Commits

Мы используем [Conventional Commits](https://www.conventionalcommits.org/) для автоматической генерации changelog:

```bash
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Типы:**
- `feat:` - новая функциональность
- `fix:` - исправление бага
- `docs:` - изменения в документации
- `style:` - форматирование кода (не влияет на логику)
- `refactor:` - рефакторинг кода
- `perf:` - улучшение производительности
- `test:` - добавление или исправление тестов
- `chore:` - изменения в процессе сборки, конфигурации

**Примеры:**
```bash
feat(auth): add JWT token refresh mechanism
fix(websocket): prevent memory leak on disconnect
docs(api): document new webhook endpoints
style(button): improve mobile responsiveness
refactor(database): use connection pooling
test(orders): add unit tests for OrderService
chore(deps): update Express to v4.18.2
```

## 💻 Стандарты кода

### TypeScript

```typescript
// ✅ Хорошо: Используйте интерфейсы для типов
interface User {
  id: string;
  username: string;
  email: string;
  createdAt: Date;
}

// ✅ Хорошо: Явно типизируйте функции
const getUserById = async (id: string): Promise<User | null> => {
  return await db.users.findUnique({ where: { id } });
};

// ✅ Хорошо: Используйте enum для констант
enum UserRole {
  ADMIN = 'admin',
  STREAMER = 'streamer',
  MODERATOR = 'moderator',
  VIEWER = 'viewer'
}

// ❌ Плохо: any types
const processData = (data: any): any => {
  return data.process();
};
```

### React компоненты

```tsx
// ✅ Хорошо: Functional components с TypeScript
import React, { FC, useState, useEffect } from 'react';
import { User } from '../types';

interface UserCardProps {
  user: User;
  onEdit: (user: User) => void;
}

const UserCard: FC<UserCardProps> = ({ user, onEdit }) => {
  const [isLoading, setIsLoading] = useState(false);

  const handleEdit = async () => {
    setIsLoading(true);
    try {
      await onEdit(user);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <div className="user-card">
      <h3>{user.username}</h3>
      <p>{user.email}</p>
      <button 
        onClick={handleEdit} 
        disabled={isLoading}
      >
        {isLoading ? 'Редактирование...' : 'Редактировать'}
      </button>
    </div>
  );
};

export default UserCard;
```

### Code Style

Мы используем:
- **ESLint** для линтинга
- **Prettier** для форматирования
- **Prettier** интегрирован с ESLint для избежания конфликтов

```bash
# Проверка кода
npm run lint
npm run lint:fix

# Форматирование
npm run format
npm run format:check

# TypeScript проверка
npm run type-check
```

### Именование файлов

- **Компоненты React**: `PascalCase.tsx`
- **Утилиты**: `camelCase.ts`
- **Константы**: `UPPER_SNAKE_CASE.ts`
- **Типы**: `camelCase.types.ts`
- **Сервисы**: `PascalCaseService.ts`

### Архитектурные принципы

- **Separation of Concerns** - разделяйте бизнес-логику и UI
- **DRY (Don't Repeat Yourself)** - избегайте дублирования кода
- **SOLID принципы** - следуйте принципам объектно-ориентированного программирования
- **Clean Architecture** - организуйте код слоями

## 🧪 Тестирование

### Запуск тестов

```bash
# Все тесты
npm test

# Watch режим
npm run test:watch

# Coverage отчет
npm run test:coverage

# Integration тесты
npm run test:integration

# E2E тесты
npm run test:e2e
```

### Написание тестов

#### Unit тесты (Jest)

```typescript
// user.service.test.ts
import { UserService } from '../user.service';
import { Database } from '../database';

describe('UserService', () => {
  let userService: UserService;
  let mockDb: jest.Mocked<Database>;

  beforeEach(() => {
    mockDb = {
      users: {
        findUnique: jest.fn(),
        create: jest.fn(),
        update: jest.fn(),
      },
    } as any;
    
    userService = new UserService(mockDb);
  });

  describe('getUserById', () => {
    it('should return user when found', async () => {
      // Arrange
      const mockUser = { id: '1', username: 'testuser' };
      mockDb.users.findUnique.mockResolvedValue(mockUser);

      // Act
      const result = await userService.getUserById('1');

      // Assert
      expect(result).toEqual(mockUser);
      expect(mockDb.users.findUnique).toHaveBeenCalledWith({
        where: { id: '1' },
      });
    });

    it('should return null when user not found', async () => {
      // Arrange
      mockDb.users.findUnique.mockResolvedValue(null);

      // Act
      const result = await userService.getUserById('999');

      // Assert
      expect(result).toBeNull();
    });
  });
});
```

#### Integration тесты

```typescript
// orders.integration.test.ts
import request from 'supertest';
import { app } from '../app';

describe('Orders API Integration', () => {
  describe('POST /api/orders', () => {
    it('should create new order', async () => {
      const orderData = {
        game: 'Cyberpunk 2077',
        userId: 'user123',
        price: 2999,
      };

      const response = await request(app)
        .post('/api/orders')
        .send(orderData)
        .expect(201);

      expect(response.body).toMatchObject({
        id: expect.any(String),
        game: orderData.game,
        status: 'pending',
      });
    });

    it('should validate required fields', async () => {
      const invalidData = {
        game: 'Cyberpunk 2077',
        // missing userId and price
      };

      await request(app)
        .post('/api/orders')
        .send(invalidData)
        .expect(400);
    });
  });
});
```

#### E2E тесты (Playwright)

```typescript
// dashboard.e2e.test.ts
import { test, expect } from '@playwright/test';

test.describe('Dashboard', () => {
  test('should display user statistics', async ({ page }) => {
    // Login
    await page.goto('/login');
    await page.fill('[name="username"]', 'testuser');
    await page.fill('[name="password"]', 'password123');
    await page.click('[type="submit"]');

    // Navigate to dashboard
    await page.click('[data-testid="dashboard-link"]');

    // Check dashboard content
    await expect(page.locator('h1')).toContainText('Dashboard');
    await expect(page.locator('[data-testid="stats-total-users"]')).toContainText('150');
    await expect(page.locator('[data-testid="stats-active-orders"]')).toContainText('23');
  });

  test('should filter orders by status', async ({ page }) => {
    await page.goto('/dashboard/orders');

    // Filter by pending status
    await page.selectOption('[data-testid="status-filter"]', 'pending');
    await page.waitForSelector('[data-testid="orders-table"]');

    // Verify filtered results
    const orders = await page.locator('[data-testid="order-row"]').count();
    expect(orders).toBeGreaterThan(0);

    // All orders should have pending status
    for (let i = 0; i < orders; i++) {
      const status = await page.locator(`[data-testid="order-row"]:nth-child(${i + 1}) [data-testid="order-status"]`).textContent();
      expect(status).toBe('Pending');
    }
  });
});
```

### Покрытие тестами

Мы стремимся к следующему покрытию:
- **Unit тесты**: минимум 80%
- **Integration тесты**: все API endpoints
- **E2E тесты**: основные пользовательские сценарии

## 📝 Документация

### Что документировать

- **Публичные API** - все endpoints и их параметры
- **Компоненты React** - props и их использование
- **Сервисы и утилиты** - методы и их назначение
- **Конфигурация** - все важные настройки
- **Deployment** - инструкции по развертыванию

### Формат документации

```typescript
/**
 * Сервис для работы с пользователями
 * 
 * @example
 * ```typescript
 * const userService = new UserService(db);
 * const user = await userService.getUserById('123');
 * ```
 */
export class UserService {
  /**
   * Получает пользователя по ID
   * @param id - Уникальный идентификатор пользователя
   * @returns Пользователь или null если не найден
   * @throws {ValidationError} Если ID некорректный
   */
  async getUserById(id: string): Promise<User | null> {
    if (!id || typeof id !== 'string') {
      throw new ValidationError('User ID must be a non-empty string');
    }

    return await this.db.users.findUnique({
      where: { id },
      include: {
        orders: true,
        permissions: true,
      },
    });
  }
}
```

### Обновление документации

При изменениях в коде:

1. **Обновите JSDoc** в коде
2. **Обновите README** если изменился public API
3. **Обновите examples** если изменились usage patterns
4. **Обновите changelog** для breaking changes

## 🐛 Сообщения об ошибках

### Создание Issue

#### Bug Report Template

```markdown
**Bug Description**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

**Expected Behavior**
A clear and concise description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain your problem.

**Environment:**
- OS: [e.g. Windows 10, macOS Big Sur]
- Node.js version: [e.g. 18.17.0]
- Bot version: [e.g. 2.0.0]
- Browser: [e.g. Chrome 116.0, Safari 16.0]

**Additional Context**
Add any other context about the problem here.

**Error Log**
```
Paste relevant error logs here
```
```

#### Feature Request Template

```markdown
**Is your feature request related to a problem? Please describe.**
A clear and concise description of what the problem is. Ex. I'm always frustrated when [...]

**Describe the solution you'd like**
A clear and concise description of what you want to happen.

**Describe alternatives you've considered**
A clear and concise description of any alternative solutions or features you've considered.

**Additional context**
Add any other context or screenshots about the feature request here.
```

### Quality Requirements для Issues

- **Воспроизводимость**: четкие шаги для воспроизведения
- **Полнота**: достаточно информации для понимания проблемы
- **Конкретность**: избегайте общих описаний
- **Релевантность**: связано с функциональностью проекта

## 🔀 Pull Request процесс

### Pre-PR Checklist

Перед созданием PR убедитесь:

- [ ] **Код следует стандартам** проекта (ESLint, Prettier)
- [ ] **Тесты добавлены** для новой функциональности
- [ ] **Документация обновлена** при необходимости
- [ ] **Все тесты проходят** локально
- [ ] **Commit сообщения** следуют conventional commits
- [ ] **Branch актуальна** с последними изменениями из develop
- [ ] **Нет merge conflicts**

### PR Template

```markdown
## Описание изменений

Краткое описание изменений и причины их внесения

## Тип изменений

- [ ] Исправление бага (non-breaking change)
- [ ] Новая функция (non-breaking change)
- [ ] Breaking change (исправление или функция, которая нарушает обратную совместимость)
- [ ] Обновление документации

## Как это тестировалось

Опишите тесты, которые вы запустили для проверки изменений

## Checklist

- [ ] Мой код следует стилевым стандартам проекта
- [ ] Я выполнил self-review кода
- [ ] Я прокомментировал сложные части кода
- [ ] Я обновил соответствующую документацию
- [ ] Мои изменения не генерируют новые warnings
- [ ] Я добавил тесты, которые доказывают, что мое исправление эффективно или что моя функция работает
- [ ] Новые и существующие unit тесты проходят локально с моими изменениями
- [ ] Я добавил необходимые изменения в CHANGELOG.md
```

### Review процесс

#### Для авторов PR

- **Отвечайте на комментарии** конструктивно и быстро
- **Вносите требуемые изменения** или объясняйте свое решение
- **Обновляйте документацию** при необходимости
- **Убедитесь, что все тесты проходят**
- **Обновляйте PR** при изменении базы кода

#### Для рецензентов

- **Будьте конструктивными** в своих комментариях
- **Фокусируйтесь на коде**, а не на человеке
- **Предлагайте альтернативы** когда не согласны
- **Поощряйте хорошие практики** и качественный код
- **Проверяйте тесты** и покрытие

### Criteria для Merge

PR может быть слит когда:

- ✅ **Все тесты проходят**
- ✅ **Получены 2 approved** от maintainers
- ✅ **Нет pending changes** запросов
- ✅ **Нет merge conflicts**
- ✅ **CI/CD пайплайны прошли успешно**
- ✅ **Code coverage не снизился**

## 🚀 Release процесс

### Версионирование

Мы следуем [Semantic Versioning](https://semver.org/):

- **MAJOR** (x.0.0) - breaking changes
- **MINOR** (2.x.0) - новая функциональность, backward compatible
- **PATCH** (2.1.x) - исправления bugs, backward compatible

### Подготовка релиза

1. **Обновите changelog**
2. **Увеличьте версию** в package.json
3. **Создайте release ветку** от develop
4. **Проведите testing** на staging
5. **Создайте PR** в main

### Автоматический релиз

GitHub Actions автоматически:

1. **Создаст release notes** на основе коммитов
2. **Сгенерирует changelog**
3. **Создаст Git tag**
4. **Загрузит Docker images**
5. **Опубликует npm пакет** (если применимо)
6. **Создаст архив** с исходным кодом

## 🎯 Часто задаваемые вопросы

### Как получить помощь?

1. **Проверьте документацию** в `/docs`
2. **Поищите в existing issues** на GitHub
3. **Создайте новый issue** с вопросом
4. **Присоединитесь к Discord** серверу проекта

### Как выбрать задачу для работы?

1. **Просмотрите issues** с label `good first issue`
2. **Проверьте roadmap** в проекте
3. **Создайте issue** для обсуждения новой идеи
4. **Присоединяйтесь к обсуждениям** в Discussions

### Как получить статус maintainer?

Maintainers выбираются на основе:
- **Качества кода** в PR
- **Активности** в проекте
- **Помощи** другим участникам
- **Знания архитектуры** проекта

---

## 💝 Благодарности

Спасибо всем контрибьюторам Twitch AI Bot! Ваш вклад делает проект лучше:

- Каждый PR, issue и комментарий ценится
- Мы признаем вклад в release notes
- Лучшие контрибьюторы получают special recognition

### Hall of Fame

*Здесь будет список активных контрибьюторов*

---

**Помните**: этот проект существует благодаря добровольным усилиям. Будьте терпеливы, уважительны и поддерживайте дружелюбную атмосферу в сообществе.

*Удачи в контрибьюции! 🎉*

---

*Последнее обновление: 2025-11-05*