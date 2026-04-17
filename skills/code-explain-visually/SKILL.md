---
name: code-explain-visually
description: Explain code with diagrams, analogies, and step-by-step walkthroughs. Use when the user wants help understanding a function, file, module, request flow, architecture slice, or unfamiliar codebase area, especially when a visual explanation would make the behavior easier to follow.
---

# Code Visual Explain

Turn confusing code into a clear mental model.

Use this skill when the user asks for an explanation, walkthrough, diagram, flow, architecture overview, or "how this code works."

## Workflow

### 1. Read the actual code first

- Inspect the relevant files, types, tests, or diffs before explaining.
- Anchor the explanation in real symbols, control flow, and file references.
- Separate what is directly confirmed by code from what is inferred.

### 2. Choose the right visual

Pick the diagram style that matches the question:

- `flowchart` for control flow, request paths, or decision branches
- `sequenceDiagram` for interactions between services, classes, APIs, or async steps
- `classDiagram` or a simple relationship map for structure and ownership
- `stateDiagram` for lifecycles, modes, and transitions
- Prefer mermaid but use ASCII when the concept is tiny
- Use color to indicate different consepts

### 3. Explain in layers

Default structure:

1. A one or two sentence plain-English summary
2. A concrete analogy that maps to the real code
3. A diagram that shows the important moving parts
4. A step-by-step walkthrough of what happens
5. A short "gotchas" section covering edge cases, misconceptions, or easy-to-miss behavior

For larger systems, start with the overview and then zoom into the most important path.

## Rules

- Do not invent behavior that is not visible in the code.
- Do not use an analogy without mapping it back to the actual code elements.
- Keep diagrams compact and readable. Avoid decorative nodes or irrelevant branches.
- If the code is ambiguous, say what is uncertain instead of pretending it is settled.
- Match the depth to the user's goal: onboarding overview, bug-hunt walkthrough, or deep implementation explanation.
