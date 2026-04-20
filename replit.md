# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Artifacts

### WORLDVIEW (`artifacts/worldview`)
- Real-time tactical geospatial intelligence interface
- Map engine: MapLibre GL JS with CARTO Dark Matter basemap
- Flight data: ADS-B via adsb.lol (military + public aviation)
- Features: live aircraft markers, heading rotation, click-to-inspect panel, 10s auto-refresh
- CORS-safe: adsb.lol is proxied via Express API routes (`/api/proxy/adsb/mil`, `/api/proxy/adsb/global`)
- Note: MapLibre requires WebGL — works in deployed/real browsers; Replit preview sandbox lacks GPU acceleration

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
