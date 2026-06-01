# Base Project Template

[![GitHub](https://img.shields.io/badge/GitHub-base--project--template-blue?logo=github)](https://github.com/yourusername/base-project-template)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue.svg)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)](https://nodejs.org/)
[![npm workspaces](https://img.shields.io/badge/npm-workspaces-blue.svg)](https://docs.npmjs.com/cli/v8/using-npm/workspaces)
[![GitHub Actions](https://img.shields.io/badge/CI/CD-GitHub%20Actions-blue.svg)](https://github.com/features/actions)

> A production-ready, enterprise-grade template for building scalable applications with modern best practices, GitHub Copilot optimization, and professional development standards.

## 🎯 Overview

This comprehensive template repository provides everything you need to build professional applications at scale:

- **🏗️ Monorepo Architecture**: Multiple project types in a single repository with shared dependencies
- **📋 TypeScript-First**: Strict type safety, full IntelliSense, and excellent developer experience
- **🤖 GitHub Copilot Integration**: Optimized prompts, skill guides, and development patterns
- **🔄 CI/CD Ready**: Pre-configured GitHub Actions for testing, linting, security scanning
- **🐳 Docker Support**: Multi-stage Dockerfile and docker-compose for local development
- **📚 Complete Documentation**: Setup guides, deployment strategies, ADRs, and troubleshooting

### Perfect For

- 🌐 **Web Applications** - Full-stack React/Vue/Svelte with Express/NestJS backends
- 🖥️ **Backend Services** - Microservices, APIs, and scalable server applications
- 💻 **Desktop Applications** - Cross-platform apps with Electron or Tauri
- 🔧 **CLI Tools** - Command-line utilities and code generators
- 📦 **Shared Libraries** - Reusable types, utilities, and components
- 🚀 **Monorepo Projects** - Multiple applications with shared code
- 📱 **Progressive Web Apps** - PWA and hybrid applications

## ✨ Key Features

### 🎯 Out-of-the-Box Setup
- ✅ **npm Workspaces** - Efficient monorepo management with unified dependencies
- ✅ **TypeScript 5.0+** - Strict mode enabled with full ESLint configuration
- ✅ **Code Quality** - ESLint, Prettier, and automated formatting pre-configured
- ✅ **Git Ready** - .gitattributes, .gitignore, and conventional commits setup
- ✅ **Environment Templates** - .env.example with sensible defaults

### 🤖 GitHub Copilot Optimization
- 📝 **Development Guidelines** - Complete coding standards and best practices
- 🎓 **Skill Guides** - Domain-specific patterns (web, backend, desktop, tools)
- 📋 **Prompt Templates** - Pre-written prompts for feature implementation, bug fixes, refactoring, testing
- 🏗️ **Architecture Patterns** - SOLID principles, dependency injection, error handling
- 📚 **Reference Documentation** - Type safety, async patterns, API design, performance optimization

### 🚀 CI/CD & DevOps
- 🔄 **GitHub Actions Workflows** - Automated testing, linting, building, and security scanning
- 🐳 **Docker Support** - Multi-stage Dockerfile for production builds + docker-compose for local dev
- 🎯 **Makefile** - Common development commands for quick access
- 🔐 **Security Integration** - Dependabot config, vulnerability scanning, secret management
- 📊 **Code Quality** - Automated code analysis and coverage reporting

### 📦 Project Templates
- **Web Application** - React frontend + Express backend with TypeScript
- **API Service** - RESTful API with middleware, routing, and error handling
- **Shared Types** - Centralized TypeScript definitions for type-safe communication
- **Desktop Ready** - Structure for Electron, Tauri, or WPF applications
- **CLI Tools** - Scaffolding for command-line utilities

### 📚 Complete Documentation
- 🚀 [Quick Start Guide](./docs/getting-started/README.md) - Get running in 5 minutes
- 🔧 [Environment Setup](./docs/getting-started/environment.md) - Development environment configuration
- 🏗️ [Architecture Decisions](./docs/adr/) - ADRs for design choices
- 📖 [Deployment Guides](./docs/guides/deployment.md) - Vercel, AWS, Railway, Docker
- 🔐 [Security Policy](./SECURITY.md) - Best practices and vulnerability reporting
- 📋 [Setup Instructions](./SETUP.md) - Detailed installation and configuration

## 📁 Project Structure

```
base-project-template/
├── .github/
│   ├── workflows/                 # CI/CD pipelines
│   │   ├── ci.yml                # Build, test, lint, security
│   │   └── code-quality.yml       # Code quality analysis
│   ├── ISSUE_TEMPLATE/            # Issue templates
│   │   ├── bug.yml
│   │   └── feature.yml
│   ├── PULL_REQUEST_TEMPLATE.md   # PR template
│   ├── copilot-instructions.md    # Development standards & guidelines
│   ├── SKILLS.md                  # Programming patterns & techniques
│   ├── prompts/                   # GitHub Copilot prompts
│   │   ├── 00-quick-start.md
│   │   ├── 01-feature-implementation.md
│   │   ├── 02-bug-fixing.md
│   │   ├── 03-refactoring.md
│   │   ├── 04-api-design.md
│   │   ├── 05-testing-strategy.md
│   │   └── 06-performance-optimization.md
│   ├── skills/                    # Domain-specific guides
│   │   ├── 01-web-development.md
│   │   ├── 02-backend-development.md
│   │   ├── 03-desktop-development.md
│   │   └── README.md
│   └── README.md                  # GitHub configuration guide
│
├── web/                           # Full-stack web application
│   ├── frontend/                  # React + TypeScript + Vite
│   │   ├── src/
│   │   ├── public/
│   │   ├── vite.config.ts
│   │   ├── vitest.config.ts
│   │   ├── index.html
│   │   ├── tsconfig.json
│   │   └── package.json
│   ├── backend/                   # Express + TypeScript
│   │   ├── src/
│   │   │   ├── routes/
│   │   │   ├── middleware/
│   │   │   ├── utils/
│   │   │   └── index.ts
│   │   ├── tsconfig.json
│   │   ├── vitest.config.ts
│   │   └── package.json
│   ├── package.json               # Workspace definition
│   └── README.md
│
├── apps/                          # Backend services & APIs
│   ├── api/                       # API service template
│   │   └── package.json
│   ├── mobile/                    # Mobile backend
│   ├── admin/                     # Admin service
│   └── README.md
│
├── d️⃣ Create Your Project

**Option A: Use as GitHub Template (Recommended)**
```bash
# Click "Use this template" on GitHub
# or use GitHub CLI:
gh repo create my-project --template base-project-template --public
cd my-project
```

**Option B: Clone Repository**
```bash
git clone https://github.com/yourusername/base-project-template.git my-project
cd my-project
```

### 2️⃣ Install & Setup (5 minutes)

```bash
# Install all dependencies (includes web, backend, shared)
npm install

# Copy environment template
cp .env.example .env

# Start development servers (frontend on :5173, backend on :3000)
npm run dev
```

**Verify Setup:**
- Frontend: http://localhost:5173
- Backend API: http://localhost:3000/api/health
- Check status: `npm run type-check`

### 3️⃣ Choose Your Path

| Goal | Directory | Command |
|------|-----------|---------|
| **Full-Stack Web** | `/web` | `npm run dev -w web` |
| **Backend API Only** | `/apps/api` | `npm run dev -w apps/api` |
| **Frontend Only** | `/web/frontend` | `npm run dev -w web/frontend` |
| **Desktop App** | `/desktop` | See [desktop guide](./desktop/README.md) |
| **CLI Tool** | `/tools` | See [tools guide](./tools/README.md) |

### 4️⃣ Essential Reading

1. 📖 **[Development Guidelines](./.github/copilot-instructions.md)** - Code standards & practices
2. 🤖 **[Quick Start Prompts](./.github/prompts/00-quick-start.md)** - Using GitHub Copilot effectively
3. 🏗️ **[Architecture Guide](./ARCHITECTURE.md)** - Design decisions & patterns
4. 📚 **[Setup Instructions](./SETUP.md)** - Detailed configuration

### 5️⃣ Common Commands

```bash
# Development
npm run dev              # Start all servers
npm run build           # Build all projects
npm run test            # Run all tests
npm run test:coverage   # Generate coverage report

# Code Quality
npm run lint            # Check code quality
npm run lint:fix        # Auto-fix issues
npm run format          # Format with Prettier
npm run type-check      # TypeScript validation

# Docker
npm run docker-up       # Start PostgreSQL & Redis
npm run docker-down     # Stop containers

# Utilities
make help               # Show all Makefile commands
make setup              # Complete setup (install + docker)
```

### 6️⃣ First Contribution

1. Create feature branch: `git checkout -b feature/my-feature`
2. Make changes following [guidelines](./.github/copilot-instructions.md)
3. Test locally: `npm run test && npm run lint`
4. Commit using conventional format: `git commit -m "feat(module): add feature"`
5. Push and create PR: `git push origin feature/my-feature─ SECURITY.md                    # Security policy & best practices
├── SETUP.md                       # Detailed setup instructions
├── PROJECT_TYPES.md               # Guide for choosing project type
├── LICENSE                        # MIT License
└── README.md                      # This file
```

## 🚀 Quick Start

### 1. Create Your Project from Template

```bash
# Using GitHub CLI
gh repo create my-project --template base-project-template

# Or clone directly
git clone https://github.com/yourusername/base-project-template my-project
cd my-project
```

### 2. Update Project Identity

```bash
# Update README.md
# Update package.json name and description
# Update .github/README.md for your organization
# Add LICENSE file if needed
```

### 3. Choose Your Project Type

Navigate to the appropriate directory for your use case:

- **Web Application**: `/web/frontend` and `/web/backend`
- **Backend Service**: `/apps/api-service`
- **Desktop App**: `/desktop/electron-app`
- **CLI Tool**: `/tools/build-automation`

### 4. Read Development Guidelines

```bash
# Essential reading order:
1. .github/README.md                      # Overview
2. .github/copilot-instructions.md        # Development standards
3. .github/prompts/00-quick-start.md      # Getting started with Copilot
4. [Your project type] README.md          # Project-specific guide
```

### 5. Install Dependencies

```bash
npm install
# or for specific project
cd web/frontend && npm install
```

### 6. Start Developing

```bash
npm run dev
# Follow prompts in .github/prompts/ for your task
```

## 📚 Documentation

### Getting Started
- [Q🤖 With GitHub Copilot

This template is optimized for GitHub Copilot with pre-written prompts and skill guides:

1. **Select your task type:**
   - Feature implementation → `.github/prompts/01-feature-implementation.md`
   - Bug fixing → `.github/prompts/02-bug-fixing.md`
   - Refactoring → `.github/prompts/03-refactoring.md`
   - API design → `.github/prompts/04-api-design.md`
   - Testing → `.github/prompts/05-testing-strategy.md`
   - Performance → `.github/prompts/06-performance-optimization.md`

2. **Reference domain-specific guide:**
   - Web development → `.github/skills/01-web-development.md`
   - Backend → `.github/skills/02-backend-development.md`
   - Desktop → `.github/skills/03-desktop-development.md`

3. **Use Copilot Chat with structured prompts:**
   ```
   @copilot Follow the pattern in .github/prompts/01-feature-implementation.md
   
   Context: [Your context]
   Requirements: [What to build]
   Constraints: [Tech stack, patterns to follow]
   Include: Error handling, types, tests, documentation
   ```

4. **Verify & commit:**
   ```bash
   npm run lint && npm run test && npm run type-check
   git commit -m "feat(scope): description"
   ```

### Example Workflow: Add User Service

```bash
# 1. Read the template
cat .github/prompts/01-feature-implementation.md

# 2. Read patterns
cat .github/skills/02-backend-development.md

# 3. Use Copilot (copy the prompt template, customize with your context)

# 4. Test & verify
npm run test -w web/backend
npm run lint:fix
npm run type-check

# 5. Commit
git commit -m "feat(backend): add user service with validation and error handling")
  - Feature implementation
  - Bug fixing and debugging
  - Code refactoring
  - API design
  - Testing strategy
  - Performance optimization
- [Troubleshooting Guide](./docs/troubleshooting.md)
- [FAQ](./docs/faq.md)

## 💡 Development Workflow

### With GitHub Copilot

1. **Read the relevant prompt template** (based on your task)
2. **Reference the guidelines** (.github/copilot-instructions.md)
3. **Check SKILLS.md** for pattern examples
4. **Use Copilot with specific prompts** (not generic requests)
5. **Review and test** before committing

### Example: Implementing a Feature

```
1. Read: .github/prompts/01-feature-implementation.md
2. Reference: .github/SKILLS.md (error handling, types)
3. Use Copilot:
   "Create a [Feature] service following this pattern: [Template]
    Include: Error handling, types, unit tests, JSDoc"
4. Test: npm run test
5. Review: Check against code standards
```

## 🛠️ Technology Stack

### Frontend
| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 18+ | UI Framework |
| **TypeScript** | 5.0+ | Type Safety |
| **Vite** | 5.0+ | Build Tool |
| **Vitest** | 1.0+ | Testing Framework |
| **Zustand** | 4.4+ | State Management |
| **Axios** | 1.6+ | HTTP Client |

### Backend
| Technology | Version | Purpose |
|------------|---------|---------|
| **Express** | 4.18+ | Web Framework |
| **TypeScript** | 5.0+ | Type Safety |
| **PostgreSQL** | 14+ | Database |
| **Redis** | 7.0+ | Caching |
| **Pino** | 8.17+ | Logging |
| **JWT** | 9.1+ | Authentication |

### DevOps & Tools
| Tool | Version | Purpose |
|------|---------|---------|
| **Node.js** | 18.0+ | Runtime |
| **npm** | 9.0+ | Package Manager |
| **Docker** | 24.0+ | Containerization |
| **GitHub Actions** | - | CI/CD |
| **ESLint** | 8.0+ | Linting |
| **Prettier** | 3.0+ | Formatting |

### Optional Technologies

**For Different Project Types:**
- Vue / Svelte (alternative frontend frameworks)
- NestJS / FastAPI (alternative backends)
- Electron / Tauri (desktop applications)
- Prisma / TypeORM (database ORM)
- GraphQL (alternative API style)

## � Code Standards & Quality

### Naming Conventions
```typescript
// Variables & Functions: camelCase
const userName = 'John Doe';
function calculateTotal() {}

// Classes, Types, Interfaces: PascalCase  
class UserService {}
interface IUserProfile {}
type TUserRole = 'admin' | 'user';

// Constants: UPPER_SNAKE_CASE
const MAX_RETRIES = 3;
const DEFAULT_TIMEOUT = 5000;

// Files & Directories: kebab-case
src/user-service.ts
components/user-profile.tsx
```

### Quality Standards
- ✅ **TypeScript**: Strict mode enabled globally
- ✅ **Testing**: Minimum 80% coverage for business logic
- ✅ **Linting**: ESLint with TypeScript support
- ✅ **Formatting**: Prettier with consistent rules
- ✅ **Type Safety**: Full type annotations required
- ✅ **Error Handling**: Try-catch blocks everywhere
- ✅ **Documentation**: JSDoc on public APIs

### Pre-Commit Checks
```bash
# Automatically run before commit:
npm run lint:fix   # Fix formatting issues
npm run type-check # Verify types
npm run format     # Format code
```

### Code Review Checklist
- [ ] Follows naming conventions
- [ ] Type-safe (strict TypeScript)
- [ ] Error handling complete
- [ ] Tests pass with 80%+ coverage
- [ ] No code duplication
- [ ] Security implications reviewed
- [ ] Performance considered
- [ ] Documentation updated
- [ ] Changelog entry added (if applicable)

## 🔐 Security

This template emphasizes security best practices:
- Input validation and sanitization
- Secure authentication (JWT, OAuth)
- Authorization checks
- Environment variable management
- SQL injection prevention
- XSS protection
- CORS configuration
- Rate limiting
- Logging without exposing secrets

See [Security Guide](./docs/guides/security.md) for detailed information.

## 🧪 Testing

Comprehensive testing strategy included:
- **Unit Tests**: 80%+ coverage of business logic
- **Integration Tests**: Critical workflows
- **E2E Tests**: User-facing features
- **Performance Tests**: Benchmark comparisons

See [Testing Guide](./.github/prompts/05-testing-strategy.md) for details.

## 📦 Deployment

### Local Development
```bash
npm run dev              # Start with hot reload
npm run test            # Run tests
npm run lint            # Check code quality
```

### Production Build
```bContribution Process

1. **Fork & Clone**
   ```bash
   git clone https://github.com/yourusername/base-project-template.git
   cd base-project-template
   npm install
   ```

2. **Create Feature Branch**
   ```bash
   git checkout -b feature/my-feature
   ```

3. **Follow Development Standards**
   - Read [Development Guidelines](./.github/copilot-instructions.md)
   - Use [Code Standards](#-code-standards--quality)
   - Write tests for new features

4. **Commit with Conventional Format**
   ```bash
   # Format: type(scope): subject
   git commit -m "feat(auth): add JWT token refresh"
   git commit -m "fix(api): handle null user gracefully"
   git commit -m "docs(readme): update setup instructions"
   ```

   **Types:** & Attribution

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

### License Summary
✅ **Allowed:**
- Commercial use
- Modification
- Distribution
- Private use

❌ **Not Allowed:**
- No warranty or liability

### Attribution
While not required, we appreciate credit to [WalSplitter](https://github.com/yourusername/) and linking to this repository.

---

## 🎉 Getting Started Now!

### Ready to Build?

1. **Clone or use as template** → Start with your project
2. **Follow quick start** → Up and running in 5 minutes
3. **Read guidelines** → Understand development standards
4. **Start coding** → Build your amazing application

### Next Steps

- 📖 Read [Quick Start Guide](./docs/getting-started/README.md)
- 🤖 Explore [GitHub Copilot Prompts](./.github/prompts/)
- 🏗️ Review [Architecture Decisions](./docs/adr/)
- 🚀 Deploy your first application

---

**Template Version:** 1.0  
**Last Updated:** 2026-06-01  
**Maintained by:** Development Community  
**License:** MIT

**Questions? Issues? Ideas?**  
→ Create an [Issue](../../issues) or [Discussion](../../discussions)

**Happy Coding! 🚀: Don't accept generated code without review
5. **Iterate**: Ask Copilot to refine and improve

### Recommended Workflow

```
Read Template → Use Copilot → Test → Review → Commit
   ↓              ↓             ↓       ↓
0-5 min     5-10 min        5-10 min  5 min
```

See [Prompt Engineering Best Practices](./.github/copilot-instructions.md#prompt-engineering-best-practices) for detailed guidance.

## ❓ FAQ

**Q: Can I use this for commercial projects?**
A: Yes! This is a template designed for production applications.

**Q: Do I need to keep all project types?**
A: No, customize based on your needs. Remove unused directories.

**Q: How do I update shared types across projects?**
A: Use workspace feature in package.json for monorepo setup.

**Q: Can I use different technologies?**
A: Yes, this is a template. Adapt it to your tech stack.

See [FAQ](./docs/faq.md) for more questions.

## 📞 Support

- 📖 [Documentation](./docs/README.md)
- 🐛 [Troubleshooting](./docs/troubleshooting.md)
- 💬 [GitHub Discussions](../../discussions)
- 🔗 [GitHub Issues](../../issues)

## 🎓 Learning Resources

- [Microsoft Code Guidelines](https://docs.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
- [Clean Code Best Practices](https://clean-code-js.com/)
- [GitHub Copilot Best Practices](https://docs.github.com/copilot)

## 🚀 Next Steps

1. ✅ Clone or use as template
2. ✅ Update project identity
3. ✅ Read [Quick Start](./.github/prompts/00-quick-start.md)
4. ✅ Choose your project type
5. ✅ Review [Development Standards](./.github/copilot-instructions.md)
6. ✅ Start building with confidence!

---

**Template Version**: 1.0  
**Last Updated**: 2026  
**Maintained by**: Development Community  
**License**: MIT

**Happy Coding! 🎉**
