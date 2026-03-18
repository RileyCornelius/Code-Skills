---
name: git-worktrees
description: Create or manage isolated git worktrees for parallel feature work, experiments, reviews, or bug fixes without disturbing the current checkout. Use when the user wants a separate workspace or branch, asks to isolate work before implementation, or when working in the current tree risks conflicts or mixing unrelated changes.
---

# Git Worktrees

## Overview

Git worktrees create isolated workspaces that share a repository while keeping separate checkouts.

**Core principle:** Systematic directory selection + safety verification = reliable isolation.

Use commands that fit the current shell and platform. For concrete examples, see [references/powershell.md](references/powershell.md) for PowerShell and [references/posix.md](references/posix.md) for POSIX shells.

## Workflow

### 1. Announce intent

State that you are setting up an isolated workspace with git worktrees.

### 2. Inspect existing conventions

Follow this priority order:

- Prefer an existing `.worktrees/` directory.
- Otherwise prefer an existing `worktrees/` directory.
- Otherwise check repository guidance such as `CLAUDE.md`, `AGENTS.md`, or `README.md` for a preferred location.
- Ask the user only if the location is still ambiguous.

### 3. Verify safety for project-local directories

For `.worktrees/` or `worktrees/`, verify the directory is ignored before creating anything.

- Use `git check-ignore` instead of guessing.
- If the directory is not ignored, add an appropriate ignore rule before creating the worktree.
- If adding the ignore rule would create a visible repository change, call that out before committing it.

### 4. Create the worktree

Choose a path under the selected location and create the worktree on a branch that matches the task.

- Use `git worktree add <path> -b <branch>` when creating a new branch.
- If the branch already exists, create the worktree without `-b`.
- Change into the new worktree before running setup commands.

### 5. Prepare the project

Auto-detect the project tooling from files in the worktree.

- Install dependencies only when the repo uses a package manager that requires it.
- Run lightweight setup commands that establish a clean baseline.
- Avoid hardcoding package managers or shells when the repo indicates something else.
- Common signals: `package.json` or a Node lockfile (npm/yarn/pnpm install), `Cargo.toml` (cargo build), `pyproject.toml` or `requirements.txt` (pip/poetry install), `go.mod` (go mod download).
- Use the repository's existing scripts when available instead of inventing your own.

### 6. Verify the baseline

If the project has tests or an obvious smoke-check, run the appropriate baseline check before implementation.

- If checks fail, stop and ask whether to proceed with a dirty baseline.
- If checks pass, report the workspace as ready.

### 7. Report outcome

```
Worktree ready at <full-path>
Tests passing (<N> tests, 0 failures)
Ready to implement <feature-name>
```

## Quick Reference

| Situation | Action |
|-----------|--------|
| `.worktrees/` exists | Use it after verifying it is ignored |
| `worktrees/` exists | Use it after verifying it is ignored |
| No existing location | Check repo docs, then ask only if still ambiguous |
| Directory not ignored | Add ignore rule before creating the worktree |
| Tests fail during baseline | Report failures + ask |
| No obvious setup files | Skip dependency installation |

## Common Mistakes

### Skipping ignore verification

- **Problem:** Worktree contents get tracked, pollute git status
- **Fix:** Always use `git check-ignore` before creating a project-local worktree

### Assuming directory location

- **Problem:** Creates inconsistency, violates project conventions
- **Fix:** Follow priority: existing directory > repo guidance > ask

### Proceeding with failing tests

- **Problem:** Can't distinguish new bugs from pre-existing issues
- **Fix:** Report failures, get explicit permission to proceed

### Hardcoding setup commands

- **Problem:** Breaks on projects using different tools
- **Fix:** Auto-detect from project files and existing scripts

### Assuming a POSIX shell

- **Problem:** Commands fail in PowerShell or other environments
- **Fix:** Use the active shell, and consult [references/powershell.md](references/powershell.md) or [references/posix.md](references/posix.md) for shell-specific examples

## Example Workflow

```
You: I'm using the use-git-worktrees skill to set up an isolated workspace.

[Check .worktrees/ - exists]
[Verify ignored - git check-ignore confirms .worktrees/ is ignored]
[Create worktree: git worktree add .worktrees/auth -b feature/auth]
[Run project setup]
[Run baseline checks - passing]

Worktree ready at <full-path>
Tests passing (<N> tests, 0 failures)
Ready to implement auth feature
```

## Red Flags

**Never:**
- Create a worktree without verifying it is ignored when using a project-local directory
- Skip baseline verification when the repo has tests or a smoke-check
- Proceed with failing baseline checks without asking
- Assume directory location when it is ambiguous
- Assume shell-specific commands will work everywhere

**Always:**
- Follow directory priority: existing directory > repo guidance > ask
- Verify directory is ignored for project-local locations
- Auto-detect and run project setup
- Verify a clean baseline before implementation
