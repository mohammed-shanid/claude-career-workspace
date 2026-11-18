---
name: linkedin-audit
description: Recruiter-lens audit of the current LinkedIn profile across all 12 components, plus a consistency check against the resume and 2–3 positioning options. Produces analysis only, not final copy. Use after /start-here reports readiness, or when the user asks for a profile review.
argument-hint: "[component]"
---

# /linkedin-audit — LinkedIn Profile Audit

## Purpose
Find out what a recruiter sees and believes today, what's wrong, why it matters, and which direction to fix it in. **Don't write final profile copy here.** That's `/optimize-linkedin`, after the user chooses a positioning.

## Inputs
- **Required:** LinkedIn profile content (export and/or screenshots in `reference/`), `context/*`, `context/verification-register.md`.
- **Recommended:** job descriptions in `reference/job-descriptions/` (enables the keyword gap analysis).
- **Optional argument:** a single component to audit, for example `headline`.

## Gate
Read `analysis/onboarding-status.md`. If it's missing or says "not ready", tell the user why and suggest `/start-here`. Proceed only if the user explicitly says to audit anyway. In that case, treat all CONFLICTING and NEEDS VERIFICATION claims as unusable.

## Procedure

### 1. Urgent risks first
List anything on the **live** profile that is CONFLICTING or REJECTED in the register (for example, a certification that wasn't earned). These come before everything else, with a recommended immediate action.

### 2. Component audit
For each of the 12 components, use the same structure:

| Field | Content |
|---|---|
| Current state | Quote it exactly, or write "not visible in provided material". Never guess. |
| Weaknesses | Specific problems |
| Why it matters | The recruiter-lens reason: search findability, the first-impression skim, credibility, or consistency with the resume |
| Severity | Critical / High / Medium / Low |
| Fix direction | What should change and why. Not final copy. |
| Evidence needed | V-IDs or questions blocking the fix |

The 12 components:
1. Headline
2. Photo
3. Banner
4. About
5. Experience (one entry per role)
6. Education
7. Licenses & certifications
8. Skills
9. Projects
10. Featured
11. Recommendations
12. Content and creator positioning

Photo and banner: assess only from screenshots. Without them, give general guidance and label it **GENERAL (no screenshot)**.

### 3. Cross-cutting checks
- **Resume ↔ LinkedIn consistency.** Compare titles, dates, employer names, numbers, and credentials side by side.
- **Inflation scan.** Find every verb or claim that overstates the evidence level in `skills-and-projects.md`.
- **Seniority signal.** Does anything make them read as more senior than an early-career candidate? Does anything undersell them?
- **Keyword gap** (only if JDs exist). Extract the required and preferred terms from each JD, then map each to: present on profile / evidenced but missing / not evidenced (a real gap). Save the result to `analysis/keyword-analysis/YYYY-MM-DD-keyword-gap.md`. Never recommend adding a keyword they have no evidence for. Recommend a learning or project action instead.
- **Platform claims.** Don't assert how LinkedIn ranks profiles. If a recommendation depends on platform behavior, cite LinkedIn's own help pages with an access date, or label it a hypothesis.

### 4. Positioning options
Write `analysis/career-positioning/YYYY-MM-DD-positioning-options.md`. It contains 2–3 coherent positionings, for example:
- an "infrastructure generalist" positioning: Linux, cloud, networking, with DevOps direction;
- a cloud/DevOps-led positioning;
- a support-led positioning.

For each option, give:
- the one-line identity;
- the tracks it serves;
- the strongest supporting evidence;
- the weakest point a recruiter would probe;
- which target roles it helps and which it hurts.

Recommend one and give the reasoning. It must keep multiple entry-level paths open (see `CLAUDE.md` guardrails).

### 5. Prioritized fix list
Rank the fixes by impact ÷ effort. Separate them into "fix today (minutes)" and "fix after decisions".

## Output
- `analysis/profile-audits/YYYY-MM-DD-linkedin-audit.md`, with the status header from `CLAUDE.md`
- `analysis/career-positioning/YYYY-MM-DD-positioning-options.md`
- `analysis/keyword-analysis/YYYY-MM-DD-keyword-gap.md` (if JDs exist)
- A `CHANGELOG.md` entry
- Chat: the top 5 findings, the urgent risks, and the **decisions needed from the user**: positioning choice plus any blocking facts. Then point to `/optimize-linkedin`.

## Quality checks
- Every "current state" is quoted from the material or marked not visible.
- Every criticism has a fix direction.
- Facts, assumptions, and recommendations are labelled separately.
- No final copy has been written yet.
