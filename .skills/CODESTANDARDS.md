# CODESTANDARDS — Coding Conventions

Rules for Engineer and QA agents.

## General

- TypeScript strict mode
- No `any` types — define proper interfaces
- No `console.log` in production code
- No commented-out code in final output
- Every file has one responsibility

## Naming

```
Components:    PascalCase     → UserCard.tsx
Utilities:     camelCase      → formatDate.ts
API routes:    kebab-case     → app/api/time-entry/route.ts
Types:         PascalCase     → interface TimeEntry {}
Constants:     UPPER_SNAKE    → MAX_RETRIES
CSS classes:   kebab-case     → .card-header
```

## Files

- One component per file
- Co-locate related files (component + hook + types)
- Barrel exports only for `components/ui/`
- Max file length: 300 lines — split if longer

## Components

```tsx
// Good
export function UserCard({ name, email }: UserCardProps) {
  return (...)
}

// Bad
export default function({ name, email }: any) {
  return (...)
}
```

- Named exports (not default)
- Props interface defined above component
- Destructure props in function signature
- Server Components by default

## API Routes

```tsx
export async function POST(request: Request) {
  const body = schema.parse(await request.json())
  // ... logic
  return Response.json({ success: true })
}
```

- Validate input with Zod
- Return proper HTTP status codes
- Handle errors with try/catch
- No business logic in route — extract to `lib/`

## Database

- All queries through Supabase client
- RLS policies for authorization
- Migrations in raw SQL
- No direct SQL in components

## Error Handling

```tsx
// API
try {
  const result = await doThing()
  return Response.json(result)
} catch (error) {
  return Response.json({ error: "message" }, { status: 500 })
}

// UI
{error && <p className="text-destructive text-sm">{error}</p>}
```

## Don'ts

- No `// TODO` in final code
- No placeholder functions
- No unused imports
- No duplicate code — extract shared logic
- No hardcoded strings for user-facing text
