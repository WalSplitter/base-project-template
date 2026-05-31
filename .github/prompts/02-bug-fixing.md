# Prompt: Bug Fixing & Debugging - Vibe Coding

Use this prompt template when debugging and fixing issues with GitHub Copilot.

## Template

```
Problem:
File: [FILE_PATH]
Issue: [DESCRIPTION_OF_PROBLEM]
Current behavior: [WHAT_HAPPENS_NOW]
Expected behavior: [WHAT_SHOULD_HAPPEN]

Context:
- Related code: [CODE_SNIPPET]
- Error message: [EXACT_ERROR_OR_LOG]
- Environment: [DEV/PROD] on [NODE_VERSION/BROWSER]

Investigation:
- Affected functions: [FUNCTION_NAMES]
- Likely cause: [YOUR_HYPOTHESIS]
- Recent changes: [IF_ANY]

Solution approach:
- Type: Fix / Refactor / Optimization
- Required tests: [TEST_SCENARIOS]
- Potential side effects: [IF_ANY]

Deliverables:
1. Corrected implementation
2. Root cause analysis comment
3. Unit tests for the bug scenario
4. Prevention strategy (linting rule, type check, etc.)
```

## Example Usage

```
Problem:
File: src/services/user-service.ts
Issue: User registration sometimes creates duplicate accounts
Current behavior: Concurrent registration requests create multiple users with same email
Expected behavior: Only one user per email, reject duplicates with ValidationError

Context:
- Related code: UserService.registerUser(email, password)
- Error message: Unique constraint violation from database
- Environment: Production on Node.js 18

Investigation:
- Affected functions: registerUser, checkEmailExists
- Likely cause: Race condition between email check and user creation
- Recent changes: Increased traffic from marketing campaign

Solution approach:
- Type: Fix - Add database-level constraints and pessimistic locking
- Required tests: Concurrent registration attempts
- Potential side effects: Slightly increased query time

Deliverables:
1. Updated registerUser with transaction lock
2. Comment explaining the race condition and solution
3. Test simulating concurrent requests
4. Linting rule to catch similar patterns
```

## Debugging Checklist

- [ ] Reproduction steps clearly documented
- [ ] Error stack trace reviewed
- [ ] Recent code changes checked
- [ ] Type safety verified (TypeScript strict mode)
- [ ] Edge cases identified
- [ ] Unit test added for the bug
- [ ] Similar code patterns checked for same issue
- [ ] Performance impact assessed

## Common Fix Patterns

### Race Condition
- Use database transactions or atomic operations
- Add optimistic/pessimistic locking
- Use queues for sequential processing

### Type Mismatch
- Check TypeScript strict mode compatibility
- Verify type definitions match usage
- Add type guards for runtime validation

### Performance Issue
- Profile with browser/Node.js DevTools
- Identify bottlenecks (N+1 queries, loops, etc.)
- Apply caching or pagination strategies

### Memory Leak
- Check for unremoved event listeners
- Verify cleanup in useEffect/destructors
- Review circular references and weak maps
