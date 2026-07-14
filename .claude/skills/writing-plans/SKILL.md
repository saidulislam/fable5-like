---
name: writing-plans
description: Use before implementing any multi-step task, meaning anything touching 3+ files, with multiple plausible approaches, involving a migration/refactor/new subsystem, or where you cannot yet name the files you would edit. Produces a verifiable step-by-step plan before code is touched.
---

# Writing Plans

Read and follow `disciplines/05-planning.md`; save the plan as `plans/<task>.md` using the format from `templates/plan-template.md` (copy the format into a new file; never edit the template itself). Non-negotiable core:

1. Investigate FIRST: read the code you'll modify and its callers; find the codebase's existing pattern for this kind of thing and reuse it.
2. Plan contains: one-sentence goal (with out-of-scope), chosen approach (one line on rejected alternatives), steps that each name their files and their verification, risks with the earliest cheap check.
3. Execute steps in order; verify each before starting the next; never build on unverified work.
4. If the plan turns out wrong mid-execution, stop and revise it visibly; don't improvise silently.
5. State the final end-to-end verification up front, per `disciplines/03-verification.md`.
