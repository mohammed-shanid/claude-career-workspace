---
name: job-search-planner
description: Creates a realistic 30-day job-search plan sized to the candidate's available hours (repositioning, resume, LinkedIn, applications, outreach, interview prep), runs the weekly review from the trackers, and reports pipeline status. Use to plan the search, at each weekly review, or to check progress.
argument-hint: "[plan | weekly-review | status]"
---

# /job-search-planner — 30-Day Plan and Tracking (Modules 1 + 7)

## Purpose
Turn the search into a weekly routine they can sustain, measure it with the trackers, and adjust it based on what the numbers show. **An offer within 30 days is not guaranteed.** The plan optimizes the inputs they control.

## Inputs
- `context/target-roles.md` (tracks, chosen positioning), `context/preferences.md` (hours per week, urgency, constraints), all three trackers, `outputs/` (to judge readiness: is the LinkedIn profile approved, are tailored resumes ready, does the story bank exist?).
- **Required for `plan`:** hours per week available, and a start date. Ask if they're unknown, and save the answers to `preferences.md`.

## Modes

### `plan`: create the 30-day plan (Module 1 + Module 7)
1. **Readiness baseline.** List what's done and not done: profile, resume versions, story bank, JDs, verified credentials. Unresolved high-risk claims come first in Week 1.
2. **Capacity math.** Convert hours per week into weekly targets. State the assumptions explicitly as *planning assumptions*, not facts. For example: a tailored application takes about 45–60 minutes, a personalized outreach message about 15 minutes. Let the user adjust the assumptions. Favor fewer, tailored applications over mass applying, and explain why.
3. **Week-by-week plan.** Cover all seven Module 1 elements:
   - repositioning;
   - resume positioning;
   - LinkedIn authority (profile plus a sustainable content cadence);
   - targeted applications by track;
   - recruiter and hiring-manager outreach;
   - interview preparation (story bank, technical topics);
   - a weekly review.
   Each week lists: goals, specific tasks, target counts, and the skill commands to use.
4. **Channels.** Include job boards relevant to the candidate's market (for example, in India: LinkedIn Jobs, Naukri, Instahyre, Wellfound, company career pages), referrals, and recruiter inbound. Don't claim one channel works better than another without the user's own data. Let the weekly reviews show it.
5. **Discretion.** Because they're currently employed, note their choice of Open-to-Work visibility, and avoid public signals the employer would see. Follow `preferences.md`.
6. **Honest expectations.** Include a section on what 30 days can and can't achieve. Hiring timelines vary and are outside their control. Use leading indicators (responses, screens) to judge progress, not just offers. List the risks and what changes if Week 2 shows zero responses.

### `weekly-review`
1. Count the week's activity from `applications.csv` and `networking.csv` (by date), plus self-reported posts and prep hours (ask). Note: follow-ups due, stale applications (mark `no-response` per the `trackers/README.md` convention), and next actions overdue.
2. Diagnose using funnel ratios (applications → responses → screens → interviews), by track and by source. Be careful with small numbers: with fewer than about 10 applications, call patterns tentative.
3. Recommend 1–3 changes for next week: for example, resume version, targeting, outreach angle, or a skill gap to close.
4. Append a row to `progress.csv`. Write `outputs/job-search/YYYY-MM-DD-weekly-review.md`.

### `status`
A quick read-only snapshot: pipeline by status, follow-ups due this week, and next actions. No files written.

## Output
- `outputs/job-search/YYYY-MM-DD-30-day-plan.md` (status header; DRAFT until approved)
- `outputs/job-search/YYYY-MM-DD-weekly-review.md`, plus an appended row in `trackers/progress.csv`
- A `CHANGELOG.md` entry for plans and plan revisions.

## Quality checks
- Targets fit the stated hours. No promise of offers.
- Every task is concrete enough to tick off.
- Tracker values follow the allowed values in `trackers/README.md`.
