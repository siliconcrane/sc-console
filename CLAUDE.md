# CLAUDE.md - SC Console

This file provides guidance for Claude Code agents working in this repository.

## About This Repository

SC Console is the development hub for Silicon Crane (SC). It contains:

- **apps/sc-web/** - Astro 5 frontend with Tailwind CSS
- **workers/** - Cloudflare Workers for backend services
  - `sc-api/` - Main API worker
  - `sc-maintenance/` - Maintenance/admin worker
- **docs/** - Technical documentation
- **scripts/** - Automation scripts

## Session Start

Always run `/sod` at the start of every session to:

- Create session in Context Worker
- Download current documentation
- Establish session context for handoffs

## Build Commands

### Frontend (sc-web)

```bash
cd apps/sc-web
npm install             # Install dependencies
npm run dev             # Local dev server
npm run build           # Production build
npm run preview         # Preview production build
```

### Workers

```bash
cd workers/sc-api       # or sc-maintenance
npm install             # Install dependencies
npx wrangler dev        # Local dev server
npx wrangler deploy     # Deploy to Cloudflare
npx tsc --noEmit        # TypeScript validation
```

## Tech Stack

| Layer    | Technology                     |
| -------- | ------------------------------ |
| Frontend | Astro 5, Tailwind CSS          |
| Hosting  | Cloudflare (via Astro adapter) |
| Backend  | Cloudflare Workers (Hono)      |
| Database | Cloudflare D1                  |

## Key Files

- `apps/sc-web/src/` - Astro pages and components
- `workers/sc-api/src/index.ts` - API routes
- `docs/technical/sc-technical-spec.md` - Technical specification

## Security Requirements

- Never commit secrets to the repository
- Use environment variables for credentials
- Validate all input at API boundaries
- Use parameterized queries for D1 (always `.bind()`)

## Related Documentation

Venture-specific instructions are served by crane-context via `/sod`.
See `docs/process/` for process documentation.
