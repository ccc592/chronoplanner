# ChronoPlanner — Scheduling Reference

Load this file when generating or adjusting a schedule, or when explaining why a task was placed in a particular time slot.

---

## Advanced Scheduling Principles

### 1. Fatigue Prediction and Maintaining Momentum

Plans must anticipate fatigue — never assume energy is constant throughout the day:

- During the energy trough (T+7h~T+9h for Intermediate) and after consecutive deep focus blocks, **proactively insert admin / mechanical tasks** rather than forcing high-difficulty content
- Admin tasks during fatigue serve a dual purpose: minimal cognitive load, while providing a steady stream of "completion" dopamine to maintain daily momentum
- **Never schedule deep focus tasks when energy is depleted** — pushing through only produces low-quality output and accelerates the subsequent crash

### 2. Task Batching

Group similar task types into the same time window. Scattering them throughout the day is one of the most common and costly productivity mistakes.

- 📧 **Communications** (emails, messages, notifications) → batched into 1–2 fixed windows; never checked ad hoc throughout the day
- 📅 **Meetings / discussions** → consolidated into the same half-day where possible; protect the other half for uninterrupted focus
- ✍️ **Creative / editing work** → drafting, revision, and polishing of the same piece in continuous time; never split across multiple sessions in the same day
- 🗂 **Admin / filing** → consolidated into the trough period for batch execution

**Why it works:** Each task switch requires ~23 minutes of recovery (Attention Residue Effect). Batching minimizes the number of switches and dramatically reduces total cognitive load.

### 3. Match Tasks to Energy Levels (Eat the Frog)

- **Golden Window (peak energy)** → hardest, most important, most creative task first. Eat the biggest frog while you're sharpest. Do not save difficult tasks "for later."
- **Afternoon Secondary Peak** → medium-difficulty tasks, skill practice, collaborative or communication-heavy work
- **Energy Trough** → light admin, filing, passive learning (podcasts, videos) only. Never deep focus.
- Never defer important tasks to "when energy comes back" — the secondary peak is limited and often consumed by other commitments before the user reaches the hard tasks.

### 4. Active + Passive Task Stacking

Identify tasks that can run in parallel — boost output without consuming extra time. See break-protocol.md for the full list of recommended and prohibited pairings.

Actively scan the day's task list for stackable combinations and annotate them in the schedule.

### 5. Dynamic Adjustment Mindset

The plan is a starting point, not a fixed contract. Append this note at the end of every schedule:

> "If a block goes better than expected, pull the next mid-priority task forward. If you feel fatigued after a block, switch to admin immediately — don't push through."

---

## Scheduling Rules

Apply all of the following rules when generating or modifying any schedule:

1. Block length determined by the sleep × feel table in SKILL.md; Break Protocol (see break-protocol.md) enforced strictly between every focus block
2. The Deep Focus Golden Window is reserved exclusively for the highest-intensity tasks (Eat the Frog) — never used for admin, meetings, or mechanical tasks
3. Creative / editing tasks must not be split across different time periods (e.g. morning and afternoon). Multiple blocks of the same task within a continuous session — separated only by short breaks — are allowed and expected. If the golden window cannot fit both a deep focus and a creative task, move the creative task entirely to the afternoon secondary peak.
4. **Transition zone rule:** Tasks may begin up to 30 minutes before the calculated golden window starts if the user is warming up naturally. Do not force a hard wait if the user is already in a focused state. Apply conservative block lengths (one tier shorter) during the transition zone.
3. The 60 minutes before deep work begins is a **dopamine cool-down protection window** — no high-stimulation content permitted
4. All communications batched into 1–2 fixed windows; never checked ad hoc throughout the day
5. The energy trough period must contain only admin / mechanical tasks — deep focus is strictly prohibited regardless of priority
6. Scan and annotate active + passive task stacking opportunities in the schedule output
7. Group tasks at the same location together to minimize commute blocks; insert 🚌 Commute immediately before the destination task (deferred rule — never immediately after the previous task ends)
8. No large new knowledge input within 2 hours of sleep; review and consolidation only
9. For users with a caffeine habit: consume 60–90 minutes after waking to avoid wasting the natural cortisol peak
10. Phone stays out of sight during all deep work blocks
11. Dependencies: if Task A must precede Task B, enforce this ordering even if it conflicts with energy window matching — dependency rules override energy rules
12. If total task time (including commute buffers and calibration buffers) exceeds available hours: defer low-priority tasks first and explain why to the user
13. **Gap time rule:** If a gap of 15 minutes or more exists between two scheduled blocks (e.g. after a commute arrives early), label it explicitly as `🕐 Buffer (X min)` and suggest one low-effort activity appropriate to the time of day — do not leave it unexplained and do not fill it with a task. Suitable suggestions: grab water and settle in, review notes for the next anchor, light stretching, or simply rest.
14. **Freed slot rule:** When a plan adjustment frees up a previously occupied time slot, label it as `🕐 Free time (X min)` — do not automatically fill it with a task. The user decides what to do with it.

---

## Weekly Planning Mode

### When to Activate
User selects "B. Full week" in the opening questions, or explicitly asks for a weekly plan.

### Weekly Intake (ask in one message)

> **Week setup:**
>
> **① Days to plan** (Mon–Fri / Mon–Sun / custom)
> **② Fixed weekly anchors** — recurring meetings, classes, gym days, commute days (name + day + time + duration for each)
> **③ This week's tasks** — list everything with deadline and estimated duration
> **④ Any days with special constraints?** (e.g. "Thursday I have a dinner at 7 PM")

### Weekly Distribution Rules

1. **High-priority tasks with deadlines** → scheduled earliest in the week, in peak focus windows
2. **Deep focus heavy work** → Monday, Tuesday, Wednesday preferred (cognitively freshest after weekend)
3. **Meeting-heavy commitments** → consolidate onto 1–2 designated days; keep the remaining days protected for focus
4. **Admin batch slot** → one afternoon per week dedicated entirely to admin tasks
5. **Spaced repetition / review** → daily, in the memory consolidation window each evening
6. **Buffer** → Friday afternoon left partially open for overflow, review, and reflection

### Weekly Output Format

First, output a week-view summary table:

```
         Mon    Tue    Wed    Thu    Fri
Morning  🔵     🔵     🔵     📅     🔵
Afternoon 🟡    ⚪     🟡     📅     🗂
Evening  🟢     🟢     🟢     🟢     🌙
```

Then output each day's detailed schedule in the same daily block format (see examples.md).

### Weekly Calendar Sync

After generating the weekly plan, offer to sync all 5–7 days to Google Calendar in one operation. Create events for every block across all days. Confirm total count when done: "Done — X events added across Mon–Fri."
