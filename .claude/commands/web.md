# Web Development Patterns

Domain-specific guidance for the `/web` workspace (React frontend + Express backend).

## Frontend (React + TypeScript)

**Component structure:**

```typescript
// Functional components only, no class components
interface IUserCardProps {
  userId: string;
  onSelect: (id: string) => void;
}

export function UserCard({ userId, onSelect }: IUserCardProps) {
  const [user, setUser] = useState<IUser | null>(null);

  useEffect(() => {
    userService.getUser(userId).then(setUser);
  }, [userId]);

  if (!user) return <LoadingSpinner />;
  return <div onClick={() => onSelect(user.id)}>{user.name}</div>;
}
```

**State management:** React Context for global state, `useState`/`useReducer` locally. Use Zustand if complexity grows.

**Data fetching:** Custom hooks wrapping fetch calls. Debounce search inputs (300ms).

**Lazy loading:**

```typescript
const HeavyPage = lazy(() => import('./pages/HeavyPage'));
// Wrap in <Suspense fallback={<Spinner />}> at router level
```

## Backend (Express + TypeScript)

**Route structure:**

```
web/backend/src/
├── routes/         ← Express routers
├── controllers/    ← Request handling logic
├── services/       ← Business logic
├── middleware/     ← auth.ts, validation, error-handler
└── utils/logger.ts ← Pino logger
```

**Middleware stack (global):** Helmet → CORS → rate-limit → body-parser → routes → error-handler

**Controller pattern:**

```typescript
export async function getUser(req: Request, res: Response, next: NextFunction) {
  try {
    const user = await userService.getUserById(req.params.id);
    res.json({ success: true, data: user });
  } catch (error) {
    next(error); // Let error-handler middleware handle it
  }
}
```

## Auth flow

- JWT issued on login, stored in httpOnly cookie or Authorization header
- Verify via `web/backend/src/middleware/auth.ts`
- Refresh tokens for long sessions

## Testing in web workspace

```bash
npm run test -w web               # All tests
npm run test:watch -w web/frontend  # Frontend only, watch
npm run test:watch -w web/backend   # Backend only, watch
```
