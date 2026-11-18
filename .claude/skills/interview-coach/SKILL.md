---
name: interview-coach
description: Builds a STAR story bank from genuine, verified experiences, prepares likely behavioral and technical questions for target roles or a specific interview, and runs mock interviews with feedback. Use when preparing for interviews or building interview stories.
argument-hint: "[stories | prep <company> <role> | mock [behavioral|technical] | technical <topic>]"
---

# /interview-coach — Interview Preparation (Module 5)

## Purpose
Prepare them to explain real work clearly and honestly under questioning, especially follow-up questions.

## Inputs
`context/*`, the register, the story bank (`outputs/interviews/story-bank.md`, if it exists), and the JD and application row for `prep` mode. Default mode: `stories`.

## Rules specific to this skill
- Build stories only from experiences in `context/`. If a story needs details that aren't there (what broke, what they did, what happened), **interview the user for them**, one or two questions at a time. Never fill the gaps.
- Every story marks **"My part"** vs **"Team's part"**.
- A Result can be unquantified or even negative ("the migration slipped a week; here's what I changed"). Honest results beat invented ones.
- Mark stories that rely on SELF-REPORTED or NEEDS VERIFICATION facts as such. They must be able to defend every detail.

## Modes

### `stories`: build or extend the story bank
1. Propose candidate stories from each role and project. Rank them by how many competencies they cover for the target tracks: troubleshooting under pressure, ownership, learning something fast, client or stakeholder communication, mistake and recovery, disagreement, security judgement, automation or improvement.
2. For each chosen story, gather the details from the user, then write:
   - title;
   - source (role or project, with category);
   - competencies;
   - STAR: **S**ituation, **T**ask, **A**ction (numbered, specific, "I"), **R**esult;
   - my part vs team's part;
   - evidence IDs;
   - 3 likely follow-up questions with answer notes;
   - weak points an interviewer might probe.
3. Keep a coverage table: competency → stories. Flag the gaps.

### `prep <company> <role>`: prepare for a specific interview
Map the JD requirements to stories and technical areas. Produce:
- likely behavioral questions, mapped to stories;
- likely technical questions for that role type;
- the "walk me through your resume" answer (60–90 seconds);
- the "why this role / why leave your current job" answers (honest, with no criticism of the employer);
- questions they should ask them;
- the logistics checklist.

### `mock [behavioral|technical]`: run a mock interview
Ask one question at a time and wait for their answer. Give feedback on: structure, specificity, ownership clarity, technical accuracy, length, and anything unverifiable. Then ask a realistic follow-up. At the end, summarize: strengths, the 3 fixes, and which stories need work.

### `technical <topic>`: technical explanation and drilling
Relevant areas for the target tracks include:
- **Linux:** boot, systemd, permissions, processes, logs, disk and inode issues, package management;
- **Networking:** DNS resolution path, TCP handshake, subnetting, HTTP/TLS, common ports, troubleshooting tools;
- **AWS:** EC2, IAM, VPC, S3, CloudWatch;
- **Docker, CI/CD, Terraform/Ansible;**
- **Security basics.**

Tie each topic to their own projects (for example, "explain your OIDC setup", "how does your rollback trigger", "why SSM instead of SSH"). For each topic:
- give a clear model explanation;
- list the follow-up questions an interviewer would ask next;
- list the common mistakes;
- add a **"say this only if true"** note wherever the answer would depend on their own experience.

Be technically accurate. If unsure about a detail, say so rather than guess.

## Output
- `outputs/interviews/story-bank.md`: a living document. Update it in place, and log changes in `CHANGELOG.md`. Stories the user approves are marked `APPROVED`.
- `outputs/interviews/YYYY-MM-DD-prep-<company>-<role>.md`
- `outputs/interviews/YYYY-MM-DD-mock-<type>.md` (questions, their answers in summary, feedback)
- `outputs/interviews/technical/<topic>.md`
- After interviews, update the application row in `trackers/applications.csv` (status, next action).

## Quality checks
- No invented details. "I" vs "we" is explicit. Technical content is accurate and at entry-level depth, with deeper follow-ups marked as stretch.
