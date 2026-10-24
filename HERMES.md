# Hermes edition (fork of yitong0322/chronoplanner)

Adds a **coach mode** for a [Hermes Agent](https://github.com/NousResearch/hermes-agent)
profile (see the top of `SKILL.md`): when `~/coach/config.json` exists, plans are built
from files instead of an intake questionnaire, follow deep-work discipline (90-minute
deep blocks, 4-hour deep cap, shallow work batched into ≤2 windows), and are written to
`~/coach/plans/<date>.md|json` plus Google Calendar through Hermes' `google-workspace`
skill. Used together with the GPS Hermes edition (ccc592/gps-system).

Also removed: menstrual-cycle tracking, Notion/Obsidian/Slack/Gmail pre-scans; Claude
memory references now point at Hermes memory / `~/coach/calibration.md`.
