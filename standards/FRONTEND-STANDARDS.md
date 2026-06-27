# Frontend standards (JavaScript / TypeScript)

The shipped default is TypeScript. If the welcome wizard hears a different frontend
language or framework, it rewrites this file for that choice on first run; the
structure below stays the same.

## Language
- TypeScript by default, `strict` on. Avoid `any` — model the types.
- Modern ES modules; `const` / `let`, never `var`.
- Small components and pure functions; keep state local until it must be shared.

## Style
- Format with Prettier, lint with ESLint. CI fails on lint errors.
- Names say what they are; no abbreviations that need a decoder.

## Testing (TDD — see `TESTING-STRATEGY.md`)
- Component and unit tests with the team's runner (e.g. Vitest or Jest + Testing
  Library).
- Test what the user sees and does, not internal wiring.
- Accessibility is part of done: semantic HTML, keyboard reachable, labelled controls.

## Done
- Typed, linted, tested, accessible, and reviewed through the QA loop.
