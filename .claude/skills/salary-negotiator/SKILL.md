---
name: salary-negotiator
description: Compensation assessment and negotiation preparation based on an actual offer, the candidate's own figures, and cited market sources only — strategy, counteroffer email, talking points, likely employer responses and alternatives. Use when the user has an offer, or wants to prepare for compensation questions.
argument-hint: "[prep | offer <company>]"
disable-model-invocation: true
---

# /salary-negotiator — Compensation Negotiation (Module 6)

## Purpose
Help them negotiate confidently with real numbers. **Never invent salary benchmarks.** Everything here is **PRIVATE**.

## Modes and gates
- **`offer <company>`** (full mode) requires actual offer details: role and level, fixed pay, variable or bonus, joining bonus, other CTC components (for example PF or insurance, as listed on the offer), location and work mode, start date, notice-period expectations, offer deadline. If the offer is only verbal, note it and recommend asking for the details in writing.
- **`prep`** (no offer yet) prepares answers for "what are your expectations?" and "what's your current CTC?" using their own data and any cited market evidence.

## Inputs
- The offer details, or their current compensation (PRIVATE, stored only in this skill's output file).
- Their walk-away number and target, which only they can set. Ask; don't propose numbers out of nowhere.
- Competing offers or processes, if any.
- **Market evidence:** only with a named source, URL, access date, and caveats (self-reported data, sample size, role and level mismatch, city). Use web search only if the user agrees. If reliable data isn't found, write **"No reliable market data found"**. Don't estimate.

## Procedure
1. **Compensation assessment.**
   - Break down the offer: fixed vs variable, one-time vs recurring, guaranteed vs conditional.
   - Compare it to their own current pay, their target, and any cited market data.
   - State clearly what is a fact and what is an assumption.
2. **Leverage check.** Assess honestly. Count as leverage: competing offers, scarce verified skills for this role, and a short notice period. Don't count as leverage: claims they can't support. An early-career candidate usually has limited leverage, so plan for that.
3. **Strategy.**
   - What to ask for, and the single priority.
   - The anchor, with a justification they can say aloud.
   - The walk-away point.
   - The sequence: verbal first, then written.
   - Timing relative to the offer deadline.
4. **Counteroffer email.** Keep it short, appreciative, and specific, with one clear ask and its justification.
5. **Talking points** for a phone or video conversation, including how to handle "what's your current CTC?" and "this is our best offer".
6. **Possible employer responses**, each with a suggested reply: yes, partial, no, "we'll revisit at appraisal", and pressure to decide fast.
7. **Alternatives if base pay is fixed:**
   - joining bonus;
   - an earlier review date, written into the offer;
   - certification or training sponsorship (relevant for AWS or other credentials);
   - remote or hybrid days;
   - start-date flexibility;
   - notice-period buyout.
   Never negotiate the title upward beyond the real role.

## Output
`outputs/negotiation/YYYY-MM-DD-<company>.md` (or `-prep.md`), with the status header and a **PRIVATE** banner. Never copy figures into any other file except the `notes` column of `trackers/applications.csv`, and only if the user wants that.

## Quality checks
- Every market figure has a source and access date, or is absent.
- No guarantee that the employer will agree.
- The plan works even if the answer is no: they know their walk-away in advance.
