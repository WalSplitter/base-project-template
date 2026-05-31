# Prompt: API & Integration Design - Vibe Coding

Use this prompt template when designing APIs and integrations with GitHub Copilot.

## Template

```
API Specification:
Endpoint: [METHOD] /api/[RESOURCE]/[ACTION]
Purpose: [WHAT_DOES_IT_DO]
Use case: [WHEN_IS_IT_USED]

Request:
- Method: [GET/POST/PUT/DELETE/PATCH]
- Path: [/api/path/with/:params]
- Query params: [OPTIONAL_FILTERS]
- Body schema:
  ```
  [REQUEST_SCHEMA]
  ```
- Authentication: [TYPE/REQUIRED]
- Rate limiting: [IF_APPLICABLE]

Response:
- Success (200): [RESPONSE_SCHEMA]
- Error cases:
  - [ERROR_CODE]: [ERROR_CONDITION]
  - [ERROR_CODE]: [ERROR_CONDITION]

Implementation requirements:
- Input validation: [VALIDATION_RULES]
- Authorization: [PERMISSION_CHECKS]
- Database operations: [QUERIES_NEEDED]
- External integrations: [IF_ANY]
- Caching: [IF_APPLICABLE]

Deliverables:
1. Route/endpoint handler with full error handling
2. Request/response types with JSDoc
3. Unit tests for success and error cases
4. Integration tests with external services
5. API documentation (OpenAPI/Swagger)
```

## Example Usage

```
API Specification:
Endpoint: POST /api/users/register
Purpose: Create new user account with email and password
Use case: User self-registration flow

Request:
- Method: POST
- Path: /api/users/register
- Body schema:
  {
    email: string (email format, required)
    password: string (min 8 chars, required)
    name: string (1-100 chars, required)
  }
- Authentication: None (public endpoint)
- Rate limiting: 5 requests per 10 minutes per IP

Response:
- Success (201): 
  {
    userId: string (UUID)
    email: string
    name: string
    createdAt: ISO8601 timestamp
  }
- Error cases:
  - 400: Invalid email format or password too weak
  - 409: Email already registered
  - 429: Rate limit exceeded
  - 500: Internal server error

Implementation requirements:
- Input validation: Email format, password strength, name length
- Authorization: None required
- Database operations: Check email uniqueness, hash password, insert user
- External integrations: Send verification email
- Caching: Cache email domain validation

Deliverables:
1. UserController.register() handler
2. IUserRegistrationRequest, IUserRegistrationResponse types
3. Unit tests for all validation scenarios
4. Integration test with email service mock
5. OpenAPI spec entry
```

## REST API Best Practices

### URL Design
```
✓ /api/v1/users                    # Resource collection
✓ /api/v1/users/:id               # Resource by ID
✓ /api/v1/users/:id/posts         # Related resources
✓ /api/v1/users?role=admin        # Query filters
✓ /api/v1/users?skip=10&take=20   # Pagination
✗ /api/getUsers                    # Avoid verb names
✗ /api/user-get-by-id              # Avoid method names
```

### HTTP Methods
```typescript
POST   /api/resource          // Create
GET    /api/resource          // List
GET    /api/resource/:id      // Retrieve single
PUT    /api/resource/:id      // Replace entire
PATCH  /api/resource/:id      // Partial update
DELETE /api/resource/:id      // Delete
```

### Status Codes
```
2xx Success
  200 OK              - GET, PUT, PATCH, DELETE successful
  201 Created         - POST successful, new resource created
  204 No Content      - Successful with no response body

4xx Client Error
  400 Bad Request     - Invalid input
  401 Unauthorized    - Authentication required
  403 Forbidden       - Authenticated but not authorized
  404 Not Found       - Resource doesn't exist
  409 Conflict        - Resource conflict (duplicate email, etc.)
  429 Too Many Requests - Rate limited

5xx Server Error
  500 Internal Server Error
  503 Service Unavailable
```

### Error Response Format
```typescript
interface IErrorResponse {
  error: {
    code: string;           // Machine-readable error code
    message: string;        // Human-readable message
    details?: {            // Optional detailed information
      [key: string]: unknown;
    };
    timestamp: string;      // ISO8601 timestamp
  };
}

// Example
{
  error: {
    code: 'VALIDATION_ERROR',
    message: 'Validation failed',
    details: {
      field: 'email',
      reason: 'Invalid email format'
    },
    timestamp: '2026-05-31T12:00:00Z'
  }
}
```

## GraphQL Integration

```typescript
// Type definition
type User {
  id: ID!
  email: String!
  name: String!
  createdAt: DateTime!
  posts: [Post!]!
}

// Query
query GetUser($id: ID!) {
  user(id: $id) {
    id
    email
    name
    posts {
      id
      title
    }
  }
}

// Resolver with proper error handling
const userResolver = {
  async user(parent: unknown, args: { id: string }) {
    try {
      const user = await userService.getUserById(args.id);
      if (!user) throw new NotFoundError('User', args.id);
      return user;
    } catch (error) {
      logger.error('GraphQL user query error:', error);
      throw new ApolloError('Failed to fetch user');
    }
  }
};
```
