# LLM Wiki

- Purpose: once a week, dispatch a separate agent to create or maintain a persistent markdown wiki from the assistant's curated knowledge sources, following the pattern in the Bear note `LLM Wiki`.

## Due Rule

- Run weekly.

## Configuration

- Concept note: Bear note titled `LLM Wiki`.
- Concept note id: `B23DFFA6-E09E-47E5-96A4-7B3CAB53588F`.
- Wiki root: `assistant/wiki/llm-wiki`.
- Wiki schema file: `assistant/wiki/llm-wiki/AGENTS.md`.
- Raw sources: Bear notes tagged `#assistant/clipping`.
- Wiki index note: Bear note titled `LLM Wiki Index`.
- Wiki log note: Bear note titled `LLM Wiki Log`.

## Inputs

- This job's `Configuration` section.
- Bear concept note `LLM Wiki`.
- Bear notes tagged `#assistant/clipping`; these are the raw source layer.
- Bear topic notes tagged `#assistant/topic` and child topic tags under `#assistant/topic/<topic-subject>`.
- Existing files under `assistant/wiki/llm-wiki` when present.
- Bear note `LLM Wiki Index` when present.
- Bear note `LLM Wiki Log` when present.
- Shared Bear CLI and run-log instructions live in `docs/`.

## Actions

- Read this job's `Configuration` section before dispatch.
- Read the Bear concept note `LLM Wiki` and treat it as the design brief for the worker.
- Inspect whether `assistant/wiki/llm-wiki` already exists and summarize the current wiki state for the worker.
- Search for existing Bear notes titled `LLM Wiki Index` and `LLM Wiki Log`; create or update them through the worker, not in the dispatcher.
- Gather a bounded source inventory for the worker:
  - all Bear topic note titles, ids, child topic tags, and curated-link sections;
  - Bear clipping note titles, ids, tags, source links, and modified dates;
  - any existing `LLM Wiki Index`, `LLM Wiki Log`, and schema content.
- If the source inventory is too large for one prompt, give the worker explicit bounded sampling rules and tell it to read additional sources directly as needed.
- Dispatch exactly one separate LLM Wiki agent.
- Give the delegated agent the concept note id, wiki root, source inventory, existing wiki state, and this required behavior:
  - Create `assistant/wiki/llm-wiki` if it does not exist.
  - Create or update the wiki schema file so future agents know the page conventions, source rules, indexing rules, log format, and maintenance workflow.
  - Treat Bear notes tagged `#assistant/clipping` as the raw source layer; do not create a repo-side raw-source file.
  - Use Bear topic notes only as source-discovery and taxonomy context, not as raw sources unless they are also tagged `#assistant/clipping`.
  - Do not modify raw clipping contents from the worker unless a specific source cleanup is required and recorded.
  - Create or update markdown wiki pages that synthesize the sources into persistent, interlinked pages.
  - Maintain Bear note `LLM Wiki Index` as the content-oriented catalog of pages.
  - Maintain Bear note `LLM Wiki Log` as the chronological record of ingests, queries, and lint passes.
  - Flag contradictions, stale claims, missing cross-references, orphan pages, and topics that need better source coverage.
  - Prefer incremental maintenance over wholesale rewrites when a wiki already exists.
  - Keep generated wiki pages concise, source-linked, and easy to browse in a markdown or Obsidian-style graph.
  - Do not invent source claims; every substantive claim should trace back to a Bear note id, source link, or existing wiki page.
  - Run a final lint pass over the wiki files and record unresolved issues in Bear note `LLM Wiki Log`.
- If dispatch fails, record the exact dispatch failure in the run log and stop.
- Do not perform the wiki creation or maintenance in this dispatcher job.
- After the completion check passes, add a compact run-log entry using `docs/job-run-log.md`.

## Completion Check

- This job's `Configuration` section was read before dispatch.
- The Bear concept note `LLM Wiki` was read before dispatch.
- The current wiki root state was checked before dispatch.
- Existing Bear index and log note state was checked before dispatch.
- A bounded source inventory was gathered or explicit worker-side source-gathering rules were provided.
- Exactly one separate LLM Wiki agent was dispatched.
- The delegated agent received the concept note id, wiki root, source inventory or source-gathering rules, existing wiki state, and the required behavior listed above.
- No wiki creation or maintenance was performed by the dispatcher job.
- A run-log entry records this job's status, dispatched agent, source-inventory evidence, outputs, and any evidence gaps after the checks above pass.

## Outputs

- One separate LLM Wiki agent dispatch.
- Created or updated wiki pages under `assistant/wiki/llm-wiki` by the delegated agent.
- Created or updated Bear notes `LLM Wiki Index` and `LLM Wiki Log` by the delegated agent.
- One compact run-log entry for the LLM Wiki job attempt.
