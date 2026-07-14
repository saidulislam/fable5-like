# Discipline 04: Systematic Debugging

Shotgun debugging (changing things until the symptom disappears) is forbidden.
It sometimes "works" while leaving the real defect in place and adding noise.
Every bug gets the hypothesis loop.

## The loop

1. **Reproduce.** Get the failure to happen on demand, with the smallest input
   that triggers it. If you can't reproduce it, you're not debugging; you're
   speculating. Capture the exact command and exact output.

2. **Read the actual error.** The full message, the full stack trace, the line
   it points at. Not a skim: read it. Most bugs are solved by believing what
   the error literally says instead of what you assumed it means.

3. **Locate the boundary.** Where does reality diverge from expectation? Walk
   the data: the input was right HERE (verified), wrong THERE (verified); the
   defect is between. Add temporary prints/logs or use a debugger to verify;
   never assume a value, observe it.

4. **Form ONE hypothesis.** State it precisely enough to be falsifiable: "the
   cache key omits the locale, so the French request returns the English
   payload." If you can't state it in one sentence, you don't have one yet;
   go back to step 3.

5. **Test the hypothesis with the smallest experiment**, ideally one that
   could DISPROVE it (check the cache key contents), not a fix attempt. Wrong?
   That's progress: it eliminated a theory. Form the next one. Never stack a
   second speculative change on top of a first one.

6. **Fix the root cause.** Not the symptom. Adding a null check where it
   crashes treats the symptom; finding why the value was null treats the
   cause. Ask "why" one level deeper than where the error appeared.

7. **Verify the fix**: re-run the exact reproduction from step 1 and watch it
   pass. Then run the surrounding tests to check you broke nothing. If
   feasible, add a regression test that fails without the fix.

## Rules within the loop

- **One variable at a time.** Change one thing, observe, revert if it didn't
  help. Multiple simultaneous changes make the eventual "it works" meaningless.
- **Revert dead ends.** Failed experiments get undone before the next one.
  Debugging residue (stray logs, commented-out code) never ships.
- **Track your hypotheses.** After 2-3 failed ones, write the list down (what
  you thought, what disproved it) using `templates/investigation-notes.md`;
  it prevents circular re-testing of dead theories.
- **Question the harness too.** Sometimes the test is wrong, the fixture is
  stale, the environment differs. "Works on my machine" boundaries (env vars,
  versions, timezone, locale) are hypotheses like any other.
- **Escalate honestly.** If several loop iterations produce nothing, present
  your reproduction, hypothesis history, and the boundary you've narrowed to.
  A precise "here is where it diverges and I don't know why yet" is genuinely
  useful; a speculative patch is not.
