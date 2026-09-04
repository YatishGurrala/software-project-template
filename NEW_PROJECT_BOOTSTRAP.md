# New Project Bootstrap

This document is the standard first-run onboarding and verification checklist for repositories instantiated from this template. It ensures human engineers and AI coding agents align on context, branch status, and documentation baselines before starting feature implementation.

---

## 1. Read Project Rules

Before modifying the repository, inspect and read:

- **[AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md)** — Core operating principles, agent permissions, and Definition of Done.
- **[README.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/README.md)** — Project overview and setup guidance.
- **[PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md)** — Feature tracking source of truth.
- **[ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md)** — Current-state system architecture.
- **[CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md)** — Active workstream tracker.
- **[DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md)** — Historical architecture decision log.
- **[RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md)** — Branch hierarchy and promotion safety gates.

> **Rule:** Do not implement product features until the initial repository state has been inspected and understood.

---

## 2. Inspect Git State

Execute read-only Git inspection commands to understand repository topology:

- `git status`
- `git branch -a`
- `git remote -v`
- `git log --oneline --decorate --all`

Confirm:
- Current working branch (must be `dev`)
- Existing local branches
- Existing remote tracking branches
- Whether the working tree is clean

The expected default branch hierarchy is:
```text
dev (active development)
 ↓
main (preview / staging)
 ↓
prod (production)
```

---

## 3. Template Branch Verification

Repositories created from GitHub templates may use the **"Include all branches"** option.

- **If `dev`, `main`, and `prod` already exist:**
  - Do **NOT** recreate them.
  - Verify each branch exists locally and remotely as appropriate.
  - Inspect their commit histories.
  - Do **NOT** automatically merge, rebase, reset, cherry-pick, delete, or rewrite any branch.
  - Report any unexpected branch-history relationship before continuing.
- **If only `dev` exists:**
  - Do **NOT** automatically create `main` or `prod`.
  - Report the current state and wait for explicit approval before creating downstream branches.

> **Rule:** Normal project work must begin from `dev`.

---

## 4. Initialize Project Documentation

Replace generic template placeholders with confirmed information about the actual project:

- **[README.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/README.md):**
  - Project name, description, and purpose.
  - Development status and setup/run instructions when known.
- **[PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md):**
  - Replace example entries with real, confirmed product capabilities.
  - Do not invent hypothetical features.
- **[ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md):**
  - Document the actual current implementation.
  - If implementation does not exist yet, explicitly state that the baseline is being initialized.
  - Keep future architectural plans under [Future Considerations](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md#future-considerations).
- **[CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md):**
  - Document the active project task only if one has been explicitly defined.
  - If no task has been provided yet, state that no active implementation task has been defined yet.
  - Do not invent an initialization task just to populate this file.
- **[DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md):**
  - Remove template example entries where appropriate.
  - Record only real technical and architectural decisions made for the project.
- **[RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md):**
  - Retain `dev → main → prod` unless the project explicitly approves an override.
- **[AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md):**
  - Preserve universal operating rules and Definition of Done.
  - Append project-specific guidelines only when confirmed.

---

## 5. Git Safety Rules

The agent must **NOT** automatically:
- `commit`
- `push`
- `merge`
- `rebase`
- `cherry-pick`
- `reset`
- `force-push`
- Create or delete branches
- Switch branches

...unless **explicitly requested by the user**. Read-only Git inspection (`status`, `diff`, `log`, `branch`) is permitted.

---

## 6. Before Implementation Check

Before starting the first feature, the agent must report:
- Repository tree structure
- Current working branch
- `git status` output
- Local and remote branch state
- Summary of documentation updated
- Remaining unfilled placeholders
- Missing requirements or ambiguities

> **Rule:** Stop and wait for user approval before starting implementation if initialization reveals anything unexpected.

---

## Standard Release Model Summary

```text
dev (active development)
 ↓
main (preview / staging)
 ↓
prod (production)
```

- `dev` = active development and local testing
- `main` = preview / staging / release candidate
- `prod` = production only
- Never commit directly to `prod`.
- Normal releases must flow: `dev → main → prod`.
- After a production release, return working context to `dev`.
