# Base Project Template

A professional, production-ready GitHub template repository for building modern applications with best practices, GitHub Copilot optimization, and modular architecture.

## 🎯 Overview

This template provides a comprehensive foundation for creating web applications, backend services, desktop applications, CLI tools, and shared libraries. It includes professional development guidelines, Copilot-optimized prompts, programming skills documentation, and best practices aligned with Microsoft and industry standards.

### Perfect For

- 🌐 Web applications (React, Vue, Svelte)
- 🖥️ Backend services (Node.js, .NET, Python)
- 💻 Desktop applications (Electron, Tauri)
- 🔧 CLI tools and utilities
- 📦 Shared libraries and packages
- 🚀 Microservices architecture
- 📱 Progressive web apps (PWA)

## ✨ Key Features

### Professional Guidelines
- **GitHub Copilot Instructions** - Complete development standards following Microsoft practices
- **Programming Skills** - Reference documentation for common patterns and techniques
- **Code Quality Standards** - Naming conventions, SOLID principles, error handling
- **Security Best Practices** - Authentication, authorization, data protection

### Development Productivity
- **Prompt Templates** - Optimized prompts for different development scenarios
- **Quick Start Guide** - Get productive in minutes
- **Architecture Decisions** - Clear patterns and design guidelines
- **Testing Strategies** - Comprehensive testing approaches

### Modular Architecture
- **Web Projects** - Frontend and backend separation with shared code
- **Applications & Services** - Backend services, microservices, workers
- **Desktop Apps** - Electron, Tauri, WPF applications
- **Tools & Utilities** - CLI tools, build scripts, generators
- **Shared Libraries** - Common types, utilities, error handling
- **Documentation** - Comprehensive docs and guides

## 📁 Directory Structure

```
base-project-template/
├── .github/
│   ├── copilot-instructions.md    # Development guidelines
│   ├── SKILLS.md                  # Programming patterns reference
│   ├── prompts/                   # Development prompt templates
│   │   ├── 00-quick-start.md
│   │   ├── 01-feature-implementation.md
│   │   ├── 02-bug-fixing.md
│   │   ├── 03-refactoring.md
│   │   ├── 04-api-design.md
│   │   ├── 05-testing-strategy.md
│   │   └── 06-performance-optimization.md
│   └── README.md                  # GitHub configuration guide
│
├── web/                           # Web applications
│   ├── frontend/                  # Client application
│   ├── backend/                   # Server application
│   └── README.md
│
├── apps/                          # Backend services
│   ├── api-service/
│   ├── worker-service/
│   ├── websocket-service/
│   └── README.md
│
├── desktop/                       # Desktop applications
│   ├── electron-app/
│   ├── tauri-app/
│   └── README.md
│
├── tools/                         # CLI tools and utilities
│   ├── build-automation/
│   ├── code-generator/
│   └── README.md
│
├── shared/                        # Shared libraries
│   ├── types/
│   ├── utils/
│   ├── constants/
│   ├── errors/
│   └── README.md
│
├── docs/                          # Documentation
│   ├── getting-started.md
│   ├── architecture.md
│   ├── guides/
│   └── README.md
│
├── LICENSE
└── README.md
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
- [Quick Start Guide](./.github/prompts/00-quick-start.md)
- [Development Setup](./docs/getting-started.md)
- [Project Structure Guide](./docs/architecture.md)

### Development
- [GitHub Copilot Instructions](./.github/copilot-instructions.md)
- [Programming Skills Reference](./.github/SKILLS.md)
- [Code Standards & Conventions](./.github/copilot-instructions.md#code-standards)

### Project Types
- [Web Applications](./web/README.md)
- [Backend Services](./apps/README.md)
- [Desktop Applications](./desktop/README.md)
- [CLI Tools](./tools/README.md)
- [Shared Libraries](./shared/README.md)

### Tools & Resources
- [Prompt Templates](./.github/prompts/)
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
- **Framework**: React / Vue / Svelte
- **Language**: TypeScript
- **Styling**: Tailwind CSS / Styled Components
- **State**: Zustand / Redux / Pinia
- **Testing**: Jest / Vitest / React Testing Library

### Backend
- **Runtime**: Node.js / .NET / Python
- **Framework**: Express / NestJS / FastAPI
- **Database**: PostgreSQL / MongoDB / SQL Server
- **API**: REST / GraphQL
- **Testing**: Jest / pytest / unittest

### Desktop
- **Framework**: Electron / Tauri / WPF
- **Language**: TypeScript / C# / Rust
- **UI**: React / Vue / XAML

### DevOps
- **Version Control**: Git / GitHub
- **CI/CD**: GitHub Actions
- **Container**: Docker
- **Deployment**: Vercel / Heroku / AWS / Docker

## 📖 Code Standards

### Naming Conventions
```
Variables/Functions:     camelCase
Classes/Types/Interfaces: PascalCase
Constants:              UPPER_SNAKE_CASE
Files/Folders:          kebab-case
```

### Quality Standards
- ✅ TypeScript strict mode
- ✅ 80%+ test coverage for business logic
- ✅ SOLID principles
- ✅ Type safety first
- ✅ Error handling by default
- ✅ Comprehensive JSDoc documentation

### Code Review Checklist
- [ ] Follows naming conventions
- [ ] Type safe (strict TypeScript)
- [ ] Error handling complete
- [ ] Tests pass (80%+ coverage)
- [ ] No code duplication
- [ ] Security implications reviewed
- [ ] Performance impact assessed
- [ ] Documentation clear and current

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
```bash
npm run build           # Compile/bundle
npm run start           # Run production server
npm run test:coverage   # Check coverage
```

### Docker
```bash
docker build -t my-app .
docker run -p 3000:3000 my-app
```

### Cloud Platforms
- **Vercel/Netlify**: Frontend hosting
- **Heroku/Railway**: Backend hosting
- **AWS/Azure/GCP**: Enterprise deployment
- **Docker Hub**: Container registry

See [Deployment Guide](./docs/guides/deployment.md) for cloud-specific instructions.

## 🤝 Contributing

### Development Standards
1. Follow [Code Standards](./.github/copilot-instructions.md#code-standards)
2. Write tests for all features
3. Use [Conventional Commits](https://www.conventionalcommits.org/)
4. Reference related issues/PRs
5. Update documentation

### Commit Message Format
```
type(scope): subject

body

footer
```

**Types**: feat, fix, docs, style, refactor, perf, test, chore

### Pull Request Process
1. Create feature branch: `git checkout -b feature/feature-name`
2. Implement feature with tests
3. Ensure tests pass: `npm run test`
4. Check code quality: `npm run lint`
5. Create pull request with description
6. Address review feedback
7. Merge when approved

## 📝 License

This template is provided under the MIT License. See [LICENSE](LICENSE) for details.

## 🤖 Using with GitHub Copilot

### Best Practices

1. **Be Specific**: Provide context and examples
2. **Reference Patterns**: Link to existing implementations
3. **Set Constraints**: Define tech stack and standards
4. **Review Code**: Don't accept generated code without review
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
