# ChronoPlanner — Examples Reference

Load this file when you need a worked example to verify output format, or when a user asks to see a sample plan.

---

## Example 1: Standard Single Day (Intermediate Chronotype, Average State)

**Input:**
- Wake: 7:00, Intermediate chronotype
- Sleep: 7.5h, feeling Normal → 45-min blocks
- Morning: gym 45 min
- Fixed: lunch 12:30–13:30, team meeting 15:00–16:00
- Tasks: project report (90 min, high, home), LeetCode (60 min, high, home), emails (30 min, low, home), Anki (30 min, mid, home)
- Weather: sunny 26°C
- End by: 21:00

**Output:**
```
[07:00–07:45] 🏋️ Gym (45 min) — BDNF + norepinephrine boost; deep focus window opens immediately after
[07:45–08:45] ☕ Dopamine cool-down + breakfast (60 min) — cortisol rising; no high-stimulation content
[08:45–09:30] 🔵 Project report (45 min) — peak cortisol + BDNF; hardest task first (Eat the Frog)
[09:30–09:40] 😴 Break: step outside briefly (10 min) — sunny 26°C, good conditions
[09:40–10:25] 🔵 Project report cont. (45 min)
[10:25–10:35] 😴 Break: diaphragmatic breathing (10 min)
[10:35–11:20] 🔵 LeetCode (45 min) — still in golden window; second high-priority task
[11:20–11:30] 😴 Break: walk outside (10 min)
[12:30–13:30] 🍽️ Lunch (fixed anchor)
[13:30–14:00] ⚪ Emails (30 min) — energy trough; batched admin only
[14:00–14:30] 😴 Break: power nap ≤ 20 min or outdoor walk without earphones
[15:00–16:00] 📅 Team meeting (fixed anchor)
[19:30–20:00] 🟢 Anki review (30 min) — memory consolidation window; pre-sleep retention peak
[20:00–21:00] 🌙 Wind down — journaling, light reading; no new input

📊 Deep focus 2.25h · Admin 30min · Review 30min · Done by 21:00 ✓
🌤️ Weather: sunny 26°C — outdoor breaks recommended at 09:40 and 11:20.

Would you like me to add this to your Google Calendar?
```

---

## Example 2: Night Owl, Poor State

**Input:**
- Wake: 9:00, Night Owl chronotype
- Sleep: 5.5h, feeling Groggy → 25-min blocks
- No morning exercise
- Fixed: lunch 13:00–14:00
- Tasks: essay writing (90 min, high, home), research reading (60 min, mid, home), reply emails (30 min, low, home)
- Weather: rainy
- End by: 22:00

**Output:**
```
[09:00–11:30] ☕ CAR + dopamine cool-down (150 min) — Night Owl: first 2.5h post-wake are low-function; no hard tasks; light breakfast, no high-stimulation content
[11:30–11:55] 🔵 Essay writing (25 min) — approaching golden window; short block due to poor sleep state
[11:55–12:00] 😴 Break: look out window / stretch (5 min) — rainy: indoor breaks only
[12:00–12:25] 🔵 Essay writing cont. (25 min)
[12:25–12:30] 😴 Break: diaphragmatic breathing (5 min)
[13:00–14:00] 🍽️ Lunch (fixed anchor)
[14:00–14:30] 😴 Break: power nap ≤ 20 min
[14:30–14:55] 🔵 Essay writing cont. (25 min) — entering Night Owl golden window
[14:55–15:05] 😴 Break: indoor walk / stretch (10 min) — rainy weather, indoor only
[15:05–15:30] 🟡 Research reading (25 min)
[15:30–15:40] 😴 Break: doodling / mind-wander (10 min)
[15:40–16:05] 🟡 Research reading cont. (25 min)
[16:05–16:35] ⚪ Reply emails (30 min) — approaching trough; admin batch
[20:00–20:30] 🟢 Review essay notes (30 min) — memory consolidation window
[21:00–22:00] 🌙 Wind down — no new input; light reading only

📊 Deep focus 1.25h · Creative 50min · Admin 30min · Review 30min · Done by 22:00 ✓
⚠️ Poor sleep note: only 25-min blocks used. Consider rescheduling essay writing's remaining 40 min to tomorrow if quality feels low.
🌧️ Weather: rainy — all breaks moved indoors.
```

---

## Example 3: Location Change with Commute

**Input:**
- Wake: 6:30, Intermediate chronotype
- Sleep: 8h, feeling Sharp → 60-min blocks
- Morning: no exercise
- Fixed: lunch 12:00–13:00
- Tasks: deep coding (120 min, high, home), study at NTU library (90 min, high, NTU Library), gym (60 min, mid, Gym)
- Commute: Home → NTU: 25 min; NTU → Gym: 15 min
- Weather: clear 29°C
- End by: 20:00

**Output:**
```
[06:30–07:30] ☕ Dopamine cool-down + breakfast (60 min) — CAR peak; no high-stimulation content
[07:30–08:30] 🔵 Deep coding (60 min) — peak cortisol window; highest-priority task first
[08:30–08:45] 😴 Break: step outside (15 min) — 29°C, sunny
[08:45–09:45] 🔵 Deep coding cont. (60 min)
[09:45–10:00] 😴 Break: stretch / walk around (15 min)
[12:00–13:00] 🍽️ Lunch (fixed anchor)
[13:30–13:55] 🚌 Commute: Home → NTU Library (25 min) — recommended: podcast or language listening
[13:55–14:55] 🔵 NTU Library study (60 min) — afternoon secondary peak; location change batched after lunch
[14:55–15:10] 😴 Break: look out library window (15 min)
[15:10–15:55] 🔵 NTU Library study cont. (45 min)
[18:45–19:00] 🚌 Commute: NTU Library → Gym (15 min) — recommended: audiobook
[19:00–20:00] 🏋️ Gym (60 min) — evening exercise; body temp still elevated

📊 Deep focus 2.75h · Library study 1.75h · Gym 1h · Commute 40min · Done by 20:00 ✓
🌤️ Weather: clear 29°C — outdoor breaks at 08:30; commute walks are comfortable.

Would you like me to add this to your Google Calendar?
```

---

## Example 4: Weekly Plan (Excerpt)

**Week-view table:**
```
         Mon      Tue      Wed      Thu      Fri
Morning  🔵🔵    🔵🔵    🔵🔵    📅📅    🔵🔵
Afternoon 🟡⚪   🟡      🟡      📅      🗂🌙
Evening  🟢      🟢      🟢      🟢      🟢🌙
```

**Monday detail (excerpt):**
```
[08:00–09:00] 🔵 Thesis writing (60 min)
[09:00–09:15] 😴 Break: outdoor walk
[09:00–10:00] 🔵 Thesis writing cont. (60 min)
[13:00–13:30] ⚪ Email batch (30 min) — trough
[14:00–15:00] 🟡 Research reading (60 min)
[20:00–20:30] 🟢 Anki (30 min)
```

*(Full daily schedules follow same format as Examples 1–3)*
