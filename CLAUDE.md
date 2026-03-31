---
description:
alwaysApply: true
---

# Norfolk Starter — Project Context for Cursor / Claude Code

> READ THIS BEFORE MAKING ANY CHANGES.

---

## WHAT THIS IS

A **clean boilerplate** for Norfolk AI web applications. Clone and rename for each new project.

---

## TECH STACK

| Layer | Technology |
|-------|-----------|
| Runtime | Node.js >=20 |
| Framework | Next.js 16 (App Router), Turbopack |
| Language | TypeScript 5 (strict) |
| UI | React 19 |
| Styling | Tailwind CSS v4 + shadcn/ui (new-york) + Radix |
| Charts | Recharts |
| Validation | Zod + react-hook-form |
| ORM / DB | Prisma 6 + PostgreSQL 16 |
| Auth | Clerk v7 (@clerk/nextjs) |
| Icons | Lucide |
| Testing | Vitest |
| Deployment | Vercel + GitHub Actions |

---

## FILE STRUCTURE

```
app/
  layout.tsx               ← ROOT layout with <ClerkProvider>
  globals.css              ← Tailwind v4 imports + theme
  (app)/
    layout.tsx             ← Authenticated shell (header + UserButton)
    page.tsx               ← Home page
  api/
    health/route.ts        ← Health check endpoint
  sign-in/[[...sign-in]]/  ← Clerk sign-in
  sign-up/[[...sign-up]]/  ← Clerk sign-up
components/
  ui/                      ← shadcn primitives
lib/
  db.ts                    ← Prisma client singleton
  utils.ts                 ← cn() utility
  http/api-response.ts     ← jsonOk / jsonErr helpers
prisma/
  schema.prisma            ← Database schema (add your models here)
  seed.ts                  ← Seed data
public/
  logo-*.svg               ← Norfolk AI brand logos
middleware.ts              ← Clerk auth middleware
docker-compose.yml         ← Local Postgres
.env.example               ← Environment variable template
```

---

## AUTHENTICATION — DO NOT MODIFY

- `middleware.ts` at PROJECT ROOT
- Uses `clerkMiddleware` + `createRouteMatcher`
- Public routes: `/sign-in`, `/sign-up`, `/sso-callback`
- `ClerkProvider` wraps app in `app/layout.tsx`
- `UserButton` in `app/(app)/layout.tsx` header

---

## DATABASE

- **Local dev:** Docker Postgres via `docker-compose.yml`
- **Production:** Neon PostgreSQL (pooled `DATABASE_URL` on Vercel)
- Prisma Client generated to `lib/generated/prisma` (gitignored)
- `tsconfig.json` maps `@prisma/client` to that folder
- `postinstall` runs `prisma generate`

---

## API CONVENTIONS

- JSON envelope: `{ ok: true, data }` on success
- Errors: `{ ok: false, error: { message, code?, details? } }`
- Helpers: `jsonOk()` / `jsonErr()` from `lib/http/api-response.ts`

---

## BRAND

- **Colors:** Navy `#1E2D45`, Teal `#0097A7`, Cyan `#00BCD4`, Gold `#FFC107`
- **Theme:** Dark mode by default
- **Font:** Geist (sans + mono)
- **Logos:** `/public/logo-*.svg`

---

## DEPLOYMENT

- Push to `main` → Vercel auto-deploys
- GitHub Actions workflow in `.github/workflows/vercel-deploy.yml`
- Custom domain configured on Vercel + DNS on GoDaddy (norfolk.ai)

---

## SCRIPTS

```bash
npm run dev          # Local dev (Turbopack)
npm run build        # Production build
npm run db:migrate   # Prisma migrations
npm run db:studio    # Prisma Studio GUI
npm run db:seed      # Seed database
npm run test         # Run tests
npm run lint         # ESLint
```

---

## RULES FOR AI ASSISTANTS

1. **NEVER** change `middleware.ts` without explicit permission
2. **NEVER** change `DATABASE_URL` or run migrations without permission
3. **NEVER** modify `app/layout.tsx` ClerkProvider wrapper
4. **NEVER** hardcode secrets or API keys
5. **ALWAYS** use `next/image` with `unoptimized` for SVG files
6. **ASK** before installing new packages
7. **ASK** before changing auth, database, or deployment config
8. **COMMIT** only when explicitly asked
9. Docker Postgres for local dev is valid — localhost is not broken
10. Keep files under ~500 lines — split by concern when growing

---

## AGENT SKILLS

Skills live in `.agents/skills/<name>/SKILL.md` (Cursor) and `.claude/skills/<name>/SKILL.md` (Claude Code).
When editing a skill, update BOTH to identical content. Keep skills compact (<120 lines).
