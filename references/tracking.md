# ChronoPlanner — Tracking Reference

> In coach mode (`~/coach/config.json` exists) the end-of-day review is run by `gps-daily` (evening review) and daily metrics live in `~/coach/tracking/`. Use this file for the Pattern Learning rules; store calibration notes in `~/coach/calibration.md` instead of Claude memory, and skip Google Sheets.

Load this file when:
- User says "day done", "wrap up", "end of day", "I'm done for today", or similar
- User asks for a weekly report or productivity summary
- Applying duration calibration buffers in Round 5 (pattern learning data)

---

## End-of-Day Review Protocol (P6.15)

### Trigger phrases
"day done" / "wrap up" / "end of day" / "I'm done" / "that's it for today" / "日程结束" / "今天结束了"

### Review questions (ask in one message)

> **Quick end-of-day check-in — 3 questions:**
>
> **① Tasks**
> Which tasks did you complete today? Which were deferred? Which were dropped entirely?
> (You can copy from today's plan or just list them)
>
> **② Plan quality score**
> How well did today's schedule fit your actual rhythm? 1–5
> - 1 = completely off, timing felt wrong all day
> - 3 = mostly worked, a few adjustments needed
> - 5 = near-perfect, would use the same structure again
>
> **③ Energy accuracy**
> Did your energy actually follow the predicted pattern?
> - Yes, roughly as expected
> - Morning was better than predicted
> - Morning was worse than predicted
> - Afternoon was better than predicted
> - Afternoon was worse than predicted

### After collecting review data

1. Calculate completion metrics:
   - Tasks completed vs scheduled: X / Y (Z%)
   - Total deep focus time achieved (sum of completed 🔵 blocks)
   - Any tasks that took significantly longer or shorter than estimated

2. Generate a brief end-of-day summary:
> "Today's summary:
> ✅ Completed: [list] · ⏩ Deferred: [list] · ❌ Dropped: [list]
> 🎯 Completion rate: X/Y tasks (Z%)
> 🔵 Deep focus achieved: Xh Ymin
> 📊 Plan quality: [score]/5
> [Any duration calibration notes — see Pattern Learning below]"

3. Store data (see Storage Protocol below)

4. Update memory with calibration notes (see Pattern Learning below)

---

## Pattern Learning (P6.13)

### What to track
After each end-of-day review, compare estimated vs actual duration for any task where the user reports a significant difference (>20% over or under).

Extract calibration signals:
- Task type (coding, writing, admin, review, creative, meetings)
- Estimated duration
- Actual duration (user-reported)
- Over/under ratio

### Calibration rules

**After 3+ data points for the same task type:**
- Calculate average ratio (actual / estimated)
- If ratio > 1.15 consistently → flag as "tends to underestimate"
- If ratio < 0.85 consistently → flag as "tends to overestimate"

**Store as memory note:**
> "Coding tasks: user typically runs 25% over estimate (based on 5 sessions). Apply 1.25x buffer suggestion in Round 5."
> "Writing tasks: user typically finishes 10% under estimate (based on 3 sessions). No buffer needed."

**Apply in Round 5:**
When a task type has a calibration note, surface the buffer suggestion before applying:
> "Based on 5 past sessions, you usually take about 25% longer on coding tasks. Want me to schedule 75 min instead of 60 min?"

**Reset calibration:** If user explicitly says "I've changed my workflow" or "that's not accurate anymore", clear the calibration note for that task type.

---

## Habit Tracking Layer (P6.14)

### Daily metrics to record (after each end-of-day review)
- Date
- Deep focus time achieved (minutes)
- Completion rate (tasks done / tasks scheduled, %)
- Plan quality score (1–5)
- Chronotype used
- Sleep hours
- Morning exercise (Y/N)
- Break adherence (self-reported: followed break protocol / mostly / skipped most breaks)

### Storage options

**Option A — Hermes memory (always available):**
Store a rolling 7-day summary as a memory note:
> "ChronoPlanner weekly summary (week of Apr 14):
> Avg deep focus: 3.2h/day · Avg completion rate: 78% · Avg quality score: 3.8
> Best day: Tuesday (4.5h focus, 90% completion)
> Skipped breaks: Wednesday and Friday"

Update this summary every time a new day is reviewed. Keep only the most recent 2-week window in memory to avoid bloat.

**Option B — Google Sheets (if connected, preferred):**
Write one row per day to a sheet named "ChronoPlanner Log":

| Date | Focus (min) | Completion % | Quality | Sleep (h) | Exercise | Chronotype | Break adherence |
|------|------------|-------------|---------|-----------|----------|------------|-----------------|
| 2026-04-17 | 195 | 80 | 4 | 7.5 | Y | Intermediate | Mostly |

If Google Sheets is connected but the sheet doesn't exist yet, create it automatically on first write and confirm:
> "I've created a 'ChronoPlanner Log' sheet in your Google Drive to track your daily metrics."

### Weekly Report

**Trigger:** User says "weekly report" / "how was my week" / "productivity summary" / or automatically offer every Sunday evening after end-of-day review.

**Report format:**
> **ChronoPlanner Weekly Report — Week of [date]**
>
> 📊 **Overview**
> - Days tracked: X/7
> - Avg deep focus per day: Xh Ymin
> - Avg task completion rate: X%
> - Avg plan quality score: X.X/5
>
> 🏆 **Best day:** [day] — Xh focus, X% completion
> ⚠️ **Toughest day:** [day] — [brief note]
>
> 📈 **Trends**
> - Focus time: [up/down/stable] vs last week
> - Completion rate: [up/down/stable] vs last week
>
> 💡 **Observations**
> - [1–3 data-driven observations, e.g. "You consistently skip breaks on Fridays — consider scheduling shorter blocks on Friday afternoons"]
> - [e.g. "Your morning exercise days average 45 more minutes of deep focus than non-exercise days"]
> - [e.g. "Coding tasks are consistently running over — calibration buffer applied from next session"]
>
> 🎯 **Next week suggestion**
> [One concrete scheduling suggestion based on the week's data]

If data is stored in Google Sheets, pull from the sheet for the report. If only memory is available, use the rolling summary.

---

## Storage Protocol Summary

| Data | Primary storage | Fallback |
|------|----------------|---------|
| Task duration calibration | Hermes memory / `~/coach/calibration.md` | Hermes memory only |
| Daily metrics | Google Sheets row | Hermes memory rolling summary |
| Weekly report source | Google Sheets (7 rows) | Hermes memory summary |
| Calibration notes | Hermes memory / `~/coach/calibration.md` | Hermes memory only |

**Privacy note:** Never store specific task names or content in Google Sheets without user consent. Store only metrics (duration, completion rate, scores). Task names stay in Hermes memory only if the user has provided them in context.
