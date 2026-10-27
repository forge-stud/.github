# Contributing to fOrge

These rules apply to every fOrge repository unless a repository defines its own `CONTRIBUTING.md`. They exist so fOrge's code stays healthy, secure and understandable, no matter who joins or leaves the team.

## The five golden rules

1. **GitHub is the source of truth.** Code, decisions, documentation and task tracking live here. A decision made in a call, a chat group or an AI conversation does not exist until it is written down in GitHub.
2. **Every change goes through a pull request.** Nobody pushes directly to `main`, including maintainers.
3. **Every pull request is reviewed by someone other than its author.**
4. **Never commit secrets or customer data.** See [Secrets and sensitive data](#secrets-and-sensitive-data).
5. **Major milestones are approved by the Chairman** before they are considered complete or released to production.

## Workflow

1. **Start from an issue.** Every piece of work has an issue that explains what and why. If none exists, create one using the right template.
2. **Create a branch from `main`** following the naming convention below.
3. **Commit small, focused changes** following the commit convention below.
4. **Open a pull request.** If it is not ready for review yet, start its title with `WIP:`. Fill in the template completely and link the issue with `Closes #123`.
5. **Request a review** from another developer.
6. **Address feedback** until the reviewer approves.
7. **Merge with "Squash and merge"** and delete the branch.

### Branch names

Format: `type/issue-number-short-description`

| Prefix | Use for | Example |
|---|---|---|
| `feature/` | New functionality | `feature/42-mobile-money-checkout` |
| `fix/` | Bug fixes | `fix/57-negative-stock-count` |
| `hotfix/` | Urgent production fixes | `hotfix/61-login-timeout` |
| `docs/` | Documentation only | `docs/63-api-auth-guide` |
| `chore/` | Maintenance, dependencies, configuration | `chore/70-update-dependencies` |
| `refactor/` | Code restructuring with no behaviour change | `refactor/74-split-order-service` |

Keep branches short-lived and merge within a few days. Long-running branches create painful conflicts.

### Commit messages

We use [Conventional Commits](https://www.conventionalcommits.org): `type(scope): short description`

```
feat(checkout): add mobile money payment option
fix(inventory): prevent stock count from going negative
docs(api): document authentication endpoints
chore(deps): update dependencies
```

Code, comments, commit messages and technical documentation are written in English so the codebase stays accessible to contributors across West Africa. User-facing text is French-first.

## Pull requests

- One concern per pull request. Aim for fewer than 400 changed lines.
- Review your own diff before requesting a review.
- Never merge your own pull request without an approving review.
- **Emergency exception:** a `hotfix/` may be merged without review only with the Chairman's written approval in the pull request, and it must be reviewed within 1 business day afterwards.
- Reviewers respond within 1 business day.

### What reviewers check

- **Correctness:** does it do what the issue asks, including edge cases?
- **Security:** authentication and authorization on every endpoint, validated inputs, no injection risks, no sensitive data in logs or error messages, no new fraud opportunity.
- **West African conditions:** works on mobile, on slow or unstable connections, recovers gracefully from network loss, French text for users.
- **Maintainability:** readable, tested, documented.
- **Dependencies:** no new library without a clear reason.

## Secrets and sensitive data

**Never commit:** API keys, passwords, tokens, database credentials, JWT secrets, payment credentials, `.env` files, backups or database dumps, or customer personal data (names, phone numbers, addresses, transaction records).

**Store secrets in:** GitHub Secrets (for CI) or Cloudflare Secrets (for running services). Production credentials are held by fOrge owners only.

Document required configuration in a `.env.example` file with placeholder values.

Never paste secrets or real customer data into issues, chats or AI tools.

**If you commit a secret by accident:** tell the Platform-Admin team immediately. The secret must be revoked and replaced. Deleting the file or commit is not enough, because it stays in the history. Reporting quickly is never punished. Hiding it is a serious breach.

## Testing

- Write automated tests for business logic, especially anything involving money, stock, authentication or permissions.
- Test UI changes on a low-end Android phone, or in Chrome DevTools with network throttling set to "Slow 3G".

## Documentation and decisions

- Update the README and `docs/` when behaviour changes.
- Record architecture decisions as short decision records in `docs/decisions/` (context, decision, consequences).
- Add user-facing changes to `CHANGELOG.md`.

## Milestones and approvals

Work is grouped into GitHub Milestones. When a milestone is complete, the lead developer opens a **Milestone approval request** issue. The Chairman reviews it, may ask for changes, and approves by commenting "Approved" and applying the `governance: approved` label. Nothing is released to production before approval.

## Ownership

All code, documentation, designs and data created for fOrge belong to fOrge and live in fOrge organization repositories. Do not keep fOrge code in personal repositories, personal cloud storage or unapproved third-party services. When someone leaves, their access ends and their work stays with fOrge, which is why everything must be in GitHub and documented.

## Questions

Ask in the relevant issue or pull request. If the answer is a decision, record it in GitHub.
