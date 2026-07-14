# Agent Operating Template: Guide

A portable operating system for coding agents. It packages the working
discipline of a top-tier agent as files any model can load: verification
before claims, systematic debugging, plan-then-execute, grounded claims,
human writing voice, a quality loop, design craft, and operational safety.

An honest note first: files cannot transfer raw model capability. Process
transfers well; it raises the floor a lot and the ceiling a little.
`MODEL-NOTES.md` says what to still watch per model.

This file is deliberately NOT named README.md, so copying the template never
overwrites a project's own README.

## Install

**New project:** copy the folder contents into the project root, skipping
the repo's own README.md and LICENSE (they describe and license the
template repo, not your project; relicense your project as you choose)
and any harness-generated state files (anything in `.claude/` other than
`settings.json` and `skills/`, such as `scheduled_tasks.lock`). Claude Code
works immediately: CLAUDE.md imports AGENTS.md and the memory index at
session start, and the skills and hook live under `.claude/`.

**Existing project: merge, do not overwrite.**

1. Existing CLAUDE.md: keep it, add two lines at the top
   (`@AGENTS.md` and `@memory/MEMORY.md`), and copy over the
   "Claude Code specifics" section from this template's CLAUDE.md.
2. Existing AGENTS.md: merge this template's AGENTS.md into it, resolving
   duplicates once (keep the stricter rule where they differ).
3. Existing `.claude/settings.json`: merge the keys (`effortLevel`,
   `alwaysThinkingEnabled`, `hooks`) instead of replacing the file.
4. `disciplines/`, `checklists/`, `templates/`, `.claude/skills/` copy
   as-is; they do not collide with normal projects.
5. Existing `.github/` content: merge, never replace. If the project
   already has `.github/copilot-instructions.md`, append this template's
   version (or keep the stricter rules); `instructions/` and `prompts/`
   files copy in alongside existing ones unless names collide. An existing
   `.gitignore` gets this template's entries appended, not overwritten.
6. `memory/` starts empty on purpose. Never copy a filled memory directory
   between unrelated projects. In shared repos, gitignore the memory
   contents but keep the index tracked, since CLAUDE.md imports it and the
   import needs the file to exist on fresh clones:
   add `memory/*`, `!memory/MEMORY.md`, `plans/`, and `notes/` to
   `.gitignore`. Memories can contain personal or project-private facts.

**GitHub Copilot (VS Code, coding agent, code review, CLI):** the `.github/`
folder carries the Copilot wiring, and the root AGENTS.md is read natively
by the coding agent and CLI (in VS Code, enable the `chat.useAgentsMdFile`
setting; VS Code also reads CLAUDE.md). Three layers:
`.github/copilot-instructions.md` auto-loads the condensed rules on every
Copilot surface; `.github/instructions/*.instructions.md` apply the writing
and design rules by file type; `.github/prompts/*.prompt.md` expose the
gates as slash commands in VS Code chat (/debug, /plan, /verify-done,
/grounded, /slop-check, /quality-gate, /design-craft). Note there is no
hook equivalent, so the commit gate is instruction-only on Copilot. Read
the Copilot section of `MODEL-NOTES.md`.

**Other non-Claude harnesses (MiniMax and similar):** if the harness
auto-loads AGENTS.md, you are done. If it loads nothing, paste the block
from `SYSTEM-PROMPT.md` into the system prompt and keep the repo files as
reference. Then read the MiniMax section of `MODEL-NOTES.md`.

## Cost note

The defaults favor quality over cost: reasoning effort preset to xhigh, and
quality-loop reviews on deliverables. Expect the loop to multiply token
spend by roughly the number of review rounds it runs (unmeasured; depends on
artifact size). If cost matters more, lower `effortLevel` in
`.claude/settings.json` and reserve the discipline 11 loop for work the user
will rely on.

## What's here

| Path | What it is |
|---|---|
| `AGENTS.md` | The canonical operating manual: ten laws, grounding, quality bar, safety, workflow, discipline index. The hub; the disciplines and checklists it references ship alongside it. |
| `CLAUDE.md` | Thin Claude Code entry: imports AGENTS.md and the memory index, lists Claude-specific extras. |
| `SYSTEM-PROMPT.md` | Paste-ready block for harnesses that auto-load nothing. |
| `disciplines/01..13` | The deep version of each rule: communication, execution, verification, debugging, planning, code quality, delegation, memory, grounding, writing voice, quality bar, design craft, operational safety. |
| `checklists/` | Hard gates: before starting, before claiming done, before committing, fact-check before delivering. |
| `templates/` | Formats for plans (`plans/<task>.md`), investigation notes (`notes/<topic>.md`), and memory entries. |
| `memory/MEMORY.md` | Cross-session memory index, auto-imported in Claude Code. Starts empty. |
| `.claude/skills/` | Seven auto-triggering gate reminders (Claude Code only). |
| `.claude/settings.json` | Effort preset, extended thinking on by default, and the commit/push checklist hook. |
| `MODEL-NOTES.md` | Per-model enforcement levels, reasoning-depth controls, failure modes to watch. |
| `.github/copilot-instructions.md` | Condensed rules, auto-loaded by every GitHub Copilot surface. |
| `.github/instructions/` | Path-scoped Copilot rules: writing voice for Markdown, design craft for UI files. |
| `.github/prompts/` | The seven gates as VS Code Copilot slash commands. |

## Honest caveats

- Skills are description-matched and invoked by the model: usually reliable,
  not guaranteed. The disciplines are the source of truth; skills are the
  reminder layer on top.
- Only the project's own test suite runs without the model's cooperation.
  The commit/push hook injects a reminder but does not block, and the slop
  grep must be run by the model. Everything here is ultimately
  instruction-backed, which weaker models can drift from; `MODEL-NOTES.md`
  tells you where to spend your own review attention.
- In our use, the most damaging single failure mode is the unverified
  success claim. If a model follows only one file, make it
  `checklists/before-claiming-done.md`.
