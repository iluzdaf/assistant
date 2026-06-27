# Daily Review Template

- Template for morning assistant review note sections.
- Use this for daily reviews that need human review in Bear.
- Keep one section per date in newest-first order, with the latest date at the top.

```md
# Assistant Daily Review

- Tags: #assistant #daily-review #needs-review

## YYYY-MM-DD

### Run Window

- Reviewed period: YYYY-MM-DD HH:MM to YYYY-MM-DD HH:MM local time
- Previous review section: YYYY-MM-DD or none found
- Run-log evidence: Checked [[Assistant Job Run Log]] entries for the reviewed period, or state missing log evidence

### Due Job Checklist

- Job index evidence: Checked `assistant/jobs/README.md` and runnable job files, or state missing evidence
- [x] Job name: Due rule evidence found and evaluated; due now: yes or no; run-log evidence or none expected
- [ ] Job name: Due rule evidence missing or incomplete; due now: unknown; evidence gap
- Result: No jobs due, due jobs listed above, or unable to determine due jobs

### Jobs Reviewed

- Job name: What ran, what changed, and completion status

### Issues Observed

- Issue or evidence gap: Impact and suggested fix

### Workflow Improvements

- [ ] Recommendation: Why it helps and what approval is needed

### Ad Hoc Workflow Candidates

- Request pattern from ad-hoc run-log `Workflow signal`: Proposed job, template, checklist, or workflow

### Scheduling Candidates

- Candidate: Suggested cadence and reason

```
