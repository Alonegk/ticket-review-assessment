# SpecStory / Cursor prompt history

**Archive date:** 28 September 2026

## How this folder is used

The assessment and `rules/prompt-history.md` expect AI session capture under `.specstory/history/` (SpecStory extension for Cursor/VS Code).

**Note:** The Cloud Agent workspace could not export a full Cursor/SpecStory transcript automatically. Entries below are curated summaries—not fabricated full session logs.

## Included artefacts (as of 28 Sep 2026)

| File | Purpose |
|------|---------|
| [`2026-09-28-rag-e2e-grounded-ask.md`](./2026-09-28-rag-e2e-grounded-ask.md) | Documented AI mistake during RAG E2E testing (mirrors `docs/prompt-history.md`) |
| [`2026-09-28-cloud-agent-bc-8fca06df-transcript.md`](./2026-09-28-cloud-agent-bc-8fca06df-transcript.md) | Cloud Agent session mirror |
| [`docs/prompt-history.md`](../docs/prompt-history.md) | Canonical prompt-history source |
| [`docs/agent-transcript-bc-8fca06df.md`](../docs/agent-transcript-bc-8fca06df.md) | Full Cloud Agent transcript (canonical path) |

Tool-call payloads and assistant “thinking” blocks are omitted in mirrors to keep files readable.

For native SpecStory exports from Desktop sessions, open the project in **Cursor Desktop** with the SpecStory extension enabled and sync `.specstory/history/` from that workspace.
