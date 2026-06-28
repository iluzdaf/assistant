# Clipping Triage

- Purpose: process new web-clipper notes, tag them `#assistant/clipping` and with the matching `#assistant/topic/<topic-subject>` tag, and extract any useful follow-up links into the matching topic note.

## Due Rule

- Run weekly.

## Inputs

- Unprocessed web-clipper notes.
- Notes that still show clipper metadata such as `tags: clippings`.
- Bear topic notes tagged `#assistant/topic`.
- Shared note format and Bear CLI instructions live in `docs/`.

## Actions

- Find clipping notes that have not yet been tagged `#assistant/clipping`.
- Treat each untagged clipping note as a candidate for triage.
- Read the highlighted text and metadata in each clipping note.
- Add `#assistant/clipping` and the matching slugged `#assistant/topic/<topic-subject>` tag to every clipping note that is processed.
- If a clipping note has no useful title, give it a short searchable title from the page title, article heading, source name, or strongest highlighted subject before tagging it.
- Leave the clipping note body unchanged after tagging it, except for the note title when the original title is blank, `Untitled`, only a URL, or otherwise generic.
- Use the topic note title to derive a lowercase hyphenated topic subject tag under `#assistant/topic/`, so the clipping stays searchable from both directions without creating root-level topic tags.
- If a highlighted portion contains a follow-up link, match it to the appropriate topic note by keyword against the topic title and description.
- When a topic match is strong enough, insert the follow-up link into the topic note's `Curated links` section using the same unchecked checkbox + metadata format used by `topic curation`.
- If the topic note does not yet have a `Curated links` section, create it near the top of the note before inserting the link.
- If a clipping has multiple plausible topic matches, prefer the strongest keyword match and leave the rest for manual review.
- Skip any note that already has `#assistant/clipping` on later runs.
- After the completion check passes, add a run-log entry using `docs/job-run-log.md`.

## Completion Check

- Only unprocessed clipping notes were selected for triage.
- Every processed clipping note was tagged `#assistant/clipping` and with the matching `#assistant/topic/<topic-subject>` tag.
- Every processed clipping note with a blank, `Untitled`, URL-only, or generic title was given a short searchable title.
- Processed clipping note bodies were not rewritten, except for allowed note-title cleanup.
- Follow-up links were matched to the appropriate topic note using keyword matching.
- Topic-note additions were inserted into the topic note's `Curated links` section using the same unchecked checkbox + metadata format as `topic curation`.
- Notes already tagged `#assistant/clipping` were skipped on subsequent runs.
- A run-log entry records this job's status, outputs, and any evidence gaps after the checks above pass.

## Outputs

- Clipping notes tagged `#assistant/clipping`.
- Clipping notes with useful searchable titles.
- Topic notes updated with follow-up links extracted from clipping notes.
- One run-log entry for the clipping triage attempt.
