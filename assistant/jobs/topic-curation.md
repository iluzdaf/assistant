# Topic Curation

- Purpose: find a small weekly set of article links for each maintained topic and append them to the matching rolling Bear topic note.

## Due Rule

- Run weekly.

## Inputs

- Bear notes tagged `#topic`.
- Topic notes are the source of truth for the editable topic list.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Find every Bear note tagged `#topic`.
- Treat each tagged note as a rolling topic note.
- Search for current article links relevant to each topic note.
- Collect only articles in v1; do not include videos or social posts.
- Target 3-5 strong links per topic for the week.
- If a topic has no good matches on the first pass, broaden the search until at least one acceptable article is found.
- Append the curated items to the same topic note.
- Write each curated item as a checkbox line with metadata:
  - title
  - source link
  - source type
  - date
  - short reason it was selected
- Keep `#topic` reserved for the topic notes only so the job can find them reliably.

## Completion Check

- Every Bear note tagged `#topic` was found and treated as a topic note.
- Only article sources were collected.
- Each topic received 3-5 curated items when possible.
- Topics with no immediate matches were searched more broadly until at least one acceptable article was found.
- Curated items were appended to the existing rolling topic note rather than creating a separate output structure.
- Each appended item uses a checkbox line with title, source link, source type, date, and a short selection reason.
- `#topic` remains reserved for topic notes and is not used on the weekly output entries.

## Outputs

- Updated Bear topic notes with weekly article curation entries.
