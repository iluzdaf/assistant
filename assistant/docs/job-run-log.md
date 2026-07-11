# Job Run Log

- Shared convention for recording actual assistant job activity.
- Use this log so daily reviews can summarize runs from durable local evidence, not only automation memory or ad hoc notes.

## Location

- Write all job activity to one canonical Bear note.
- Title: `Assistant Job Run Log`.
- Tags: `#assistant/job-run-log`.
- Create the canonical Bear note when missing.
- Keep the canonical note small enough to sync quickly.
- Rotate the canonical note when it becomes unwieldy, normally when it is older than 14 days, larger than 250 KB, or visibly slow to sync.
- Preserve rotated content in a separate archive note titled `Assistant Job Run Log Archive - YYYY-MM-DD to YYYY-MM-DD`.
- Archive notes use `#assistant/job-run-log-archive`, not a child of `#assistant/job-run-log`, so searches for the canonical tag return one active note.
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
- Keep routine entries to one line under the date heading.
- Use the expanded template only for failures, stopped jobs, migrations, one-off repairs, or evidence gaps that need durable detail.
- Put detailed evidence in the job output note, source issue, PR, automation memory, or final response when available; the run log should name the evidence, not copy it.
- For heartbeat passes, write one `heartbeat-dispatch` line that lists due jobs, skipped jobs, and key outputs.
- Write separate job lines only for jobs that changed external state, found new work, failed, stopped, or need human follow-up.
- Do not write separate no-op lines for every skipped heartbeat job when the dispatch line already records the due-rule evidence.

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

- Add one compact entry for each attempted manual job.
- For heartbeat dispatch, add one compact dispatch entry for the pass, plus compact per-job entries only when the job changed state, produced a user-facing output, failed, stopped, or needs human follow-up.
- Include no-op runs only when they are the main attempted job or when the no-op evidence is not already captured by the heartbeat-dispatch line.
- Add lightweight `ad-hoc` entries for manual requests that mutate notes, repo files, external systems, or workflow state.
- Add lightweight `ad-hoc` entries for manual requests that reveal a reusable workflow pattern, but keep them to one line unless a failure needs detail.
- Write completion entries only after the job completion check passes.
- If a job fails before completion, write a failure entry after capturing the failure evidence.
- Do not log tiny conversational answers that do not change state or reveal a reusable workflow pattern.
- Do not record secrets, private message bodies, full email contents, or long raw command output.

## Compact Entry Template

Use this for routine successful and no-op work:

```md
## YYYY-MM-DD

- HH:MM `job-name` status: outcome; outputs: note/title/label/file or none; evidence: compact source; follow-up: owner/action or none.
```

Examples:

```md
- 08:37 `clipping-triage` completed: tagged 5 clipping notes and fixed 1 generic title; outputs: AI in Education, AI Automation, AI Vampire, Chess clipping tags; evidence: Bear tag readbacks; follow-up: none.
- 09:00 `heartbeat-dispatch` completed: due email/product jobs ran; skipped daily-review current date exists, weekly jobs last ran 2026-07-11; outputs: Emails Needing Review unchanged; evidence: Gmail labels, GitHub queue scans; follow-up: review Gmail 19f4bc799a4d4706.
```

## Expanded Entry Template

Use this only for failures, stopped jobs, migrations, one-off repairs, or evidence gaps that need durable detail:

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
