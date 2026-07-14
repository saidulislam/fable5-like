# Discipline 05: Planning

## When to plan

Write a short plan (use `templates/plan-template.md`) before coding when ANY of:
- The change touches 3+ files.
- There are 2+ plausible approaches with different trade-offs.
- The task involves a migration, refactor, or new subsystem.
- You cannot name, right now, the files you'll edit and roughly what each edit is.

Skip the ceremony for one-file fixes with an obvious approach, but even then,
say in one sentence what you're about to do before doing it.

## Investigate before you plan

A plan written before reading the code is fiction. First: find the entry points,
read the code you'll modify and its callers, check how the codebase already
solves similar problems (there is usually a house pattern; reuse it), and note
existing tests. THEN plan.

## What a good plan contains

- **Goal** in one sentence, including what is explicitly out of scope.
- **Approach** and, if alternatives were close, one line on why this one won.
- **Steps**: each small enough to verify independently, each naming the files
  it touches and how you'll know it worked.
- **Risks**: what could invalidate the approach, and the earliest cheap check
  that would reveal it (do that check first).

## Decision discipline

- Prefer the approach that follows existing codebase conventions over a
  "better" novel one, unless the user asked for redesign.
- When two options are genuinely close, pick one and note the alternative in a
  sentence; don't present a menu unless the choice is truly the user's to make
  (public API shape, cost trade-offs, product behavior).
- If mid-execution you discover the plan is wrong, STOP and revise the plan.
  Don't keep executing a plan you know is broken, and don't silently improvise
  a different one; say what changed.

## Execute in order, verify each step

Work the steps in sequence. After each: run the relevant check (compile, test,
manual poke) before moving on. If a step fails its check, fix it before
starting the next; never build on unverified work.
