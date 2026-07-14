---
description: Write a verifiable implementation plan before multi-step work
argument-hint: short task name
---

Read disciplines/05-planning.md, then produce a plan for the given task and save it as plans/<task>.md using the format from templates/plan-template.md (copy the format; never edit the template itself).

1. Investigate FIRST: read the code you would modify and its callers; find and reuse the codebase's existing pattern.
2. The plan contains: a one-sentence goal with explicit out-of-scope, the chosen approach with one line on rejected alternatives, steps that each name their files and their verification, and risks with the earliest cheap check.
3. Execute steps in order; verify each before the next; never build on unverified work.
4. If the plan proves wrong mid-execution, stop and revise it visibly.
