---
name: start-here
description: Onboarding and evidence collection for the career workspace. Inventories reference material, resolves conflicting or unverified claims with the user, and reports whether the LinkedIn audit can start. Use on first run, after the user adds documents, or when asked what is still missing.
argument-hint: "[status]"
---

# /start-here — Onboarding and Evidence Collection

## Purpose
Turn scattered materials into a verified evidence base. This is the gate for everything else. Rerun it whenever new material arrives. With the `status` argument, only report readiness; don't ask questions.

## Inputs
- **Read:** `CLAUDE.md` rules, all of `context/`, `reference/README.md` (inventory), and every file in `reference/`.
- **From the user** (request whatever is missing, in this order):
  1. **Answers to CONFLICTING high-risk claims** in the register's "Priority conflicts" table.
  2. **Latest resume.** Confirm that the resume in `reference/resume/` is current, or add a newer one to `reference/resume/`.
  3. **LinkedIn:** the profile URL (already known), plus screenshots of what the PDF export omits: photo, banner, headline, Featured, Projects, full Skills list, Licenses & Certifications (with credential IDs), Recommendations, recent Activity, Open-to-Work settings. These go in `reference/linkedin/`.
  4. **Project documentation:** repo READMEs, the paper PDF or acceptance email, the award certificate. These go in `reference/projects/`.
  5. **Certificates:** PDFs, Credly or verification links, offer and experience letters. These go in `reference/certificates/`.
  6. **2–3 job descriptions** for roles they actually wants, ideally one per track. These go in `reference/job-descriptions/`.
  7. **Preferences:** the unknown fields in `context/preferences.md`.

## Procedure
1. **Inventory.** List `reference/` recursively. For any file not yet in `reference/README.md`, read it, identify what it actually is (filenames can mislead), and append a row to the inventory. Detect duplicates by checksum. Never modify, move, or rename the source files.
2. **Extract claims** from new material. Add new claims to `context/verification-register.md`, or upgrade existing ones. A third-party document (certificate, letter, publication page) → VERIFIED. The user's own resume or LinkedIn → SELF-REPORTED at most.
3. **Check public evidence** if useful: fetch the public URLs already present in their materials (GitHub repos, IEEE Xplore page). Record what was confirmed, plus the URL and access date, in the register's Sources column. Don't search for them elsewhere on the web.
4. **Ask focused questions.** Use at most 5 per round, highest risk first, and never ask anything already answered in `context/`. Use AskUserQuestion for questions with discrete answers (for example, "Was the AWS Developer – Associate exam passed? Yes / No, it was AWS Academy / Not sure"). Use plain conversation for open-ended ones.
5. **Record answers immediately.** Update the register status, the relevant context file, and `CHANGELOG.md`. If the user says a claim is wrong, mark it REJECTED and note where it currently appears publicly (for example, "still live on LinkedIn: remove").
6. **Write `analysis/onboarding-status.md`.** This is a live working document that is overwritten each run. It contains:
   - an evidence summary with counts per status;
   - the materials received and still missing;
   - unresolved high-risk claims;
   - **urgent live-profile risks**: claims on the current public LinkedIn that are CONFLICTING or REJECTED and should be fixed now, before the full optimization;
   - the readiness verdict.

## Readiness gate for `/linkedin-audit`
Ready only when **all** of these are true:
- LinkedIn content is available (the export is already present; screenshots are recommended, but the audit can proceed without them and will mark the visual sections "not assessed").
- The current resume is confirmed.
- Every **Critical/High** CONFLICTING item is either resolved, or the user has explicitly said "audit anyway". In that case the audit treats those items as unusable.
- At least one target track is prioritized, or the user agrees to let the audit propose one.

Job descriptions are recommended but not required for the audit. They are required for `/resume-optimizer`.

## Output
- Updated: `context/*.md`, `reference/README.md` (inventory rows only), `CHANGELOG.md`
- Created or overwritten: `analysis/onboarding-status.md`
- Chat summary: what changed, the remaining questions, and the readiness verdict with the exact next command.

## Quality checks
- No claim was upgraded without a document or an explicit user confirmation.
- No question repeats something already answered in `context/`.
- Private fields (phone, salary, notice period) were not copied into any non-private file.
