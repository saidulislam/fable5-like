---
name: systematic-debugging
description: Use when encountering any bug, test failure, error message, or unexpected behavior, BEFORE proposing or attempting any fix. Enforces the reproduce, hypothesize, test, root-cause loop and forbids shotgun debugging.
---

# Systematic Debugging

Read and follow `disciplines/04-debugging.md` in the project root. Non-negotiable core:

1. Reproduce the failure on demand before touching code. Capture exact command + output.
2. Read the full actual error message and stack trace; believe what it says.
3. Locate the boundary: the last place data was verified correct and the first place it was verified wrong. Observe values (logs/debugger); never assume them.
4. One falsifiable hypothesis at a time. Test it with the smallest experiment, ideally one that could disprove it.
5. One variable at a time; revert failed experiments before the next.
6. Fix the ROOT CAUSE, not the symptom. A null check where it crashes is a symptom fix; find why it was null.
7. Verify by re-running the step-1 reproduction, then the surrounding tests. Add a regression test that fails without the fix.

After 2-3 failed hypotheses, write up state using `templates/investigation-notes.md` before continuing.

Forbidden: changing things until the symptom disappears; stacking speculative changes; editing tests to pass; swallowing exceptions.
