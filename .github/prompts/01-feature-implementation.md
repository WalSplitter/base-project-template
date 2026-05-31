# Prompt: Feature Implementation - Vibe Coding

Use this prompt template when implementing new features with GitHub Copilot.

## Template

```
Context:
I'm building a [PROJECT_TYPE] application for [USE_CASE].
Current architecture: [BRIEF_ARCHITECTURE]
Existing patterns: [REFERENCE_EXISTING_CODE]

Requirements:
- Feature: [FEATURE_NAME]
- Functionality: [WHAT_IT_SHOULD_DO]
- Input: [INPUT_SPECIFICATION]
- Output: [OUTPUT_SPECIFICATION]
- Success criteria: [SUCCESS_CRITERIA]

Constraints:
- Technology stack: [TECH_STACK]
- Must follow: [CODE_STANDARDS_FROM_guidelines]
- Use existing types: [TYPE_REFERENCES]
- Error handling: [ERROR_SCENARIOS]

Deliverables:
1. Main implementation file with comprehensive error handling
2. Unit tests with happy path and error scenarios
3. JSDoc documentation
4. Integration with existing services
```

## Example Usage

```
Context:
I'm building a TypeScript web application for user management.
Current architecture: Service-based with dependency injection
Existing patterns: BaseRepository<T> for data access, ValidationError for errors

Requirements:
- Feature: Create user registration service
- Functionality: Accept email/password, validate input, hash password, save to database
- Input: { email: string, password: string, name: string }
- Output: { userId: string, createdAt: Date }
- Success criteria: User saved with hashed password, validation errors caught

Constraints:
- Technology stack: TypeScript, Node.js, PostgreSQL
- Must follow: Naming conventions (camelCase), SOLID principles
- Use existing types: from /src/types/user.ts
- Error handling: ValidationError for invalid input, NotFoundError for conflicts

Deliverables:
1. UserService class with registerUser() method
2. Unit tests covering valid registration and validation errors
3. JSDoc with @param, @returns, @throws
4. Integration with existing UserRepository
```

## Tips for Better Results

1. **Be Specific**: Instead of "create a function", specify the exact signature and behavior
2. **Provide Examples**: Show existing patterns or expected input/output
3. **Set Constraints**: Define technology choices and code standards upfront
4. **Reference Context**: Link to existing implementations for consistency
5. **Define Success**: Be clear about what "done" looks like

## Refinement Prompts

After initial implementation, use these refinement prompts:

- "Add comprehensive error handling for [SCENARIO]"
- "Optimize the performance by [STRATEGY]"
- "Add unit tests covering [EDGE_CASES]"
- "Refactor to follow [PATTERN] design pattern"
- "Add TypeScript strict mode compatibility"
