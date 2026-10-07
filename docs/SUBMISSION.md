# Submission notes

**Prepared for assessment submission — 28 September 2026**

## Pre-submission checklist

| Item | Command / location | Status |
|------|-------------------|--------|
| Backend unit & API tests | `./gradlew test` | Run before submit |
| Frontend tests | `cd frontend && npm test` | Run before submit |
| Frontend lint + build | `cd frontend && npm run lint && npm run build` | Run before submit |
| Specs & plan | `spec/`, `plan/implementation-plan.md` | Present |
| Prompt history | `docs/prompt-history.md`, `.specstory/history/` | Present |
| AI mistake documented | `docs/prompt-history.md` | Present |
| Local run instructions | Root `README.md` | Present |

## Automated verification (what exists)

There is **no GitHub Actions / Jenkins pipeline** in this repo. Verification is **Gradle + npm scripts**:

| Flow | Command | What it covers |
|------|---------|----------------|
| **Default backend CI** | `./gradlew test` | Tickets, state machine, mocked RAG, H2 profile; excludes `ollama-e2e` tag |
| **Ollama full-stack (optional)** | `./gradlew ollamaE2eTest` | `RagEndToEndIntegrationTest` — needs Postgres + pgvector + Ollama |
| **Frontend** | `npm test`, `npm run lint`, `npm run build` | State machine UI logic, ESLint, production build |

Manual review gates (AI prompts, not executable): `commands/review-spec.md`, `commands/review-code.md`, `commands/generate-tests.md`, `commands/review-rag-output.md`.

## PostgreSQL-gated integration tests

Several integration tests need a **running PostgreSQL** instance with the **pgvector** extension. They use JUnit `@EnabledIf` and `RagIntegrationConditions#isPostgresReady`.

When PostgreSQL is unreachable, these tests are **skipped** (not failed):

- `PgVectorTicketKnowledgeVectorStoreIntegrationTest`
- `RagRetrievalEvaluationIntegrationTest` (R1–R5 retrieval fixtures)
- `TicketCreateTransitionIngestionIntegrationTest`

**Run locally:** start Postgres with pgvector, then `./gradlew test`.

Env overrides: `PGVECTOR_IT_JDBC_URL`, `PGVECTOR_IT_DB_USER`, `PGVECTOR_IT_DB_PASSWORD`.

Optional Ollama E2E: `./gradlew ollamaE2eTest` (see root `README.md`).

Default `./gradlew test` still validates tickets, state machine, and RAG logic via H2 and mocked components without PostgreSQL.

## Recommended submission run sequence

```bash
# 1. Backend (no Ollama required)
./gradlew test

# 2. Frontend
cd frontend && npm test && npm run lint && npm run build

# 3. Optional — with local Postgres + Ollama
./gradlew ollamaE2eTest
```
