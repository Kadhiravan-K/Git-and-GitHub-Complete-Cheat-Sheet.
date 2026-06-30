# Conventional Commits 1.0.0 Cheat Sheet

## Commit Format

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Examples

```text
feat(auth): add Google OAuth login support
fix(api): resolve token expiration issue
docs: update installation instructions
refactor(database): simplify query builder
```

---

# Standard Commit Types

| Type     | Purpose                                      | SemVer Impact |
| -------- | -------------------------------------------- | ------------- |
| feat     | Adds a new feature                           | MINOR         |
| fix      | Fixes a bug                                  | PATCH         |
| docs     | Documentation changes                        | None          |
| style    | Formatting, whitespace, linting              | None          |
| refactor | Code restructuring without changing behavior | None          |
| perf     | Performance improvements                     | None          |
| test     | Add or modify tests                          | None          |
| build    | Build system or dependency changes           | None          |
| ci       | CI/CD configuration changes                  | None          |
| chore    | Maintenance tasks                            | None          |
| revert   | Reverts previous commits                     | Depends       |

---

# Basic Examples

## New Feature

```text
feat: add dark mode support
```

## Bug Fix

```text
fix: prevent application crash on startup
```

## Documentation Update

```text
docs: correct README installation steps
```

## Refactoring

```text
refactor: simplify authentication service
```

## Performance Improvement

```text
perf: optimize image loading speed
```

## Testing

```text
test: add unit tests for payment service
```

---

# Using Scopes

Scopes identify the affected area of the project.

## Syntax

```text
type(scope): description
```

## Examples

```text
feat(auth): add OTP verification
fix(api): handle null responses
docs(readme): update examples
test(payment): add integration tests
```

Common scopes:

```text
auth
api
database
ui
backend
frontend
config
payment
docker
readme
```

---

# Breaking Changes

Breaking changes indicate incompatible API changes.

## Method 1: Using !

```text
feat!: remove legacy authentication system
```

```text
fix(api)!: change response structure
```

## Method 2: Using BREAKING CHANGE Footer

```text
feat: introduce new configuration format

BREAKING CHANGE: old config files are no longer supported.
```

## Method 3: Using Both

```text
feat(api)!: redesign REST API

BREAKING CHANGE: v1 endpoints have been removed.
```

### SemVer Result

| Commit Type     | Version Change |
| --------------- | -------------- |
| fix             | 1.0.0 → 1.0.1  |
| feat            | 1.0.0 → 1.1.0  |
| BREAKING CHANGE | 1.0.0 → 2.0.0  |

---

# Commit Body

Use the body to explain *why* the change was made.

## Example

```text
fix: prevent duplicate API requests

Introduce request identifiers and ignore stale responses.
Remove timeout-based mitigation strategy because it is no
longer necessary after implementing request tracking.
```

---

# Footers

Footers provide additional metadata.

## Syntax

```text
Token: Value
```

## Examples

```text
Reviewed-by: John Doe
Refs: #123
Closes: #42
Co-authored-by: Jane Doe
Acked-by: Team Lead
```

Example:

```text
fix: resolve payment timeout issue

Reduce retry intervals and improve error handling.

Reviewed-by: John Doe
Refs: #452
Closes: #451
```

---

# Complete Examples

## Feature Commit

```text
feat(payment): add UPI payment support
```

## Bug Fix Commit

```text
fix(login): prevent session timeout after refresh
```

## Documentation Commit

```text
docs(api): update authentication examples
```

## Refactoring Commit

```text
refactor(cache): simplify cache invalidation logic
```

## Performance Commit

```text
perf(search): reduce query execution time by 30%
```

## CI Commit

```text
ci: add automated security scanning workflow
```

## Dependency Update

```text
build: upgrade React to version 19
```

## Maintenance Task

```text
chore: remove unused assets
```

---

# Revert Commits

```text
revert: remove experimental caching layer
```

Example with reference:

```text
revert: rollback payment gateway migration

Refs: abc1234
```

---

# Recommended Team Rules

✅ One logical change per commit
✅ Use lowercase commit types
✅ Keep descriptions short and imperative
✅ Use scopes for larger projects
✅ Include bodies for complex changes
✅ Use BREAKING CHANGE when required
✅ Follow semantic versioning principles

---

# Recommended Commit Workflow

```text
1. Make one logical change
2. Stage files
3. Choose commit type
4. Add optional scope
5. Write short description
6. Add body if necessary
7. Add footer metadata
8. Commit
```

Example:

```text
feat(auth): add password reset feature

Users can now reset forgotten passwords using email
verification tokens.

Closes: #231
Reviewed-by: Team Lead
```

---

# Quick Reference

```text
feat     -> New feature
fix      -> Bug fix
docs     -> Documentation
style    -> Formatting only
refactor -> Code restructuring
perf     -> Performance improvement
test     -> Tests
build    -> Build system changes
ci       -> CI/CD changes
chore    -> Maintenance work
revert   -> Revert previous commit
```

---

# Semantic Version Mapping

```text
fix  -> PATCH -> 1.0.0 -> 1.0.1
feat -> MINOR -> 1.0.0 -> 1.1.0
BREAKING CHANGE -> MAJOR -> 1.0.0 -> 2.0.0
```

---

# Golden Rule

```text
If users gain functionality:
feat:

If users receive a bug fix:
fix:

If users must change their code:
BREAKING CHANGE
```
