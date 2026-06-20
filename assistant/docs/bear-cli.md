# Bear CLI

- Entry point: `/Applications/Bear.app/Contents/MacOS/bearcli`
- Bear CLI help: run `bearcli help` or `bearcli help <subcommand>`.
- Run Bear CLI commands outside the sandbox.

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
