# Git — Deep Product & Market Research

**Owner / Content Creator:** Sandeep Barupal  
**Copyright:** © 2026 Sandeep Barupal. All rights reserved, except third-party resources under their own terms.  
**Research status:** Deep-research baseline v1.0 — desk research; repository collaboration scope requires validation.

## 1. Product thesis
Git is a distributed version-control system; a Git collaboration product is a separate layer that adds hosted repositories, identity, pull/merge requests, review, CI/CD, issues, releases and governance. The project must state clearly whether it is a Git learning/client tool, a repository hosting platform, or a collaboration product integrated with existing Git hosts.

## 2. Ecosystem and competitors
Git itself stores history as objects and refs and supports branching/merging locally. GitHub, GitLab and Bitbucket provide hosted collaboration workflows around repositories. These layers should not be conflated. Official Git documentation and Pro Git are foundational; GitHub features documentation is a useful source for hosted workflows. Sources: [Git documentation](https://git-scm.com/doc), [Pro Git book](https://git-scm.com/book/en/v2), [GitHub Features](https://github.com/features).

| Category | Examples | Comparison areas |
|---|---|---|
| Version control core | Git | Object model, branches, merges, remotes and recovery |
| Hosted collaboration | GitHub, GitLab, Bitbucket | Reviews, permissions, checks, releases and issue integration |
| Desktop Git clients | GitKraken and others | Visual history, conflict resolution, ease of recovery |
| CI/CD | GitHub Actions and alternatives | Trigger model, secrets, permissions, artifacts and quotas |

## 3. Feature specification
### P0 for a collaboration workspace
- Repository list, branches, commit history, tags and release records.
- Diff viewer with syntax-aware display and accessible line navigation.
- Pull/merge request workflow, reviewers, comments, checks and merge policies.
- Conflict explanation and safe recovery guidance.
- Branch protection, scoped roles, audit events and webhook management.
- Repository import/export and clear provider integration status.
### P1
- Issue tracking, project boards, release automation, CI/CD status, code owners and CODEOWNERS support.
- Signed commits/tags, dependency and secret alerts, rulesets and required checks.
### P2
- Organization-wide policy insights, code search, reusable automation and enterprise audit/export.

## 4. Page map
Repositories; Repository Overview; Files; Commits; Branches; Tags/Releases; Diff; Pull/Merge Requests; Review; Checks/CI; Issues; Projects; Security; Access/Roles; Webhooks; Audit; Settings.

## 5. Architecture
If hosting Git repositories, use proven Git server/storage primitives rather than implementing the Git object protocol from scratch. Separate repository storage, metadata database, authorization, search indexing, CI workers and artifact storage. Treat Git hooks and CI jobs as untrusted execution; isolate workers and scope tokens. Use queues for webhooks, retries and delivery logs.

## 6. Security and governance
Least-privilege repository permissions; branch protection; mandatory review/checks for protected branches; secret scanning; short-lived CI credentials; signed provenance where required; audit logs; retention/backup and restore drills. Prevent fork/PR code from accessing privileged secrets. Protect webhooks with signatures and replay controls.

## 7. Metrics and acceptance criteria
- Commit/branch history is consistent with the underlying repository.
- Unauthorized users cannot read private content or trigger protected merges.
- CI logs clearly show the permission context and secrets are withheld from untrusted jobs.
- Webhook retries are idempotent and observable.
- Metrics: PR lead time, review wait time, failed CI rate, deployment frequency, recovery time and policy violations.

## 8. Risks and validation
Risks: scope confusion, repository data loss, permission bugs, unsafe CI, storage scaling and vendor API limits. Validate whether users want a Git client, a GitHub-style hosting platform, or a unified dashboard for multiple providers. This decision changes architecture and cost dramatically.

## 9. References
- [Git documentation](https://git-scm.com/doc)
- [Pro Git book](https://git-scm.com/book/en/v2)
- [GitHub Features](https://github.com/features)
- [GitHub REST API docs](https://docs.github.com/en/rest)
- [GitHub Codespaces docs](https://docs.github.com/en/codespaces)

## 10. Next work
Write a product-boundary decision record, compare current GitHub/GitLab/Bitbucket collaboration workflows, define permissions and threat model, then prototype repository history and review flows.