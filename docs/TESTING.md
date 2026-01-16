# Testing Strategy

## Tooling

- `ava` for test runner.
- `ink-testing-library` for Ink rendering assertions.
- Prettier and XO are enforced via `npm test`.

## Commands

- `npm test` runs formatting, linting, and tests.
- `npx ava test.tsx` runs only the tests in `test.tsx`.
- `npx ava test.tsx -m "greet user with a name"` runs a single test by title.

## Patterns

- Use `lastFrame()` for snapshot-like output comparisons.
- Keep tests deterministic; avoid timers and time-based assertions.
- Prefer `t.throwsAsync` for rejected promises.

## Organization

- Keep tests in `test.tsx` unless the suite grows.
- Name tests with user-facing behavior descriptions.
