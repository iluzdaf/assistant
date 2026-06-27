# Email Triage

- Purpose: process the canonical email review note, clear spam separately, triage new inbox email, add sections for anything that needs review, and summarize only non-spam inbox email that does not need review.

## Due Rule

- Run on every heartbeat pass.
- On each heartbeat, process existing email review notes, spam-folder email, and new inbox email without the `Codex/Triaged` label.
- On each heartbeat, also re-scan open sections in the canonical Bear note `Emails Needing Review` so completed reviews can be archived even when no new email is due.

## Inputs

- Inbox email without the `Codex/Triaged` label.
- Spam-folder email, checked separately from inbox triage.
- The canonical Bear note `Emails Needing Review` tagged `#assistant/email/needs-review`.
- Shared note format, writing guide, and Bear CLI instructions live in `docs/`.

## Actions

- Re-scan open email sections in `Emails Needing Review` for unchecked `reply:` change requests.
- Apply each unchecked `reply:` request to the fenced draft reply, then tick that `reply:` checkbox.
- Re-scan email sections for checked `Send reply` checkboxes; send the current fenced draft in Gmail only for sections where `Send reply` is checked.
- Re-scan email sections for completed actions; when every checkbox in a section's `Recommended next step` is ticked, archive the corresponding Gmail message and remove that section from `Emails Needing Review`.
- Check spam separately from inbox triage.
- If any spam message requires action, move it to the inbox so it can enter the normal needs-review flow.
- Clear the remaining spam folder without summarizing those messages.
- Check inbox for new email that does not have the `Codex/Triaged` label.
- Collect non-spam inbox emails that do not have an obvious action into the canonical summary note using `docs/email-summary-template.md`.
- Create or update one Bear note titled `Email Summary` tagged `#assistant/email/summary`.
- Add each run's summarized emails under the current local-date section `## YYYY-MM-DD`, using one run subsection per heartbeat.
- Keep date sections newest-first, inserting a new summary date above older date sections.
- Do not create a second section for a summary date that already exists.
- Archive each summarized email after it has been summarized.
- For each email that has an obvious action, create or update the matching section in `Emails Needing Review` using `docs/email-review-template.md`.
- Create the canonical review note if missing, titled `Emails Needing Review` and tagged `#assistant/email/needs-review`.
- Add each review email under the current local-date section `## YYYY-MM-DD`, using one subsection per email.
- Keep date sections newest-first, inserting a new review date above older date sections.
- Do not create a second section for a review date or email that already exists.
- Keep each needs-review email in the inbox and label it with `Codex/Triaged`.
- Use the email writing guide when drafting or revising reply text.
- If the email needs a reply draft, put the draft, any `reply:` change requests, and the `Send reply` checkbox inside the section's `Recommended next step` subsection.
- If a review email does not need a reply draft, use a checkbox for the next non-draft action and omit the fenced reply block and `Send reply` checkbox.
- After the completion check passes, add a run-log entry using `docs/job-run-log.md`.

## Completion Check

- Open needs-review sections from earlier passes are re-scanned before new email is triaged.
- Treat `- [ ]` as an open task and `- [x]` as a completed task in Bear.
- A checked `reply:` line means that draft edit has already been applied and should be ignored on later runs.
- `reply:` checkboxes do not authorize sending.
- Only the dedicated checked `Send reply` checkbox authorizes sending the fenced draft in Gmail.
- Completed needs-review emails are archived, not summarized.
- When every checkbox in a section's `Recommended next step` is ticked, the corresponding email is archived and the section is removed from `Emails Needing Review`.
- Spam messages are handled separately from summary creation.
- Spam messages are never added to the summary note unless first moved to the inbox because they require action.
- The remaining spam folder is cleared after important or actionable messages are moved to the inbox.
- The email summary uses `docs/email-summary-template.md`, is titled `Email Summary`, and is tagged `#assistant/email/summary`.
- The current summary date section appears above older date sections.
- The note has no duplicate date section for the current summary date.
- Each email that needs review has a corresponding section in `Emails Needing Review`.
- New review sections appear under the current local-date heading above older date sections.
- The canonical review note has no duplicate date section or duplicate email section for the current review email.
- Draft replies follow the email writing guide.
- The canonical review note is titled `Emails Needing Review` and tagged `#assistant/email/needs-review`.
- Review sections keep the `reply:` change requests, `Send reply` checkbox, and draft reply inside the `Recommended next step` subsection when a draft is needed.
- Review-only emails without a draft close out after their non-draft action is complete.
- All summarized emails are non-spam inbox messages with no obvious action.
- All summarized emails are archived after being summarized.
- The automation memory records that this job already ran for the current unread or untriaged email set.
- A run-log entry records this job's status, outputs, and any evidence gaps after the checks above pass.

## Outputs

- Tasks for emails that need review.
- One Bear note titled `Emails Needing Review` for review follow-ups.
- One Bear note titled `Email Summary` summarizing non-spam inbox emails that did not need review.
- One run-log entry for the email triage attempt.
