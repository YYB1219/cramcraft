# CramCraft AI — Exam Week Study Planner

Exam week, planned in 60 seconds. CramCraft AI turns exam dates, weakest topics and messy lecture notes into a spaced-repetition study plan, flashcards and self-quizzes — entirely on-device. No sign-up, no uploads, no cost.

## Run it

Open `index.html` in any modern browser. That's it — no build step, no server, no dependencies. It also works offline after the first load.

## What it does

1. **Add your exams** — subject, exam date, topics, and an honest confidence rating (1–5) per subject.
2. **Paste your notes** (optional) — key terms and definition sentences are extracted in the browser and turned into flashcards and fill-in-the-blank quiz questions.
3. **Generate** — a transparent planning engine builds a day-by-day plan:
   - **Priority scoring:** `priority = (6 − confidence) × urgency`, where urgency rises as the exam approaches — weak topics close to the exam are scheduled first.
   - **Spaced repetition:** every topic gets a Learn session plus reviews at 7 / 4 / 2 / 1 / 0 days before the exam (compressed automatically when the exam is sooner).
   - **Daily capacity:** sessions are capped by your available hours; overflow rolls forward but never past the exam date.
4. **Study & track** — tick sessions off (progress is saved in `localStorage`), flip flashcards, mark cards "still shaky" to bring them back sooner, and take the cloze quiz.
5. **Export** — download the plan as a calendar file (`.ics`, imports into Google/Apple/Outlook Calendar), as Markdown, copy it, or print it.

## How it works (tech)

- Single-file HTML/CSS/vanilla JavaScript — zero dependencies, zero network calls.
- The planning engine is a set of pure functions (`buildPlan`, `makeFlashcards`, `makeCloze`, `planToICS`, `planToMarkdown`) in a DOM-free script block, so it can be unit-tested with Node.js.
- Note processing uses definition-sentence pattern extraction ("X is / are / refers to …") to build flashcards and cloze questions locally. Nothing is sent to a server — student notes stay in the tab.
- Responsible AI by design: the scheduling logic is fully transparent and explainable (every session shows its priority score), there is no black-box model, and no personal data ever leaves the device.

## Project structure

```
index.html   — the entire app (UI + engine + styles)
README.md    — this file
submission.md — Devpost submission copy, demo video script, screenshot list
```

## Built for

SLAY HACKS 2026 (Devpost) — solo project by a first-time hackathon participant.

## License

MIT
