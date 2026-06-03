# Claude Development Guidelines

Professional development standards and best practices for this project.

## Project Overview

Monorepo with npm workspaces using TypeScript 5.0+ strict mode.

**Workspaces:**

```
web/frontend     → React (port 5173)
web/backend      → Express (port 3000)
apps/api         → Standalone API service
shared/types     → Shared TypeScript interfaces
desktop/         → Electron/Tauri apps
tools/           → CLI utilities
```

**Key commands:**

```bash
npm install                          # Install all dependencies
npm run dev --workspaces             # Start all services
npm run dev -w web                   # Start web workspace
npm run test -w <workspace>          # Run tests
npm run test:coverage -w <workspace> # Coverage report
npm run type-check --workspaces      # TypeScript check
npm run lint:fix -w <workspace>      # Fix linting
npm run build --workspaces           # Build all
make docker-up                       # Start PostgreSQL + Redis
```

## Code Standards

### Naming Conventions

- `camelCase` → variables, functions
- `PascalCase` → classes, types, interfaces (prefix interfaces with `I`)
- `UPPER_SNAKE_CASE` → constants
- `kebab-case` → file and folder names

### File Structure per Module

```
module/
├── index.ts          # Public exports
├── types.ts          # Type definitions
├── constants.ts      # Module constants
├── module.ts         # Core implementation
├── module.test.ts    # Tests (alongside source)
├── utils.ts          # Helper functions
└── README.md         # Module documentation
```

### Import Order

```typescript
// 1. Standard library
import fs from 'fs';
// 2. Third-party
import axios from 'axios';
// 3. Local workspace
import { UserService } from './services';
import { IConfig } from './types';
// 4. Shared packages
import { logger } from '@shared/logger';
```

## Development Principles

- **SOLID** – Single Responsibility, Open/Closed, etc.
- **DRY** – No code duplication
- **KISS** – Prefer simple over clever
- **Fail Fast** – Validate inputs early with meaningful errors
- **Type Safety** – No `any`, use strict TypeScript
- **Error Handling** – Custom error classes, always handle all paths

## TypeScript Patterns

Always define shared types in `shared/types/src/index.ts`.

```typescript
// Discriminated unions for API responses
type ApiResponse<T> = { success: true; data: T } | { success: false; error: string; code: number };

// Custom error classes
class ValidationError extends AppError {
  readonly statusCode = 400;
  constructor(
    public readonly field: string,
    message: string
  ) {
    super(message);
  }
}
```

## Testing Standards

- Framework: **Vitest** (`*.test.ts` alongside source)
- Coverage target: **80%+** for business logic
- Pattern: **AAA** (Arrange-Act-Assert)
- Mock external deps: database, Redis, external APIs

```typescript
describe('UserService', () => {
  it('should return user when user exists', async () => {
    // Arrange
    mockRepository.findById.mockResolvedValue(expectedUser);
    // Act
    const result = await userService.getUserProfile('user-123');
    // Assert
    expect(result).toEqual(expectedUser);
  });
});
```

## API Design

- Use `IApiResponse<T>` wrapper from `shared/types/`
- Validate with **Joi**, log with **Pino**, secure with **Helmet**
- URL pattern: `/api/v1/<resource>/<action>`
- Error format: `{ error: { code, message, details?, timestamp } }`

## Security

- Input validation on all external data
- Parameterized queries (never string concatenation)
- JWT via `web/backend/src/middleware/auth.ts`
- Secrets via environment variables only
- Sanitize user input in UI (XSS prevention)

## Git Workflow

Conventional Commits format:

```
feat(auth): add two-factor authentication
fix(api): handle null user in getUserProfile
refactor(shared): extract base repository class
test(web): add coverage for login flow
perf(db): replace N+1 with JOIN query
```

Branch naming: `feature/`, `bugfix/`, `docs/`, `refactor/`

## Domain-Specific Guides

Use Claude slash commands for domain-specific patterns:

- `/project:web` – Frontend & full-stack web patterns
- `/project:backend` – Backend & microservices patterns
- `/project:desktop` – Electron/Tauri/WPF patterns
- `/project:tools` – CLI & automation patterns
- `/project:shared` – Shared library patterns

---

**Version**: 1.0 | **Last Updated**: 2026
