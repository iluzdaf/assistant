# Email Triage

- Purpose: triage unread email in inbox or spam, create Bear notes for anything that needs review, and create one summary note for everything else before archiving it.

## Due Rule

- Run on every heartbeat pass.
- On each heartbeat, process any unread or untriaged email in inbox or spam since the previous heartbeat.

## Inputs

- Unread or untriaged email in inbox or spam.
- Shared note format, writing guide, and Bear CLI instructions live in `docs/`.

## Actions

- Read email.
- If an email is in spam but is clearly not spam and does not need review, mark it as not spam.
- Identify emails that need your review.
- For each email that needs review, create or update the matching Bear note.
- Link each review task back to the Bear note using the subject-based reference shape.
- Use the email writing guide when drafting or revising reply text.
- Inspect the note's `Recommended next step` checkbox state before deciding whether the email is complete.
- If the email needs a reply draft, put the draft and any requested changes inside the note's `Recommended next step` section.
- Write the `Recommended next step` section as a review-action checkbox, optional requested-change lines, a send checkbox, and a fenced draft block when a reply draft is needed.
- If a review email does not need a reply draft, use the review-action checkbox for the next non-draft action and omit the fenced reply block and send checkbox.
- If a review email already has a draft reply, revise the draft to satisfy any requested changes before sending.
- Do not treat `Send reply` as send-ready while requested changes are still unmet.
- If every checkbox in `Recommended next step` is ticked, archive the Bear note and archive the corresponding email.
- If the matching needs-review Bear note is archived, archive the corresponding email too.
- Collect all emails that do not need review into one summary note for the run.
- Archive each non-review email after it has been summarized.

## Completion Check

- Spam-folder messages that are clearly not spam are marked as not spam.
- Each email that needs review has a corresponding task.
- Each created task points back to the Bear note for that email.
- Draft replies follow the email writing guide.
- Review notes keep the review-action checkbox, requested changes, send checkbox, and draft reply inside the `Recommended next step` section when a draft is needed.
- The `Send reply` checkbox is the approval signal to send the current reply on the next heartbeat pass only after the requested changes are reflected.
- Existing draft replies are revised when requested changes are present.
- Notes with unmet requested changes remain unarchived until the draft matches the requested changes.
- The heartbeat checks the note's checkbox state, not just whether the note is open.
- Review-only emails without a draft close out after their non-draft action is complete.
- When every checkbox in `Recommended next step` is ticked, the Bear note and the corresponding email are archived.
- If a needs-review Bear note is archived, the corresponding email is archived too.
- All emails that do not need review are captured in a single summary note.
- All non-review emails are archived after being summarized.
- The automation memory records that this job already ran for the current unread or untriaged email set.

## Outputs

- Tasks for emails that need review.
- Bear notes for review follow-ups.
- One Bear note summarizing all emails that did not need review.
