# STACK — Project Tech Stack

This file provides project context to all agents. Customize it for your project.

## Stack

- **Frontend:** Next.js 16, React 19, TypeScript, TailwindCSS
- **UI Kit:** shadcn/ui
- **Backend:** Next.js API Routes
- **Database:** Supabase (PostgreSQL + pgvector)
- **Auth:** Supabase Auth
- **Hosting:** Vercel
- **AI:** Vercel AI SDK + OpenAI

## Project Structure

```
├── app/
│   ├── api/           # API routes
│   ├── (auth)/        # Auth pages
│   ├── dashboard/     # Main app
│   └── page.tsx       # Landing
├── components/
│   └── ui/            # shadcn/ui components
├── lib/
│   ├── supabase.ts    # DB client
│   ├── schemas.ts     # Zod schemas
│   └── utils.ts       # Helpers
└── public/
```

## Conventions

- App Router (not Pages Router)
- Server Components by default, `"use client"` only when needed
- API routes in `app/api/[name]/route.ts`
- Zod for all validation
- Supabase RLS for authorization

## Dependencies

```json
{
  "next": "^16",
  "react": "^19",
  "@supabase/supabase-js": "latest",
  "ai": "latest",
  "zod": "latest",
  "zustand": "latest"
}
```

## Environment

```
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
OPENAI_API_KEY=
```
