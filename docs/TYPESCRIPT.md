# TypeScript Guidelines

## Compiler + Config

- Base config uses `@sindresorhus/tsconfig`.
- Output targets `dist/` via `tsconfig.json`.

## Module Conventions

- Use ESM imports everywhere.
- Local imports must include `.js` extensions (ex: `./app.js`).
- Group imports: Node/external packages first, then internal modules.

## Types

- Use explicit props types for React components.
- Keep union types readable and narrow; prefer literal unions.
- Avoid `any` unless unavoidable and documented.

## React + Ink

- Use function components only.
- Keep render functions pure; side effects go in hooks.
- Prefer explicit `undefined`/`null` checks for optional values.

## Naming

- Components: `PascalCase`.
- Types: `PascalCase` with `Props` suffix for component props.
- Functions: `camelCase`.
- Constants: `UPPER_SNAKE_CASE` only for truly static values.
