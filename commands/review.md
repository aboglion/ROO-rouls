---
description: שלח קובץ לסקירת roo-architect
argument-hint: <file-path> [spec description]
mode: roo-workflow
---

<new_task>
<mode>roo-architect</mode>
<message>
Review file: $ARGUMENTS

Check ALL:
- Spec contract / logic correctness / edge cases
- No duplicates, no dead code, no secrets, no junk
- SOLID: Single Responsibility, Open/Closed, Dependency Inversion
- Security: inputs validated, errors not exposed to client, no SQL injection surface
- Performance: no O(n²), all I/O async, lists paginated
- Async safety: all async in try/catch, no unhandled rejections
- Test coverage: happy path, edge case, error path

Signal: attempt_completion result="clean"
        OR result="issue: [problem] in [file]:[line] — [what must change]"
</message>
</new_task>

דווח בעברית: תוצאת הסקירה עם פירוט כל ממצא.
