# Architecture

## Overview

HospQueue is a terminal-based queue manager built with Ink (React for CLI). The application has a small surface area right now and is designed to grow into a multi-role workflow (receptionist, doctor, admin). The runtime entry point is `source/cli.tsx`, which parses CLI flags and renders `source/app.tsx`.

## Core Flow

- CLI entrypoint uses `meow` to parse input flags.
- The CLI renders the root Ink component with explicit props.
- Rendering must stay pure; side effects belong in hooks.

## Application Boundaries

- UI components live in `source/` and render Ink primitives.
- CLI parsing/validation lives in `source/cli.tsx`.
- Tests live in `test.tsx` using `ink-testing-library`.

## Data + State

- Keep state immutable and localized to components.
- Prefer derived render state over storing duplicates.
- When in doubt, keep state minimal to avoid unnecessary rerenders.

## Error Handling

- Fail fast for CLI errors and invalid flags.
- Use explicit error messages for user-facing failures.

## Extensibility Notes

- Add new CLI flags in `source/cli.tsx` and pass them as props.
- Keep components small and focused on a single responsibility.
