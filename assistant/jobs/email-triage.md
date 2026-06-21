# Email Triage

- Purpose: triage unread email in inbox or spam, create Bear notes for anything that needs review, and create one summary note for everything else before archiving it.

## Due Rule

- Run daily at or after 9:00 and 21:00.
- At each scheduled run, process any unread or untriaged email in inbox or spam since the previous run.

## Inputs

- Unread or untriaged email in inbox or spam.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Read email.
- If an email is in spam but is clearly not spam and does not need review, mark it as not spam.
- Identify emails that need your review.
- For each email that needs review, create or update the matching Bear note.
- Link each review task back to the Bear note using the subject-based reference shape.
- Write the `Recommended next step` section as one or more checkbox lines so the item is searchable as a Bear TODO.
- If the matching needs-review Bear note is archived, archive the corresponding email too.
- Collect all emails that do not need review into one summary note for the run.
- Archive each non-review email after it has been summarized.

## Completion Check

- Spam-folder messages that are clearly not spam are marked as not spam.
- Each email that needs review has a corresponding task.
- Each created task points back to the Bear note for that email.
- Each `Recommended next step` entry in a needs-review Bear note uses checkbox syntax.
- If a needs-review Bear note is archived, the corresponding email is archived too.
- All emails that do not need review are captured in a single summary note.
- All non-review emails are archived after being summarized.
- The automation memory records that this job already ran for the current unread or untriaged email set.

## Outputs

- Tasks for emails that need review.
- Bear notes for review follow-ups.
- One Bear note summarizing all emails that did not need review.
