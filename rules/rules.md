## Core Rules — All Modes

### שפה
- דיבור עם המשתמש: עברית תמיד
- קוד, paths, commits, identifiers, CLI output: אנגלית תמיד
- לא לתרגם שמות משתנים, functions, או מושגים טכניים

### 🔒 הגנת קוד — CRITICAL
- **אסור למחוק קובץ, פונקציה, או קוד עובד — ללא אישור מפורש מהמשתמש**
- **אסור לעשות git rm, rm, או כל מחיקה — ללא WAIT ואישור**
- **לפני כל שינוי הרסני (rename, move, delete, overwrite) — הצג מה עומד לקרות ו-WAIT**
- אסור לבצע full rewrite של קובץ קיים — minimal diff בלבד, אלא אם התבקש במפורש
- אסור לשנות קבצים שאינם ברשימת ה-sub-task הנוכחי
- אסור לשכפל לוגיקה קיימת — חפש ושתף תחילה

### 🔒 הגנת נתונים
- אסור hardcode secrets — משתני סביבה בלבד
- ללא קבצי זבל: *.bak, *.tmp, קוד מת, console.log שנשכח
- אסור לcommit: .env, *.log, node_modules, __pycache__

### גישה לקבצים
- קרא רק קבצים הנחוצים לטאסק הנוכחי — אסור לסרוק codebase שלם
- אם מידע קיים ב-memory-bank/project-memory.md — אסור לקרוא את הקובץ מחדש
- שמור שימוש ב-context window מתחת ל-80%

### token discipline
- קרא memory פעם אחת בכל session — cache לכל ה-session
- הפנה לקבצים ב-path — אסור להדביק תוכן קובץ שלם
- patches ו-diffs בלבד — לא rewrites מלאים אלא אם נדרש במפורש
- עדכן memory פעם אחת בסיום task + כל פעם שמתגלה מידע חדש
