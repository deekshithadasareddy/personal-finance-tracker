# Personal Finance Tracker — Workspace

## Overview

A full-stack personal finance tracker web application called "Ledger". Users can track income and expenses, set budgets with alerts, view analytics with charts, and export reports.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (artifacts/finance-tracker)
- **API framework**: Express 5 (artifacts/api-server)
- **Database**: PostgreSQL + Drizzle ORM
- **Authentication**: Clerk (whitelabel)
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Charts**: Recharts
- **Build**: esbuild (CJS bundle)

## Key Features

1. **User Authentication** — Clerk-based sign up/sign in with OAuth support
2. **Transactions** — Add/edit/delete income and expenses with categories
3. **Categories** — Custom expense categories with colors and icons
4. **Budgets** — Monthly budget limits per category with alert thresholds
5. **Analytics** — Monthly trends, category breakdowns, net balance charts
6. **Dashboard** — Financial summary, recent transactions, budget alerts
7. **Export** — CSV export for transactions, PDF via browser print

## Architecture

- `lib/api-spec/openapi.yaml` — API contract (source of truth)
- `lib/api-client-react/` — Generated React Query hooks
- `lib/api-zod/` — Generated Zod validation schemas
- `lib/db/src/schema/` — Database schema (categories, transactions, budgets)
- `artifacts/api-server/src/routes/` — Backend routes
- `artifacts/finance-tracker/src/` — React frontend

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

## Database Tables

- `categories` — User-owned expense categories (name, color, icon)
- `transactions` — Income and expense entries (type, amount, description, category, date, notes)
- `budgets` — Monthly budget limits per category with alert thresholds
