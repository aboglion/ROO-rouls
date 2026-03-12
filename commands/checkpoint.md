---
description: שמור checkpoint — commit + עדכון זיכרון + סיכום
mode: roo-workflow
---

1. `git status --short`
2. אם יש uncommitted:
   `git add . && git commit -m "chore: checkpoint [YYYY-MM-DD HH:MM]"`
3. עדכן memory-bank/project-memory.md:
   - Current State
   - Token Budget (updated timestamp)
   - Decision Log: "checkpoint — [reason if known]"
4. דווח:
   ```
   ✅ Checkpoint נשמר
   📁 [files committed]
   🔋 טוקנים: [used]/[total] ([X]%)
   🔀 Commit: [hash]
   🧠 זיכרון: עודכן
   ```
