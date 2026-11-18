---
name: linkedin-content
description: Plans and drafts authentic technical LinkedIn posts (Linux, cloud/AWS, networking, security, DevOps learning, projects, troubleshooting lessons) grounded in the candidate's real work, or reviews a draft they wrote. Never posts. Use for a content calendar, a specific post, or feedback on a draft.
argument-hint: "[plan | draft <topic> | review]"
---

# /linkedin-content — Technical Content Strategy

## Purpose
Show real technical credibility through useful posts, at a pace they can sustain. Quality and accuracy matter more than frequency. **Claude drafts; they post.**

## Inputs
- The chosen positioning (`context/target-roles.md`). Content should reinforce it. If no positioning is chosen yet, recommend running `/linkedin-audit` first, but allow `draft` for a clearly standalone topic.
- `context/preferences.md` (willingness to post, frequency, topics to avoid), `context/skills-and-projects.md`, the register.
- **Raw material from them.** Every post must come from something real: a lab they did, a bug they fixed, a config they wrote, a concept they learned. Ask for the specifics: the commands, errors, what they tried, what worked. Never invent an experience or a "lesson".

## Modes

### `plan`
Write a 4-week calendar at a sustainable cadence. Default to 1 post per week unless they want more. Each entry has a theme, a working title, the source material it needs from them, and how it supports the positioning.

Themes to draw from:
- Linux administration;
- cloud infrastructure and AWS labs;
- networking and security;
- the DevOps learning journey;
- project breakdowns (from the projects in `context/skills-and-projects.md`);
- real troubleshooting lessons.

Save it to `outputs/content/content-plan.md`. This is a living document; log changes in `CHANGELOG.md`.

### `draft <topic>`
Produce:

| Field | Content |
|---|---|
| Topic | |
| Target audience | For example, recruiters for cloud support roles, or junior engineers learning Terraform |
| Objective | What a reader should think or know afterward |
| Opening hook | Specific and concrete, not clickbait |
| Complete draft | The full post |
| Technical details | Commands, configs, concepts. Check them for accuracy, and flag anything uncertain. |
| Suggested visual | Architecture diagram, redacted terminal screenshot, before/after. Optional. |
| Evidence IDs | V-IDs or source material |
| Redaction check | No secrets, keys, internal hostnames or IPs, client names, employer internals |

### `review`
They paste their draft. Give feedback on: technical accuracy, clarity, the hook, length, credibility risks, redaction, and consistency with their profile claims. Suggest specific edits and keep their voice.

## Content rules
- **No:**
  - engagement bait ("Comment YES", "Agree?", "Like if…");
  - fabricated stories;
  - fake thought leadership or generic motivation;
  - "I'm thrilled to announce" boilerplate;
  - copying or closely paraphrasing other creators;
  - hashtag stuffing (use a few relevant hashtags at most);
  - emoji walls.
- Make no claims about how LinkedIn's algorithm ranks posts. If timing or format advice is given, label it a hypothesis, or cite LinkedIn's own documentation with an access date.
- Posts about the current employer's systems need their confirmation that they're shareable.
- Use first person, plain language, and a learning tone where that's accurate. Never overstate expertise.

## Output
- `outputs/content/YYYY-MM-DD-<slug>.md` per post, with the status header. Mark it `APPROVED` when they approve, and `PUBLISHED <date>` after they post it themselves.
- Count published posts in `posts_published` during `/job-search-planner weekly-review`.

## Quality checks
- Every claim is true and technically accurate. Nothing sensitive is exposed.
- The post is useful to the stated audience even if they never hire them.
