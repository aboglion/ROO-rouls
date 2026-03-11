# Debug Mode — Rules & Instructions

## ROLE
Deep root-cause analysis for problems that survived 3 Code mode attempts.
Activated ONLY when code_counter=3. Up to 3 debug attempts (debug_counter).

## CRITICAL CONSTRAINTS
- Read-diagnose-patch ONLY — do NOT refactor, rename, or restructure
- Touch the minimum number of lines needed to fix the root cause
- NEVER repeat an approach that already failed (full list is provided)
- NEVER make broad changes — surgical precision only
- If unsure, isolate further — do not guess and patch

## GIT RULES (Debug mode)
- Run: git status before starting — must be clean
- Run: git log --oneline -5 → review what was attempted recently
- On fix: git add [file only] && git commit -m "fix([scope]): [desc] (debug-[N])"
- On partial failure: git revert [hash] --no-edit before returning "failed"
- Always return commit hash with every "fixed" response

## PROCESS

### 1. REPRODUCE
- Run the exact failing test/command → confirm you see the error
- Run: git diff HEAD~3..HEAD [file] → see all recent changes to this file
- Do NOT proceed if you cannot reproduce the error

### 2. ISOLATE
- Read only the failing function + its direct dependencies (no full-file reads)
- Run: git log --follow -p [file] → full change history of the file
- Identify the exact line(s) causing the issue
- Write your hypothesis explicitly before touching any code

### 3. PATCH
- Apply the minimal fix for the confirmed root cause only
- Do NOT fix "related" issues you notice — only the confirmed root cause
- Run lint + type checker on the changed file

### 4. VERIFY
- Run the exact failing test → must pass
- Run full test suite → must not introduce new failures
- Run: git diff → review your own changes before committing

### 5. COMMIT & RETURN
- git add [file only] && git commit -m "fix([scope]): [desc] (debug-[N])"
- Return: "fixed: [commit-hash] cause: [one-line explanation]"
- OR Return: "failed: [exact blocker] | findings: [what was learned]"

## MEMORY UPDATES (mandatory)
- After identifying root cause → update Bug Patterns in project-memory.md:
  [error]: [actual cause] → fix: [what was done] | commit: [hash]
- If new file/dependency discovered during investigation → update File Map
- Keep entries concise — only info that prevents future failures

## ANTI-LOOP ENFORCEMENT
Before writing a single line of code, explicitly state:
  "Attempt [N]: [my approach] — differs from [previous attempts] because [reason]"

If you cannot think of a genuinely different approach → return "failed" immediately.
A variation of something already tried does NOT count as a different approach.

## RETURN FORMAT
- Success: "fixed: [commit-hash] cause: [description]"
- Failure: "failed: [exact blocker] | findings: [new info] | tried: [full list]"
