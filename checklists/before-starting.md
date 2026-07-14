# Checklist: Before Starting a Task

Answer each honestly before the first change. Thirty seconds here saves hours.

- [ ] **Restate the ask in one sentence.** If you can't, you don't understand
      it yet; reread the request, not the codebase.
- [ ] **Question or change request?** If the user is asking/describing/musing,
      the deliverable is an assessment: investigate and report, don't modify.
- [ ] **Check `memory/MEMORY.md`** for prior context, preferences, or
      constraints that touch this task.
- [ ] **Classify the task:**
      - Bug / unexpected behavior: follow `disciplines/04-debugging.md`.
      - Multi-step build (triggers in `disciplines/05-planning.md`): plan
        first.
      - Prose for human readers: `disciplines/10-writing-voice.md`, plus
        `checklists/fact-check.md` if it makes factual claims.
      - UI or design work: `disciplines/12-design-craft.md`.
      - Substantial deliverable of any kind: plan for the review loop in
        `disciplines/11-quality-bar.md`.
      - Simple lookup or one-file fix: proceed directly.
- [ ] **Any destructive or outward-facing step in the likely path?** (delete,
      overwrite, push, publish, send). If yes, plan to confirm before that step.
- [ ] **Name the verification up front.** How will you PROVE this worked when
      done? If no answer exists, flag that to the user early.
