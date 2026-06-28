# Topic Curation

- Purpose: find a small weekly set of article links for each maintained topic and append them to the matching rolling Bear topic note.

## Due Rule

- Run weekly.

## Inputs

- Bear notes tagged `#assistant/topic` or a child topic tag under `#assistant/topic/<topic-subject>`.
- Topic notes are the source of truth for the editable topic list.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Find every Bear note tagged `#assistant/topic`.
- Treat each tagged note as a rolling topic note.
- For each topic note, use a lowercase hyphenated subject tag under `#assistant/topic/<topic-subject>` when linking clippings or related notes back to that topic.
- Search for current article links relevant to each topic note.
- Collect only articles in v1; do not include videos or social posts.
- Target 3-5 strong links per topic for the week.
- If a topic has no good matches on the first pass, broaden the search until at least one acceptable article is found.
- Insert the curated items directly under the `## Curated links` section in the same topic note.
- If the `Curated links` section is missing, create it near the top of the note and place the new items there.
- Write each curated item as an unchecked checkbox line with metadata:
  - title
  - source link
  - source type
  - date
  - short reason it was selected
- Keep `#assistant/topic` and its child subject tags reserved for topic notes and topic-linked clippings so the job can find them reliably without root-level topic tags.
- After the completion check passes, add a run-log entry using `docs/job-run-log.md`.

## Completion Check

- Every Bear note tagged `#assistant/topic` was found and treated as a topic note.
- Only article sources were collected.
- Each topic received 3-5 curated items when possible.
- Topics with no immediate matches were searched more broadly until at least one acceptable article was found.
- Curated items were inserted directly under the `Curated links` section in the existing rolling topic note rather than creating a separate output structure.
- Each inserted item uses an unchecked checkbox line with title, source link, source type, date, and a short selection reason.
- `#assistant/topic` and its child subject tags remain reserved for topic notes and topic-linked clippings and are not used on weekly output entries.
- A run-log entry records this job's status, outputs, and any evidence gaps after the checks above pass.

## Outputs

- Updated Bear topic notes with weekly article curation entries.
- One run-log entry for the topic curation attempt.
