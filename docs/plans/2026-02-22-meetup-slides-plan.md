# NSRT Meetup Slides Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build an HTML slide deck for the first NSRT meetup (Russian, ~13 slides, NSRT design system)

**Architecture:** Single self-contained HTML file with inline CSS. Keyboard navigation (arrow keys), progress bar, slide transitions. Design system from `nsrt/index.html` (navy/amber/cream palette, Libre Baskerville + Source Serif 4 + JetBrains Mono).

**Tech Stack:** HTML, CSS, vanilla JS. No build step. Uses `frontend-design` skill for visual quality.

---

### Task 1: Slide system shell + title slide

**Files:**
- Create: `nsrt/presentation.html`

**Step 1:** Create the HTML file with:
- NSRT CSS variables (from index.html `:root`)
- Google Fonts (same 3 fonts as landing page)
- Slide system CSS: `.slide` (hidden by default, fullscreen grid), `.slide.active` (visible with fade-in), progress bar, slide counter
- Keyboard navigation JS: left/right arrows, progress bar update
- Blueprint grid background (same as landing page)
- Title slide (slide 1): "NSRT — Первая встреча", date, location coordinates

**Step 2:** Open in browser, verify navigation works with just the title slide.

**Step 3:** Commit: `feat: slide system shell with NSRT design system`

### Task 2: Act 1 slides (The Why) — slides 2-8

**Files:**
- Modify: `nsrt/presentation.html`

Add 7 slides using NSRT design language (section numbers in amber-on-navy badges, navy borders, tool cards):

- **Slide 2 — Icebreaker:** "Как давно вы живёте в Нови-Саде?" Three options with show-of-hands icons (<1 года, 1-3 года, 3+)
- **Slide 3 — The problem:** "У нас есть Telegram-чаты. Но знаем ли мы своих соседей?" Isolation framing for expat audience.
- **Slide 4 — Nobody's coming:** "Никто не придёт." No app, no government, no startup. We build it ourselves.
- **Slide 5 — Relational technology:** What it is — tech that strengthens bonds, not extracts. Reference RTP.
- **Slide 6 — NSRT principles:** The 5 manifesto points as a styled list (reuse `principles` styling from landing page).
- **Slide 7 — What already exists:** Dear Neighbors (111 стран, 340+ городов), Community Admin (WIP), Events API, сайт. Stat cards or tool cards.
- **Slide 8 — Ideas overview:** Category headers from the site (Знакомство, Взаимопомощь, Культура, Инфраструктура) as a grid.

**Step:** Commit: `feat: Act 1 slides — The Why`

### Task 3: Act 2 slides (The What) — slides 9-10

**Files:**
- Modify: `nsrt/presentation.html`

- **Slide 9 — Transition:** "Хватит обо мне. Давайте разберёмся вместе." Introduce Harmonica briefly — "Я сделал этот инструмент именно для таких разговоров."
- **Slide 10 — QR code / join:** Large QR code placeholder (will be replaced with actual Harmonica session link before meetup) + instructions for joining on phone.

**Step:** Commit: `feat: Act 2 slides — Harmonica transition`

### Task 4: Break + Act 3 slides (The How) — slides 11-13

**Files:**
- Modify: `nsrt/presentation.html`

- **Slide 11 — Break:** Simple "Перерыв — 10 минут" slide.
- **Slide 12 — What is vibecoding?:** "Вы описываете, что хотите. ИИ пишет код." Concept in 3 bullet points. Introduce Claude Code. "Мне нужен доброволец с ноутбуком."
- **Slide 13 — Closing:** "Вы не программист? Не нужно. Нужна проблема и желание её описать." Call to action: Telegram group, Harmonica synthesis link, nsrt.netlify.app. Buckminster Fuller quote from the landing page footer.

**Step:** Commit: `feat: Act 3 slides + closing`

### Task 5: Visual polish

**Files:**
- Modify: `nsrt/presentation.html`

Use `frontend-design` skill. Review all slides for:
- Consistent spacing and typography
- Proper use of NSRT color palette
- Readable at projector distance (large fonts, high contrast)
- Bridge decoration SVG between acts (from landing page)
- Touch/swipe support for mobile (in case people view on phones)

**Step:** Commit: `style: visual polish for projector readability`
