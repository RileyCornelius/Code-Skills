---
name: git-commit
description: Generate well-structured git commit messages with a standard subject line and optional description. Use when committing staged changes, writing commit messages, or when the user asks to commit.
---

# Git Commit

## General Rules

- Commit messages must have a subject line and may have a description.
- The subject line should start with Standard Terminology.
- The subject line should be capitalized and must not end in a period.
- The subject line should be written in imperative mood (_Fix_, not _Fixed_ / _Fixes_ etc.).
- The description should only contain explanations as to _what_ and _why_, never _how_. The latter belongs in documentation and implementation.

### Standard Terminology

**First Word** | **Meaning**
--- | ---
Add | Create a capability e.g. feature, class, dependency.
Remove | Remove a capability e.g. feature, class, dependency.
Update | Update a capability e.g. feature, class, dependency.
Fix | Fix an issue e.g. bug, typo, accident, misstatement.
Refactor | A change that just refactors existing code.
Optimize | Refactor of performance, e.g. speed up code.
Start | Begin doing something; e.g. create a feature flag.
Bump | Release a version must contain a version number.

### Description

Use the description to explain the background and reasoning, not the implementation. You can save all fellow developers and your future self some time by explaining _why_ you did _what_ instead of _how_ you did it. Only use a description when the reasoning is not obvious. If the reasoning is obvious, skip the description and just write a clear subject line.

- Describe why a change is being made.
- How does it address the issue?
- What effects does it have?
- Describe any limitations of the current code.
- Do not assume the reader understands what the original problem was.
- Bullet points are okay.
- Descriptions are not always necessary.

## Examples

In keeping with the standard output of git itself, all commit subject lines must be written in imperative mood.

**Good**
- Add feature X
- Refactor X for readability
- Update getting started documentation
- Remove deprecated methods
- Bump v1.0.0

**Bad**
- Fixed bug with Y
- Changing behavior of X

**Ugly**
- More fixes for broken stuff
- Sweet new API methods
- 42
