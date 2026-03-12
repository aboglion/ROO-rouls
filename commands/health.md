---
description: בדיקת בריאות מלאה — lint, types, tests, secrets, junk
mode: roo-workflow
---

<new_task>
<mode>roo-code</mode>
<message>
Run full project health check. Report ALL findings — hide nothing.

1. LINT: run eslint / flake8 / relevant linter — all warnings + errors
2. TYPES: tsc --noEmit / mypy — all issues
3. TESTS: full suite — pass count, fail count, names of ALL failed tests
4. SECRETS: grep -rn "password\|secret\|api_key\|token\|private_key" --include="*.ts" --include="*.py" --include="*.js" --include="*.env*" . | grep -v "node_modules\|.git\|test\|spec\|example"
5. JUNK: find . -name "*.bak" -o -name "*.tmp" -o -name "*.log" | grep -v "node_modules\|.git"
6. DEPS: check for packages with known vulnerabilities (npm audit / pip-audit if available)

Signal: attempt_completion result="healthy: [summary]" OR result="issues: [complete list]"
</message>
</new_task>

דווח:
```
🟢/🔴 Lint:    [result]
🟢/🔴 Types:   [result]
🟢/🔴 Tests:   [X passed | Y failed: name1, name2]
🟢/🔴 Secrets: [clean | found at file:line]
🟢/🔴 Junk:    [none | list]
🟢/🔴 Deps:    [clean | N vulnerabilities]
```
