# ChronoPlanner

[🇨🇳 中文](./README-CN.md) | 🇬🇧 English

> A Claude skill that builds your daily schedule around your biology — not a generic template.

ChronoPlanner is a Claude skill that generates science-based daily and weekly plans grounded in **circadian rhythm research**, **attention span science**, and **dopamine regulation principles**. It matches each task to the time window where your brain is biologically primed to handle it — and learns your patterns over time.

---

## What Makes It Different

Most AI planners treat all hours as equal. ChronoPlanner doesn't.

It calculates your personal energy windows from your wake time, chronotype, and sleep quality — then schedules accordingly. Deep focus when cortisol peaks. Admin during the trough. Review before sleep. It also handles the practical friction that kills real plans.

**Core features:**
- **Pre-scan** — silently reads Google Calendar, Tasks, Gmail, Notion, Todoist, Slack, and weather before asking a single question
- **Chronotype-aware** — 3-question MEQ assessment; Night Owl golden window shifts 3–4 hours later than Morning Lark
- **Sleep-calibrated blocks** — sleep hours × subjective feel → precise focus block length (25 / 45 / 60–90 min)
- **Dopamine cool-down** — 60-min protection window before deep work
- **Task batching** — communications in fixed windows; creative work in continuous sessions
- **Eat the Frog** — hardest task in the peak window, always
- **Commute-aware** — detects location changes, inserts 🚌 commute blocks right before the destination task
- **Task dependencies** — Task B only scheduled after Task A completes
- **Weather-adaptive breaks** — outdoor breaks only if conditions are good
- **Plan adjustment** — "my meeting moved to 3 PM" re-slots only affected blocks
- **Menstrual cycle awareness** — optional; adjusts block length and break frequency by phase
- **Weekly mode** — distributes tasks across Mon–Fri with a week-view summary
- **End-of-day review** — triggered by "day done"; tracks completion rate and plan quality
- **Pattern learning** — after 3+ sessions, suggests duration buffers for task types you consistently underestimate
- **Habit tracking** — daily metrics stored in Google Sheets; weekly report on request
- **Google Calendar / Notion / Obsidian output** — sync or export your plan after generation

---

## Who It's For

✅ Students and knowledge workers with flexible schedules
✅ Anyone juggling deep work, admin, and errands in the same day
✅ People who exercise in the morning and want to leverage that window
✅ Night owls who need a schedule that actually fits their biology
✅ Anyone who's tried time-blocking but found it too rigid to maintain

❌ Not ideal for fully fixed 9-to-5 schedules with no flexibility
❌ Not a long-term project manager — plans one day or one week at a time

---

## Installation

### Option A — Claude.ai (Web / Mobile)

1. Go to **Settings → Skills** in Claude.ai
2. Create a new skill and paste the contents of `SKILL.md`
3. Save — ChronoPlanner activates automatically when you ask Claude to plan your day

> **Note:** The `references/` folder contains supporting files that Claude loads on demand. Upload the full folder structure for best results.

### Option B — Claude Code

```bash
git clone https://github.com/yitong0322/chronoplanner ~/.claude/skills/chronoplanner
```

### Option C — System Prompt (any Claude interface or API)

Paste the contents of `SKILL.md` into your system prompt. Works with Claude API, Cursor, and any tool that accepts a system prompt.

---

## How It Works

### Step 0: Pre-Scan (Silent, Automatic)

Before asking anything, ChronoPlanner scans your connected tools and checks your memory:

| Source | What It Does |
|--------|-------------|
| 🧠 Memory | Loads saved chronotype, wake time, calibration notes |
| 📅 Google Calendar | Fetches today's events → auto-locked as anchors |
| ✅ Google Tasks / Todoist / Linear / TickTick | Fetches tasks due today |
| 📧 Gmail / Outlook | Scans for actionable emails (max 5) |
| 📝 Notion | Surfaces pages tagged today or this week |
| 💬 Slack | Scans mentions/DMs for action items (max 3) |
| 🌤️ Weather | Fetches current conditions → affects break recommendations |

Unconnected tools are skipped silently. Results shown in one summary line before any questions.

### Step 1: Intake Questionnaire

Asks only what the pre-scan didn't already answer — one combined message for the essentials, then per-task questions one at a time.

| Round | What It Asks | When |
|-------|-------------|------|
| 1–3 (combined) | Plan type (day/week), wake time, fixed anchors | Always; skips pre-filled fields |
| 4 | Task list | Only if not found in pre-scan |
| 5 | Duration, priority, location, dependencies | Only for missing fields, one task at a time |
| 6 | Sleep hours + feel, chronotype (MEQ), target end time | Always |

### Step 2: Generate Plan

Confirmation summary → full annotated schedule → offer to sync to Google Calendar, Notion, or Obsidian.

### Step 3: End-of-Day Review (optional)

Say **"day done"** at any time to trigger a 3-question review:
- Which tasks completed / deferred / dropped?
- Plan quality score (1–5)
- Did your energy match the prediction?

Results feed into Pattern Learning and Habit Tracking automatically.

---

## Output Format

```
[Time] 🔵 Task (duration) — reason
[Time] ☕ Dopamine cool-down (60 min) — no high-stimulation content
[Time] 😴 Break: method (duration)
[Time] 🍽️ Lunch (fixed / suggested)
[Time] 🚌 Commute: Home → Café (20 min) — recommended: podcast
[Time] 🕐 Buffer (15 min) — arrived early; settle in, review agenda
[Time] 🕐 Free time (45 min) — freed by schedule change; use as you like
[Time] ⚪ Admin task (duration) — energy trough; batched
```

**Legend:** 🔵 Deep focus · 🟡 Creative/skill · 🟢 Review · ⚪ Admin · 😴 Break · 🍽️ Meal · 🚌 Commute · 🕐 Buffer/Free · ☕ Cool-down · 🌙 Relaxation

---

## Example

**User message:**
> Wake 7:00, Intermediate, 7.5h sleep feeling normal, gym 45 min. Lunch 12:30–13:30. Tasks: project report (90 min, high), LeetCode (60 min, high), emails (30 min, low), Anki (30 min, mid). End by 21:00.

**Output (excerpt):**
```
[07:00–07:45] 🏋️ Gym (45 min) — BDNF boost; focus window opens immediately after
[07:45–08:45] ☕ Dopamine cool-down + breakfast (60 min)
[08:45–09:30] 🔵 Project report (45 min) — peak cortisol; Eat the Frog
[09:30–09:40] 😴 Break: step outside (10 min)
[09:40–10:25] 🔵 Project report cont. (45 min)
[10:25–10:35] 😴 Break: diaphragmatic breathing (10 min)
[10:35–11:20] 🔵 Project report cont. (45 min)
[11:20–11:30] 😴 Break: walk outside (10 min)
[12:30–13:30] 🍽️ Lunch (fixed anchor)
[13:30–14:00] ⚪ Emails (30 min) — energy trough; batched admin
[14:00–15:00] 🔵 LeetCode (60 min) — afternoon secondary peak
[19:30–20:00] 🟢 Anki (30 min) — memory consolidation window
[20:00–21:00] 🌙 Wind down

📊 Deep focus 3.75h · Admin 30min · Review 30min · Done by 21:00 ✓

Would you like me to add this to your Google Calendar?
```

---

## File Structure

```
chronoplanner/
├── SKILL.md              # Core logic — install this
├── SKILL-CN.md           # Chinese version
├── README.md             # This file
├── README-CN.md          # Chinese README
├── TODO.md               # Roadmap and changelog
├── LICENSE
└── references/           # Loaded by Claude on demand
    ├── science.md        # Hormonal rhythm, attention, dopamine science
    ├── break-protocol.md # Break recommendations by type
    ├── scheduling.md     # Scheduling rules + weekly mode
    ├── tracking.md       # End-of-day review, pattern learning, weekly report
    └── examples.md       # Worked examples
```

---

## Scientific Background

- **Cortisol Awakening Response (CAR)** — post-wake cortisol surge primes prefrontal cortex
- **BDNF and exercise** — aerobic training elevates brain-derived neurotrophic factor for 2–4 hours
- **Attention Residue Effect** (Sophie Leroy, 2009) — task switches cost ~23 min of recovery
- **Dopamine baseline regulation** (Anna Lembke) — high-stimulation content raises baseline, causing structural resistance to focused work
- **Two-process model of sleep** — circadian rhythm + sleep pressure interaction
- **Spaced repetition and memory consolidation** — pre-sleep review maximizes overnight retention

---

## License

MIT — free to use, modify, and redistribute.

---

## Contributing

PRs welcome. If you've tested a modification that improves output quality, open a PR with a brief description of what changed and why.

Found a bug or have a feature idea? Open an issue.
