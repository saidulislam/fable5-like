---
description: Systematic debugging loop for any bug, test failure, or unexpected behavior
---

Read disciplines/04-debugging.md and apply its loop to the problem at hand:

1. Reproduce the failure on demand with the smallest input; capture the exact command and output.
2. Read the full actual error message and stack trace; believe what it says.
3. Locate the boundary: last place the data was verified correct, first place verified wrong. Observe values; never assume them.
4. One falsifiable hypothesis at a time, tested with the smallest experiment that could disprove it.
5. One variable at a time; revert failed experiments before the next.
6. Fix the ROOT CAUSE, not the symptom.
7. Verify by re-running the exact reproduction, then the surrounding tests. Add a regression test that fails without the fix.

Forbidden: changing things until the symptom disappears, stacking speculative changes, editing tests into passing, swallowing exceptions. After 2 to 3 failed hypotheses, write the state to notes/<topic>.md using the format from templates/investigation-notes.md (copy the format; never edit the template itself).
