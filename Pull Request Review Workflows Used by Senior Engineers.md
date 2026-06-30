````md
# Part 3: Pull Request Review Workflows Used by Senior Engineers

---

# Overview

Pull Requests (PRs) are one of the most important quality control mechanisms in professional software development.

Senior engineers use Pull Requests not only to merge code but also to:

- Maintain code quality
- Share knowledge across the team
- Prevent bugs from reaching production
- Enforce architecture standards
- Improve maintainability
- Automate testing and deployment pipelines

---

# Standard Enterprise Workflow

```text
main
 │
 ├── develop
 │
 ├── feature/authentication
 ├── feature/payment
 ├── feature/dashboard
 │
 ├── release/v2.0
 │
 └── hotfix/security-fix
````

---

# Workflow 1: Feature Development PR

## Step 1: Update Local Main Branch

```bash
git checkout main
git pull origin main
```

---

## Step 2: Create Feature Branch

```bash
git checkout -b feat/user-authentication
```

---

## Step 3: Development Work

```bash
git add .
git commit -m "feat(auth): implement JWT authentication"
```

Example Conventional Commit:

```text
feat(auth): implement JWT authentication
```

---

## Step 4: Push Feature Branch

```bash
git push origin feat/user-authentication
```

---

## Step 5: Open Pull Request

PR Title:

```text
feat(auth): implement JWT authentication
```

Example PR Description:

```text
## Summary
Implemented JWT based authentication system.

## Changes
- Added login endpoint
- Added refresh token support
- Added access token middleware

## Testing
- Unit tests passed
- Integration tests passed

## Breaking Changes
None

## Related Issues
Closes #24
```

---

## Step 6: Code Review

Senior engineer checks:

* Code readability
* Naming conventions
* Security vulnerabilities
* Performance issues
* Architecture compliance
* Test coverage
* Documentation updates

---

## Step 7: Resolve Review Comments

```bash
git add .
git commit -m "fix(auth): resolve PR review comments"
git push
```

Git automatically updates the PR.

---

## Step 8: Merge Pull Request

Preferred method:

```text
Squash and Merge
```

Result:

```text
feat(auth): implement JWT authentication
```

Advantages:

* Cleaner history
* Easier changelog generation
* Better release notes

---

# Workflow 2: Keeping Feature Branch Updated

## Rebase Strategy

```bash
git checkout main
git pull origin main

git checkout feat/user-authentication
git rebase main
```

Resolve conflicts if necessary.

Then push:

```bash
git push --force-with-lease
```

Never use:

```bash
git push --force
```

---

# Workflow 3: Hotfix Pull Request

Production issue discovered.

Create hotfix branch:

```bash
git checkout main
git pull origin main

git checkout -b hotfix/login-timeout
```

Fix issue:

```bash
git add .
git commit -m "fix(auth): resolve production login timeout issue"
```

Push:

```bash
git push origin hotfix/login-timeout
```

Create emergency PR.

Review priority:

```text
Critical
```

Merge directly into:

```text
main
```

Then back merge:

```text
main -> develop
```

---

# Workflow 4: Documentation Pull Request

```bash
git checkout -b docs/api-documentation
```

Commit:

```bash
git commit -m "docs(api): update authentication examples"
```

---

# Workflow 5: Dependency Upgrade Pull Request

```bash
git checkout -b build/dependency-upgrade
```

Commit:

```bash
git commit -m "build(deps): upgrade express to v5"
```

---

# Workflow 6: CI/CD Pipeline Changes

```bash
git checkout -b ci/github-actions-update
```

Commit:

```bash
git commit -m "ci(actions): optimize build pipeline"
```

---

# Workflow 7: Refactoring Pull Request

```bash
git commit -m "refactor(auth): simplify token validation logic"
```

Rules:

* No functional changes.
* No new features.
* No bug fixes.

Only internal improvements.

---

# Workflow 8: Performance Optimization Pull Request

```bash
git commit -m "perf(database): reduce query execution time"
```

---

# Workflow 9: Test Improvements Pull Request

```bash
git commit -m "test(auth): add integration tests for login flow"
```

---

# Workflow 10: Reverting Pull Request

```bash
git revert commit_hash
git push
```

Conventional Commit:

```text
revert: rollback JWT authentication implementation

Refs: 2a84bde
```

---

# Senior Engineer Pull Request Checklist

## Functionality

* [ ] Feature works correctly
* [ ] Edge cases handled
* [ ] Error handling implemented

---

## Code Quality

* [ ] Code follows style guide
* [ ] Naming conventions followed
* [ ] No duplicate code
* [ ] Functions are small and focused

---

## Security

* [ ] Input validation exists
* [ ] Authentication enforced
* [ ] Authorization verified
* [ ] Secrets not committed

---

## Performance

* [ ] Database queries optimized
* [ ] No unnecessary loops
* [ ] Caching considered

---

## Testing

* [ ] Unit tests added
* [ ] Integration tests added
* [ ] Existing tests passing

---

## Documentation

* [ ] README updated
* [ ] API docs updated
* [ ] Migration guide added if necessary

---

# Common Review Comments From Senior Engineers

## Naming Issues

Bad:

```python
x = calculate()
```

Good:

```python
monthly_revenue = calculate_monthly_revenue()
```

---

## Large Functions

Bad:

```text
500 line function
```

Good:

```text
Split into smaller reusable functions
```

---

## Hardcoded Values

Bad:

```python
timeout = 300
```

Good:

```python
DEFAULT_TIMEOUT_SECONDS = 300
```

---

## Missing Error Handling

Bad:

```python
user = database.get_user(id)
return user.name
```

Good:

```python
user = database.get_user(id)

if user is None:
    raise UserNotFoundException()
```

---

# Conventional Commit Types Used in Pull Requests

| Type     | Purpose                     | SemVer Impact |
| -------- | --------------------------- | ------------- |
| feat     | New feature                 | MINOR         |
| fix      | Bug fix                     | PATCH         |
| docs     | Documentation               | None          |
| style    | Formatting                  | None          |
| refactor | Internal improvement        | None          |
| perf     | Performance improvement     | PATCH         |
| test     | Testing changes             | None          |
| build    | Dependency or build changes | None          |
| ci       | CI/CD changes               | None          |
| chore    | Maintenance work            | None          |
| revert   | Revert previous change      | Depends       |
| feat!    | Breaking feature            | MAJOR         |
| fix!     | Breaking fix                | MAJOR         |

---

# Senior Team Merge Strategy

Preferred order:

```text
Developer
    ↓
Pull Request
    ↓
Automated Tests
    ↓
Code Review
    ↓
Approval
    ↓
Squash Merge
    ↓
Deployment
```

---

# Recommended Pull Request Size

Ideal:

```text
100 - 400 lines changed
```

Acceptable:

```text
400 - 800 lines changed
```

Risky:

```text
800+ lines changed
```

Large Pull Requests increase:

* Review time
* Defect probability
* Merge conflicts

---

# Golden Rules Used by Senior Engineers

1. Small Pull Requests are easier to review.
2. Every Pull Request should have a single responsibility.
3. Every Pull Request should pass CI before review.
4. Every feature should include tests.
5. Use Conventional Commits consistently.
6. Never merge code that you do not understand.
7. Prefer squash merge for clean history.
8. Use rebase to keep feature branches updated.
9. Document breaking changes.
10. Treat Pull Request reviews as knowledge sharing, not gatekeeping.

---

```
```
