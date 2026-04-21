# Code Skills

Reusable coding skills for AI agents.

## Available Skills

- `code-brainstorming`: Turn coding ideas into approved designs and planning-ready implementation briefs before coding starts.
- `code-debugging`: Investigate bugs, failing tests, broken builds, and unexpected behavior before proposing fixes.
- `code-explain-visually`: Explain code with diagrams, analogies, and step-by-step walkthroughs when a visual mental model helps.
- `code-reviewing`: Review code for correctness, regressions, testing gaps, and merge readiness.
- `code-simplifier`: Simplify recently changed code for clarity, consistency, and maintainability without changing behavior.
- `git-commit`: Write clear, imperative commit messages using the repository's commit style.
- `git-worktrees`: Create isolated git worktrees when feature work needs a separate workspace.

## Install With the `skills` or `gh` CLI

Install from the GitHub repo:

```bash
npx skills add RileyCornelius/Code-Skills
```

```bash
gh skills install RileyCornelius/Code-Skills
```

## Manual Install

### Global Install

```bash
git clone https://github.com/RileyCornelius/Code-Skills.git
cp -r Code-Skills/skills/* ~/.agents/skills/
```

Claude Code uses the same pattern with `~/.claude/skills` instead of `~/.agents/skills`.

### Project Install

```bash
git clone https://github.com/RileyCornelius/Code-Skills.git
mkdir -p .agents/skills
cp -r Code-Skills/skills/* .agents/skills/
```
