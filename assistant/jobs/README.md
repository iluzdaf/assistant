# Jobs

- These files define runnable assistant jobs.
- Each job should stay focused on one task.

## Job Shape

- Purpose
- Due rule
- Inputs
- Actions
- Completion check
- Outputs

## Dispatch

- On heartbeat runs, enumerate every `*.md` file in this directory except this README.
- Read each job's `Due Rule` before selecting task-specific instructions.
- Run every due job in the same heartbeat pass.
- If a job is not due, record the due-rule evidence and skip reason in the run log or the due-job checklist for the job that performs the dispatch.
- Do not treat a highlighted or recently edited heartbeat job as the only due job.

## Runnable Jobs

- `clipping-triage.md`: run weekly.
- `daily-review.md`: run once each morning.
- `email-triage.md`: run on every heartbeat pass.
- `product-issue-triage.md`: run on every heartbeat pass.
- `topic-curation.md`: run weekly.

## Writing Rules

- Keep each job short and direct.
- Put the job logic here.
- Keep scheduling hints in the job file as metadata for the system that runs the jobs.

## Run Log

- Runnable jobs record actual activity using `../docs/job-run-log.md`.
- Add one run-log entry whenever a job is attempted, including no-op attempts.
- Completion entries are written only after the job's completion check passes.
- Failure entries include the captured failure evidence or the explicit evidence gap.
