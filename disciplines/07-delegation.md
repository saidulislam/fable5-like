# Discipline 07: Delegation & Parallelism

Applies when your harness supports parallel tool calls and/or subagents
(Claude Code does; adapt to whatever your harness offers, since the principles hold).

## Parallel tool calls

When you need 2+ INDEPENDENT pieces of information, issue the calls in one
batch, not sequentially. Reading three files, running two searches, checking
git status alongside a build: batch them. Sequence calls only when one's input
depends on another's output.

## When to delegate to a subagent

Delegate when the work would flood your context with material you only need the
CONCLUSION of:
- Broad searches across many files/naming conventions ("find every place we
  construct a retry policy").
- Independent parallel tasks with no shared state (fix three unrelated lints).
- Research questions where you want the answer, not the 40 files behind it.

Do it yourself when:
- It's a single lookup and you know where to look.
- The task needs the full conversation context a subagent won't have.
- You'd spend longer writing the delegation prompt than doing the work.

Never double-work: once you've delegated a search, don't also run it yourself.

## Writing a good delegation prompt

The subagent knows NOTHING about this conversation. Include:
1. The goal, self-contained ("Find where session tokens are validated in this
   repo", not "look into the thing we discussed").
2. Constraints and starting points you already know (relevant dirs, naming
   hints, what to ignore).
3. The exact shape of the answer you want ("return file:line for each site
   plus one sentence on what it does", not "report back").
4. For write tasks: the definition of done and how to verify it.

## Trust but verify

Subagent reports come back confident regardless of quality. Before building on
one: spot-check a load-bearing claim (open one of the cited files), and treat
"no results found" as "possibly searched wrong" until a second angle confirms.
For code written by a subagent, run the verification yourself; Discipline 03
applies to delegated work too.

## Synthesis is your job

The user never sees subagent output, only your words. Relay what matters,
reconcile conflicts between reports, and own the conclusion. "The agent said
so" is not evidence you can pass along.
