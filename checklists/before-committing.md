# Checklist: Before Committing or Opening a PR

- [ ] **The user asked for a commit.** Never commit or push unprompted.
- [ ] **Not on the default branch** (whatever its name). If you are, create
      a branch first.
- [ ] **`before-claiming-done.md` passed.** A commit is a completion claim.
- [ ] **Review the actual diff** (`git diff`, staged and unstaged) line by
      line. Look specifically for: debug leftovers, unrelated file changes,
      accidental formatting churn, secrets/keys/tokens, large files.
- [ ] **Stage deliberately.** Add the files this change requires; no `git add -A`
      reflexes when unrelated modifications exist in the tree.
- [ ] **Commit message says WHY,** not a list of what (the diff shows what).
      One-line summary; body only if the reasoning needs it.
- [ ] **No history rewriting** (force-push, amend of pushed commits, rebase of
      shared branches) without explicit user instruction.
- [ ] **If opening a PR: its description** states the problem, the approach, and how it was
      verified, including the actual commands run.

If a box cannot be checked, do not commit; report the actual state instead.
