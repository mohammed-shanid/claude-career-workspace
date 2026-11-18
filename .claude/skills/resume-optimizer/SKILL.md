---
name: resume-optimizer
description: ATS-aware resume analysis and tailoring for a specific target role or job description. Finds weak descriptions and missing evidence, rewrites the summary and three key bullets, and produces a tailored LaTeX copy without touching the original. Use when the user targets a role or posting.
argument-hint: "<target role | path to JD in reference/job-descriptions/>"
---

# /resume-optimizer — Resume Analysis and Tailoring (Module 2)

## Purpose
Make the resume more relevant and credible for one target role, for both ATS parsing and a human skim. **Never guarantee ATS selection.**

## Inputs
- **Required:** a target. Either a JD file path (preferred) or a role name from `context/target-roles.md`. If neither is given, ask.
- **Resume:** the newest file in `reference/resume/`, otherwise the resume source the user names. Confirm which one if that's ambiguous.
- `context/*`, the register, and the latest LinkedIn draft in `outputs/linkedin/` if one exists (for consistency).

## Gate
- **Never edit files in `reference/`.** Work on a copy.
- If the target is a role name with no JD, proceed, but say the keyword analysis is generic and less reliable. Recommend adding a real JD.

## Procedure
1. **Parse the resume.** Note its structure, sections, length, and any ATS-risk formatting. If the skills section is a table (for example a LaTeX `tabular`) or the layout uses columns, note it: some parsers handle these poorly, so flag it as a *possible* risk, not a certainty.
2. **Analyze the JD.** Extract must-have and nice-to-have requirements, tools, and responsibilities. Build a matrix: requirement → evidence (V-ID or resume line) → **Strong / Partial / Gap**.
3. **Weak-spot review.** List the weak descriptions (vague, duty-not-outcome, verb overstates evidence, buried relevance) and the missing evidence (claims with no example). For each, explain why it's weak and what would fix it, including the question to ask the user.
4. **Rewrite the professional summary** for this target. Write 2–3 lines, entry-level honest.
5. **Improve three major achievement bullets.** Choose the three with the highest relevance to the JD. For each, show before → after → why → evidence IDs. Quantify only from the register. If a number would help but doesn't exist, ask the user for it and leave the bullet unquantified in the meantime.
6. **Tailored version (optional, on request or by default for JD targets).** Copy the resume `.tex` to the output folder and apply the changes there: reorder skills toward the JD, adjust the header line, swap in the new summary and bullets, and drop low-relevance items to stay at one page. Keep everything consistent with LinkedIn (titles, dates, numbers, credentials).
7. **Compile check.** `pdflatex` is available locally. Compile in the output folder and confirm the result is one page. If compilation fails, report the error and don't hide it.
8. **ATS readability checklist.** Check for: standard section headings, a consistent date format, contact information in the body (not a header or footer), no text in images, and a text layer you can extract from the PDF. Name the file `Firstname_Lastname_<Role>.pdf`.

## Output
`outputs/resumes/YYYY-MM-DD-<role-slug>/` containing:
- `analysis.md`: status header, JD matrix, weak spots, summary rewrite, three bullet rewrites, open questions, and the gaps that **cannot** be fixed with wording (with a learning or project suggestion for each).
- `resume.tex` and the compiled `resume.pdf` (if a tailored version was produced).
- A `CHANGELOG.md` entry. When used for an application, put the folder path in the `resume_version` column of `trackers/applications.csv`.

## Quality checks
- No new skills, tools, or metrics appear that aren't in the register.
- Verbs match the evidence levels in `skills-and-projects.md`.
- The resume and LinkedIn tell the same story. List any remaining differences explicitly.
- It is one page, and it reads cleanly in a 30-second human skim.
