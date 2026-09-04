# Release Process

This document outlines the standard release lifecycle, branching conventions, deployment safety gates, and rollback guidance for this repository.

---

## Core Release Principles

- **Default Promotion Hierarchy:** Releases follow the strict three-tier hierarchy: `dev → main → prod`.
- **No Direct Commits to Production:** Never push or commit directly to the `prod` branch.
- **Preview & Staging Validation:** All changes destined for production must be validated on `main` (preview/staging) prior to `prod` promotion.
- **No Skipping Stages:** Do not merge `dev` directly into `prod` or promote feature branches directly to `prod` unless an emergency exception is explicitly approved.
- **Git Awareness:** Always check `git status` and `git branch` prior to staging, committing, or promoting changes.
- **Protected History:** Never force-push (`git push --force`) to shared or protected branches (`prod`, `main`, `dev`), and never rewrite published commit history without explicit team approval.
- **Clean Commits:** Keep unrelated features, refactors, or fixes out of release commits.
- **Post-Release Context:** After completing a release to `prod`, return active working context to `dev`.

---

## Default Branch Model

```text
[ Feature / Topic Branches ]
             ↓
            dev   (active development & local testing)
             ↓
            main  (preview / staging / release candidate)
             ↓
            prod  (production deployment only)
```

### Branch Responsibilities

| Branch | Role | Rules & Responsibilities |
|---|---|---|
| `dev` | **Active Development** | Default branch for ongoing feature implementation, bug fixes, and developer testing. Feature branches branch from and merge back into `dev`. Unfinished or experimental work must not be promoted past `dev`. |
| `main` | **Preview / Staging** | Release-candidate environment for staging verification and pre-production testing. Receives changes from `dev` only after local development validation passes. |
| `prod` | **Production Only** | Reflects the live, verified production deployment. Never receives direct implementation commits; updated strictly by promoting validated releases from `main`. |

> **Note on Customization:** This `dev → main → prod` model is the default for repositories created from this template. If a specific project requires an alternative model (e.g., direct `main → prod`), it must be explicitly documented in this file and reflected in [AGENTS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/AGENTS.md).

---

## Standard Development & Promotion Workflow

```text
1. Development on `dev`
   ↓
2. Local Validation (tests, lints, manual checks)
   ↓
3. Merge `dev` into `main` (via PR or promotion)
   ↓
4. Preview / Staging Validation on `main`
   ↓
5. Merge `main` into `prod` (Production Release)
   ↓
6. Production Verification & Monitoring
   ↓
7. Return working context to `dev`
```

### 1. Development on `dev`
- Implement code aligned with [CURRENT_TASK.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/CURRENT_TASK.md).
- Run unit/integration tests and static analysis locally.
- Validate feature functionality against acceptance criteria.

### 2. Promotion to `main` (Preview / Staging)
- Confirm `dev` is clean and passing all tests.
- Open a pull request targeting `main` using the standard PR template (`.github/pull_request_template.md`).
- Deploy/run in the staging/preview environment.
- Conduct end-to-end and integration smoke testing on preview build.

### 3. Promotion to `prod` (Production)
- Confirm all preview/staging acceptance tests pass on `main`.
- Complete the [Pre-Release Checklist](#pre-release-checklist).
- Promote `main` to `prod` (via approved PR or designated release tag).
- Trigger production deployment.

### 4. Post-Release & Return to `dev`
- Perform [Post-Release Verification](#post-release-verification) on live environment.
- Synchronize documentation ([PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md), [ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md), [DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md)).
- Switch local branch back to `dev` for subsequent task execution.

---

## Partial Releases

If `dev` contains in-progress or experimental work that is **not** ready for release:

- **Do Not Bulk Merge:** Never merge all of `dev` into `main` when unapproved work is present.
- **Isolate Scoped Release:** Create a dedicated release branch or cherry-pick approved feature branches onto a release staging branch with explicit user approval.
- **Preserve History:** Do not rewrite git history or perform silent rebase operations without approval.

---

## Hotfixes (Emergency Production Fixes)

For critical production defects requiring immediate resolution:

1. **Branch Hotfix:** Create a hotfix branch branched directly from `prod` (e.g., `hotfix/<issue-name>`).
2. **Targeted Fix:** Apply the minimal fix required to resolve the incident.
3. **Validate:** Test the hotfix thoroughly.
4. **Promote to `prod`:** Merge the hotfix branch into `prod` with explicit user approval.
5. **Back-Port Immediately:** Merge the fix back into `main` and `dev` so branches never diverge or regress:
   ```text
   hotfix branch → prod (deploy)
                ↘ main
                ↘ dev
   ```

---

## Pre-Release Checklist

- [ ] All automated tests and build validation pass.
- [ ] No uncommitted or untracked changes remain in working directory (`git status`).
- [ ] Staging/preview smoke testing completed successfully on `main`.
- [ ] Documentation updated ([PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md), [ARCHITECTURE.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/ARCHITECTURE.md), [DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md)).
- [ ] Target environment variables and secrets are configured.
- [ ] Rollback strategy identified in case of deployment failure.

---

## Post-Release Verification

- [ ] Verify deployment health and availability on live URL / production environment.
- [ ] Execute critical-path user flows and smoke tests.
- [ ] Monitor application error logs and metrics for anomalies.
- [ ] Mark completed features as `DONE` in [PRODUCT_FEATURES.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/PRODUCT_FEATURES.md).
- [ ] Switch active branch back to `dev`.

---

## Rollback Guidance

- If a release introduces critical bugs or downtime, revert `prod` to the last known stable release tag or commit.
- Prioritize rapid restoration of stable service over in-place live debugging.
- Conduct a root-cause post-mortem, document lessons in [DECISIONS.md](file:///Users/yatishgurrala/Desktop/PersonalDocs/Side%20hustle/software-project-template/DECISIONS.md), and fix the defect on `dev` (or via hotfix) before redeploying.
