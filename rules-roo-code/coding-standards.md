# Code Mode — Standards & Instructions

## ROLE
Implementation, tests, and static analysis.
You receive a SPEC and a file path. You deliver working, tested, committed code.

## GIT RULES (Code mode)
- Run: git status before starting — must be clean
- On success: git add [changed files only — NEVER git add .]
- git commit -m "[type]([scope]): [description]"
- Return: "done: [commit-hash]" — always include the hash
- On failure: do NOT commit partial work — return error description instead

## CODE QUALITY
- TypeScript: strict mode | Python: PEP8
- camelCase vars | PascalCase classes | UPPER_SNAKE constants
- const by default, never var
- ?. and ?? over manual null checks
- JSDoc on all public functions | Type hints on every Python function
- Max nesting: 4 levels | Max params: 5

## FUNCTIONS & FILES
- Functions: target <80 lines, split only on clear logical boundary
- Files: target <500 lines | Classes: target <400 lines
- Split ONLY if clear logical boundary — never just for line count
- One class per file always

## ERROR HANDLING
- try/catch ALL async ops — never empty catch blocks
- Log: message + context + stack trace (never to client)
- Never expose stack traces or internal errors to client responses

## TESTING (TDD)
- Write test BEFORE writing the function
- Target 75% coverage minimum
- pytest (Python) / Jest (TypeScript)
- All tests in SCRIPTS/tests/
- 3 cases minimum: success + edge + failure
- Mock external deps only — never mock internal modules

## FILE STRUCTURE
- Group by feature: /users/user.model.ts NOT /models/user.ts
- SCRIPTS/tests/ → tests
- SCRIPTS/migrations/ → DB migrations
- SCRIPTS/utils/ → one-time scripts (delete after use)

## SQL
- Migrations always — never edit schema manually
- Parameterized queries always — never string interpolation
- Index foreign keys and frequently filtered columns

## PERFORMANCE
- No O(n²) without written justification
- All I/O async/await — never .then().catch()
- Cache expensive operations
- Paginate all list endpoints

## SELF REVIEW CHECKLIST
Before returning "done", verify:
- [ ] Does output match SPEC exactly?
- [ ] All 3 test cases pass (success + edge + failure)?
- [ ] lint + formatter + type checker: 0 errors, 0 warnings?
- [ ] No logic duplicated from elsewhere?
- [ ] No hardcoded secrets?
- [ ] No dead code or junk left behind?
- [ ] Does this break any existing callers?
- [ ] Are async operations properly awaited?
- [ ] Only the specified file was changed?

## RETURN FORMAT
- Success: "done: [commit-hash]"
- Failure: "error: [exact description] | file: [path] | line: [N] | attempted: [what was tried]"
