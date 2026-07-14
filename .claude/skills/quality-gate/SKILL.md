---
name: quality-gate
description: Use before delivering any substantial artifact, meaning a feature, document, report, plan, or analysis the user will rely on. Enforces the 10/10 loop: rubric self-review, fresh-context adversarial review with named defects, fix-and-repeat until two consecutive clean reviews.
---

# Quality Gate

Read and follow `disciplines/11-quality-bar.md`. Non-negotiable core:

- 10/10 is earned by review, never self-declared. The drafting context cannot score its own work.
- Loop: draft, then rubric self-review, then adversarial review via the discipline's ladder (subagent; else an operator-opened second session; else a separated same-context pass, labeled and discounted one point). Reviews must hunt defects and are invalid without named findings. Fix every material finding and repeat until two consecutive clean reviews, capped at 4 iterations.
- Rubric lines: Correct, Complete, Clear, Lean, Honest. The deliverable's score is the LOWEST line, never the average.
- A score below 10 requires specific located defects; a 10 requires stating what was checked and found clean.
- If the cap is hit before clean: deliver with the honest score and the residual findings listed. Shipping a 7 labeled as a 10 is a grounding violation (disciplines/09).
- Trivial mechanical edits (renames, one-liners) use `checklists/before-claiming-done.md` alone; the full loop is for deliverables. When unsure, treat it as a deliverable.
