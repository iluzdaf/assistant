# Job Run Log

- Shared convention for recording actual assistant job activity.
- Use this log so daily reviews can summarize runs from durable local evidence, not only automation memory or ad hoc notes.

## Location

- Write all job activity to one canonical Bear note.
- Title: `Assistant Job Run Log`.
- Tags: `#assistant #job-run-log`.
- Create the canonical Bear note when missing.
- Treat the note as append-only.
- Group entries under one local-date heading per day: `## YYYY-MM-DD`.
- Keep local-date sections in newest-first order, with the latest date at the top.
- Link to output Bear notes by title when a job creates or updates them.

## How To Write

- Use `docs/bear-cli.md` for Bear commands.
- Search for the exact canonical title before writing.
- If the note does not exist, create it with the required title and tags.
- Append new entries to the end of the relevant local-date section.
- If the local-date section does not exist, insert it above the previous latest date section before adding entries for that date.
- Do not create a second section for a date that already exists.
- Verify the saved entry before treating the run-log write as complete.

## When To Write

- Add one entry for each attempted runnable job.
- Include no-op runs when the job was checked and had no work to do.
- Write completion entries only after the job completion check passes.
- If a job fails before completion, write a failure entry after capturing the failure evidence.
- Do not record secrets, private message bodies, full email contents, or long raw command output.

## Entry Template

```md
## YYYY-MM-DD

### HH:MM local - job-name - status

- Run window: YYYY-MM-DD HH:MM to YYYY-MM-DD HH:MM local time
- Trigger: heartbeat, daily review, manual request, or other
- Status: completed, no-op, failed, or blocked
- Work done: Short factual summary
- Outputs: Bear note titles, labels, file paths, or none
- Evidence: Completion check, failure evidence, or explicit evidence gap
- Follow-up: Next action, owner, or none
```
