# Prompt history

Recorded AI-assisted development notes for the Ticket Management System assessment.

**Last updated:** 28 September 2026

---

## 2026-09-28 — RAG E2E: flaky `grounded=true` assertion

**Phase:** Testing / RAG review

**What was asked:** Add full-stack RAG E2E tests using real Ollama and assert `grounded=true` on `/api/ai/ask` whenever retrieval succeeded.

**What went wrong:** Retrieval worked, but the chat model occasionally returned the exact no-match phrase (`No relevant tickets found.`), causing intermittent CI failures. The test used `Assumptions.assumeFalse` to skip failures, which masked regressions and conflicted with the evaluation strategy (mock the LLM for generation; test retrieval on its own).

**AI mistakes caught:**
- Treating probabilistic LLM output as a deterministic test gate
- Combining retrieval success and generation success in a single assertion

**Fix applied:** Default `./gradlew test` uses deterministic embeddings and a mocked `ChatModel` for ask/citation tests. Live Ollama runs under the `ollama-e2e` JUnit tag (`./gradlew ollamaE2eTest`). E2E ask tests validate retrieval and HTTP shape only—not `grounded=true` from the live model.

**SpecStory mirror:** `.specstory/history/2026-09-28-rag-e2e-grounded-ask.md`
