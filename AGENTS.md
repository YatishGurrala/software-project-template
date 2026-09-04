# Agent Instructions

This document defines the core operating principles and rules for AI coding agents working in this repository.

---

## 1. Required Context Loading

Before making meaningful changes, inspect and read the relevant project context files:

1. **[README.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/README.md)** — Project overview and setup baseline.
2. **[PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md)** — Source of truth for product capabilities and status.
3. **[ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md)** — Current-state system architecture (not aspirational).
4. **[CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md)** — Active workstream, scope, and acceptance criteria.
5. **[DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md)** — Historical architecture and product decisions.
6. **[RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md)** — Branching hierarchy and release discipline (read whenever branching, merging, or releasing).

---

## 2. Global Engineering Principles

- **Understand before modifying:** Read existing implementations, abstractions, and tests before writing code.
- **Targeted changes:** Favor precise, targeted modifications over broad refactors or unnecessary rewrites.
- **Respect established scope:** Keep implementation strictly aligned with [CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md). Avoid opportunistic, unrelated cleanup during active tasks.
- **No speculative requirements:** Never fabricate product requirements or silently guess behavior. If requirements are ambiguous, document the ambiguity and ask for clarification.
- **Preserve working logic:** Do not replace functioning code simply because an alternative pattern looks cleaner or more modern.
- **Preserve backward compatibility:** Do not introduce breaking changes to APIs, data models, or interfaces unless explicitly requested or approved.
- **Design & UI preservation:** Do not redesign user interfaces, component hierarchies, or core architectures unless explicitly instructed.
- **Reuse existing patterns:** Reuse existing abstractions, helper functions, and design patterns within the codebase where reasonable.
- **Dependency discipline:** Do not introduce new external libraries or dependencies unless they provide clear, justifiable value.
- **Quality & security baseline:** Always consider input validation, error handling, edge cases, privacy, and security.
- **Secrets protection:** Never commit secrets, credentials, API keys, private tokens, or sensitive configuration into source control.

---

## 3. Git Operations & Agent Permissions

AI agents must strictly respect Git repository state and human control over branch history:

- **No Autonomous Modifying Git Operations:** The agent must **not** autonomously execute `git commit`, `git push`, `git merge`, `git rebase`, `git cherry-pick`, `git branch -d`/`-D`, `git checkout`/`git switch` to a new branch, or force-push (`git push --force`) unless the user **explicitly requests that specific Git action**.
- **Read-Only Inspection Allowed:** The agent is permitted to run non-destructive, read-only Git inspection commands when necessary to understand state: `git status`, `git diff`, `git log`, `git branch`, and `git show`.
- **Pre-Action Verification:** Before performing any explicitly requested commit, push, or merge, the agent must check and verify the current branch and `git status`.
- **No Implicit Commits:** Never assume that completing a code edit, fix, or task implies the agent should automatically stage, commit, or push.
- **Strict Adherence to Release Flow:** When Git operations are requested, the agent must follow the branching and promotion flow defined in [RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md) exactly.

---

## 4. Default Branch & Promotion Discipline

This repository adheres to a standard three-tier branch lifecycle by default:

```text
dev (active development)
 ↓
main (preview / staging)
 ↓
prod (production)
```

- **Branch Roles:**
  - `dev`: Active development and daily implementation. Feature branches branch from `dev`.
  - `main`: Preview, staging, and pre-production validation. Receives changes from `dev` only after development validation passes.
  - `prod`: Production runtime only. Represents the currently approved production deployment.
- **Release Hierarchy:** Normal release flow strictly follows `dev → main → prod`. Never skip `main` during normal releases.
- **Production Guardrails:**
  - Never commit or push directly to `prod`.
  - Never merge `dev` directly into `prod` or feature branches directly into `prod` without explicit emergency authorization.
  - Never make `prod` the default working branch.
- **Post-Release Return:** Following any production release promotion, return active development context to `dev`.
- **Partial Releases:** If `dev` contains incomplete work not intended for release, do not merge `dev` into `main` in bulk. Isolate releases via clean feature/release branches with user approval; never silently cherry-pick or rewrite history.
- **Hotfixes:** Hotfixes must be branched from `prod`, validated, promoted to `prod` with explicit approval, and promptly back-merged into `main` and `dev`.

---

## 5. Documentation Discipline

Documentation in this repository is operational and active, not decorative:

- **[PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md):** Source of truth for product capability status.
- **[ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md):** Describes the architecture as it exists today, not future concepts.
- **[CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md):** Tracks only the single active task or workstream.
- **[DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md):** Records key technical/product decisions, context, tradeoffs, and consequences.
- **[RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md):** Defines branch workflow, release checklist, and safety gates.

---

## 6. Definition of Done

### For Coding Tasks:
A task is **not complete** until all of the following criteria are satisfied:

1. **Implementation Complete:** Code meets all functional requirements outlined in [CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md).
2. **Validation Complete:** Relevant automated tests, linting, or manual verification steps have passed.
3. **Regressions Considered:** Potential side effects and regressions have been assessed.
4. **Documentation Synchronized:** Affected project documentation has been updated.
5. **Feature Matrix Updated:** [PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md) reflects new/updated feature statuses.
6. **Architecture Updated:** [ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md) is updated if structural or architectural changes occurred.
7. **Current Task Closed:** [CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md) reflects the final status and outcome.
8. **Decisions Logged:** Any important architectural or technical decisions are recorded in [DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md).
9. **Git Review:** Git diff and status have been reviewed to ensure clean, focused changes.

> **Rule:** An agent must not mark work complete while documentation is knowingly stale or out of sync.

### For Production Releases:
A production release is **not complete** until:
1. `dev` changes were fully tested and validated.
2. `main` (preview/staging) was verified and approved.
3. `main` was promoted to `prod` following the defined checklist.
4. Production verification and post-deploy checks were completed.
5. Relevant documentation and feature statuses were synchronized.
6. Active branch returned to `dev` for continued development.

---

## 7. Extending or Overriding These Instructions

Project-specific agent instructions may extend this document or customize workflows. However, any modification or override to default branch strategies, permissions, or engineering rules must be **explicitly documented** in [RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md) and [AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md), and must never happen silently.
