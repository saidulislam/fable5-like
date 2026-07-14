# Discipline 06: Code Quality

## Blend in

Write code that reads like the surrounding code wrote it. Before editing a file,
absorb its conventions: naming style, error-handling idiom, comment density,
import ordering, test structure. The codebase's existing pattern beats your
preferred pattern. If the codebase does something one way in ten places, do it
that way in the eleventh, even if you know a "better" way.

## Minimal diffs

Change what the task requires and nothing else. No drive-by refactors, no
reformatting untouched lines, no renaming things you happened to pass, no
upgrading dependencies "while you're in there". Every extra changed line is
review burden and regression surface. If you notice something genuinely worth
fixing outside scope, mention it in your report instead of changing it.

## Comments

A comment exists to state a constraint the code cannot express: a non-obvious
invariant, a workaround with its reason, a warning about ordering. Never write
comments that narrate what the next line does, say where code came from, or
justify your change to a reviewer; that's PR-conversation, not code, and it's
noise the day it merges.

```
# BAD:  increment the counter
# BAD:  changed from v1 logic to fix the bug
# GOOD: order matters: the audit hook reads the session, so flush after it runs
```

## Simplicity

- Prefer the boring solution. Cleverness is a cost you're charging every future
  reader.
- Don't add abstraction for one caller. Extract when the second or third real
  use appears.
- Don't add configuration, flags, or generality nobody asked for.
- Delete code instead of commenting it out; version control remembers.

## Robustness where it counts

- Handle the failure modes that can actually occur at this boundary (user
  input, network, filesystem), not imaginary ones deep in trusted internals.
- Errors should carry enough context to debug from the message alone.
- Never swallow exceptions to make a symptom disappear.

## Tests

- New behavior gets a test when the project has a test culture; match the
  existing test style and placement.
- Test the behavior, not the implementation; a good test survives a refactor.
- A regression test for a bug should FAIL without the fix. Check that it does.
