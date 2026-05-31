# Web Applications

Dedicated directory for web-based projects including frontend applications, web services, and progressive web apps.

## Project Structure

```
web/
├── frontend/                   # Client-side application
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── pages/            # Page components
│   │   ├── hooks/            # Custom React/Vue hooks
│   │   ├── services/         # API clients, services
│   │   ├── store/            # State management
│   │   ├── styles/           # Global styles
│   │   ├── types/            # TypeScript interfaces
│   │   ├── utils/            # Utility functions
│   │   └── index.ts/tsx      # Entry point
│   ├── public/               # Static assets
│   ├── tests/                # Test files
│   ├── package.json
│   ├── tsconfig.json
│   └── README.md
│
├── backend/                   # Server-side application
│   ├── src/
│   │   ├── api/
│   │   │   ├── routes/       # API endpoints
│   │   │   ├── controllers/  # Request handlers
│   │   │   └── middleware/   # Express/Koa middleware
│   │   ├── services/         # Business logic
│   │   ├── models/           # Data models
│   │   ├── database/         # Database configuration
│   │   ├── config/           # App configuration
│   │   ├── types/            # TypeScript interfaces
│   │   ├── utils/            # Utility functions
│   │   └── index.ts          # Server entry point
│   ├── tests/
│   ├── package.json
│   ├── tsconfig.json
│   └── README.md
│
└── shared/                    # Code shared between frontend and backend
    ├── types/                # Shared TypeScript types
    ├── constants/            # Shared constants
    ├── utils/                # Shared utilities
    └── package.json
```

## Technology Recommendations

### Frontend Framework

#### React
```bash
# Setup
npx create-react-app web/frontend --template typescript

# Key Libraries
- React Router for navigation
- Axios or Fetch API for HTTP
- Zustand or Redux for state management
- Tailwind CSS for styling
- Jest & React Testing Library for testing
```

#### Vue 3
```bash
# Setup
npm create vite@latest web/frontend -- --template vue-ts

# Key Libraries
- Vue Router for navigation
- Axios for HTTP
- Pinia for state management
- Tailwind CSS for styling
- Vitest for testing
```

#### Svelte
```bash
# Setup
npm create vite@latest web/frontend -- --template svelte-ts

# Key Libraries
- SvelteKit for routing and SSR
- Axios for HTTP
- Svelte stores for state
- Tailwind CSS for styling
```

### Backend Framework

#### Express.js + TypeScript
```bash
# Setup
npm init -y && npm install express typescript @types/express

# Project Structure
- Use middleware for error handling
- Separate routes and controllers
- Service layer for business logic
- Error handling middleware
```

#### NestJS
```bash
# Setup
npm i -g @nestjs/cli
nest new web/backend

# Features
- Decorators for routes and middleware
- Dependency injection out of box
- Built-in testing utilities
- Type-safe controllers
```

#### FastAPI (Python)
```bash
# Setup
pip install fastapi uvicorn

# Features
- Automatic API documentation
- Type hints for validation
- Async/await support
- Built-in security features
```

## Common Patterns

### API Communication

```typescript
// src/services/api-client.ts
import axios, { AxiosInstance, AxiosError } from 'axios';

class ApiClient {
  private client: AxiosInstance;

  constructor(baseURL: string) {
    this.client = axios.create({
      baseURL,
      headers: {
        'Content-Type': 'application/json'
      }
    });

    this.setupInterceptors();
  }

  private setupInterceptors(): void {
    this.client.interceptors.response.use(
      response => response,
      (error: AxiosError) => this.handleError(error)
    );
  }

  private handleError(error: AxiosError): Promise<never> {
    // Log error, redirect, refresh token, etc.
    return Promise.reject(error);
  }

  async get<T>(url: string): Promise<T> {
    const response = await this.client.get<T>(url);
    return response.data;
  }

  async post<T>(url: string, data: unknown): Promise<T> {
    const response = await this.client.post<T>(url, data);
    return response.data;
  }
}
```

### Authentication Flow

```typescript
// Backend: Token generation
async registerUser(email: string, password: string) {
  const hashedPassword = await hashPassword(password);
  const user = await userRepository.create({ email, password: hashedPassword });
  
  const token = generateToken({ userId: user.id });
  return { user, token };
}

// Frontend: Token storage and usage
function useAuth() {
  const [token, setToken] = useState<string | null>(
    localStorage.getItem('auth_token')
  );

  const login = async (email: string, password: string) => {
    const { token } = await apiClient.post('/auth/login', { email, password });
    localStorage.setItem('auth_token', token);
    setToken(token);
  };

  return { token, login };
}
```

### State Management (Zustand)

```typescript
// src/store/user-store.ts
import create from 'zustand';

interface IUserState {
  user: IUser | null;
  isLoading: boolean;
  error: string | null;
  setUser: (user: IUser | null) => void;
  setLoading: (loading: boolean) => void;
  fetchUser: (id: string) => Promise<void>;
}

export const useUserStore = create<IUserState>((set) => ({
  user: null,
  isLoading: false,
  error: null,
  
  setUser: (user) => set({ user }),
  setLoading: (isLoading) => set({ isLoading }),
  
  fetchUser: async (id) => {
    set({ isLoading: true });
    try {
      const user = await apiClient.get(`/users/${id}`);
      set({ user, error: null });
    } catch (error) {
      set({ error: (error as Error).message });
    } finally {
      set({ isLoading: false });
    }
  }
}));
```

## Getting Started

1. Choose your frontend framework (React/Vue/Svelte)
2. Choose your backend framework (Express/NestJS/FastAPI)
3. Read [.github/copilot-instructions.md](../.github/copilot-instructions.md)
4. Review [.github/prompts/](../.github/prompts/) for development guides
5. Set up development environment:
   ```bash
   cd web/frontend && npm install
   cd ../backend && npm install
   ```
6. Start development:
   ```bash
   # Terminal 1: Frontend
   npm run dev

   # Terminal 2: Backend
   npm run dev
   ```

## Testing

```bash
# Frontend
npm run test              # Run tests
npm run test:coverage    # Generate coverage report

# Backend
npm run test              # Run tests
npm run test:coverage    # Generate coverage report
```

## Deployment

- **Frontend**: Netlify, Vercel, GitHub Pages, AWS S3
- **Backend**: Heroku, AWS EC2, DigitalOcean, Render
- **Database**: PostgreSQL (RDS), MongoDB Atlas, Supabase

---

**Last Updated**: 2026  
**Version**: 1.0
