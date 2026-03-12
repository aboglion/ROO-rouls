---
description: הצג תוכנית קיימת או הפעל Planner על task חדש
argument-hint: [<task-number> | new "<task description>"]
mode: roo-workflow
---

ללא ארגומנט:
  סרוק tasks/ לקבצים PENDING/IN-PROGRESS
  הצג כל sub-task בפירוט:
  ```
  📋 task-[NNN]: [name]
  Status: [status] | [X/Y] | Priority: [P]
  Sub-tasks:
    [>/<x>/[ ]/[!]] T[N] | [🟢/🟡/🔴] | [file] — [description]
    Accepts: [criterion]
  ```

עם מספר task ("plan 3"):
  הצג tasks/task-003-*.md במלואו

עם "new [description]":
  הפעל LARGE MODE planning:
  1. שלח ל-roo-planner ב-new_task
  2. הצג תוכנית למשתמש
  3. שאל: "מאשר? אתחיל?" → WAIT
