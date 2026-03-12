---
description: רשימת כל הטאסקים עם פירוט מלא כולל retry counters
mode: roo-workflow
---

סרוק tasks/ והצג הכל:

**▶ פעילים (IN-PROGRESS):**
task-[NNN]: [name] | [X/Y] | code_retries=[N] debug_retries=[N]
  [>] בביצוע | [x] הושלם | [ ] ממתין | [!] תקוע

**⏸ ממתינים (PENDING):**
task-[NNN]: [name] | תלוי ב: [deps or "—"]

**✅ הושלמו:**
task-[NNN]: [name] | [date]

**❌ תקועים (loop_halted=true):**
task-[NNN]: [name] | עצר ב: T[N] [sub-task] | גישות שנכשלו: [N]

אם אין טאסקים: "אין טאסקים פעילים — מה תרצה לבנות?"
