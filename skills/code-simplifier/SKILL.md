---
name: code-simplifier
description: Simplify recently changed code for clarity, consistency, and maintainability without changing behavior. Use when the user wants a cleanup, refactor, polish pass, or readability improvement on code that already works and should keep the same functionality.
---

# Code Simplifier

Refine code to make it easier to read, reason about, and maintain while preserving behavior.

## Operating Rules

1. **Preserve functionality**
   - Do not intentionally change user-visible behavior, outputs, interfaces, or side effects.
   - Treat behavioral safety as a requirement, not a hope.
   - Before finishing, verify preservation with the strongest available signal:
     - Run existing targeted tests when they exist.
     - Add a focused regression test first when the simplification touches non-trivial logic and no adequate test covers it.
     - If no automated check is available, explicitly compare before/after behavior and call out the remaining risk.

2. **Follow project standards**
   - Read the repository's documented standards before simplifying code.
   - Use `CLAUDE.md`, `AGENTS.md`, `README.md`, lint config, formatter config, and nearby examples as possible sources.
   - If no explicit standard exists, follow the dominant local style in the surrounding code instead of inventing a new one.

3. **Enhance clarity**
   - Reduce unnecessary complexity and nesting.
   - Eliminate redundant code and unnecessary abstractions.
   - Improve readability through clear variable and function names.
   - Consolidate related logic when it improves comprehension.
   - Remove comments that only restate obvious code.
   - Avoid nested ternary operators when a clearer `if/else` chain or `switch` is better.
   - Choose clarity over brevity. Explicit code is often better than dense one-liners.

4. **Maintain balance**
   - Do not oversimplify in ways that reduce clarity or maintainability.
   - Do not introduce cleverness that is harder to debug or extend.
   - Do not collapse too many concerns into a single function or component.
   - Do not remove abstractions that are still earning their keep.
   - Do not optimize for fewer lines at the expense of readability.

5. **Control scope**
   - Default to code that was recently modified, unless the user explicitly broadens the request.
   - Determine scope in this order:
     - User-specified files, symbols, or directories.
     - Staged or unstaged changes in git.
     - The current branch diff against its base when that is the clearest definition of "recently modified."
     - Files touched in the current session, if available from local context.
   - If none of these produce a clear scope, state the ambiguity and choose the smallest reasonable scope instead of roaming through the codebase.

## Workflow

1. Identify the target scope using the scope rules above.
2. Read nearby code and repo standards so the simplification matches local patterns.
3. Look for opportunities to reduce complexity, duplication, and incidental noise.
4. Make the smallest changes that materially improve readability and maintainability.
5. Verify that behavior remains unchanged using tests or the strongest available check.
6. Document only the meaningful changes or residual risks that affect understanding.
