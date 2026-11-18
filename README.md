# Claude Career Workspace

**A job-search workspace for [Claude Code](https://claude.com/claude-code) that refuses to make things up.**

Most AI resume tools will happily turn "helped with deployments" into "led a cloud migration that cut costs 40%." That gets you through a keyword filter and then sinks you in the first technical interview.

This workspace works the other way. Every claim about you is logged in a **verification register** with its source and status. Every resume line, LinkedIn section and interview story is built only from claims that pass. When a number doesn't exist, it asks you instead of inventing one.

It's plain Markdown, CSV and LaTeX. There is nothing to install, no database and no web app. Open the folder in Claude Code and run a slash command.

---

## What it does

| Command | What you get |
|---|---|
| `/start-here` | Inventories your resume, LinkedIn export and documents, finds claims that contradict each other, and asks you to resolve them before anything gets written |
| `/linkedin-audit` | A recruiter-lens review of all 12 profile sections, a resume-vs-LinkedIn consistency check, and 2–3 positioning options with trade-offs |
| `/optimize-linkedin [section]` | Copy-paste-ready profile sections: 3 scored headline variations, About, Experience, Skills, Featured |
| `/resume-optimizer <job description>` | A requirement → evidence matrix (Strong / Partial / Gap), rewritten summary and bullets with before → after → why, and a tailored one-page LaTeX resume, compiled and checked for a clean text layer |
| `/recruiter-outreach` | Under-100-word messages and follow-ups for a named person and a real opening, logged in a tracker. Never sent for you |
| `/interview-coach` | A STAR story bank built only from verified experience, likely questions for a specific interview, and mock interviews with feedback |
| `/job-search-planner` | A 30-day plan sized to the hours you actually have, plus weekly reviews driven by your tracker numbers |
| `/linkedin-content` | Technical post drafts grounded in work you really did, or feedback on your own draft |
| `/salary-negotiator` | Negotiation prep from a real offer and cited market data only. No invented benchmarks |

## How the evidence system works

```text
your resume, LinkedIn export,          context/verification-register.md
certificates, public repos,     ──►    every claim + source + status
your answers in conversation           (VERIFIED, CONFIRMED BY USER, SELF-REPORTED,
                                        NEEDS VERIFICATION, CONFLICTING, REJECTED)
                                                      │
                                                      ▼
                                   only VERIFIED / CONFIRMED BY USER claims
                                   reach approved public material
```

- **Your resume and LinkedIn are treated as claims, not evidence.** When they disagree (dates, titles, client counts), the conflict is flagged and stays out of final copy until you resolve it.
- **Verbs match the evidence.** "Studied", "used", "built" and "maintained in production" are different claims, and the skills map records which one applies.
- **"I" and "we" stay separate.** Team results aren't attributed to you alone.
- **Public checks are logged.** When a claim can be checked on a public page (a GitHub repo, a publication record), the URL and access date go into the register.
- **No guarantees.** It never promises ATS selection, recruiter replies or offers, and it doesn't claim to know LinkedIn's ranking algorithm.

## What it will never do

- Post, send, apply, connect or edit anything on LinkedIn, email or job portals. Everything is a draft you act on yourself.
- Put your phone number, address, salary or anything you mark private into public-facing material.
- Overwrite an approved document. New versions get a new date, and every substantive change is logged in `CHANGELOG.md`.

## Quick start

1. **Use this template, then make your copy private.** Your copy will hold your phone number, salary expectations and application history.
2. Put your resume in `reference/resume/` and your LinkedIn PDF export in `reference/linkedin/`.
3. Open the folder in Claude Code and run:

```text
/start-here        # collects your evidence and resolves conflicting facts
/linkedin-audit    # section-by-section critique of your current profile
/optimize-linkedin # rewritten profile copy (only after the audit)
```

4. Paste a job description into a chat, or save it in `reference/job-descriptions/`, and run `/resume-optimizer`.

LaTeX resume compilation needs `pdflatex` installed locally. Everything else is plain text.

## Folder map

```text
CLAUDE.md                 Rules Claude follows in every session
CHANGELOG.md              Record of every substantive change
context/                  What's known about you, and how sure it is
  verification-register.md  Every claim, with its source and status (the single source of truth)
  career-profile.md         Identity, education, credentials, seniority
  experience.md             Each role, with discrepancies and open questions
  skills-and-projects.md    Skills mapped to evidence levels; projects
  target-roles.md           Target roles grouped into tracks; chosen positioning
  preferences.md            Location, work mode, constraints (some fields private)
reference/                Your source material. Claude never edits it
analysis/                 Audits, positioning options, onboarding status
outputs/                  Drafts and approved deliverables, one folder per module
trackers/                 applications.csv, networking.csv, progress.csv
.claude/skills/           One folder per slash command, with the full workflow
```

## Who it's for

It was built for an early-career technical job search: cloud, DevOps, Linux, support and security roles. Some defaults reflect that, such as the interview-coach technical topics and the example job boards. The evidence rules, trackers and workflow apply to any field. Change `context/target-roles.md` and the skills follow it.

## Customizing

- **Tracks and roles:** edit `context/target-roles.md` and the `track` values in `trackers/README.md`.
- **Rules:** `CLAUDE.md` is short on purpose. Add your own guardrails, such as words to avoid or claims never to make.
- **Workflows:** each skill is a single `SKILL.md` in `.claude/skills/<name>/`. Edit the procedure directly.

## Credits

The module structure (30-day plan, resume rewrite, headline writer, cold outreach, interview stories, salary negotiation, job-search map) was inspired by a set of seven career prompts shared on social media; the original author is unknown. The evidence register, verification rules and skills in this repo are new work built on top of that idea.

## License

MIT. See `LICENSE`.
