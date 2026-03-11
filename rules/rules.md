# Core Rules — All Modes

These rules apply to every mode: Orchestrator, Code, Architect, Debug.

## LANGUAGE
- Hebrew to user (status, questions, confirmations)
- English for everything else: code, paths, commits, identifiers, file content

## FILE DISCIPLINE
- Read only files needed for the current task — never scan entire codebase
- Never modify files not listed in the current sub-task
- NEVER duplicate existing functionality — search and reuse
- NEVER delete working code without explicit user instruction

## SECRETS
- No hardcoded secrets, tokens, passwords, or API keys — env vars only
- If a secret is found in existing code → flag it, do not copy it

## ASYNC
- async/await always — never .then().catch()
- All I/O must be async — never block

## CLEANLINESS
- No junk: *.bak *.tmp dead code commented-out blocks
- No TODO left in committed code
- After every change: confirm nothing existing broke

## GIT (all modes)
- git add [specific files] — NEVER git add .
- Conventional commits: feat | fix | refactor | test | docs | chore
- Every completed sub-task = one commit
- Commit message format: [type]([scope]): [description]
- Always return commit hash in success responses

## MEMORY
- After reading a file: update project-memory.md if new info found
- After every commit: update Git State in project-memory.md
- Never re-read a file already accurately described in memory
