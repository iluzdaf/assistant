# Daily Review

- Purpose: create a morning review of recent assistant jobs, issues, workflow improvements, and ad hoc requests that could become repeatable workflows.

## Due Rule

- Run once each morning.
- Review the period since the last successful daily review note.
- If no prior daily review note exists, review the previous local day.

## Inputs

- Runnable job files under `jobs/`, including each job's `Due Rule`.
- Bear job run-log notes from the reviewed period, following `docs/job-run-log.md`.
- Automation memory from the reviewed period.
- Job outputs or Bear notes created by assistant jobs during the reviewed period.
- Visible recent ad hoc assistant requests from the reviewed period.
- Any available completion notes, failure notes, or runner status from the reviewed period.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Find the most recent successful daily review note tagged `#assistant #daily-review`.
- Determine the review window from that note, or use the previous local day when no prior note exists.
- Read `jobs/README.md` and each runnable job file under `jobs/` to identify due rules for the review time.
- Add a `Due Job Checklist` section that lists every runnable job checked, its due rule evidence, whether it is due now, and any missing evidence.
- Mark a due-job checklist item checked only when that job's due rule was found and evaluated; leave it unchecked when evidence is missing or the due state is unknown.
- Use `No jobs due` only when every runnable job and due rule was found and evaluated as not due for the review time.
- Use `Unable to determine due jobs` when job files, due rules, timestamps, runner status, or other required evidence is missing.
- Read the Bear job run-log notes for the review window before using automation memory or ad hoc notes.
- Review jobs that ran during the window and summarize what each job did.
- Treat missing run-log entries for expected jobs as evidence gaps, not proof that nothing ran.
- Identify issues, failures, unclear instructions, repeated friction, or missing completion evidence.
- Recommend workflow improvements that would make existing jobs more reliable or easier to operate.
- Review visible ad hoc assistant requests and identify patterns that could become jobs, templates, checklists, or scheduled checks.
- Keep recommendations proposal-only; do not create new runnable jobs or templates without explicit approval.
- Create or update one Bear note using `docs/daily-review-template.md`.
- Tag the note `#assistant #daily-review #needs-review`.
- Include at least one unchecked checkbox in the `Follow-ups` section so Bear shows the note in To Do.
- After the Bear note is verified, add a run-log entry for the daily review using `docs/job-run-log.md`.

## Completion Check

- The review window is stated in the note.
- The due-job checklist lists every runnable job checked, its due rule evidence, due-now result, and any evidence gap.
- Checked due-job checklist items have evaluated due-rule evidence; unchecked due-job checklist items have an explicit evidence gap.
- `No jobs due` appears only when all runnable jobs were checked and none were due for the review time.
- Missing job or schedule evidence is stated as `Unable to determine due jobs`, not as `No jobs due`.
- Bear job run-log notes for the review window were checked, or the missing log evidence is stated.
- Jobs reviewed, issues observed, workflow improvements, ad hoc workflow candidates, scheduling candidates, and follow-ups are all present.
- Evidence gaps are stated instead of treated as facts.
- Recommendations are proposal-only and do not change runnable workflow files.
- The Bear note exists and is tagged `#assistant #daily-review #needs-review`.
- The `Follow-ups` section includes at least one unchecked checkbox.
- A run-log entry records this daily review's status, output note, and any evidence gaps after the checks above pass.
- Automation memory is updated only after the Bear note and run-log entry are verified.

## Outputs

- One Bear note titled `Assistant Daily Review - YYYY-MM-DD`.
- Proposal-only workflow and scheduling recommendations for review.
- One run-log entry for the daily review attempt.
