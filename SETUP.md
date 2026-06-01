# Project Setup Guide

## Prerequisites

Before you begin, ensure you have the following installed:

### Required

- **Node.js**: 18.0.0 or later
  - Download: https://nodejs.org/
  - Verify: `node --version`

- **npm**: 9.0.0 or later (included with Node.js)
  - Verify: `npm --version`

- **Git**: Latest stable version
  - Download: https://git-scm.com/

### Recommended

- **Visual Studio Code**: Latest version
  - Download: https://code.visualstudio.com/
  - Extensions: ESLint, Prettier, GitLens

- **Docker** (for database and services)
  - Download: https://www.docker.com/products/docker-desktop/

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/base-project-template.git
cd base-project-template
```

### 2. Install Dependencies

```bash
npm install
```

This will install all dependencies for the root project and all workspaces.

### 3. Setup Environment Variables

```bash
cp .env.example .env
```

Edit `.env` and fill in your configuration:

```env
NODE_ENV=development
PORT=3000
DATABASE_URL=postgresql://user:password@localhost:5432/dbname
JWT_SECRET=your-secret-key-here
```

### 4. Database Setup (if using PostgreSQL)

```bash
# Using Docker
docker run --name postgres -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres

# Or use your own PostgreSQL instance
psql -U postgres -c "CREATE DATABASE dbname;"
```

## Development

### Run Development Server

```bash
npm run dev
```

This starts all development servers in watch mode.

### Run Specific Project

```bash
# Web application
npm run dev -w web

# API service
npm run dev -w apps/api

# Desktop app
npm run dev -w desktop/electron
```

### Code Quality

```bash
# Format code
npm run format

# Check formatting
npm run format:check

# Lint code
npm run lint

# Fix lint issues
npm run lint:fix

# Type check
npm run type-check
```

### Testing

```bash
# Run all tests
npm run test

# Run tests in watch mode
npm run test:watch

# Run with coverage
npm run test:coverage
```

### Build

```bash
# Build all projects
npm run build

# Build specific project
npm run build -w web
```

## Project Structure

```
base-project-template/
├── web/                    # Full-stack web application
│   ├── src/
│   ├── package.json
│   └── tsconfig.json
├── apps/
│   ├── api/               # REST API service
│   ├── mobile/            # Mobile app service
│   └── admin/             # Admin dashboard
├── desktop/
│   ├── electron/          # Electron desktop app
│   └── tauri/             # Tauri desktop app
├── tools/
│   ├── cli/               # Command-line tools
│   ├── generators/        # Code generators
│   └── scripts/           # Utility scripts
├── shared/
│   ├── types/             # Shared TypeScript types
│   ├── utils/             # Shared utilities
│   ├── config/            # Shared configuration
│   └── components/        # Shared React components
├── docs/                  # Documentation
├── .github/
│   ├── copilot-instructions.md   # Development guidelines
│   ├── prompts/           # Copilot prompt templates
│   ├── skills/            # Copilot skill guides
│   └── workflows/         # GitHub Actions
├── package.json           # Root package configuration
├── tsconfig.json          # TypeScript configuration
├── .eslintrc.json         # ESLint configuration
└── .prettierrc.json       # Prettier configuration
```

## Troubleshooting

### Port Already in Use

```bash
# Find process using port 3000
lsof -i :3000

# Kill process
kill -9 <PID>
```

### Database Connection Issues

```bash
# Check PostgreSQL is running
psql -U postgres -c "SELECT 1;"

# Check .env configuration
cat .env | grep DATABASE_URL
```

### Node Module Issues

```bash
# Clear npm cache
npm cache clean --force

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

### Git Issues

```bash
# Update git submodules (if applicable)
git submodule update --init --recursive

# Check git configuration
git config --list
```

## IDE Setup

### VS Code

1. Install recommended extensions:
   - ESLint
   - Prettier
   - TypeScript Vue Plugin
   - GitLens

2. Create `.vscode/settings.json`:

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "typescript.tsdk": "node_modules/typescript/lib"
}
```

### IntelliJ IDEA

1. Install ESLint plugin
2. Enable ESLint in Settings > Languages & Frameworks > JavaScript > Code Quality Tools > ESLint
3. Configure Prettier in Settings > Languages & Frameworks > JavaScript > Prettier

## Git Workflow

### Create Feature Branch

```bash
git checkout -b feature/my-feature
```

### Commit Changes

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```bash
git commit -m "feat(module): add new feature"
git commit -m "fix(module): resolve issue #123"
git commit -m "docs: update README"
```

### Push and Create PR

```bash
git push origin feature/my-feature
```

Then create a Pull Request on GitHub.

## Getting Help

- 📖 [Documentation](./docs/)
- 🤝 [Contributing Guide](./CONTRIBUTING.md)
- 📋 [Development Guidelines](./.github/copilot-instructions.md)
- 💬 [GitHub Discussions](https://github.com/yourusername/base-project-template/discussions)

---

**Last Updated**: 2026-06-01
