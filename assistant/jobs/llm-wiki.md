# LLM Wiki

- Purpose: once a week, dispatch a separate agent to create or maintain a persistent Bear-based wiki from the assistant's curated clipping sources, following the pattern in the Bear note `LLM Wiki`.

## Due Rule

- Run weekly.

## Configuration

- Concept note: Bear note titled `LLM Wiki`.
- Concept note id: `B23DFFA6-E09E-47E5-96A4-7B3CAB53588F`.
- Wiki tag: `#assistant/llm-wiki`.
- Wiki schema note: Bear note titled `LLM Wiki Schema`.
- Raw sources: Bear notes tagged `#assistant/clipping`.
- Wiki index note: Bear note titled `LLM Wiki Index`.
- Wiki log note: Bear note titled `LLM Wiki Log`.
- Wiki page notes: Bear notes titled `LLM Wiki: <Page Title>`.

## Inputs

- This job's `Configuration` section.
- Bear concept note `LLM Wiki`.
- Bear notes tagged `#assistant/clipping`; these are the raw source layer.
- Bear topic notes tagged `#assistant/topic` and child topic tags under `#assistant/topic/<topic-subject>`.
- Bear note `LLM Wiki Schema` when present.
- Bear note `LLM Wiki Index` when present.
- Bear note `LLM Wiki Log` when present.
- Bear notes tagged `#assistant/llm-wiki`.
- Shared Bear CLI and run-log instructions live in `docs/`.

## Actions

- Read this job's `Configuration` section before dispatch.
- Read the Bear concept note `LLM Wiki` and treat it as the design brief for the worker.
- Search for existing Bear notes titled `LLM Wiki Schema`, `LLM Wiki Index`, and `LLM Wiki Log`; create or update them through the worker, not in the dispatcher.
- Search for Bear notes tagged `#assistant/llm-wiki` and summarize the current wiki state for the worker.
- Gather a bounded source inventory for the worker:
  - all Bear topic note titles, ids, child topic tags, and curated-link sections;
  - Bear clipping note titles, ids, tags, source links, and modified dates;
  - any existing `LLM Wiki Schema`, `LLM Wiki Index`, `LLM Wiki Log`, and `LLM Wiki: <Page Title>` content.
- If the source inventory is too large for one prompt, give the worker explicit bounded sampling rules and tell it to read additional sources directly as needed.
- Dispatch exactly one separate LLM Wiki agent.
- Give the delegated agent the concept note id, wiki tag, source inventory, existing wiki state, and this required behavior:
  - Create or update Bear note `LLM Wiki Schema` so future agents know the page conventions, source rules, indexing rules, log format, and maintenance workflow.
  - Treat Bear notes tagged `#assistant/clipping` as the raw source layer; do not create a repo-side raw-source file.
  - Use Bear topic notes only as source-discovery and taxonomy context, not as raw sources unless they are also tagged `#assistant/clipping`.
  - Do not modify raw clipping contents from the worker unless a specific source cleanup is required and recorded.
  - Create or update Bear notes titled `LLM Wiki: <Page Title>` as the persistent, interlinked wiki pages.
  - Maintain Bear note `LLM Wiki Index` as the content-oriented catalog of pages.
  - Maintain Bear note `LLM Wiki Log` as the chronological record of ingests, queries, and lint passes.
  - Tag all wiki schema, index, log, and page notes with `#assistant/llm-wiki`.
  - Flag contradictions, stale claims, missing cross-references, orphan pages, and topics that need better source coverage.
  - Prefer incremental maintenance over wholesale rewrites when a wiki already exists.
  - Keep generated wiki notes concise, source-linked, and easy to browse in Bear through wiki links.
  - Do not invent source claims; every substantive claim should trace back to a Bear note id, source link, or existing wiki page.
  - Run a final lint pass over the wiki notes and record unresolved issues in Bear note `LLM Wiki Log`.
- If dispatch fails, record the exact dispatch failure in the run log and stop.
- Do not perform wiki synthesis in this dispatcher job.
- After the completion check passes, add a compact run-log entry using `docs/job-run-log.md`.

## Completion Check

- This job's `Configuration` section was read before dispatch.
- The Bear concept note `LLM Wiki` was read before dispatch.
- Existing Bear schema, index, log, and page note state was checked before dispatch.
- A bounded source inventory was gathered or explicit worker-side source-gathering rules were provided.
- Exactly one separate LLM Wiki agent was dispatched.
- The delegated agent received the concept note id, wiki tag, source inventory or source-gathering rules, existing wiki state, and the required behavior listed above.
- No wiki synthesis was performed by the dispatcher job.
- A run-log entry records this job's status, dispatched agent, source-inventory evidence, outputs, and any evidence gaps after the checks above pass.

## Outputs

- One separate LLM Wiki agent dispatch.
- Created or updated Bear notes `LLM Wiki Schema`, `LLM Wiki Index`, `LLM Wiki Log`, and `LLM Wiki: <Page Title>` by the delegated agent.
- One compact run-log entry for the LLM Wiki job attempt.
