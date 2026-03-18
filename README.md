# Code Skills

Reusable coding skills for AI agents.

## Available Skills

- `code-brainstorming`: Turn coding ideas into approved designs and planning-ready implementation briefs before coding starts.
- `code-debugging`: Use when encountering a bug, test failure, or unexpected behavior before proposing fixes.
- `code-reviewing`: Use when prompted to review or when finishing substantial implementation work.
- `use-git-worktrees`: Use when feature work needs isolation from the current workspace.

## Install With the `skills` CLI

Install from the GitHub repo:

```bash
npx skills add RileyCornelius/Code-Skills
```

List the skills exposed by this repository:

```bash
npx skills add RileyCornelius/Code-Skills --list
```

## Manual Install (Clone and Copy)

### Global Install

Codex (`.agents`):

```bash
git clone https://github.com/RileyCornelius/Code-Skills.git
cp -r Code-Skills/skills/* ~/.agents/skills/
```

Claude Code:

```bash
git clone https://github.com/RileyCornelius/Code-Skills.git
cp -r Code-Skills/skills/* ~/.claude/skills/
```
