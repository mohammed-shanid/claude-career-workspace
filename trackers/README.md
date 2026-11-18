# Trackers

These are plain CSVs, so open them in any spreadsheet app. Skills read and append to them. **Use the allowed values exactly**, because weekly reviews count them.

Private file: these trackers contain names of real people and application details. Don't share them publicly.

## applications.csv

| Column | Meaning / allowed values |
|---|---|
| id | `A-001`, `A-002`, … |
| date_added | YYYY-MM-DD |
| company, role, location | Free text |
| track | Your track codes from `context/target-roles.md` (default: `A`, `B`, `C`, `other`) |
| work_mode | `onsite`, `hybrid`, `remote`, `unknown` |
| source | `linkedin-jobs`, `naukri`, `company-site`, `referral`, `recruiter-inbound`, `instahyre`, `wellfound`, `other` |
| job_url, jd_file | Link; path in `reference/job-descriptions/` |
| resume_version | Path in `outputs/resumes/` that was sent |
| referral_contact_id | `N-xxx` from networking.csv, if any |
| status | `saved`, `applied`, `screening`, `interviewing`, `offer`, `rejected`, `withdrawn`, `no-response` |
| date_applied, last_update, next_action_date | YYYY-MM-DD |
| next_action, notes | Free text |

Mark `no-response` 21 days after applying with no reply. This is a working convention, not an industry rule. Adjust it if you like.

## networking.csv

| Column | Meaning / allowed values |
|---|---|
| id | `N-001`, … |
| date | Date the row was created (YYYY-MM-DD) |
| name, title, company | The person |
| contact_type | `recruiter`, `hiring-manager`, `engineer`, `alumni`, `referral`, `other` |
| channel | `linkedin-connect`, `linkedin-message`, `email`, `in-person`, `other` |
| linked_application_id | `A-xxx`, if tied to an application |
| purpose | `referral`, `role-inquiry`, `advice`, `follow-up`, `thank-you` |
| message_file | Path in `outputs/outreach/` |
| status | `drafted`, `sent`, `accepted`, `replied`, `meeting`, `referred`, `no-response`, `closed` |
| date_sent, follow_up_date | YYYY-MM-DD |
| outcome, notes | Free text |

**Claude drafts and sets `drafted`. You send the message and change it to `sent`.**

## progress.csv

One row per week, appended by `/job-search-planner weekly-review`.

| Column | Meaning |
|---|---|
| week | `W1`, `W2`, … |
| start_date, end_date | YYYY-MM-DD |
| applications_sent … rejections | Counts for that week, from the other two trackers |
| posts_published | LinkedIn posts actually published |
| prep_hours | Interview and technical prep hours (self-reported) |
| profile_changes | Short note on LinkedIn or resume changes applied |
| what_worked, what_to_change | One line each |
