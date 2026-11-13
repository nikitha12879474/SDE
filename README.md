# Shared Bill Splitter

A TypeScript full-stack shared-home bill splitter built for the DoCoDeGo SDE intern assignment.

## Stack
- API: Hono on Cloudflare Workers
- Database: Cloudflare D1 (SQLite)
- Web: React, Vite, TanStack Router
- Tests: Vitest

## Features
- Create homes and add members
- Split bills in integer cents, assigning remainder cents by member creation order
- Idempotent share payments protected by SQLite uniqueness and conditional updates
- Outstanding balances per member
- Responsive UI with loading, empty, and error states

## Run
Install dependencies with `pnpm install`, then run `pnpm dev`.

## Validation
Run `pnpm check`, `pnpm typecheck`, `pnpm test`, and `pnpm build`.

## Decisions
1. Store money as integer cents to avoid floating-point rounding errors.
2. Use database constraints and conditional updates to protect invariants under concurrent requests.
3. Use an idempotency key per share payment so retries return the original result without charging twice.

## AI use
ChatGPT was used for implementation assistance. The author should review and understand every submitted line before recording the walkthrough.
