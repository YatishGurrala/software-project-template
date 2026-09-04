# Software Project Template

A universal, tech-stack-agnostic repository scaffold designed for modern software development with human and AI agent collaboration.

---

## Purpose

Starting a software project with AI coding assistants requires consistent context preservation. Without structured operational documentation, agents and developers risk hallucinating requirements, breaking existing architecture, or losing track of historical trade-offs.

This template provides a lightweight, living documentation framework that keeps human engineers and AI agents fully synchronized from day one.

---

## What's Included

- **[NEW_PROJECT_BOOTSTRAP.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/NEW_PROJECT_BOOTSTRAP.md)** — First-run checklist for newly spawned projects, guiding Git state verification, branch inspection, and document initialization.
- **[AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md)** — Core operating rules, engineering principles, context-loading orders, and Definition of Done for AI coding assistants.
- **[PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md)** — Living source of truth for product capabilities, feature status, and priority matrices.
- **[ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md)** — Real-time documentation of the system's actual (not aspirational) architecture, modules, and security postures.
- **[CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md)** — Active workstream tracker defining current scope, out-of-scope items, implementation plan, and validation criteria.
- **[DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md)** — Immutable architectural and technical decision log (ADR) recording context, choices, and trade-offs.
- **[RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md)** — Standard `dev → main → prod` branch hierarchy, release checklists, promotion gates, and rollback policies.
- **[.github/pull_request_template.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/.github/pull_request_template.md)** — Standardized PR template enforcing documentation synchronization and validation checks.

---

## Starting a New Project

To spin up a new software project using this template:

1. **Create Repository:** Create a repository using this GitHub template.
2. **Include All Branches:** Select **"Include all branches"** when creating the repository so the standard `dev`, `main`, and `prod` branches are copied into the new repository.
3. **Open Bootstrap Guide:** Open [NEW_PROJECT_BOOTSTRAP.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/NEW_PROJECT_BOOTSTRAP.md).
4. **Orient the Agent:** Give its instructions to the coding agent before implementation begins.
5. **Verify Branches & Release Flow:** Verify branch and history state before using the normal `dev → main → prod` release workflow.

---

## Recommended First Agent Prompt

When kicking off work with an AI agent in a newly created project repository, start with:

```text
Read AGENTS.md, NEW_PROJECT_BOOTSTRAP.md, and all project documentation. Inspect the repository before making changes. Follow the bootstrap checklist to accurately describe this project's current state. Do not implement new features until the project baseline is understood.
```

---

## Philosophy

Documentation in this repository is **lightweight and operational**.

The goal is not excessive paperwork or bureaucracy. The goal is to preserve clear, deterministic context so that human developers and AI agents can seamlessly pick up, resume, and extend work without rediscovering the same constraints or re-debating past decisions.
