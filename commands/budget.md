---
description: תקציב טוקנים — הצג / אפס
argument-hint: [reset <number>]
mode: roo-workflow
---

קרא Token Budget מ-memory-bank/project-memory.md:

```
🔋 תקציב טוקנים
────────────────────────────────
כולל:   [total]
שנוצל:  [used] ([X]%)
נותרו:  [remaining]
עודכן:  [timestamp]

[progress bar 30 chars]

```

אזהרות אוטומטיות:
≥80% → ⚠️  תקציב נמוך — שקול /checkpoint
≥95% → ⛔ קרוב לגמר — checkpoint מיידי מומלץ

אם ארגומנט "reset [N]":
  עדכן ב-memory: total=[N], used=0, remaining=[N], updated=[now]
  ✅ תקציב אופס ל-[N] טוקנים
