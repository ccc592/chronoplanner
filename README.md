# ChronoPlanner

[🇨🇳 中文](./README-CN.md) | 🇬🇧 English

> A Claude skill that builds your daily schedule around your biology — not a generic template.

ChronoPlanner is a Claude skill that generates science-based daily plans grounded in **circadian rhythm research**, **attention span science**, and **dopamine regulation principles**. Instead of asking you to fill a calendar top-to-bottom, it matches each task to the time window where your brain is biologically primed to handle it.

Also available in Chinese: [SKILL-CN.md](./SKILL-CN.md)

---

## What Makes It Different

Most AI planners treat all hours as equal. ChronoPlanner doesn't.

It calculates your personal energy windows relative to your actual wake-up time, then schedules tasks accordingly — deep focus when cortisol peaks, admin during the trough, review before sleep. It also handles the practical friction that kills real plans: location changes, commute buffers, fixed anchor events, and fatigue prediction.

**Core principles built in:**
- Cortisol Awakening Response (CAR) and BDNF timing
- Attention Residue Effect (23-minute recovery after task switches)
- Dopamine cool-down before deep work
- Task batching to minimize context switching
- Eat the Frog — hardest task in the peak window
- Active + Passive task stacking during commutes
- Fatigue prediction — admin tasks when energy drops, not deep work
- Deferred commute scheduling — commute blocks placed right before the destination task, not stranded hours early
- Auto-inferred lunch block when not specified
- Google Calendar sync — adds the full plan to your calendar after generation

---

## Who It's For

✅ Students and knowledge workers with flexible schedules  
✅ Anyone with a mix of deep work, admin, and errands in the same day  
✅ People who exercise in the morning and want to leverage that window  
✅ Anyone who's tried time-blocking but found it too rigid to maintain  

❌ Not ideal for people with fully fixed 9-to-5 schedules with no flexibility  
❌ Not a task manager — it plans a single day at a time, not long-term projects  

---

## Installation

### Option A — Claude.ai (Web / Mobile)

1. Go to **Settings → Skills** in Claude.ai
2. Create a new skill and paste the contents of `SKILL.md`
3. Save — ChronoPlanner will activate automatically when you ask Claude to plan your day

### Option B — Claude Code

```bash
mkdir -p ~/.claude/skills/chronoplanner
curl -o ~/.claude/skills/chronoplanner/SKILL.md \
  https://raw.githubusercontent.com/yitong0322/chronoplanner/main/SKILL.md
```

### Option C — System Prompt (any Claude interface or API)

Copy the full contents of `SKILL.md` and paste it into your system prompt field. Works with Claude API, Cursor, and any tool that accepts a system prompt.

---

## How It Works

ChronoPlanner opens with a single combined message covering the three essential questions, then asks follow-up questions only for information that's missing. If you provide everything upfront, it skips straight to generating your plan.

| Round | What It Asks | When |
|-------|-------------|------|
| 1–3 (combined) | Wake-up time, plan scope, fixed anchor events | Always, in one message |
| 4 | Today's task list | Only if not provided |
| 5 | Duration, priority, and location per task | Only for missing fields, one task at a time |
| 6 | Focus level today + target end time | Always |

After all rounds, Claude outputs a one-paragraph confirmation summary, then generates the full schedule.

---

## Output Format

Each schedule block follows this structure:

```
[Time slot] 🔵 Task name (duration) — One-sentence reason
[Time slot] 😴 Break: recommended method (duration)
[Time slot] 🍽️ Lunch (suggested) — adjust time if needed
[Time slot] 🚌 Commute: Home → Café (20 min) — recommended: podcast / audiobook
[Time slot] ⚪ Reply to emails (30 min) — energy trough; admin only
...
```

**Legend**

| Icon | Meaning |
|------|---------|
| 🔵 | Deep focus task |
| 🟡 | Creative / collaborative / skill practice |
| 🟢 | Review / consolidation |
| ⚪ | Admin / mechanical task |
| 😴 | Break (method specified) |
| 🍽️ | Lunch (fixed or auto-suggested) |
| 🚌 | Commute buffer (placed right before destination task) |
| ☕ | Dopamine cool-down / caffeine timing |
| 🌙 | Relaxation / light reading / journaling |

Only blocks with content are listed — empty time gaps are not explained.

---

## Example

**User message:**
> Wake up 6:30, gym 45 min. Tasks: LeetCode (60 min, high, home), reading notes (60 min, mid, café), reply emails (30 min, low, home), Anki review (30 min, mid, home), tech video (60 min, low, home). Focus: average. Done by 9 PM.

**ChronoPlanner output (excerpt):**

```
[06:30–07:15] 🏋️ Gym (45 min) — exercise elevates BDNF; deep focus window opens immediately after
[07:15–08:15] ☕ Dopamine cool-down + breakfast (60 min) — no high-stimulation content; cortisol rising
[08:15–09:00] 🔵 LeetCode (45 min) — peak cortisol; hardest task first (Eat the Frog)
[09:00–09:10] 😴 Break: look out the window / stretch (10 min)
[09:10–09:55] 🔵 LeetCode continued (45 min)
[09:55–10:05] 😴 Break: diaphragmatic breathing (10 min)
[10:05–10:50] 🟡 Reading notes (45 min) — still in golden window; creative absorption
[10:50–11:10] 🚌 Commute: Home → Café (20 min) — recommended: podcast or language listening
[11:10–11:55] 🟡 Reading notes continued (45 min, @ Café)
[12:00–13:00] 🍽️ Lunch (suggested)
[13:00–13:30] ⚪ Reply to emails (30 min) — energy trough; batched admin only
[14:30–15:15] 🟢 Anki review (45 min) — secondary peak; spaced repetition consolidates morning learning
[15:25–16:25] ⚪ Tech video (60 min) — passive absorption; secondary peak
[20:00–20:30] 🟢 Anki second pass (30 min) — memory consolidation window; pre-sleep review
[20:30–21:00] 🌙 Wind down — journaling, light reading, no new information input

📊 Summary: Deep focus 1.5h · Creative 1.5h · Review 1h · Admin 1h · Commute 20min · Done by 21:00 ✓

Would you like me to add this plan to your Google Calendar?
```

---

## Google Calendar + Apple Calendar Sync

After generating your plan, ChronoPlanner will ask if you'd like to add it to Google Calendar. If you say yes, it creates a separate calendar event for every block — tasks, breaks, commutes, and the dopamine cool-down window — using the Google Calendar MCP connector.

If you have Google Calendar synced to your Apple Calendar on iPhone or Mac, events will appear there automatically.

---

## Customization

The skill is designed to be forked and adapted. Common modifications:

- **Different wake-up range** — edit the options in the opening questions
- **Add your own morning routine types** — extend the morning habits section under Core Science Principles
- **Change output language** — a Chinese version is available at `SKILL-CN.md`; you can also hardcode a preferred language at the top of `SKILL.md`
- **Adjust focus block lengths** — edit the Poor / Average / Good table under Attention Span Principles

---

## Scientific Background

ChronoPlanner draws on the following research areas:

- **Cortisol Awakening Response (CAR)** — the post-wake cortisol surge that primes executive function
- **BDNF and exercise** — aerobic exercise elevates brain-derived neurotrophic factor, enhancing learning readiness
- **Attention Residue Effect** — Sophie Leroy's research on the cognitive cost of task switching (~23 min recovery)
- **Dopamine baseline regulation** — Anna Lembke's work on high-stimulation content and its effect on baseline motivation
- **Two-process model of sleep regulation** — circadian rhythm + sleep pressure interaction
- **Spaced repetition and memory consolidation** — pre-sleep review and its effect on overnight memory processing

---

## License

MIT — free to use, modify, and redistribute.

---

## Contributing

PRs welcome. If you've tested a modification that improves output quality, open a PR with a brief description of what changed and why.
