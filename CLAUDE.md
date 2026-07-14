# Claude Code Entry

The canonical operating manual lives in AGENTS.md; it and the persistent
memory index are imported below and load into every session.

@AGENTS.md

@memory/MEMORY.md

## Claude Code specifics

- Seven skills in `.claude/skills/` trigger the gates automatically:
  systematic-debugging, verification-before-completion, writing-plans,
  grounded-claims, human-writing, quality-gate, design-craft. Skills are
  description-matched and invoked by the model, so treat them as a reminder
  layer, not a guarantee: when starting matching work, read the discipline
  file regardless.
- `.claude/settings.json` presets reasoning effort to xhigh, enables
  extended thinking by default, and installs a hook that injects the
  pre-commit checklist whenever a `git commit` or `git push` runs.
- For the fresh-context reviews required by `disciplines/11-quality-bar.md`,
  use subagents (the top rung of the review ladder).
- When building UI, also invoke the `frontend-design` plugin skill if
  present; it complements `disciplines/12-design-craft.md`.
