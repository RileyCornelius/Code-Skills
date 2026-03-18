# POSIX Worktree Commands

Use these examples when the active shell is a POSIX shell such as `bash` or `zsh`. Prefer the repo's established tooling and conventions over these examples.

## Check for existing worktree directories

```bash
for d in .worktrees worktrees; do
  [ -d "$d" ] && printf '%s\n' "$d"
done
```

## Search repo docs for worktree guidance

```bash
rg -n "worktree" CLAUDE.md AGENTS.md README.md 2>/dev/null
```

## Verify a project-local directory is ignored

```bash
git check-ignore .worktrees
git check-ignore worktrees
```

If neither path is ignored, add an ignore rule before creating the worktree.

## Detect repo root and project name

```bash
repo_root="$(git rev-parse --show-toplevel)"
project_name="$(basename "$repo_root")"
```

## Create the worktree

New branch:

```bash
git worktree add <path> -b <branch>
```

Existing branch:

```bash
git worktree add <path> <branch>
```

