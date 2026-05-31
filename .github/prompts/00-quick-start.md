# Prompt: Quick Start - Vibe Coding Template

Quick reference for efficient development with GitHub Copilot using this template.

## Getting Started

### 1. Choose Your Project Type

```
Web Application (React/Vue/Svelte)     → /web
Backend Service (Node.js/Python/.NET)  → /apps
Desktop Application (Electron/Tauri)   → /desktop
Command-Line Tool                      → /tools
Shared Libraries                       → /shared
```

### 2. Essential Copilot Commands

#### Feature Development
```
@copilot /explain [function]           # Understand existing code
@copilot /refactor                     # Improve code quality
@copilot /tests                        # Generate test cases
@copilot /doc                          # Generate documentation
```

#### Quick Patterns
- Create new service with dependency injection
- Implement error handling with try-catch
- Add validation with Zod schemas
- Create unit tests with mocks
- Setup API endpoint with error handling

### 3. Naming Your Prompts

Be specific and provide context:

```
✓ "Create a TypeScript utility function that validates user email addresses"
✓ "Refactor this database query to use eager loading instead of N+1"
✓ "Write unit tests for the payment processing edge cases"
✗ "Make a function"
✗ "Fix this"
```

## Common Vibe Coding Patterns

### Pattern 1: Feature Development (30 mins)

```
1. Define requirements clearly
2. Create types/interfaces first
3. Implement core logic
4. Add error handling
5. Write unit tests
6. Document with JSDoc
```

Copilot prompt:
```
Create a [Feature] service with:
- [Requirements]
- Error handling for: [error cases]
- Following: [code patterns from project]
- Include: JSDoc, unit tests
```

### Pattern 2: Bug Investigation (20 mins)

```
1. Reproduce the issue
2. Locate source code
3. Analyze root cause
4. Implement fix
5. Add regression test
6. Verify fix
```

Copilot prompt:
```
Bug: [Symptom]
File: [location]
Root cause: [hypothesis]

Fix this by:
- [approach]
- Including: [test cases]
```

### Pattern 3: Code Review (10 mins)

```
1. Skim the changes
2. Check naming conventions
3. Verify error handling
4. Review test coverage
5. Request improvements
```

Copilot prompt:
```
Review this code for:
- SOLID principles compliance
- Type safety (strict TypeScript)
- Test coverage
- Performance issues
```

### Pattern 4: Performance Tuning (45 mins)

```
1. Identify bottleneck
2. Measure baseline
3. Apply optimization
4. Re-measure
5. Document trade-offs
```

Copilot prompt:
```
Optimize [code] for [metric]:
- Current: [baseline]
- Target: [goal]
- Constraints: [limits]

Use: [technique: caching, pagination, etc.]
```

## File Organization Quick Reference

```
app-name/
├── src/
│   ├── domain/          # Business logic
│   │   ├── models/      # Data models
│   │   └── services/    # Business services
│   ├── infrastructure/  # External integrations
│   │   ├── repositories/
│   │   ├── http-clients/
│   │   └── config/
│   ├── api/             # API layer (if applicable)
│   │   ├── routes/
│   │   ├── controllers/
│   │   └── middleware/
│   ├── ui/              # UI components (if frontend)
│   │   ├── components/
│   │   ├── pages/
│   │   └── hooks/
│   ├── shared/          # Shared utilities
│   │   ├── types.ts
│   │   ├── constants.ts
│   │   └── utils/
│   └── index.ts         # Main entry point
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── docs/                # Project documentation
└── package.json
```

## Troubleshooting

### Copilot Generating Wrong Code?
1. **Be more specific**: Add example input/output
2. **Reference patterns**: Link to similar implementations
3. **Set constraints**: Mention tech stack and requirements
4. **Ask for iterations**: "Start simple, then optimize"

### Type Errors in Generated Code?
1. Check imports are complete
2. Verify interface definitions match
3. Review TypeScript compiler errors
4. Ask Copilot to add type safety

### Tests Not Passing?
1. Verify mocks match actual service signatures
2. Check async/await handling
3. Review error message details
4. Ask Copilot to fix specific assertion

## Best Practices

### ✓ DO
- Ask Copilot to explain before changing code
- Test generated code before committing
- Reference existing patterns in prompts
- Break large requests into smaller steps
- Review security/performance implications

### ✗ DON'T
- Accept generated code without review
- Skip unit tests for generated functions
- Ignore TypeScript warnings/errors
- Mix incompatible dependencies
- Commit without running linter/formatter

## Next Steps

1. Read [copilot-instructions.md](copilot-instructions.md) for detailed standards
2. Review [SKILLS.md](SKILLS.md) for programming patterns
3. Pick a prompt from [prompts/](prompts/) for your use case
4. Create first feature using the template
5. Share patterns back to team
