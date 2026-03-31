# Norfolk Starter

Clean boilerplate for **Norfolk AI** web applications. Clone this repo to start a new project with the full stack pre-configured.

## Tech stack

| Layer | Technology |
|-------|-----------|
| Framework | **Next.js 16** (App Router) + **React 19** + **TypeScript 5** |
| Styling | **Tailwind CSS 4** + **shadcn/ui** (new-york) + **Radix** primitives |
| Database | **Prisma 6** + **PostgreSQL 16** (Neon prod / Docker local) |
| Auth | **Clerk v7** |
| Charts | **Recharts** |
| Validation | **Zod** + **react-hook-form** |
| Icons | **Lucide** |
| Testing | **Vitest** |
| Deployment | **Vercel** + **GitHub Actions** |

## Getting started

```bash
# 1. Clone and rename
git clone https://github.com/ricardocidale/norfolk-starter.git my-new-project
cd my-new-project

# 2. Set up environment
cp .env.example .env
# Edit .env with your Clerk keys and database URL

# 3. Start local Postgres
docker compose up -d

# 4. Install dependencies
npm install

# 5. Run database migrations
npx prisma migrate dev

# 6. Start dev server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Starting a new project from this template

1. Clone the repo and rename the folder
2. Create a new Clerk application at [dashboard.clerk.com](https://dashboard.clerk.com)
3. Create a new Neon database at [console.neon.tech](https://console.neon.tech)
4. Update `.env` with your new keys
5. Add your models to `prisma/schema.prisma`
6. Run `npx prisma migrate dev` to create tables
7. Build your app in `app/(app)/page.tsx` and `app/api/`

## Project structure

```
app/
  layout.tsx               Root layout (ClerkProvider, Geist fonts, dark mode)
  globals.css              Tailwind v4 theme and variables
  (app)/                   Authenticated routes
    layout.tsx             Header with UserButton
    page.tsx               Home page (edit this)
  api/
    health/route.ts        Health check endpoint
  sign-in/                 Clerk sign-in page
  sign-up/                 Clerk sign-up page
components/
  ui/                      shadcn/ui components
lib/
  db.ts                    Prisma client singleton
  utils.ts                 cn() utility
  http/api-response.ts     JSON response helpers
prisma/
  schema.prisma            Database schema
  seed.ts                  Seed data
public/
  logo-*.svg               Norfolk AI brand assets
```

## Scripts

| Command | Purpose |
|---------|---------|
| `npm run dev` | Dev server (Turbopack) |
| `npm run build` | Production build |
| `npm run db:migrate` | Run Prisma migrations |
| `npm run db:studio` | Open Prisma Studio |
| `npm run db:seed` | Seed database |
| `npm run test` | Run Vitest tests |
| `npm run lint` | ESLint |

## Adding shadcn components

```bash
npx shadcn@latest add button
npx shadcn@latest add dialog
npx shadcn@latest add table
```

Components are added to `components/ui/`.

## API conventions

All API routes use a standard JSON envelope:

```typescript
import { jsonOk, jsonErr } from "@/lib/http/api-response";

// Success
return jsonOk({ items }, 200);

// Error
return jsonErr("Not found", 404, "NOT_FOUND");
```

## Documentation

| File | Purpose |
|------|---------|
| **README.md** | This file — setup, structure, conventions |
| **CLAUDE.md** | AI assistant rules and project contracts |
| **.cursorrules** | Cursor-specific AI context |

## Deploy (Vercel)

1. Create a Neon PostgreSQL instance and set `DATABASE_URL` in Vercel
2. Set Clerk keys in Vercel environment variables
3. Push to `main` — Vercel auto-deploys
