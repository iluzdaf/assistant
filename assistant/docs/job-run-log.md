# Job Run Log

- Shared convention for recording actual assistant job activity.
- Use this log so daily reviews can summarize runs from durable local evidence, not only automation memory or ad hoc notes.

## Location

- Write all job activity to one canonical Bear note.
- Title: `Assistant Job Run Log`.
- Tags: `#assistant/job-run-log`.
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
- Write GitHub issue references as `issue 123`, `owner/repo issue 123`, or the full issue URL.
- Do not write bare `#123` or `owner/repo#123` issue references in Bear note body text; Bear treats hash tokens as tags and adds noise to the tag list.
- Keep hash tags only for intentional Bear tags, such as the canonical footer tag.
- Verify the saved entry before treating the run-log write as complete.
- Include a compact `Open triaged inbox threads` line in heartbeat-dispatch and email-triage entries when the inbox still contains already-triaged mail, so it is clear that the thread is open in inbox but not new work.

## How To Read A Bounded Date Section

- Do not export the full `Assistant Job Run Log` for routine daily-review checks.
- Search within the canonical note for the target local-date heading first, for example `## YYYY-MM-DD`.
- Use the returned byte offset as the start point for a bounded `bearcli cat` read with `--offset` and `--limit`.
- Read only enough chunks to cover the target date section and stop when the next `## YYYY-MM-DD` heading appears.
- If a bounded read still truncates before the section end, record the truncation as an evidence gap and use targeted `search-in` checks for required job names, `Workflow signal`, and weekly-run state.
- Prefer targeted `search-in` checks over full-note reads when confirming whether a specific run-log entry, job name, weekly state, or workflow signal exists.

Common command shape:

```sh
/Applications/Bear.app/Contents/MacOS/bearcli search-in NOTE_ID --string '## YYYY-MM-DD' --context 0 --format json
/Applications/Bear.app/Contents/MacOS/bearcli cat NOTE_ID --offset OFFSET --limit 20000 --format json
/Applications/Bear.app/Contents/MacOS/bearcli search-in NOTE_ID --string 'Workflow signal' --context 300 --format json
```

## When To Write

- Add one entry for each attempted runnable job.
- Include no-op runs when the job was checked and had no work to do.
- Add lightweight `ad-hoc` entries for manual requests that mutate notes, repo files, external systems, or workflow state.
- Add lightweight `ad-hoc` entries for manual requests that reveal a reusable workflow pattern, even when the change is small.
- Write completion entries only after the job completion check passes.
- If a job fails before completion, write a failure entry after capturing the failure evidence.
- Do not log tiny conversational answers that do not change state or reveal a reusable workflow pattern.
- Do not record secrets, private message bodies, full email contents, or long raw command output.

## Entry Template

```md
## YYYY-MM-DD

### HH:MM local - job-name - status

- Run window: YYYY-MM-DD HH:MM to YYYY-MM-DD HH:MM local time
- Trigger: heartbeat, daily review, manual request, or other
- Status: completed, no-op, failed, or stopped
- Work done: Short factual summary
- Outputs: Bear note titles, labels, file paths, or none
- Weekly run state: For heartbeat-dispatch entries, list each weekly job and its last successful run date, or `none found`
- Open triaged inbox threads: For heartbeat-dispatch and email-triage entries, list already-triaged inbox threads that are still sitting in inbox, or `none found`
- Workflow signal: Possible job, template, checklist, or workflow improvement, or none
- Evidence: Completion check, failure evidence, or explicit evidence gap
- Follow-up: Next action, owner, or none
```
