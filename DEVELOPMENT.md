# 🛠️ Руководство по разработке Auto Claude

Подробные инструкции по запуску, разработке и сборке Auto Claude для разработчиков.

---

## 📋 Требования

### Обязательно:

- **Node.js** >= 22.0.0 (рекомендуется 24+)
- **npm** >= 10.0.0
- **Python** >= 3.12
- **Git**

### Опционально:

- **uv** - быстрый менеджер пакетов Python (рекомендуется)
- **Claude Pro/Max** - для использования функций AI
- **CMake** - для сборки нативных зависимостей

### Проверка установленных версий:

```bash
node --version    # v24.0.0 или выше
npm --version     # 10.0.0 или выше
python --version  # 3.12.0 или выше
git --version     # Любая версия
```

---

## 🚀 Быстрый старт

### 1. Клонирование репозитория

```bash
git clone https://github.com/AndyMik90/Auto-Claude.git
cd Auto-Claude
```

### 2. Установка всех зависимостей

```bash
# Установка зависимостей для frontend и backend
npm run install:all
```

Эта команда автоматически:
- Установит npm зависимости для frontend
- Создаст Python виртуальное окружение
- Установит Python зависимости

### 3. Настройка окружения

```bash
# Backend
cd apps/backend
cp .env.example .env
# Отредактируйте .env и добавьте CLAUDE_CODE_OAUTH_TOKEN
```

Получите токен:
```bash
claude setup-token
# Скопируйте токен в apps/backend/.env
```

### 4. Запуск приложения

```bash
# Из корня проекта
npm start

# ИЛИ для режима разработки с hot reload
cd apps/frontend
npm run dev
```

---

## 📦 Установка зависимостей (детально)

### Frontend (Electron + React)

```bash
cd apps/frontend
npm install
```

**Что устанавливается:**
- Electron
- React + TypeScript
- Vite (сборщик)
- Tailwind CSS
- Radix UI компоненты
- И другие зависимости (~1000+ пакетов)

### Backend (Python)

**Вариант 1: С помощью uv (рекомендуется)**

```bash
cd apps/backend
uv venv
uv pip install -r requirements.txt
```

**Вариант 2: Стандартный Python**

```bash
cd apps/backend
python -m venv .venv

# Активация виртуального окружения:
# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate

# Установка зависимостей
pip install -r requirements.txt
```

**Что устанавливается:**
- Claude Agent SDK
- Graphiti (система памяти)
- FastAPI (для API endpoints)
- И другие зависимости

---

## 🔧 Режим разработки

### Запуск в режиме разработки

```bash
cd apps/frontend
npm run dev
```

**Что происходит:**
- ✅ Vite запускает dev server на `http://localhost:5173`
- ✅ Electron открывает окно приложения
- ✅ DevTools открываются автоматически
- ✅ Hot Module Replacement (HMR) включен - изменения применяются мгновенно
- ✅ Remote debugging включен на порту 9222 (для E2E тестов)

### Структура процесса

```
npm run dev
├── Vite Dev Server (localhost:5173) - рендерер
├── Electron Main Process - главный процесс
└── Electron Preload - изолированный контекст
```

### Логи в режиме разработки

**Где смотреть логи:**
- **Backend логи** → Терминал, где запущен `npm run dev`
- **Frontend логи** → DevTools Console (F12)
- **Main process логи** → Терминал с `[main]` префиксом
- **Renderer логи** → DevTools Console

**Пример логов:**
```bash
[main] App ready
[CLI Tools] Detected claude: C:\Users\...\claude.cmd
[PythonEnvManager] Venv ready
[vite] hmr update /components/Insights.tsx
```

---

## 📦 Сборка для продакшена

### Подготовка к сборке

1. **Обновите версию** (если нужно):

```bash
# Из корня проекта
node scripts/bump-version.js patch   # 2.7.4 → 2.7.5
node scripts/bump-version.js minor   # 2.7.4 → 2.8.0
node scripts/bump-version.js major   # 2.7.4 → 3.0.0
```

2. **Убедитесь, что зависимости установлены:**

```bash
npm run install:all
```

### Сборка для текущей платформы

```bash
cd apps/frontend

# Сборка для вашей ОС
npm run build
```

**Результат:**
```
apps/frontend/dist/
├── win-unpacked/          # Windows (если собираете на Windows)
├── mac/                   # macOS (если собираете на macOS)
└── linux-unpacked/        # Linux (если собираете на Linux)
```

### Сборка для конкретной платформы

```bash
cd apps/frontend

# Windows
npm run build:win
# Результат: dist/Auto-Claude-{version}-win32-x64.exe

# macOS
npm run build:mac
# Результат: dist/Auto-Claude-{version}-darwin-{arch}.dmg

# Linux
npm run build:linux
# Результат: dist/Auto-Claude-{version}-linux-x86_64.AppImage
```

### Доступные форматы

| Платформа | Форматы | Команда |
|-----------|---------|---------|
| **Windows** | `.exe` (installer), `.zip` | `npm run build:win` |
| **macOS** | `.dmg`, `.zip` | `npm run build:mac` |
| **Linux** | `.AppImage`, `.deb`, `.flatpak` | `npm run build:linux` |

### Тестирование собранного приложения

```bash
# Установите собранное приложение
# Windows: запустите .exe
# macOS: откройте .dmg и перетащите в Applications
# Linux: сделайте .AppImage исполняемым и запустите

# Проверьте:
# 1. Приложение запускается
# 2. Нет ошибок в логах
# 3. Все функции работают
# 4. Автообновление работает (если тестируете на production версии)
```

---

## 🐛 Отладка

### Backend (Python)

**Прямой запуск spec runner:**

```bash
cd apps/backend

# Интерактивный режим
python spec_runner.py --interactive

# С конкретной задачей
python spec_runner.py --task "Add user authentication"

# С принудительным уровнем сложности
python spec_runner.py --task "Fix button" --complexity simple
```

**Запуск автономной сборки:**

```bash
cd apps/backend

# Запуск build
python run.py --spec 001

# Список всех specs
python run.py --list

# Просмотр изменений
python run.py --spec 001 --review

# Merge в проект
python run.py --spec 001 --merge
```

**Отладка с помощью debugger:**

```python
# Добавьте в код:
import pdb; pdb.set_trace()

# Или используйте IDE debugger (VS Code, PyCharm)
```

### Frontend (Electron)

**DevTools:**
- Автоматически открываются в режиме `npm run dev`
- Или нажмите `F12` в работающем приложении

**Remote Debugging:**

```bash
# Приложение уже запущено с --remote-debugging-port=9222
# Подключитесь через Chrome:
chrome://inspect
# Найдите удаленную цель и нажмите "inspect"
```

**Логи приложения:**

| ОС | Путь к логам |
|----|--------------|
| **Windows** | `%APPDATA%\Auto Claude\logs\` |
| **macOS** | `~/Library/Logs/Auto Claude/` |
| **Linux** | `~/.config/Auto Claude/logs/` |

### Проблемы и решения

#### ❌ "Claude Code CLI not found"

**Причина:** Claude CLI не установлен или не в PATH

**Решение:**
```bash
npm install -g @anthropic-ai/claude-code
claude --version
```

#### ❌ "Python not found"

**Причина:** Python не установлен или не в PATH

**Решение:**
```bash
# Проверьте установку
python --version  # или python3 --version

# Если не установлен:
# Windows: winget install Python.Python.3.12
# macOS: brew install python@3.12
# Linux: sudo apt install python3.12
```

#### ❌ "Module not found" ошибки

**Причина:** Зависимости не установлены или устарели

**Решение:**
```bash
# Frontend
cd apps/frontend
rm -rf node_modules package-lock.json
npm install

# Backend
cd apps/backend
rm -rf .venv
uv venv
uv pip install -r requirements.txt
```

#### ❌ Electron не запускается

**Причина:** Кэш Vite или старая сборка

**Решение:**
```bash
cd apps/frontend
rm -rf node_modules/.vite out dist
npm install
npm run dev
```

#### ❌ "Process exited with code -4058" в Insights

**Причина:** Проблема с запуском Python команды `py -3`

**Решение:** Эта проблема исправлена в коммите с исправлениями insights-executor.ts

#### ❌ Чат выходит за границы экрана

**Причина:** Отсутствует `break-words` в CSS

**Решение:** Эта проблема исправлена в коммите с добавлением `break-words` в Insights.tsx

---

## 🧪 Тестирование

### Backend тесты

```bash
# Установите тестовые зависимости (один раз)
cd apps/backend
uv pip install -r ../../tests/requirements-test.txt

# Запуск всех тестов
../../apps/backend/.venv/bin/pytest tests/ -v

# Запуск одного файла
../../apps/backend/.venv/bin/pytest tests/test_security.py -v

# Запуск конкретного теста
../../apps/backend/.venv/bin/pytest tests/test_security.py::test_bash_command_validation -v

# Пропустить медленные тесты
../../apps/backend/.venv/bin/pytest tests/ -m "not slow"
```

### Frontend тесты

```bash
cd apps/frontend

# Unit тесты
npm test

# Watch режим
npm run test:watch

# Coverage
npm run test:coverage

# E2E тесты
npm run build
npm run test:e2e
```

---

## 📚 Структура команд

### Основные команды

| Команда | Где запускать | Описание |
|---------|---------------|----------|
| `npm run install:all` | Корень | Установка всех зависимостей |
| `npm start` | Корень | Сборка и запуск приложения |
| `npm run dev` | apps/frontend | Режим разработки с HMR |
| `npm run build` | apps/frontend | Сборка для продакшена |
| `npm run build:win` | apps/frontend | Сборка для Windows |
| `npm run build:mac` | apps/frontend | Сборка для macOS |
| `npm run build:linux` | apps/frontend | Сборка для Linux |
| `npm test` | apps/frontend | Запуск frontend тестов |
| `npm run test:backend` | Корень | Запуск backend тестов |

### Backend команды

```bash
cd apps/backend

# Создание spec
python spec_runner.py --interactive
python spec_runner.py --task "Your task description"

# Запуск build
python run.py --spec 001

# Управление builds
python run.py --list              # Список specs
python run.py --spec 001 --review # Просмотр изменений
python run.py --spec 001 --merge  # Merge в проект
python run.py --spec 001 --discard # Удалить build

# QA
python run.py --spec 001 --qa        # Запустить QA
python run.py --spec 001 --qa-status # Статус QA
```

### Утилиты

```bash
# Bump версии
node scripts/bump-version.js patch|minor|major

# Валидация spec
python apps/backend/validate_spec.py --spec-dir apps/backend/specs/001-feature --checkpoint all

# Линтинг
npm run lint              # Frontend
ruff check apps/backend/  # Backend
```

---

## 🏗️ Архитектура проекта

```
Auto-Claude/
├── apps/
│   ├── backend/              # Python бэкенд
│   │   ├── agents/          # Planner, Coder, QA agents
│   │   ├── spec_agents/     # Spec creation agents
│   │   ├── core/            # Claude SDK client, security
│   │   ├── integrations/    # Graphiti, Linear, GitHub
│   │   └── prompts/         # System prompts для агентов
│   │
│   └── frontend/            # Electron + React frontend
│       ├── src/
│       │   ├── main/       # Electron main process
│       │   ├── preload/    # Preload scripts
│       │   └── renderer/   # React UI
│       └── resources/      # Icons, assets
│
├── tests/                   # Тесты
├── scripts/                 # Build scripts
├── guides/                  # Документация
└── .github/                 # CI/CD workflows
```

---

## 🔐 Настройка окружения

### Backend .env файл

```bash
# apps/backend/.env

# ОБЯЗАТЕЛЬНО: Claude Code OAuth Token
CLAUDE_CODE_OAUTH_TOKEN=your-token-here

# Graphiti Memory (опционально, но рекомендуется)
GRAPHITI_ENABLED=true
ANTHROPIC_API_KEY=your-api-key

# Electron MCP для E2E тестов (опционально)
ELECTRON_MCP_ENABLED=true
ELECTRON_DEBUG_PORT=9222

# Linear Integration (опционально)
LINEAR_API_KEY=your-linear-key

# GitHub (опционально, для GitHub Issues/PRs)
GITHUB_TOKEN=your-github-token
```

### Frontend .env файл

```bash
# apps/frontend/.env

# Sentry для error tracking (опционально)
SENTRY_DSN=your-sentry-dsn

# Режим отладки
DEBUG=true
DEBUG_UPDATER=true

# Vite dev server (автоматически)
ELECTRON_RENDERER_URL=http://localhost:5173
```

---

## 🚀 CI/CD (GitHub Actions)

### Автоматическая сборка

При пуше в `main` ветку GitHub Actions автоматически:

1. ✅ Запускает тесты (frontend + backend)
2. ✅ Собирает для всех платформ (Windows, macOS, Linux)
3. ✅ Создает GitHub Release с changelog
4. ✅ Публикует сборки с SHA256 checksums
5. ✅ Обновляет README с последней версией

### Локальное тестирование CI

```bash
# Установите act (GitHub Actions local runner)
# https://github.com/nektos/act

# Запуск CI локально
act -j build
```

---

## 📖 Дополнительные ресурсы

- **CLAUDE.md** - Инструкции для Claude Code AI
- **CONTRIBUTING.md** - Руководство по contributing (на английском)
- **RELEASE.md** - Процесс релиза
- **guides/** - Детальные гайды (Linux build, и т.д.)

---

## 💡 Полезные советы

### Hot Reload

В режиме `npm run dev` изменения применяются автоматически:

- ✅ **Frontend (.tsx, .ts, .css)** → Instant HMR (без перезагрузки)
- ✅ **Main process (.ts в src/main/)** → Перезапуск main process
- ❌ **Backend (.py)** → Требуется ручной перезапуск

### Отладка с VS Code

**.vscode/launch.json:**

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Electron Main",
      "type": "node",
      "request": "launch",
      "cwd": "${workspaceFolder}/apps/frontend",
      "runtimeExecutable": "npm",
      "runtimeArgs": ["run", "dev"],
      "outputCapture": "std"
    },
    {
      "name": "Python Backend",
      "type": "python",
      "request": "launch",
      "program": "${workspaceFolder}/apps/backend/run.py",
      "args": ["--spec", "001"],
      "cwd": "${workspaceFolder}/apps/backend",
      "console": "integratedTerminal"
    }
  ]
}
```

### Быстрая очистка

```bash
# Очистить все build артефакты
rm -rf apps/frontend/dist apps/frontend/out apps/frontend/node_modules/.vite
rm -rf apps/backend/.venv apps/backend/__pycache__

# Переустановить зависимости
npm run install:all
```

---

## ❓ FAQ

**Q: Сколько времени занимает первая сборка?**
A: ~5-10 минут (зависит от скорости интернета и CPU)

**Q: Можно ли собрать для macOS на Windows?**
A: Нет, electron-builder требует нативную ОС для каждой платформы

**Q: Как обновить зависимости?**
A: `npm run install:all` переустановит все зависимости

**Q: Нужен ли Docker?**
A: Нет, все работает нативно без Docker

**Q: Где хранятся данные приложения?**
A: В `.auto-claude/` директории вашего проекта (git-ignored)

---

## 🤝 Поддержка

- **Discord**: [Join Community](https://discord.gg/KCXaPBr4Dj)
- **Issues**: [Report Bug](https://github.com/AndyMik90/Auto-Claude/issues)
- **Discussions**: [Ask Questions](https://github.com/AndyMik90/Auto-Claude/discussions)

---

**Удачной разработки!** 🚀
