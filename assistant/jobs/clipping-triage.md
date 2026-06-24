# Clipping Triage

- Purpose: process new web-clipper notes, tag them `#clipping` and with the matching topic tag, and extract any useful follow-up links into the matching topic note.

## Due Rule

- Run weekly.

## Inputs

- Unprocessed web-clipper notes.
- Notes that still show clipper metadata such as `tags: clippings`.
- Bear topic notes tagged `#topic`.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Find clipping notes that have not yet been tagged `#clipping`.
- Treat each untagged clipping note as a candidate for triage.
- Read the highlighted text and metadata in each clipping note.
- Add `#clipping` and the matching topic tag to every clipping note that is processed.
- Leave the clipping note body unchanged after tagging it.
- Use the topic note title as the topic tag so the clipping stays searchable from both directions.
- If a highlighted portion contains a follow-up link, match it to the appropriate topic note by keyword against the topic title and description.
- When a topic match is strong enough, append the follow-up link to that topic note using the same checkbox + metadata format used by `topic curation`.
- If a clipping has multiple plausible topic matches, prefer the strongest keyword match and leave the rest for manual review.
- Skip any note that already has `#clipping` on later runs.
- After the completion check passes, add a run-log entry using `docs/job-run-log.md`.

## Completion Check

- Only unprocessed clipping notes were selected for triage.
- Every processed clipping note was tagged `#clipping` and with the matching topic tag.
- Processed clipping note bodies were not rewritten.
- Follow-up links were matched to the appropriate topic note using keyword matching.
- Topic-note additions used the same checkbox + metadata format as `topic curation`.
- Notes already tagged `#clipping` were skipped on subsequent runs.
- A run-log entry records this job's status, outputs, and any evidence gaps after the checks above pass.

## Outputs

- Clipping notes tagged `#clipping`.
- Topic notes updated with follow-up links extracted from clipping notes.
- One run-log entry for the clipping triage attempt.
