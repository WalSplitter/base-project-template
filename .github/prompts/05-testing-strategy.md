# Prompt: Testing Strategy - Vibe Coding

Use this prompt template when writing tests with GitHub Copilot.

## Template

```
Test Context:
Module: [MODULE_NAME]
Function: [FUNCTION_NAME]
File: [FILE_PATH]

What to Test:
- Happy path: [SUCCESSFUL_SCENARIO]
- Edge cases: [BOUNDARY_CONDITIONS]
- Error scenarios: [EXCEPTION_CASES]
- Integration: [EXTERNAL_DEPENDENCIES]

Test Requirements:
- Framework: [JEST/VITEST/MOCHA]
- Type: Unit / Integration / E2E
- Mock targets: [SERVICES/APIS/DATABASE]
- Coverage goal: [PERCENTAGE]
- Performance requirements: [IF_ANY]

Test Cases:
1. [TEST_NAME]
   - Setup: [PREREQUISITES]
   - Act: [FUNCTION_CALL]
   - Assert: [EXPECTED_RESULT]

2. [TEST_NAME]
   - Setup: [PREREQUISITES]
   - Act: [FUNCTION_CALL]
   - Assert: [EXPECTED_RESULT]

Deliverables:
1. Complete test file with all scenarios
2. Mock/fixture setup
3. Assertion coverage > [PERCENTAGE]%
4. Performance benchmarks (if applicable)
```

## Example Usage

```
Test Context:
Module: UserService
Function: getUserProfile
File: src/services/user-service.test.ts

What to Test:
- Happy path: User exists, return profile
- Edge cases: User with no profile data, deleted user reference
- Error scenarios: Database down, user not found, auth failure
- Integration: Database query, caching layer

Test Requirements:
- Framework: Jest
- Type: Unit + Integration
- Mock targets: UserRepository, CacheService
- Coverage goal: 90%
- Performance requirements: Each test < 100ms

Test Cases:
1. Should return user profile when user exists
   - Setup: Mock repository returns valid user
   - Act: userService.getUserProfile('user-123')
   - Assert: Returns correct profile data

2. Should throw NotFoundError when user does not exist
   - Setup: Mock repository returns null
   - Act: userService.getUserProfile('invalid-id')
   - Assert: Throws NotFoundError

3. Should cache result on second call
   - Setup: Mock repository, spy on cache
   - Act: Call getUserProfile twice
   - Assert: Repository called once, cache hit on second call

Deliverables:
1. user-service.test.ts with all test cases
2. Mock fixtures for User and database
3. Coverage report showing 90%+
4. Performance baseline (100ms target met)
```

## Testing Patterns

### AAA Pattern (Arrange-Act-Assert)

```typescript
describe('UserService', () => {
  describe('getUserProfile', () => {
    it('should return user profile when user exists', async () => {
      // Arrange
      const userId = 'user-123';
      const expectedUser: IUserProfile = {
        id: userId,
        email: 'john@example.com',
        name: 'John Doe',
        createdAt: new Date('2026-01-01')
      };
      userRepository.findById = jest.fn().mockResolvedValue(expectedUser);

      // Act
      const result = await userService.getUserProfile(userId);

      // Assert
      expect(result).toEqual(expectedUser);
      expect(userRepository.findById).toHaveBeenCalledWith(userId);
    });
  });
});
```

### Mocking External Dependencies

```typescript
describe('PaymentService', () => {
  let paymentService: PaymentService;
  let mockStripeApi: jest.Mocked<IStripeAPI>;
  let mockEmailService: jest.Mocked<IEmailService>;

  beforeEach(() => {
    mockStripeApi = {
      charge: jest.fn(),
      refund: jest.fn()
    } as jest.Mocked<IStripeAPI>;

    mockEmailService = {
      sendReceipt: jest.fn().mockResolvedValue(undefined)
    } as jest.Mocked<IEmailService>;

    paymentService = new PaymentService(mockStripeApi, mockEmailService);
  });

  it('should charge card and send receipt email', async () => {
    mockStripeApi.charge.mockResolvedValue({ transactionId: 'txn-123' });

    await paymentService.processPayment(100, 'user@example.com');

    expect(mockStripeApi.charge).toHaveBeenCalledWith(100);
    expect(mockEmailService.sendReceipt).toHaveBeenCalledWith('user@example.com', expect.any(String));
  });
});
```

### Testing Error Scenarios

```typescript
describe('UserValidator', () => {
  it('should throw ValidationError for invalid email', () => {
    expect(() => {
      userValidator.validateEmail('invalid-email');
    }).toThrow(ValidationError);

    expect(() => {
      userValidator.validateEmail('invalid-email');
    }).toThrow('Invalid email format');
  });

  it('should throw ValidationError with detailed info', () => {
    try {
      userValidator.validateEmail('invalid-email');
      fail('Should have thrown error');
    } catch (error) {
      expect(error).toBeInstanceOf(ValidationError);
      expect(error.field).toBe('email');
    }
  });
});
```

### Integration Testing

```typescript
describe('UserService Integration', () => {
  let db: Database;
  let userService: UserService;

  beforeAll(async () => {
    db = new Database(':memory:');
    await db.initialize();
    userService = new UserService(new UserRepository(db));
  });

  afterEach(async () => {
    await db.clear();
  });

  it('should persist and retrieve user correctly', async () => {
    const userData = { email: 'test@example.com', name: 'Test User' };
    
    const user = await userService.registerUser(userData);
    const retrieved = await userService.getUserProfile(user.id);

    expect(retrieved).toMatchObject(userData);
  });
});
```

### Testing Async Operations

```typescript
describe('AsyncOperations', () => {
  it('should handle promise resolution', async () => {
    const result = await userService.fetchUser('user-123');
    expect(result).toBeDefined();
  });

  it('should timeout after specified duration', async () => {
    jest.useFakeTimers();
    
    const promise = userService.fetchWithTimeout('url', 1000);
    jest.advanceTimersByTime(1001);

    await expect(promise).rejects.toThrow(TimeoutError);
  });

  it('should retry on failure', async () => {
    const spy = jest.fn()
      .mockRejectedValueOnce(new Error('Network error'))
      .mockResolvedValueOnce({ id: 'user-123' });

    const result = await withRetry(() => spy());

    expect(spy).toHaveBeenCalledTimes(2);
    expect(result).toEqual({ id: 'user-123' });
  });
});
```

## Test Coverage Targets

```
Critical Path (Business Logic):    80%+ coverage
Common Utilities:                   85%+ coverage
API Handlers:                       70%+ coverage
Infrastructure Code:                50%+ coverage
Generated Code:                     0% (skip)
```
