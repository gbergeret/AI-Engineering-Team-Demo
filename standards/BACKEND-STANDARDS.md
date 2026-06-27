# Backend standards (Python)

The shipped default is Python. If the welcome wizard hears a different backend
language, it rewrites this file for that language on first run; the structure below
stays the same.

## Language
- Python 3.11+. Type hints on public functions; check with mypy or pyright.
- Follow PEP 8; format with Black, lint with Ruff. CI fails on lint errors.
- Small, single-purpose functions; explicit over clever.

## APIs and data
- Validate input at the edge (e.g. Pydantic models); never trust the caller.
- Keep business logic out of the framework layer so it stays testable.
- A migration for every schema change; never edit a migration that has shipped.

## Testing (TDD — see `TESTING-STRATEGY.md`)
- `pytest`; write the failing test first.
- Unit-test logic in isolation; a few integration tests across the API and DB.
- Fixtures over shared mutable state; tests pass in any order.

## Done
- Typed, formatted, linted, tested, and reviewed through the QA loop.
