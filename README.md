# Software Project Template

A universal, tech-stack-agnostic repository scaffold designed for modern software development with human and AI agent collaboration.

---

## Purpose

Starting a software project with AI coding assistants requires consistent context preservation. Without structured operational documentation, agents and developers risk hallucinating requirements, breaking existing architecture, or losing track of historical trade-offs.

This template provides a lightweight, living documentation framework that keeps human engineers and AI agents fully synchronized from day one.

---

## What's Included

- **[AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md)** — Core operating rules, engineering principles, context-loading orders, and Definition of Done for AI coding assistants.
- **[PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md)** — Living source of truth for product capabilities, feature status, and priority matrices.
- **[ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md)** — Real-time documentation of the system's actual (not aspirational) architecture, modules, and security postures.
- **[CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md)** — Active workstream tracker defining current scope, out-of-scope items, implementation plan, and validation criteria.
- **[DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md)** — Immutable architectural and technical decision log (ADR) recording context, choices, and trade-offs.
- **[RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md)** — Generic branch hierarchy, release checklists, promotion gates, and rollback policies.
- **[.github/pull_request_template.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/.github/pull_request_template.md)** — Standardized PR template enforcing documentation synchronization and validation checks.

---

## Starting a New Project

To spin up a new software project using this template:

1. **Use this Template:** Click "Use this template" on GitHub to create a new repository.
2. **Replace Placeholder Content:** Review each markdown file and replace generic placeholders with your project's specific details.
3. **Define Product Vision:** Populate [PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md) with initial planned capabilities (`PLANNED`, `IDEA`).
4. **Document Initial Architecture:** Fill in [ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md) with your target stack, data models, and directory structure.
5. **Confirm Branch Strategy:** Verify or customize the default `dev → main → prod` branch workflow in [RELEASE_PROCESS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/RELEASE_PROCESS.md).
6. **Set First Task:** Initialize [CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md) with the first concrete engineering task (such as repository initialization or baseline scaffolding).
7. **Orient the Agent:** Direct your AI coding assistant to read [AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md) before executing code changes.

---

## Recommended First Agent Prompt

When kicking off work with an AI agent in a newly created project repository, start with:

```text
Read AGENTS.md and all project documentation. Inspect the repository before making changes. Update the project documentation to accurately describe this project's current state. Do not implement new features until the project baseline is understood.
```

---

## Philosophy

Documentation in this repository is **lightweight and operational**.

The goal is not excessive paperwork or bureaucracy. The goal is to preserve clear, deterministic context so that human developers and AI agents can seamlessly pick up, resume, and extend work without rediscovering the same constraints or re-debating past decisions.
