# Docs

- Shared reference docs live here.

## Purpose

- Put reusable reference material here, not runnable job logic.
- Keep these docs stable enough that multiple jobs can rely on them.
- Use this folder for templates, tool instructions, and shared conventions.

## What Belongs Here

- Template docs that define the required shape and tone of notes or outputs.
- Tool docs that explain how to call an external tool or app and any constraints around it.
- Shared formatting or naming conventions used across jobs.

## Template Rules

- Keep templates short, direct, and easy to scan.
- Describe what the template is for before the example block.
- Use placeholders such as `YYYY-MM-DD`, `sender name`, or `Short subject` instead of real data.
- Include only fields that are expected every time; avoid one-off job logic in templates.
- Put the canonical template in a fenced `md` block so jobs can copy the exact structure.
- Keep tags, headings, and link shapes explicit when they are required by downstream workflows.

## Tool Instruction Rules

- Document one tool or integration per file when practical.
- State the base action shape or entrypoint first.
- Call out execution constraints clearly, especially sandbox or environment requirements.
- List the common actions and parameters jobs are expected to use.
- Record any return values, naming conventions, or searchability rules that affect automation output.
- Keep usage guidance operational and concrete rather than descriptive.

## Current Files

- `bear-cli.md`: Bear note commands, constraints, and note-title conventions.
- `daily-review-template.md`: template for daily assistant review note sections that need review in Bear.
- `job-run-log.md`: Bear run-log convention for assistant job activity evidence.
- `github-issue-triage.md`: GitHub issue read/write conventions for product issue triage.
- `product-issue-review-card-template.md`: Bear card template for product issues needing human intervention.
- `email-writing-guide.md`: reply style guide for email drafts.
- `email-review-template.md`: template for email review note sections.
- `email-summary-template.md`: template for email summary note sections.
