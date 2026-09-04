# Decision Log (ADR)

This document tracks significant architectural, product, and technical decisions made throughout the project lifecycle.

---

## Log Rules

- **Record Significant Decisions:** Log structural, architectural, library, and data model decisions that have lasting impact. Do not log trivial implementation details or routine bug fixes.
- **Immutable History:** Never rewrite or delete historical decisions to hide previous choices.
- **Superseding Decisions:** If a past decision is changed, create a new entry with status `Accepted`, mark the old decision as `Superseded` or `Reversed`, and link between them.

---

## Example Entry

<!-- Example decision entry below. Replace or delete once actual decisions are recorded. -->

## YYYY-MM-DD — [Example] Monolithic vs Modular Directory Layout

**Status:** Accepted

**Context**
The repository was initialized as a universal project template requiring clear boundaries between operational documentation and upcoming application source code.

**Decision**
Adopt root-level operational markdown documentation (`AGENTS.md`, `PRODUCT_FEATURES.md`, `ARCHITECTURE.md`, `CURRENT_TASK.md`, `DECISIONS.md`, `RELEASE_PROCESS.md`) alongside a standard `.github` workflow directory.

**Reasoning**
Placing core context files at the repository root guarantees immediate visibility for both AI agents and human contributors upon opening the workspace, minimizing context discovery latency.

**Consequences**
All future contributors and AI agents must maintain these root-level documents as source-of-truth project artifacts.

---

<!-- Add new decisions below in chronological order using the format above -->
