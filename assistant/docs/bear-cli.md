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
- Prefer `bearcli cat` for raw note body reads.
- Use `bearcli show` for structured metadata; include `content` explicitly when structured body output is needed.
- Check `bearcli help <subcommand>` when a command shape is uncertain; local CLI help overrides stale examples.
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

- Command: `bearcli edit`
- Common args:
  - note `id` or `--title`
  - `--find`
  - one of `--replace`, `--insert-after`, or `--insert-before`
  - `--all` only when every matching occurrence should be edited

## Append Note

- Command: `bearcli append`
- Common args:
  - note `id` or `--title`
  - `--content`, or omit it to read content from stdin
  - `--position beginning` or `--position end`

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
- Default fields are `id`, `title`, and `tags`.
- `--fields all` omits body content.
- Use `--fields all,content` when structured metadata plus body content is required.
- Locked notes return metadata but reject `--fields content`.

## Cat Note

- Command: `bearcli cat`
- Common args:
  - note `id` or `--title`
  - `--offset` and `--limit` for byte-range reads of large notes
  - `--format json` when the raw body should be JSON-escaped
- Default output is the raw note body.
- Use this for most note-content reads and readbacks after writes.

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
