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

## Writing Rules

- Keep each job short and direct.
- Put the job logic here.
- Keep scheduling hints in the job file as metadata for the system that runs the jobs.

## Run Log

- Runnable jobs record actual activity using `../docs/job-run-log.md`.
- Add one run-log entry whenever a job is attempted, including no-op attempts.
- Completion entries are written only after the job's completion check passes.
- Failure entries include the captured failure evidence or the explicit evidence gap.
