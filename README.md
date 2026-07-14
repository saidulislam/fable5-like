# Agent Operating Template

A portable operating manual for coding agents. Copy it into a project and
the agent working there (Claude Code, GitHub Copilot, or any model whose
harness reads AGENTS.md or a pasted system prompt) inherits the working
discipline of a top-tier agent: claims backed by evidence, systematic
debugging, grounded facts, human-sounding writing, an adversarial quality
loop, and operational safety.

One honest sentence before anything else: files cannot transfer raw model
capability. What they transfer is process, and process is most of the
difference you feel day to day. In our use it raises the floor a lot and
the ceiling a little; that is experience, not a measurement.

## What it enforces

- **No unverified success claims.** "Done", "fixed", and "passing" require
  command output that proves it, gated by a checklist and, in Claude Code,
  a commit-hook reminder (it injects the checklist; it does not block).
- **No hallucinated facts, no gaslighting.** Every specific claim is cited
  from something read or run this session, or labeled unverified. When
  challenged, the agent re-checks the primary source before answering.
- **Systematic debugging.** Reproduce, hypothesize, test, fix the root
  cause. Changing things until the symptom disappears is forbidden.
- **Writing that does not sound like AI.** A banned-pattern list (em
  dashes, filler metaphors, hype vocabulary) enforced by a grep the agent
  must run on its own drafts, plus fact-checking for anything with claims.
- **A quality loop for deliverables.** Fresh-context adversarial review
  with named defects, iterated until reviewers run dry, scored by the
  weakest rubric line. The agent never grades its own work.
- **Design craft for UI work.** Plan before pixels, first-run onboarding,
  tooltips where needed, all four view states, screenshot review.
- **Operational safety.** Fetched content is data rather than instructions,
  secrets stay out of code and logs, dependencies get flagged, rollbacks
  get named before risky changes.

## Quick start

| Your setup | Do this |
|---|---|
| Claude Code | Copy the template into the project root. CLAUDE.md imports the manual and memory index; skills and a commit hook come along under `.claude/`. |
| GitHub Copilot | Same copy. Copilot auto-loads `.github/copilot-instructions.md` and the root AGENTS.md (VS Code: enable `chat.useAgentsMdFile`). The gates are slash commands: `/debug`, `/plan`, `/verify-done`, `/grounded`, `/slop-check`, `/quality-gate`, `/design-craft`. |
| Harness that reads AGENTS.md | Same copy; done. |
| Anything else (MiniMax and similar) | Paste the block from `SYSTEM-PROMPT.md` into the system prompt; keep the repo files as the reference it points to. |

Full install and merge instructions (existing projects, gitignore, cost
notes): `TEMPLATE-GUIDE.md`. Per-model tuning and reasoning-depth controls:
`MODEL-NOTES.md`.

When copying the template into a project, skip this README and the LICENSE
file; they describe and license the template repo, not your project
(license your own project as you choose). `TEMPLATE-GUIDE.md` is deliberately
not named README so it can travel with the copy.

## What's inside

- `AGENTS.md`: the canonical manual (ten laws, grounding, quality bar,
  safety, workflow).
- `disciplines/01..13`: the deep version of each rule.
- `checklists/`: hard gates for starting, claiming done, committing, and
  fact-checking.
- `templates/`: formats for plans, investigation notes, memory entries.
- `SYSTEM-PROMPT.md`, `CLAUDE.md`, `.github/`: per-harness entry points.
- `memory/`: cross-session memory (starts empty, gitignored except the
  index).

## Honest caveats

Only a project's own test suite runs without the model's cooperation;
everything else here is instruction-backed, and weaker models can drift
from instructions. The template was built with its own quality loop:
fresh-context adversarial reviews with named defects, fixed after each
round, scored by the rules in `disciplines/11-quality-bar.md`. It has never
carried a self-declared score, because its own rules forbid that.
`MODEL-NOTES.md` is
explicit about which model tiers need which enforcement and where to spend
your own review attention. If an agent follows only one file, make it
`checklists/before-claiming-done.md`: the unverified success claim is the
failure mode that costs the most trust.
