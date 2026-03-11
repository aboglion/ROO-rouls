## Code Quality
- TypeScript strict mode | PEP8 for Python
- camelCase vars, PascalCase classes, UPPER_SNAKE constants
- const by default, never var | ?. and ?? over null checks
- JSDoc on all public functions | Type hints on every Python function
- Max nesting: 4 levels | Max params: 5

## Functions & Files
- Functions: target <80 lines, split only on clear logical boundary
- Files: target <500 lines | Classes: target <400 lines
- Split ONLY if clear logical boundary — never just for line count

## Error Handling
- try/catch ALL async ops — never empty catch blocks
- Log: message + context + stack trace
- Never expose stack traces to client

## Testing (TDD)
- Write test before function | Target 75% coverage
- pytest (Python) / Jest (TypeScript)
- All tests in SCRIPTS/tests/
- 3 cases min: success + edge + failure
- Mock external deps only — never internal modules

## File Structure
- SCRIPTS/tests/ → tests | SCRIPTS/migrations/ → DB migrations
- SCRIPTS/utils/ → one-time scripts (delete after use)
- Group by feature: /users/user.model.ts NOT /models/user.ts
- One class per file always

## SQL
- Migrations always — never edit schema manually
- Parameterized queries always — never string interpolation
- Index foreign keys and filtered columns

## Performance
- No O(n²) without justification
- All I/O async | Cache expensive ops
- Paginate all list endpoints
