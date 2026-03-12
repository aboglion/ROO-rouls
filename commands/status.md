---
description: מצב נוכחי — פרויקט, טאסקים, תקציב טוקנים, git
mode: roo-workflow
---

בצע ודווח בעברית:

1. קרא memory-bank/project-memory.md
2. סרוק tasks/ — כל קבצים
3. הרץ: `git log --oneline -5`
4. הרץ: `git status --short`

```
📦 פרויקט: [name] | [state]
🔋 טוקנים: [used]/[total] ([X]%) נותרו: [remaining]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📋 פעילים:
  ▶ task-[NNN]: [name] | [X/Y] sub-tasks | Priority: [P]

✅ הושלמו: [count] tasks

❌ תקועים: [count] tasks (loop_halted)

🔀 Git:
  [5 commits]
  uncommitted: [files or "נקי"]
```
