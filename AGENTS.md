## AGENTS.md

Agent-facing documentation for the project. **Keep this file updated** on architectural changes.

## Docs Structure

```
AGENTS.md           ← This file (overview)
docs/ADR/           ← Decision records
docs/ARCH.md        ← Architecture details
docs/INK_DOCS.md    ← Ink reference notes
docs/NODE_NATIVE_FETCH_USAGE.md ← Native fetch guidance
docs/TESTING.md     ← Test strategy
docs/TYPESCRIPT.md  ← Strict TS guidelines
```

## Project Overview

HospQueue is a terminal-based queue manager. It targets small hospitals and clinics to efficiently manage patient flow and reduce waiting room chaos. It replaces traditional paper tickets and manual whiteboards with a simple, real-time digital queue system that tracks patients from registration to discharge. Staff log in securely with role-based access—receptionists handle registrations, doctors manage consultations, and admins oversee everything—ensuring smooth coordination while maintaining clear separation of responsibilities.

## MVP: App Base Features - Remove this section after implementing

The app's core features include fast patient registration with auto-generated ticket numbers and adjustable priority levels (low, medium, high) to handle urgent cases first. A central live queue view displays waiting patients sorted by priority and arrival time, showing key details like ticket number, name, wait time, and assigned doctor. Receptionists can call the next patient, assign doctors, or update statuses (waiting, consulting, discharged), while doctors see their assigned patients and can add notes or mark consultations complete. A dedicated full-screen display mode turns any monitor into a waiting room board, showing the current queue, a large clock, and gentle notifications when patients are called—all updating automatically to keep everyone informed and minimize confusion.

## Tech Stack Notes

- Prisma ORM with the `@prisma/adapter-better-sqlite3` SQLite driver adapter is the standard database setup for local development.

## Ink TUI Reminder

- This is a TUI application built with Ink (React for CLI), not a web app.
- React components render to the terminal via Ink primitives, not DOM elements.
- Do not assume browsers, HTML, or CSS; treat UI as terminal output.

## Setup Notes

- Node.js >= 22 is required.
- `npm install` installs dependencies; output ships via `dist/`.
- `source/` holds TypeScript and JSX (Ink + React).

## Commands

- `npm run build` compiles TypeScript to `dist/`.
- `npm run dev` runs TypeScript in watch mode.
- `npm test` runs Prettier checks, XO lint, and AVA tests.

### Running a single test

- `npx ava test.tsx -m "greet user with a name"` runs one test by title.
- `npx ava test.tsx` runs only the tests in `test.tsx`.

## Code Style

- TypeScript only; adhere to `@sindresorhus/tsconfig` defaults.
- Use React function components with explicit props typing.
- Prefer named exports for utilities and default exports for components.
- Keep imports grouped: Node/external packages, then internal modules.
- Use `.js` extension in local ESM imports (ex: `./app.js`).
- Keep Ink UI pure; avoid side effects during render.
- Use explicit `undefined` or `null` checks before rendering optional values.
- Favor immutable updates for state/collections.

### Formatting

- Prettier is enforced via `npm test`.
- Use tabs (see existing files).
- Keep JSX compact; avoid unnecessary fragments.

### Naming

- Files: `kebab-case` for folders, `camelCase` for functions.
- Components: `PascalCase`.
- Types: `PascalCase`, `Props` suffix for props types.
- Constants: `UPPER_SNAKE_CASE` only for truly static values.

### Error Handling

- Validate CLI input in `source/cli.tsx` using `meow`.
- Prefer `t.throwsAsync` in AVA for rejected promises.
- Fail fast with clear error messages for user-facing CLI issues.

## Testing

- Tests live in `test.tsx` and use `ava` + `ink-testing-library`.
- Snapshot-like output comparisons should rely on `lastFrame()`.
- Keep tests deterministic; avoid time-based assertions.

## Commits

- Use Conventional Commits for commit messages.

## Dates

**Don't assume current year** (training cutoff issue). Run `date "+%Y-%m-%d"` if date unknown.
