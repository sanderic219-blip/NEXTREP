# NEXTREP

NEXTREP helps athletes train, measure improvement, compete, and build recruiting visibility.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/nextrep/` — React athlete app and visual system
- `artifacts/api-server/src/routes/nextrep.ts` — athlete, training, coach, and competition API
- `lib/api-spec/openapi.yaml` — API contract and generated-client source of truth
- `lib/db/src/schema/nextrep.ts` — athlete, training, workout, and coach-message data

## Architecture decisions

- The first product slice is athlete-first; coach, parent, organization, and recruiter workspaces are later role-specific phases.
- REP Score rewards training consistency and verified improvement rather than popularity.
- The current coach endpoint is deterministic and schedule-aware; a later phase can replace it with a managed AI model without changing the client contract.

## Product

- Daily athlete dashboard with REP Score, streak, XP, schedule, weekly goal, and training recommendation
- Personalized drill feed with persistent like, save, and add-to-workout actions
- Coach conversation, performance progress, challenges, leaderboard, editable athlete profile, and recruiting card
- Athlete sign-in and account-specific dashboard customization, private wallpaper/photo uploads, and saved Daily Mindset messages

## Visual direction

- Default palette: baby blue (#89CFF0), white, and black. No orange in default branding or highlights.
- Keep sign-in copy simple and natural. Dashboard customization supports any user-selected accent color.
- Use the supplied dark sports-dashboard reference for the hero and lower-left Daily Mindset area without replacing existing product pages.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
