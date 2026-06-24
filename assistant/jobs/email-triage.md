# Email Triage

- Purpose: process existing email review notes, clear spam separately, triage new inbox email, create Bear notes for anything that needs review, and summarize only non-spam inbox email that does not need review.

## Due Rule

- Run on every heartbeat pass.
- On each heartbeat, process existing email review notes, spam-folder email, and new inbox email without the `Codex/Triaged` label.
- On each heartbeat, also re-scan open Bear notes tagged `#email #needs-review` from earlier passes so completed reviews can be archived even when no new email is due.

## Inputs

- Inbox email without the `Codex/Triaged` label.
- Spam-folder email, checked separately from inbox triage.
- Open Bear notes tagged `#email #needs-review` that were created by earlier triage passes.
- Shared note format, writing guide, and Bear CLI instructions live in `docs/`.

## Actions

- Re-scan open email Bear notes for unchecked `reply:` change requests.
- Apply each unchecked `reply:` request to the fenced draft reply, then tick that `reply:` checkbox.
- Re-scan Bear notes for checked `Send reply` checkboxes; send the current fenced draft in Gmail only for notes where `Send reply` is checked.
- Re-scan Bear notes for completed actions; when every checkbox in `Recommended next step` is ticked, archive the Bear note and archive the corresponding Gmail message.
- If a matching needs-review Bear note is archived, archive the corresponding email too.
- Check spam separately from inbox triage.
- If any spam message requires action, move it to the inbox so it can enter the normal needs-review flow.
- Clear the remaining spam folder without summarizing those messages.
- Check inbox for new email that does not have the `Codex/Triaged` label.
- Collect non-spam inbox emails that do not have an obvious action into one summary note for the run.
- Archive each summarized email after it has been summarized.
- For each email that has an obvious action, create or update the matching Bear note tagged `#email #needs-review`.
- Keep each needs-review email in the inbox and label it with `Codex/Triaged`.
- Link each review task back to the Bear note using the subject-based reference shape.
- Use the email writing guide when drafting or revising reply text.
- If the email needs a reply draft, put the draft, any `reply:` change requests, and the `Send reply` checkbox inside the note's `Recommended next step` section.
- If a review email does not need a reply draft, use a checkbox for the next non-draft action and omit the fenced reply block and `Send reply` checkbox.
- After the completion check passes, add a run-log entry using `docs/job-run-log.md`.

## Completion Check

- Open needs-review notes from earlier passes are re-scanned before new email is triaged.
- Treat `- [ ]` as an open task and `- [x]` as a completed task in Bear.
- A checked `reply:` line means that draft edit has already been applied and should be ignored on later runs.
- `reply:` checkboxes do not authorize sending.
- Only the dedicated checked `Send reply` checkbox authorizes sending the fenced draft in Gmail.
- Completed needs-review emails are archived, not summarized.
- When every checkbox in `Recommended next step` is ticked, the Bear note and the corresponding email are archived.
- If a needs-review Bear note is archived, the corresponding email is archived too.
- Spam messages are handled separately from summary creation.
- Spam messages are never added to the summary note unless first moved to the inbox because they require action.
- The remaining spam folder is cleared after important or actionable messages are moved to the inbox.
- Each email that needs review has a corresponding task.
- Each created task points back to the Bear note for that email.
- Draft replies follow the email writing guide.
- Review notes are tagged `#email #needs-review` and keep the `reply:` change requests, `Send reply` checkbox, and draft reply inside the `Recommended next step` section when a draft is needed.
- Review-only emails without a draft close out after their non-draft action is complete.
- All summarized emails are non-spam inbox messages with no obvious action.
- All summarized emails are archived after being summarized.
- The automation memory records that this job already ran for the current unread or untriaged email set.
- A run-log entry records this job's status, outputs, and any evidence gaps after the checks above pass.

## Outputs

- Tasks for emails that need review.
- Bear notes tagged `#email #needs-review` for review follow-ups.
- One Bear note summarizing non-spam inbox emails that did not need review.
- One run-log entry for the email triage attempt.
