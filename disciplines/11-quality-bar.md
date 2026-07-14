# Discipline 11: The Quality Bar (10/10 or say why not)

"Make it 10/10" is not an instruction a model can follow; models rate their
own work generously and call a 7 a 10. Quality comes from a loop: an
operational definition of 10/10, an adversarial review that must name
defects, and iteration until reviewers run dry. This discipline defines that
loop.

## What 10/10 means (operationally)

A deliverable is 10/10 when ALL of these hold:

1. **Complete**: every part of the original request is covered; reread the
   ask sentence by sentence and map each requirement to where it's met.
2. **Verified**: behavior demonstrated per `disciplines/03-verification.md`
   (code) or fact-checked per `checklists/fact-check.md` (prose). Not
   "should work"; observed.
3. **Defect-free under attack**: a skeptical fresh-context reviewer,
   explicitly instructed to find problems, finds no material defect.
4. **Nothing to cut**: no padding, no dead code, no section that exists to
   look thorough. Removing any part would lose something real.
5. **Honest**: limitations and untested paths are stated, not hidden. A
   9 with a written known-issues list outranks a fake 10.

The author never declares 10/10. Only a review pass can.

## The loop

1. **Draft** against the relevant disciplines (03/06 for code, 09/10 for
   prose, 05 for plans).
2. **Self-review** with the rubric below. Fix what you find. This pass is
   cheap and catches the embarrassing 20%.
3. **Adversarial review, in the freshest context available.** The ladder,
   in order of preference: (a) a subagent given only the artifact and the
   rubric; (b) a second session or chat that the operator opens with only
   the artifact and the rubric; (c) if the harness allows neither, a
   separated reviewer pass in the same session that re-reads the artifact
   from disk. A rung-(c) score is labeled "same-context review", discounted
   by one point, and the label is shown to the user. The reviewer's
   instruction is fixed:
   > "Score each rubric line 1-10; the artifact's score is the lowest line,
   > never the average. You must list specific, located
   > defects to justify any score below 10, and you must actively hunt for
   > them; your job is to find problems, not to approve. A score without
   > named defects is invalid, and a 10 is invalid without a statement of
   > what you checked and found clean. Do not grade on effort or
   > politeness."
4. **Fix every material finding.** Not "acknowledge": fix. A finding is
   material if it could change what the user does or trusts: wrong
   behavior, a missing requirement, a false or unsourced claim, a broken
   gate. Pure style nits are minor. A finding you disagree with gets
   rebutted with evidence, not silently skipped or waved off as immaterial.
5. **Repeat 3-4** until a review returns no material findings, then run ONE
   more independent review to confirm (a single clean pass can be luck).
   Two consecutive clean reviews = done.
6. **Cap at 4 review rounds total, confirming pass included.** If the first
   clean review lands on the final round, ship with one clean review and say
   so. If it's still not clean at the cap, stop polishing and report
   honestly: current score, the residual findings, and why they resist
   fixing. Endless polish is its own failure mode.

## Rubric (adapt per artifact)

Score each 1-10; the deliverable's score is the LOWEST line, not the average:

| Line | Code | Prose/docs |
|---|---|---|
| Correct | Does what was asked; verified with output | Facts checked; claims sourced |
| Complete | All requirements; edge cases handled or flagged | Answers the full brief |
| Clear | Reads like the codebase; obvious to the next dev | One read is enough; no rereads needed |
| Lean | No dead code, no unneeded abstraction | Nothing to cut; no padding |
| Honest | Limitations stated; tests reflect reality | Uncertainty flagged; no hype |

## Anti-gaming rules

- **Self-scores are invalid.** The drafting context always overrates its
  own work. Use the highest rung of the review ladder the harness allows;
  a rung-(c) same-context score is never presented as an independent review
  and always carries its label and one-point discount.
- **A score needs named defects.** "8/10, pretty good" is not a review.
  Every point below 10 maps to a specific, located problem; a 10 requires a
  statement of what was checked and found clean.
- **Lowest line wins.** No averaging a 5 in correctness against 10s in
  style. A beautiful wrong answer is a wrong answer.
- **No grade inflation across rounds.** Round 2's reviewer does not know or
  care that round 1 said 6; each review starts cold.
- **Shipping a 7 labeled as a 7 is honest work. Shipping a 7 labeled as a
  10 is gaslighting** (Discipline 09) and worse than the defect itself.

## Calibration: where the full loop applies

The full adversarial loop is for DELIVERABLES: features, documents, reports,
plans, anything the user will rely on or pass onward. For trivial mechanical
work (a rename, a one-line fix), the existing gates
(`before-claiming-done.md`) already carry the bar; forcing a review panel on
a typo fix is waste dressed as rigor. When unsure whether something is a
deliverable, treat it as one.
