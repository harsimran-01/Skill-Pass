# SkillPass

SkillPass is a digital skill passport prototype that helps students prove competencies and helps recruiters verify and match candidates.

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

- `artifacts/skillpass/src/App.tsx` — routed React prototype, demo data, localStorage persistence, and product interactions
- `artifacts/skillpass/src/index.css` — SkillPass visual system and responsive styling
- `artifacts/skillpass/src/pages/not-found.tsx` — fallback route

## Architecture decisions

- The first build is frontend-only because the project brief calls for a college prototype, not production infrastructure.
- Demo data is seeded in the client and persisted through localStorage so the assessment and evidence flows survive refreshes.
- The public verification flow is intentionally separate from the signed-in-style workspace shell to make the recruiter story easy to demonstrate.

## Product

The prototype includes a landing page, student dashboard, digital passport, timed Java assessment, public passport verification, recruiter search, role matching, evidence vault, notifications, and settings. It follows the demo story from adding proof to recruiter verification.

## User preferences

No additional preferences recorded.

## Gotchas

- This prototype expects browser localStorage; clearing site data resets the demo state.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
