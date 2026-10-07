# Spec-Driven Development (SDD) Workflow

**Source:** Ticket Management System assessment (`docs/assessment.pdf`)  
**Last reviewed:** 28 September 2026

## Workflow

```
Requirement → Specification → Plan / Tasks → Implementation → Testing → Review → Fix
```

**Principles:**

- Write specifications **before** writing implementation code.
- Avoid one-shot prompts such as “Build the complete application.”
- The assessment evaluates **process** (specs, validation, grounding) as well as the working application.

## Specification artefacts (pre-implementation)

```
spec/
├── requirements.md
├── architecture.md
├── data-model.md
├── api-contract.md
├── state-machine.md
├── rag-ingestion.md
├── rag-api-contract.md
├── evaluation-strategy.md
├── ui-flow.md
└── test-strategy.md
```

## Steering files

Reusable AI and engineering guidance lives in `rules/`, `skills/`, and `commands/`.

## AI mistake documentation

- Record at least **one meaningful AI mistake** (incorrect code or ungrounded answer) caught during development.
- Primary location: `docs/prompt-history.md` (mirrored under `.specstory/history/`).

## Token optimisation (advisory)

Assessment mentions Graphify, Caveman, Codebase-memory MCP, and prompt caching—optional, not required for acceptance.

## Review commands

At each phase gate, use:

- `commands/review-spec.md`
- `commands/review-code.md`
- `commands/generate-tests.md`
- `commands/review-rag-output.md`
