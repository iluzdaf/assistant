# Job Run Log

- Shared convention for recording actual assistant job activity.
- Use this log so daily reviews can summarize runs from durable local evidence, not only automation memory or ad hoc notes.

## Location

- Write one Markdown file per local day.
- Default path: `$CODEX_HOME/automations/assistant/run-log/YYYY-MM-DD.md`.
- If `$CODEX_HOME` is unset, use `~/.codex/automations/assistant/run-log/YYYY-MM-DD.md`.
- Create the directory and dated file when missing.
- Treat the file as append-only during the day.

## When To Write

- Add one entry for each attempted runnable job.
- Include no-op runs when the job was checked and had no work to do.
- Write completion entries only after the job completion check passes.
- If a job fails before completion, write a failure entry after capturing the failure evidence.
- Do not record secrets, private message bodies, full email contents, or long raw command output.

## Entry Template

```md
## HH:MM local - job-name - status

- Run window: YYYY-MM-DD HH:MM to YYYY-MM-DD HH:MM local time
- Trigger: heartbeat, daily review, manual request, or other
- Status: completed, no-op, failed, or blocked
- Work done: Short factual summary
- Outputs: Bear note titles, labels, file paths, or none
- Evidence: Completion check, failure evidence, or explicit evidence gap
- Follow-up: Next action, owner, or none
```
