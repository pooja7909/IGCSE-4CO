# IGCSE Edexcel 4CP0 Computer Science — Self-Study Hub

A static-HTML revision site for the **Pearson Edexcel International GCSE in Computer Science (4CP0)** specification. Covers all six topics with notes, quizzes, activities, exam-style questions and a full Python Code Lab — no backend, no database, no sign-in.

## Topic order (matches the official Pearson spec)

1. **Problem solving** — algorithms, decomposition, abstraction
2. **Programming** — code, constructs, data types, I/O, operators, subprograms (drives Paper 2)
3. **Data** — binary, hex, ASCII, compression, encryption
4. **Computers** — hardware, logic, software, programming languages
5. **Communication and the internet** — networks, security, web
6. **The bigger picture** — emerging trends, issues and impact

## What's in this repo

```
index.html                              — Homepage with the 6 topic cards
about.html                              — Spec aims, AO weights, command words, pseudocode reference
past-papers.html                        — Past-paper guide + 6-week practice plan

topic-1-problem-solving.html            — ✅ Provided
topic-2-programming.html                — ✅ Provided (full Python self-study app)
topic-3-data.html                       — (drop your file here)
topic-4-computers.html                  — (drop your file here)
topic-5-communication-internet.html     — (drop your file here)
topic-6-bigger-picture.html             — (drop your file here)
```

The homepage cards already point at the filenames above. As soon as you add a topic HTML file with the matching name, the card becomes live.

## Key spec facts referenced in the site

- **Subject code:** 4CP0 · **Paper 1:** 4CP0/01 · **Paper 2:** 4CP0/02
- **Paper 1:** 2 hours · 80 marks · 50% · written, assesses all 6 topics
- **Paper 2:** 3 hours · 80 marks · 50% · on-screen practical, Python/C#/Java
- **Grades:** 9–1 scale (9 highest)
- **Assessment objectives:** AO1 27.5% (knowledge) · AO2 42.5% (apply) · AO3 30% (analyse)
- **First teaching:** September 2017 · **First examination:** June 2019

## How student progress works

The HUD chips at the top of every page (🔥 streak and ⭐ XP) read from the browser's **localStorage**. The Python app writes to these keys whenever students earn XP or extend their streak, and every page reads them on load — so progress is shared across the whole site without a backend.

Keys used: `igcse_py_streak`, `igcse_py_xp`, `igcse_py_mastery`, `igcse_py_quiz_best`, `igcse_py_quiz_att`, `igcse_py_code_solved`, `igcse_py_exam_att`, `igcse_py_last_visit`.

If you want each topic page to award XP too, copy these helpers from the Python app:

```js
function get(k, def){ try { const v = localStorage.getItem(k); return v===null ? def : JSON.parse(v); } catch(e){ return def; } }
function set(k, v){ try { localStorage.setItem(k, JSON.stringify(v)); } catch(e){} }
function addXP(n){ set('igcse_py_xp', get('igcse_py_xp', 0) + n); }
```

## Marking topic cards as "ready" or "coming soon"

In `index.html` each topic card has a class of `coming` (greyed-out button) or `ready` (button is live). When you upload a real topic HTML file, change the class on the matching card:

```html
<!-- Before you upload your file: -->
<div class="topic-card t3 coming" data-topic="3">

<!-- After you upload it: -->
<div class="topic-card t3 ready" data-topic="3">
```

Topics 1 and 2 are already marked `ready`.

## Deploying to GitHub + Vercel

1. **Create a GitHub repo**
   - github.com → New repository → name it (e.g. `igcse-4cp0-hub`) → Public → Create
   - Click **Add file → Upload files** and drag in every file from this folder
   - Commit

2. **Connect Vercel**
   - vercel.com → Sign in with GitHub
   - **Add New → Project** → import this repo
   - Leave all defaults (Vercel detects it as a static site) → Deploy
   - ~30 seconds later you get a URL like `igcse-4cp0-hub.vercel.app`

3. **Share with students**
   - Send them the Vercel URL
   - Their progress saves to their own browser, private to their device
   - Push any update to GitHub → Vercel auto-deploys it in seconds

## Privacy / safety

- No accounts, no cookies for tracking, no analytics
- All progress data is in the student's own browser
- The Python Code Lab marks code locally in the browser — no code is sent anywhere
- Safe to share with under-16 students

## Licence

Educational content for use by individual students preparing for IGCSE 4CP0. **Not affiliated with or endorsed by Pearson Edexcel.**
