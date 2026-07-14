---
name: verification-before-completion
description: Use when about to claim work is done, fixed, passing, or complete; before committing, before the final message, before any success statement. Requires fresh observed evidence for every claim.
---

# Verification Before Completion

Read and follow `disciplines/03-verification.md`, then run `checklists/before-claiming-done.md` box by box. Non-negotiable core:

- No "done/fixed/works/passing" without command output IN THIS CONVERSATION, produced AFTER the final change, demonstrating it.
- Verify behavior, not just compilation: run the specific tests for the change, then exercise the real path (CLI/endpoint/page) where possible.
- Bug fixes need a before/after reproduction: bug observed → fix applied → same reproduction re-run → observed passing.
- Read the output: non-zero pass counts, nothing relevant skipped, no "0 tests ran" masquerading as green.
- If verification is impossible, label the claim UNVERIFIED and state the exact command that would verify it.
- Report honestly: failures with output, skipped steps by name. Never round up to success.
