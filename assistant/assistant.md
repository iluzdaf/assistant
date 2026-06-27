# Assistant

- Repo-first source of truth for all jobs.
- Inspect every runnable job for due work before selecting task-specific files.
- Run every due job, not only the first or most obvious heartbeat job.
- Update automation memory only after completion checks pass.

## Instruction Policy

- Read `jobs/README.md` and `docs/README.md` as routing docs before selecting task-specific files.
- For heartbeat runs, enumerate all `jobs/*.md` files, read each `Due Rule`, and record the due/not-due decision before running due jobs.
- For task-specific work, read only the relevant job files, templates, and tool docs before editing or running that task.
- Do not recursively read all job and docs files unless the task requires a repo-wide instruction audit.

## Where To Look

- `jobs/README.md`: how runnable job files are structured.
- `jobs/clipping-triage.md`: weekly job for web-clipper note triage.
- `jobs/daily-review.md`: morning review job for assistant activity and workflow recommendations.
- `jobs/email-triage.md`: heartbeat job for Gmail and email review-note triage.
- `jobs/product-issue-triage.md`: heartbeat job for configured GitHub product issue triage.
- `jobs/topic-curation.md`: weekly job for topic article curation.
- `docs/README.md`: shared reference docs for Bear details.
- `docs/bear-cli.md`: Bear note commands and conventions.
- `docs/daily-review-template.md`: template for daily assistant review note sections.
- `docs/job-run-log.md`: Bear run-log convention for job activity evidence.
- `docs/github-issue-triage.md`: GitHub issue read/write conventions for product issue triage.
- `docs/product-issue-review-card-template.md`: Bear card template for product issues needing human intervention.
- `docs/email-writing-guide.md`: reply style guide for email drafts.
- `docs/email-review-template.md`: template for email review note sections.
- `docs/email-summary-template.md`: template for email summary note sections.

## Working Style

- Keep machine-specific config local.
- Keep shared rules in one place.
- Keep instructions short and direct.
- Avoid repeating shared guidance in job specs.
