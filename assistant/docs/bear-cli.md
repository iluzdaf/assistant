# Bear CLI

- Entry point: `/Applications/Bear.app/Contents/MacOS/bearcli`
- Bear CLI help: run `bearcli help` or `bearcli help <subcommand>`.
- Always run Bear CLI commands with escalated permissions, outside the workspace sandbox.
- In Codex, set `sandbox_permissions: "require_escalated"` and explain that Bear CLI reads or writes the local Bear database outside the repository sandbox.
- Do not first try Bear CLI inside the sandbox; it commonly fails or hides the real Bear database access problem.

## Execution Rules

- Use the absolute entry point; do not assume `bearcli` is on `PATH`.
- Request escalation for reads as well as writes, including `search`, `show`, `cat`, and `search-in`.
- Request escalation for mutations, including `create`, `append`, `edit`, `overwrite`, `archive`, `trash`, and `tags`.
- When a Bear write succeeds, verify it with an escalated read before treating the step as complete.
- If Bear commands crash with exit code `134`, `kLSNoExecutableErr`, or Bear app launch errors, record the evidence gap and stop after the same failure pattern repeats.

## Create Note

- Command: `bearcli create`
- Common args:
  - note title as the first positional argument
  - `--content`
- Returns:
  - note `id`
  - note `title`
  - note tags

## Edit Note

- Command: `bearcli add`
- Common args:
  - note `id` or `--title`
  - `--content`
  - `--position`

## Overwrite Note

- Command: `bearcli overwrite`
- Common args:
  - note `id` or `--title`
  - `--content`
  - `--base`
  - `--force`

## Show Note

- Command: `bearcli show`
- Common args:
  - note `id` or `--title`
  - `--fields`
  - `--format json`

## Search Notes

- Command: `bearcli search`
- Common args:
  - search query
  - `--format json`

## Trash Or Archive

- Trash command: `bearcli trash`
- Archive command: `bearcli archive`
- Common args:
  - note `id` or `--title`

## Tag Actions

- `bearcli tags add`
- `bearcli tags remove`
- `bearcli tags rename`
- `bearcli tags delete`

## Conventions

- Keep titles short and searchable.
- Prefer subject-based titles for email notes so `[[Subject]]` links stay stable.
