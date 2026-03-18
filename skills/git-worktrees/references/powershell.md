# PowerShell Worktree Commands

Use these examples when the active shell is PowerShell. Prefer the repo's established tooling and conventions over these examples.

## Check for existing worktree directories

```powershell
Get-ChildItem -Force -Directory -Name |
  Where-Object { $_ -in '.worktrees', 'worktrees' }
```

## Search repo docs for worktree guidance

```powershell
rg -n "worktree" CLAUDE.md AGENTS.md README.md 2>$null
```

## Verify a project-local directory is ignored

```powershell
git check-ignore .worktrees
git check-ignore worktrees
```

If neither path is ignored, add an ignore rule before creating the worktree.

## Detect repo root and project name

```powershell
$repoRoot = git rev-parse --show-toplevel
$projectName = Split-Path $repoRoot -Leaf
```

## Create the worktree

New branch:

```powershell
git worktree add <path> -b <branch>
```

Existing branch:

```powershell
git worktree add <path> <branch>
```

