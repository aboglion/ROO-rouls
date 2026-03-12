---
description: בטל שינויים — קובץ ספציפי, הכל, או stash
argument-hint: [<file-path> | --all | --stash]
mode: roo-workflow
---

ללא ארגומנט:
  הרץ: `git status --short`
  שאל: "מה לבטל?
  1. קובץ ספציפי — אמור את ה-path
  2. הכל (git checkout -- .)
  3. שמור ב-stash לשחזור עתידי
  4. ביטול — אל תעשה כלום"
  WAIT

עם שם קובץ:
  הצג: `git diff [file]`
  שאל: "לבטל שינויים אלה ב-[file]? [כן/לא]" → WAIT
  אם כן: `git checkout -- [file]`
  עדכן Current State ב-memory

עם --all:
  הצג: `git status --short`
  ⚠️ שאל: "לבטל את כל השינויים? זה בלתי הפיך! [כן/לא]" → WAIT
  אם כן: `git checkout -- .`

עם --stash:
  `git stash push -m "manual-stash [YYYY-MM-DD HH:MM]"`
  ✅ Stash נשמר. שחזור: `git stash pop`

דווח בעברית על מה בוצע.
