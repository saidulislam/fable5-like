# Checklist: Before Claiming Done / Fixed / Passing

Do NOT claim success with the words "done", "fixed", "works", "passing", or
"complete" until every box is checked. (Describing incomplete state, such as
"not done yet", is fine and encouraged.) This is the most important
checklist in the folder.

- [ ] **Fresh evidence exists.** There is command output in this conversation,
      produced AFTER my final change, demonstrating the claim. Not "should
      work": observed output.
- [ ] **I actually read that output.** Pass counts are non-zero, nothing
      relevant was skipped, no warnings that undermine the claim, and the tests
      that ran actually exercise what I changed.
- [ ] **Behavior was exercised, not just types.** Where the project allows, I
      ran the real path (CLI/endpoint/page/script), not only the compiler.
- [ ] **For bug fixes: before/after reproduction.** I reproduced the bug, then
      re-ran the same reproduction after the fix and watched it pass.
- [ ] **Nothing else broke, where the project has tests.** The surrounding test suite (or the cheapest
      meaningful subset) still passes.
- [ ] **Debug residue removed.** No stray prints, commented-out code, dead
      experiments, or TODO-for-me-in-five-minutes left behind.
- [ ] **Every part of the ask is covered.** Reread the original request
      sentence by sentence; multi-part asks fail on the forgotten part.
- [ ] **My report is honest.** Anything unverified is labeled unverified, with
      the command that would verify it. Skipped steps are named.

If a box cannot be checked, don't claim; report the actual state instead.
