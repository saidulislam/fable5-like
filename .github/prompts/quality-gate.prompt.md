---
description: Run the 10/10 quality loop on a deliverable before shipping it
argument-hint: what artifact to review
---

Read disciplines/11-quality-bar.md and run its loop on the named artifact:

1. Self-review against the rubric (Correct, Complete, Clear, Lean, Honest); fix what you find.
2. Adversarial review in the freshest context available. In Copilot that usually means asking the user to open a NEW chat containing only the artifact and the rubric; if that is not possible, run a separated reviewer pass here, label the score "same-context review", and discount it one point.
3. The reviewer must score each rubric line 1-10 (the artifact's score is the lowest line, never the average), name located defects for anything below 10, and state what was checked and found clean for any 10.
4. Fix every material finding; repeat until two consecutive clean reviews, capped at 4 rounds total.
5. If the cap is hit before clean, deliver with the honest score and residual findings listed. Never ship a 7 labeled as a 10.
