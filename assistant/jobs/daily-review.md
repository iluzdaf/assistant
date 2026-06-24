# Daily Review

- Purpose: create a morning review of recent assistant jobs, issues, workflow improvements, and ad hoc requests that could become repeatable workflows.

## Due Rule

- Run once each morning.
- Review the period since the last successful daily review note.
- If no prior daily review note exists, review the previous local day.

## Inputs

- Automation memory from the reviewed period.
- Job outputs or Bear notes created by assistant jobs during the reviewed period.
- Visible recent ad hoc assistant requests from the reviewed period.
- Any available completion notes, failure notes, or runner status from the reviewed period.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Find the most recent successful daily review note tagged `#assistant #daily-review`.
- Determine the review window from that note, or use the previous local day when no prior note exists.
- Review jobs that ran during the window and summarize what each job did.
- Identify issues, failures, unclear instructions, repeated friction, or missing completion evidence.
- Recommend workflow improvements that would make existing jobs more reliable or easier to operate.
- Review visible ad hoc assistant requests and identify patterns that could become jobs, templates, checklists, or scheduled checks.
- Keep recommendations proposal-only; do not create new runnable jobs or templates without explicit approval.
- Create or update one Bear note using `docs/daily-review-template.md`.
- Tag the note `#assistant #daily-review #needs-review`.
- Include at least one unchecked checkbox in the `Follow-ups` section so Bear shows the note in To Do.

## Completion Check

- The review window is stated in the note.
- Jobs reviewed, issues observed, workflow improvements, ad hoc workflow candidates, scheduling candidates, and follow-ups are all present.
- Evidence gaps are stated instead of treated as facts.
- Recommendations are proposal-only and do not change runnable workflow files.
- The Bear note exists and is tagged `#assistant #daily-review #needs-review`.
- The `Follow-ups` section includes at least one unchecked checkbox.
- Automation memory is updated only after the Bear note is verified.

## Outputs

- One Bear note titled `Assistant Daily Review - YYYY-MM-DD`.
- Proposal-only workflow and scheduling recommendations for review.
