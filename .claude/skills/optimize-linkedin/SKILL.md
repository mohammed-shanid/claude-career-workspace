---
name: optimize-linkedin
description: Writes optimized, copy-paste-ready LinkedIn profile sections (headline with 3 evaluated variations, About, Experience, Skills, Featured, and the rest) based on a completed audit and a chosen positioning. Use only after /linkedin-audit; accepts a single section name or "all".
argument-hint: "[headline|about|experience|education|certifications|skills|projects|featured|recommendations|photo-banner|all]"
---

# /optimize-linkedin — LinkedIn Profile Rewrite

## Purpose
Produce the replacement profile copy, explaining each choice. The user applies the changes manually. **Never** edit LinkedIn directly.

## Gate (all required)
1. An audit exists in `analysis/profile-audits/`. If not, stop and point to `/linkedin-audit`.
2. "Chosen positioning" in `context/target-roles.md` is filled in. If not, present the options from `analysis/career-positioning/`, ask the user to choose, and record the choice.
3. For each section: every fact used is VERIFIED or CONFIRMED BY USER. SELF-REPORTED facts may appear in a DRAFT with an inline `[SELF-REPORTED: V-xxx]` marker. Anything else becomes a `[NEEDS VERIFICATION: …]` placeholder. Never quietly drop or soften a claim the user hasn't decided on. Show it as blocked.

## Inputs
The latest audit, positioning options, all of `context/`, and JDs (for keywords). Argument: the section to produce (default `all`).

## Section instructions

**Headline (Module 3).** Write 3 variations. Evaluate each in a table scored on Recruiter relevance / Role clarity / Technical keywords / Credibility / Differentiation, with a short note per criterion rather than numeric scores. Give strengths and weaknesses for each, then a recommendation. Respect the character counter in LinkedIn's editor and show each variation's character count. The headline should say what they do and for which roles, not a title they doesn't hold.

**Photo and banner.** Give recommendations only: what to change and why. For the banner, suggest a simple text or visual concept, such as a stack line or an architecture motif. If the visual sections weren't assessed, say so.

**About.** Write one recommended version and one alternative. The opening lines must work on their own, because LinkedIn truncates the About section behind "see more". Structure: what they do → evidence (roles, projects, publication) → what they're looking for → how to reach them. Use first person and plain language, and keep it consistent with the resume.

**Experience.** For each role, check that the title matches the verified official title and that the employment type is set. Write 3–5 bullets, matching verbs to evidence levels. Separate "I" from "we". Leave out confidential employer detail.

**Education.** Write one clean entry per degree, with the exact name from the certificate. Flag duplicate entries for deletion.

**Licenses & certifications.** List only VERIFIED or CONFIRMED BY USER credentials, each with its exact name, issuer, date, and credential ID or URL. Training without an exam goes under Courses or Training, not Certifications.

**Skills.** Recommend skills ordered by target-role relevance. Include only skills they could be questioned on in an interview. List which current skills to remove or deprioritize, and why.

**Projects.** For each project: name, one-line problem, their role, stack, a verifiable outcome, and a link.

**Featured.** Recommend 3–5 items, such as repos, the paper, or a project write-up. For each, say why and add a short caption.

**Recommendations.** Suggest who to ask: managers, intern supervisors, clients. Draft a short request message. You may list points the recommender *could* mention, but **never write the recommendation text itself**, because it must be the recommender's own words.

**Content positioning.** Write 2–3 sentences on what content would reinforce the positioning, then hand off to `/linkedin-content`.

## Output
- `outputs/linkedin/YYYY-MM-DD-profile-draft.md`, with `Status: DRAFT`. It contains, per section:
  - the current text;
  - the new text in a copy-paste code block, with its character count;
  - the rationale;
  - the evidence IDs;
  - any blocked items.
- A **manual application checklist** at the end, in the order to apply changes. Include visibility tips, such as turning off "share profile updates with network" while making bulk edits, if they prefer that. That is a user choice; present it as an option.
- When the user approves: set `Status: APPROVED` and add a `CHANGELOG.md` entry. Later revisions go in a new dated file.

## Quality checks
- No banned buzzwords (see `CLAUDE.md`), and no seniority inflation.
- Every number traces to a V-ID.
- Titles, dates, and credentials are identical to the current resume, or the resume is flagged for update via `/resume-optimizer`.
- Each section uses the target-role keywords from the JDs only where evidence exists.
