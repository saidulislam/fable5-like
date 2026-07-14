# Model Notes: Per-Model Tuning

Audience note: this file is written for the OPERATOR (the human running the
models). An agent told to "apply your section" should treat the operator
guidance as context and adopt the Watch-for items as its own failure modes
to guard against.

The manual is identical for every model; what varies is enforcement
tightness. Two things drive it: raw capability (as of this writing, Opus
above Sonnet, MiniMax, and typical Copilot picks) and harness integration (Claude Code auto-loads the manual,
triggers skills, and runs hooks; other harnesses may load AGENTS.md or
nothing at all). Tighten the leash as either drops. Unknown model or
harness: apply the strictest tier.

## Opus (Claude Code)

Strongest tier in the current lineup, with full harness support; the manual
works nearly as-is.

- Checklists can be applied with judgment; the non-negotiables remain law 1
  (evidence before assertions) and the debugging loop.
- Trust it with longer autonomous stretches and larger plan steps.
- Watch for: over-engineering (abstractions and config nobody asked for,
  see discipline 06) and over-long reports (discipline 01: selective, not
  compressed).

## Sonnet (Claude Code)

Very capable executor with full harness support; benefits most from
explicit gates.

- Checklists are mandatory and literal: have it check boxes with evidence,
  not vibes.
- Keep plan steps small (one file or one behavior per step) and require the
  per-step verification to actually run before the next step.
- Watch for: premature "this should fix it" claims (enforce discipline 03
  hard), agreeing with incorrect user assumptions instead of checking the
  code, and stopping at analysis when a fix was requested (law 10).
- Prefer one task per session over broad multi-part missions.

## MiniMax, or any non-Claude harness

Treat capability as Sonnet-tier until your own experience says otherwise
(an assumption, not a measurement); the documented gap is plumbing. No auto-loaded
manual, no skills, no hooks, and often no subagents, so every trigger must
be supplied by the operator.

- Entry: AGENTS.md if the harness auto-loads it; otherwise paste the block
  from SYSTEM-PROMPT.md into the system prompt. It contains the laws,
  grounding rules, and the read-this-before-that triggers that skills
  provide on Claude Code.
- Fresh review without subagents: use the ladder in
  `disciplines/11-quality-bar.md` (operator opens a second session with only
  the artifact and rubric; failing that, a separated pass labeled
  "same-context review" and discounted one point).
- Shortest leash: one small task at a time, require the plan before
  approving execution, and re-run its verification commands yourself when
  stakes matter.
- Watch for: confident fabrication of file contents and API signatures
  (require it to quote the actual lines it read) and silent scope drift. If
  fabrication recurs, paste `disciplines/09-grounding.md` into the system
  prompt as well.

## GitHub Copilot (VS Code, coding agent, code review, CLI)

Capability depends on the model picked in Copilot's model selector (GPT and
Claude tiers vary); treat it as Sonnet-tier enforcement unless you have
picked a top-tier model. The plumbing (verified against the GitHub and
VS Code docs on 2026-07-14):

- Entry: `.github/copilot-instructions.md` auto-loads everywhere; the root
  AGENTS.md is read natively by the coding agent and CLI, and by VS Code
  with `chat.useAgentsMdFile` enabled. When both exist, both are used.
- Path-scoped triggers: `.github/instructions/*.instructions.md` with
  `applyTo` globs cover the writing and design gates by file type. The
  other gates are slash commands in `.github/prompts/` (/debug, /plan,
  /verify-done, /grounded, /slop-check, /quality-gate, /design-craft);
  invoke them yourself, since nothing fires them automatically.
- No hooks: the commit gate is instruction-only here, so review diffs
  before approving commits.
- No subagents: quality-loop reviews use ladder rung (b), a fresh chat
  opened with only the artifact and rubric.
- No memory auto-import: the instructions tell the model to skim
  memory/MEMORY.md; verify it actually did when it matters.
- No effort dial: pick the strongest model in the selector and apply the
  lever 2 scaffolds below.

## Forcing reasoning depth

Two levers. The first buys real extra compute; the second shapes how the
compute is spent. Use both.

### Lever 1: harness and API settings

> Verification note: the Claude Code facts below were checked against the
> official docs (code.claude.com) on 2026-07-12 via the claude-code-guide.
> They are version-bound; re-verify after major Claude Code updates.

Claude Code (Opus / Sonnet):

- `/effort <level>` in-session, or the slider in `/model`. Levels: low,
  medium, high, xhigh, max (default high on current models). Use xhigh for
  hard coding and agentic work; max when correctness beats cost.
- Persist it: `"effortLevel": "xhigh"` in `.claude/settings.json` (accepts
  low/medium/high/xhigh; max is session-only), the env var
  `CLAUDE_CODE_EFFORT_LEVEL=xhigh`, or launch with `claude --effort xhigh`.
  This template presets xhigh, plus `alwaysThinkingEnabled` (which enables
  extended thinking by default; on current adaptive-thinking models the
  depth control is effort itself).
- One-off boost without changing settings: the keyword `ultrathink`
  anywhere in a prompt requests deeper reasoning for that turn. Per the
  docs, older keywords like "think hard" are passed through as ordinary
  prompt text and are not recognized as triggers.
- Per-skill or per-subagent: `effort: xhigh` in the frontmatter.
- `/effort ultracode` (or `--effort ultracode`): a Claude Code setting
  rather than a model effort level; sends xhigh and orchestrates dynamic
  workflows for substantive tasks. Session-only.

Direct API calls (scripting Opus/Sonnet yourself): set
`thinking: {"type": "adaptive"}` (explicit on Opus, default on current
Sonnet) plus `output_config: {"effort": "xhigh"}`. The old `budget_tokens`
parameter is deprecated (per the docs, still accepted on 4.5/4.6-era models
and scheduled for removal in future releases); do not use it in new code.

MiniMax and other harnesses: use whatever reasoning-effort or
thinking-budget parameter the provider exposes, at its top tier for hard
tasks. If none exists, lever 2 is all you have; apply it aggressively.

### Lever 2: prompt and process scaffolds (any model)

These add no compute, but they force the model to spend its compute like a
deep reasoner instead of pattern-matching to the first plausible answer:

1. **Externalize the reasoning.** Require a written plan or hypothesis table
   before any conclusion (`templates/`). A model that must write
   "hypothesis, test, result" cannot skip to a guess.
2. **Decompose.** Break one hard question into 3 to 5 explicit sub-questions
   and demand an answer to each before the synthesis.
3. **Draft, critique, revise.** Produce an answer, attack it ("list three
   ways this could be wrong, then check each"), then revise.
4. **Fresh-context verification.** A new session or subagent tries to REFUTE
   the first answer. Independent checking is the cheapest reasoning
   multiplier for mid-tier models.
5. **Forbid the shortcut.** "Do not state a conclusion until you have quoted
   the specific lines that support it." Evidence-first ordering forces the
   reasoning to actually happen.

Rule of thumb: Opus usually needs lever 1 alone. Sonnet needs lever 1 plus
scaffolds 1 and 3. For MiniMax assume lever 1 is unavailable and apply all
five scaffolds on anything non-trivial.

## Universal escalation rule

If a model repeatedly violates a discipline in a session, do not argue case
by case. Paste the specific discipline file into the conversation and ask it
to restate the rule in its own words before continuing. Restating works
better than being corrected.

## What does not transfer

Raw reasoning depth does not come from these files. On genuinely hard
problems (subtle concurrency, novel architecture, cross-cutting design),
expect to spend more of YOUR attention reviewing: read the plan before
approving it, spot-check diffs, re-run verifications. The manual makes
models honest and systematic; it does not add intelligence.
