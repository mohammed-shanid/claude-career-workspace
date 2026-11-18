---
name: recruiter-outreach
description: Drafts personalized, under-100-word outreach messages and follow-ups for a specific recruiter, hiring manager, engineer or alum about a specific company and role, and logs them in the networking tracker. Never sends anything. Use when the user has a named contact and a concrete opening or reason to reach out.
argument-hint: "<company> <role> [contact name/title]"
---

# /recruiter-outreach — Personalized Outreach (Module 4)

## Purpose
Write messages a busy recruiter or engineer would actually answer: specific, short, credible, and easy to say yes to. **Claude drafts; the user sends.**

## Inputs (ask for any that are missing; don't write generic messages)
- **Company and role.** A JD file or link if possible.
- **Recipient:** name, title, and type (`recruiter`, `hiring-manager`, `engineer`, `alumni`, `referral`). Also the relationship: none, shared connection, alum, or met before.
- **Genuine reason:** an open posting, their post or article, a team technology match, or a shared background. If there is no genuine reason, say the message will be weak and suggest finding one.
- **Channel:** LinkedIn connection note (short, and LinkedIn limits the length, so check the editor's counter), LinkedIn message, or email.
- **Evidence:** pick the single most relevant VERIFIED or CONFIRMED BY USER fact for this role, using `context/` and the register.

## Procedure
1. Choose the **ask** for the recipient type:
   - recruiter → whether their profile fits, or the right person to talk to;
   - hiring manager → a short conversation or consideration for the role;
   - engineer or alum → a 15-minute chat about the team, or a referral, but only if rapport exists or they offered.
2. Draft the **initial message** (under 100 words; connection-note version within the note limit). Structure: who I am in one line → why them and this role → one piece of evidence → one clear ask → thanks.
3. Draft **follow-up 1** (suggest sending 5–7 business days later, as a convention, not a rule) that adds something new, such as a project link or a relevant update. Then draft a **final follow-up / close-the-loop**. Never guilt-trip.
4. If the recipient type suits it, also draft a **referral request** variant.
5. Run a self-check against the quality list below, and show word and character counts.

## Output
- `outputs/outreach/YYYY-MM-DD-<company>-<role-slug>.md`: status header, context (recipient, reason, evidence used with its V-ID), the messages, counts, and the suggested follow-up dates.
- Append a row to `trackers/networking.csv` with `status=drafted` and `message_file` set. The user changes it to `sent` and fills `date_sent` after sending.
- Keep recipient names out of anything public.

## Quality checks
- Under 100 words (connection notes: within the limit). Mentions the specific company and role.
- Exactly one evidence point, and it is true. Exactly one ask.
- None of these: "I'm passionate", "I hope this finds you well", flattery, attachments pushed unasked, "please share my resume with anyone", a request for a job outright from a stranger, or any promise of results.
- Reads like a person wrote it. Read it aloud mentally, and cut anything stiff.
