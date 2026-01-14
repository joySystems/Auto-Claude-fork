# Auto Claude

**Autonomous multi-agent coding framework that plans, builds, and validates software for you.**

![Auto Claude Kanban Board](.github/assets/Auto-Claude-Kanban.png)

[![License](https://img.shields.io/badge/license-AGPL--3.0-green?style=flat-square)](./agpl-3.0.txt)
[![Discord](https://img.shields.io/badge/Discord-Join%20Community-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.gg/KCXaPBr4Dj)
[![YouTube](https://img.shields.io/badge/YouTube-Subscribe-FF0000?style=flat-square&logo=youtube&logoColor=white)](https://www.youtube.com/@AndreMikalsen)
[![CI](https://img.shields.io/github/actions/workflow/status/AndyMik90/Auto-Claude/ci.yml?branch=main&style=flat-square&label=CI)](https://github.com/AndyMik90/Auto-Claude/actions)

---

## Download

### Stable Release

<!-- STABLE_VERSION_BADGE -->
[![Stable](https://img.shields.io/badge/stable-2.7.4-blue?style=flat-square)](https://github.com/AndyMik90/Auto-Claude/releases/tag/v2.7.4)
<!-- STABLE_VERSION_BADGE_END -->

<!-- STABLE_DOWNLOADS -->
| Platform | Download |
|----------|----------|
| **Windows** | [Auto-Claude-2.7.3-win32-x64.exe](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.3/Auto-Claude-2.7.3-win32-x64.exe) |
| **macOS (Apple Silicon)** | [Auto-Claude-2.7.3-darwin-arm64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.3/Auto-Claude-2.7.3-darwin-arm64.dmg) |
| **macOS (Intel)** | [Auto-Claude-2.7.3-darwin-x64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.3/Auto-Claude-2.7.3-darwin-x64.dmg) |
| **Linux** | [Auto-Claude-2.7.3-linux-x86_64.AppImage](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.3/Auto-Claude-2.7.3-linux-x86_64.AppImage) |
| **Linux (Debian)** | [Auto-Claude-2.7.3-linux-amd64.deb](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.3/Auto-Claude-2.7.3-linux-amd64.deb) |
| **Linux (Flatpak)** | [Auto-Claude-2.7.3-linux-x86_64.flatpak](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.3/Auto-Claude-2.7.3-linux-x86_64.flatpak) |
<!-- STABLE_DOWNLOADS_END -->

### Beta Release

> ⚠️ Beta releases may contain bugs and breaking changes. [View all releases](https://github.com/AndyMik90/Auto-Claude/releases)

<!-- BETA_VERSION_BADGE -->
[![Beta](https://img.shields.io/badge/beta-2.7.2--beta.10-orange?style=flat-square)](https://github.com/AndyMik90/Auto-Claude/releases/tag/v2.7.2-beta.10)
<!-- BETA_VERSION_BADGE_END -->

<!-- BETA_DOWNLOADS -->
| Platform | Download |
|----------|----------|
| **Windows** | [Auto-Claude-2.7.2-beta.10-win32-x64.exe](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.2-beta.10/Auto-Claude-2.7.2-beta.10-win32-x64.exe) |
| **macOS (Apple Silicon)** | [Auto-Claude-2.7.2-beta.10-darwin-arm64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.2-beta.10/Auto-Claude-2.7.2-beta.10-darwin-arm64.dmg) |
| **macOS (Intel)** | [Auto-Claude-2.7.2-beta.10-darwin-x64.dmg](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.2-beta.10/Auto-Claude-2.7.2-beta.10-darwin-x64.dmg) |
| **Linux** | [Auto-Claude-2.7.2-beta.10-linux-x86_64.AppImage](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.2-beta.10/Auto-Claude-2.7.2-beta.10-linux-x86_64.AppImage) |
| **Linux (Debian)** | [Auto-Claude-2.7.2-beta.10-linux-amd64.deb](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.2-beta.10/Auto-Claude-2.7.2-beta.10-linux-amd64.deb) |
| **Linux (Flatpak)** | [Auto-Claude-2.7.2-beta.10-linux-x86_64.flatpak](https://github.com/AndyMik90/Auto-Claude/releases/download/v2.7.2-beta.10/Auto-Claude-2.7.2-beta.10-linux-x86_64.flatpak) |
<!-- BETA_DOWNLOADS_END -->

> All releases include SHA256 checksums and VirusTotal scan results for security verification.

---

## Requirements

- **Claude Pro/Max subscription** - [Get one here](https://claude.ai/upgrade)
- **Claude Code CLI** - `npm install -g @anthropic-ai/claude-code`
- **Git repository** - Your project must be initialized as a git repo

---

## Quick Start

1. **Download and install** the app for your platform
2. **Open your project** - Select a git repository folder
3. **Connect Claude** - The app will guide you through OAuth setup
4. **Create a task** - Describe what you want to build
5. **Watch it work** - Agents plan, code, and validate autonomously

> 🇷🇺 **Для разработчиков**: Подробное руководство по разработке и сборке на русском языке → [DEVELOPMENT.md](DEVELOPMENT.md)

---

## Features

| Feature | Description |
|---------|-------------|
| **Autonomous Tasks** | Describe your goal; agents handle planning, implementation, and validation |
| **Parallel Execution** | Run multiple builds simultaneously with up to 12 agent terminals |
| **Isolated Workspaces** | All changes happen in git worktrees - your main branch stays safe |
| **Self-Validating QA** | Built-in quality assurance loop catches issues before you review |
| **AI-Powered Merge** | Automatic conflict resolution when integrating back to main |
| **Memory Layer** | Agents retain insights across sessions for smarter builds |
| **GitHub/GitLab Integration** | Import issues, investigate with AI, create merge requests |
| **Linear Integration** | Sync tasks with Linear for team progress tracking |
| **Cross-Platform** | Native desktop apps for Windows, macOS, and Linux |
| **Auto-Updates** | App updates automatically when new versions are released |

---

## Interface

### Kanban Board
Visual task management from planning through completion. Create tasks and monitor agent progress in real-time.

### Agent Terminals
AI-powered terminals with one-click task context injection. Spawn multiple agents for parallel work.

![Agent Terminals](.github/assets/Auto-Claude-Agents-terminals.png)

### Roadmap
AI-assisted feature planning with competitor analysis and audience targeting.

![Roadmap](.github/assets/Auto-Claude-roadmap.png)

### Additional Features
- **Insights** - Chat interface for exploring your codebase
- **Ideation** - Discover improvements, performance issues, and vulnerabilities
- **Changelog** - Generate release notes from completed tasks

---

## Project Structure

```
Auto-Claude/
├── apps/
│   ├── backend/     # Python agents, specs, QA pipeline
│   └── frontend/    # Electron desktop application
├── guides/          # Additional documentation
├── tests/           # Test suite
└── scripts/         # Build utilities
```

---

## CLI Usage

For headless operation, CI/CD integration, or terminal-only workflows:

```bash
cd apps/backend

# Create a spec interactively
python spec_runner.py --interactive

# Run autonomous build
python run.py --spec 001

# Review and merge
python run.py --spec 001 --review
python run.py --spec 001 --merge
```

See [guides/CLI-USAGE.md](guides/CLI-USAGE.md) for complete CLI documentation.

---

## Development

Want to build from source or contribute?

- **🇷🇺 Русская документация**: [DEVELOPMENT.md](DEVELOPMENT.md) - Подробное руководство по разработке и сборке на русском языке
- **🇬🇧 English documentation**: [CONTRIBUTING.md](CONTRIBUTING.md) - Complete development setup and contribution guidelines

For Linux-specific builds (Flatpak, AppImage), see [guides/linux.md](guides/linux.md).

---

## Security

Auto Claude uses a three-layer security model:

1. **OS Sandbox** - Bash commands run in isolation
2. **Filesystem Restrictions** - Operations limited to project directory
3. **Dynamic Command Allowlist** - Only approved commands based on detected project stack

All releases are:
- Scanned with VirusTotal before publishing
- Include SHA256 checksums for verification
- Code-signed where applicable (macOS)

---

## Available Scripts

| Command | Description |
|---------|-------------|
| `npm run install:all` | Install backend and frontend dependencies |
| `npm start` | Build and run the desktop app |
| `npm run dev` | Run in development mode with hot reload |
| `npm run package` | Package for current platform |
| `npm run package:mac` | Package for macOS |
| `npm run package:win` | Package for Windows |
| `npm run package:linux` | Package for Linux |
| `npm run package:flatpak` | Package as Flatpak (see [guides/linux.md](guides/linux.md)) |
| `npm run lint` | Run linter |
| `npm test` | Run frontend tests |
| `npm run test:backend` | Run backend tests |

---

## Contributing

We welcome contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for:
- Development setup instructions
- Code style guidelines
- Testing requirements
- Pull request process

---

## Community

- **Discord** - [Join our community](https://discord.gg/KCXaPBr4Dj)
- **Issues** - [Report bugs or request features](https://github.com/AndyMik90/Auto-Claude/issues)
- **Discussions** - [Ask questions](https://github.com/AndyMik90/Auto-Claude/discussions)

---

## License

**AGPL-3.0** - GNU Affero General Public License v3.0

Auto Claude is free to use. If you modify and distribute it, or run it as a service, your code must also be open source under AGPL-3.0.

Commercial licensing available for closed-source use cases.

---

## Star History

[![GitHub Repo stars](https://img.shields.io/github/stars/AndyMik90/Auto-Claude?style=social)](https://github.com/AndyMik90/Auto-Claude/stargazers)

[![Star History Chart](https://api.star-history.com/svg?repos=AndyMik90/Auto-Claude&type=Date)](https://star-history.com/#AndyMik90/Auto-Claude&Date)

📘 Инструкция по запуску и сборке Auto Claude                                                
  
  🚀 Запуск в режиме разработки                                                                   
  Требования:                                                                                  
  
  - Node.js >= 22.0.0 (рекомендуется 24+)
  - npm >= 10.0.0
  - Python >= 3.10 (для бэкенда)

  1. Установка зависимостей

  # Из корня проекта установить ВСЕ зависимости
  npm run install:all

  # Или вручную для каждой части:

  # Frontend (Electron)
  cd apps/frontend
  npm install

  # Backend (Python)
  cd apps/backend
  uv venv
  uv pip install -r requirements.txt

  2. Запуск приложения

  # Из корня проекта
  npm start

  # ИЛИ из apps/frontend
  cd apps/frontend
  npm run dev

  Что происходит:
  - Запускается Electron с горячей перезагрузкой (HMR)
  - Открывается окно приложения
  - DevTools открываются справа (в dev режиме)
  - Изменения в коде применяются автоматически

  3. Режим отладки с удаленным подключением

  cd apps/frontend
  npm run dev  # Уже включает --remote-debugging-port=9222 для E2E тестов

  ---
  🔨 Сборка приложения для продакшена

  Подготовка к сборке

  1. Обновите версию (если нужно):
  # Patch: 2.7.4 -> 2.7.5
  node scripts/bump-version.js patch

  # Minor: 2.7.4 -> 2.8.0
  node scripts/bump-version.js minor

  # Major: 2.7.4 -> 3.0.0
  node scripts/bump-version.js major

  2. Убедитесь, что все зависимости установлены:
  npm run install:all

  Сборка для вашей платформы

  cd apps/frontend

  # Windows (создаст .exe installer)
  npm run build:win

  # macOS (создаст .dmg)
  npm run build:mac

  # Linux (создаст .AppImage)
  npm run build:linux

  # Сборка для всех платформ (требует соответствующих ОС или CI/CD)
  npm run build

  Где найти результат сборки

  После сборки файлы будут в:
  apps/frontend/dist/
  ├── win-unpacked/          # Windows распакованная версия
  ├── Auto Claude Setup.exe  # Windows installer
  ├── mac/                   # macOS build
  ├── Auto Claude.dmg        # macOS installer
  └── linux-unpacked/        # Linux build

  ---
  📦 Структура команд
  ┌──────────────────────┬───────────────────────────────────────────┐
  │       Команда        │                 Описание                  │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm start            │ Сборка + запуск Electron (из корня)       │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm run dev          │ Режим разработки с HMR (из apps/frontend) │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm run build        │ Сборка для продакшена                     │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm run build:win    │ Сборка только для Windows                 │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm run build:mac    │ Сборка только для macOS                   │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm run build:linux  │ Сборка только для Linux                   │
  ├──────────────────────┼───────────────────────────────────────────┤
  │ npm run test:backend │ Запуск тестов Python бэкенда              │
  └──────────────────────┴───────────────────────────────────────────┘
  ---
  🐛 Отладка

  Backend (Python)

  cd apps/backend

  # Запуск spec runner напрямую
  python spec_runner.py --interactive

  # Запуск с конкретной задачей
  python spec_runner.py --task "Add user authentication"

  # Запуск автономной сборки
  python run.py --spec 001

  Frontend (Electron)

  cd apps/frontend

  # Запуск с DevTools
  npm run dev

  # Логи появляются в консоли терминала
  # Можно также смотреть в DevTools (F12)

  Логи приложения

  В режиме разработки:
  - Все логи выводятся в терминал, где запущено npm run dev

  В production:
  - Windows: %APPDATA%\Auto Claude\logs\
  - macOS: ~/Library/Logs/Auto Claude/
  - Linux: ~/.config/Auto Claude/logs/

  ---
  🔧 Настройка окружения

  Backend (.env файл)

  Создайте apps/backend/.env (пример в .env.example):

  # Claude Code OAuth Token
  CLAUDE_CODE_OAUTH_TOKEN=your-token-here

  # Graphiti Memory (опционально)
  GRAPHITI_ENABLED=true
  ANTHROPIC_API_KEY=your-api-key

  # Electron MCP для E2E тестов (опционально)
  ELECTRON_MCP_ENABLED=true
  ELECTRON_DEBUG_PORT=9222

  Frontend (.env файл)

  Создайте apps/frontend/.env (пример в .env.example):

  # Sentry для отчетов об ошибках (опционально)
  SENTRY_DSN=your-sentry-dsn

  # Режим отладки
  DEBUG=true
  DEBUG_UPDATER=true

  ---
  🚨 Частые проблемы

  1. "Claude Code CLI not found"

  Решение:
  # Установите Claude Code CLI
  npm install -g @anthropic-ai/claude-code

  # Проверьте установку
  claude --version

  2. "Python not found"

  Решение:
  - Установите Python 3.10+ с https://www.python.org
  - Убедитесь, что Python в PATH:
  python --version  # или python3 --version

  3. "Module not found" ошибки

  Решение:
  # Переустановите зависимости
  cd apps/frontend
  rm -rf node_modules package-lock.json
  npm install

  cd ../backend
  rm -rf .venv
  uv venv
  uv pip install -r requirements.txt

  4. Electron не запускается

  Решение:
  # Очистите кэш
  cd apps/frontend
  npm run clean  # если есть такая команда

  # Или вручную
  rm -rf node_modules/.vite
  rm -rf out
  npm install

  5. "Build failed" при сборке

  Решение:
  - Проверьте, что все зависимости установлены
  - Убедитесь, что версия Node.js >= 22
  - Проверьте свободное место на диске
  - Попробуйте собрать с --verbose:
  npm run build:win -- --verbose

  ---
  📝 CI/CD (GitHub Actions)

  Для автоматической сборки через GitHub Actions:

  1. Пушите изменения в ветку
  2. Создайте PR в main
  3. После мержа PR:
    - GitHub Actions автоматически создаст tag
    - Соберёт для всех платформ (Windows, macOS, Linux)
    - Создаст GitHub Release с changelog
    - Обновит README с последней версией

  Подробности в RELEASE.md

  ---
  🎯 Быстрый старт для разработчиков

  # 1. Клонировать репозиторий
  git clone <your-repo-url>
  cd Auto-Claude-fork

  # 2. Установить зависимости
  npm run install:all

  # 3. Настроить бэкенд
  cd apps/backend
  cp .env.example .env
  # Отредактируйте .env и добавьте CLAUDE_CODE_OAUTH_TOKEN

  # 4. Запустить приложение
  cd ../..
  npm start

  ---
  Готово! 🎉 Теперь вы можете разрабатывать и собирать Auto Claude!

  Если есть вопросы или проблемы, проверьте:
  - apps/frontend/README.md - детали по frontend
  - CLAUDE.md - инструкции для Claude Code
  - RELEASE.md - процесс релиза
