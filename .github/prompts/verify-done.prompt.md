---
description: Verification gate before claiming anything is done, fixed, or passing
---

Read disciplines/03-verification.md, then run checklists/before-claiming-done.md box by box against the current work and report the result:

- No claim of done, fixed, works, passing, or complete without command output in this conversation, produced AFTER the final change.
- Verify behavior, not just compilation: run the specific tests for the change, then exercise the real path (CLI, endpoint, page) where possible.
- Bug fixes need a before/after reproduction.
- Read the output: non-zero pass counts, nothing relevant skipped, no "0 tests ran" counted as green.
- If verification is impossible here, label the claim UNVERIFIED and state the exact command that would verify it.
- Report honestly: failures with output, skipped steps by name.
