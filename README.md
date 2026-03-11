# 🚀 Roo WorkFlow — Global Rules System

מערכת אוטומטית מלאה לפיתוח תוכנה עם **git כמקור אמת**.
מותקנת **פעם אחת** בתיקיית הבית שלך ועובדת על **כל הפרויקטים**.

---

## 📁 מבנה הקבצים

```
~/.roo/                                    ← תיקיית הבית הגלובלית של Roo
│
├── .roomodes                              ← הגדרת 4 המודים
│
├── rules/                                 ← חוקים גלובליים לכל המודים
│   └── rules.md
│
├── rules-roo-workflow/                    ← חוקי Orchestrator בלבד
│   └── orchestrator_workflow.md
│
├── rules-roo-code/                        ← חוקי Code mode בלבד
│   └── coding-standards.md
│
├── rules-roo-architect/                   ← חוקי Architect mode בלבד
│   └── architecture.md
│
└── rules-roo-debug/                       ← חוקי Debug mode בלבד
    └── debug.md
```

---

## ⚙️ איך Roo טוען את הקבצים

Roo טוען חוקים בסדר היררכי: קודם חוקים גלובליים מ-`~/.roo/`, אחר כך חוקי פרויקט מ-`.roo/` בשורש הפרויקט. חוקי פרויקט גוברים על גלובליים במקרה של קונפליקט.

**סדר הטעינה לכל מוד:**
1. `~/.roo/rules/rules.md` — חוקים גלובליים לכולם
2. `~/.roo/rules-{mode-slug}/` — חוקים ספציפיים למוד
3. `.roo/rules/` בפרויקט (אם קיים) — override ספציפי לפרויקט

**לדוגמה — כשמוד `roo-code` פעיל, Roo קורא:**
```
~/.roo/rules/rules.md                    ← חוקים גלובליים
~/.roo/rules-roo-code/coding-standards.md ← חוקי code
.roo/rules-roo-code/ (בפרויקט, אם קיים)  ← override
```

---

## 🗂️ תפקיד כל קובץ

### `.roomodes`
מגדיר את 4 המודים. Roo קורא אותו בטעינה ויוצר את הכפתורים בממשק.
- `roo-workflow` — Orchestrator: מתכנן, מפצל משימות, מנהל git
- `roo-code` — Code mode: מממש, בודק, מבצע commit
- `roo-architect` — Architect: סוקר קוד (read-only בלבד)
- `roo-debug` — Debug: root-cause analysis, מקסימום 3 ניסיונות

### `rules/rules.md`
חוקי בסיס שחלים על **כל** המודים:
עברית למשתמש, אנגלית לקוד, אסור לשכפל לוגיקה, git add לקבצים ספציפיים בלבד, async תמיד, ניהול secrets.

### `rules-roo-workflow/orchestrator_workflow.md`
הלב של המערכת. מכיל:
- SESSION START: בדיקת git + טעינת זיכרון + זיהוי טאסק פתוח
- INIT-MEMORY: יצירת `memory-bank/project-memory.md` מ-git history
- MEMORY UPDATE RULES: מתי ואיך לעדכן זיכרון
- GIT WORKFLOW RULES: כל sub-task = commit אחד עם hash
- QUICK MODE / FULL MODE: פיצול משימות + execution loop
- RETRY RULES: code_counter (max 2) → debug_counter (max 3)
- ROLLBACK: 4 רמות rollback מוגדרות

### `rules-roo-code/coding-standards.md`
חוקי Code mode:
- TDD: כתוב טסט לפני הקוד
- lint + formatter + type checker לפני commit
- SELF REVIEW checklist לפני return
- Return format: `"done: [hash]"` או `"error: [desc]"`

### `rules-roo-architect/architecture.md`
חוקי Architect mode (read-only):
- בודק SOLID, security, performance, git hygiene
- Return format מדויק: `"clean"` או `"issue: [problem] in [file]:[line]"`
- לעולם לא עורך קבצים

### `rules-roo-debug/debug.md`
חוקי Debug mode:
- מופעל רק אחרי 3 כישלונות של Code
- reproduce → isolate → minimal patch → verify
- anti-loop: חייב לציין גישה שונה מכל הניסיונות הקודמים
- Return format: `"fixed: [hash] cause: [desc]"` או `"failed: [blocker]"`

---

## 🔄 זרימת עבודה מלאה

```
משתמש פותח Roo → בוחר 🚀 Roo WorkFlow
        ↓
SESSION START
  git status + git log --oneline -10
  קריאת memory-bank/project-memory.md
  סריקת tasks/ לאיתור IN-PROGRESS
        ↓
משתמש נותן משימה
        ↓
CLASSIFIER: QUICK (≤2 קבצים) או FULL (פיצ'ר חדש)
        ↓
FULL MODE:
  Phase 1: שאלות הבהרה (מקסימום 5)
  Phase 2: תוכנית + אישור משתמש
  Phase 3: יצירת tasks/task-NNN.md
  Phase 4: execution loop:
    לכל sub-task:
      → Code mode: כותב + בודק + commit → "done: [hash]"
      → Architect mode: סוקר → "clean" או "issue"
      → clean: ✅ הבא | issue: Code retry (גישה שונה)
      → 3 כישלונות: Debug mode (עד 3 ניסיונות)
      → 3 debug כישלונות: ❌ עצור + שאל משתמש
  Phase 5: full test suite + complete + commit
        ↓
🎉 הושלם! | קומיטים: [start-hash]..[end-hash]
```

---

## 🔁 Git כמקור אמת

**כל sub-task = commit אחד = הפיך לחלוטין.**

- כל דוח סטטוס כולל: `commit: [hash]`
- זיכרון (`project-memory.md`) מסונכרן עם `git log`
- במקרה כישלון — 4 רמות rollback:
  - `git checkout -- [file]` — קובץ בודד
  - `git revert HEAD` — commit אחרון
  - `git revert [start]..HEAD` — כל הטאסק
  - `git reset --hard [hash]` — חזרה מלאה ⚠️

---

## 🚀 התקנה

```bash
# Linux / macOS
cp -r .roo/ ~/.roo/

# Windows
xcopy .roo\ %USERPROFILE%\.roo\ /E /I
```

פתח VS Code → Roo → בחר מוד **🚀 Roo WorkFlow** → התחל לעבוד.

> **הערה:** אחרי העתקה, ייתכן שתצטרך לעשות Reload Window ב-VS Code כדי שהמודים יופיעו.

---

## 🔀 Override לפרויקט ספציפי

אם פרויקט מסוים צריך חוקים שונים, צור תיקיית `.roo/` בשורש הפרויקט:

```
my-project/
└── .roo/
    └── rules-roo-code/
        └── project-specifics.md   ← יתווסף לחוקים הגלובליים
```

חוקי פרויקט **נוספים** לגלובליים (לא מחליפים, אלא מצטברים).
