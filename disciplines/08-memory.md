# Discipline 08: Memory & Context Hygiene

## Persistent memory (across sessions)

The `memory/` directory persists what conversations don't. Convention:

- `memory/MEMORY.md` is the index; one line per memory, format:
  `- [Title](filename.md): one-line hook`. Skim it at session start.
- Each memory is ONE file holding ONE fact, written from
  `templates/memory-entry-template.md`. Types:
  - `user`: who the user is (role, expertise, preferences).
  - `feedback`: corrections and confirmed approaches, WITH the why and how to
    apply them next time.
  - `project`: goals, constraints, decisions not derivable from the code or
    git history. Convert relative dates ("next week") to absolute ones.
  - `reference`: pointers to external resources such as URLs, dashboards, tickets.

Rules:
- Before saving, check whether an existing memory covers it; update that file
  instead of duplicating. Delete memories that turn out to be wrong.
- Don't save what the repo already records (code structure, git history, this
  manual) or what matters only to the current conversation.
- Memories reflect when they were written; verify a remembered file/flag still
  exists before recommending it.

## What deserves a memory

A user correction ("stop adding docstrings to tests"), a hard-won environment
fact (the staging DB needs the VPN), a standing decision ("we chose pnpm; don't
suggest npm"), a preference ("terse answers; I'm a senior engineer"). The test:
would the next session's agent work worse without this fact?

## In-conversation context hygiene

- Read only the file sections you need; use targeted reads on large files.
- In Claude Code, skip re-reading a file you just edited (the edit tool
  errors on failure). On harnesses without that guarantee, one re-read after
  editing is correct.
- Don't re-derive facts already established this conversation, and don't
  re-open decisions the user already made.
- If the harness summarizes long context, trust the summary and continue;
  don't wrap up early or restart investigations because the session feels long.
- Keep a running notes file at `notes/<topic>.md` (using the format from
  `templates/investigation-notes.md`, copied, never edited in place) on long
  investigations, so a context reset costs minutes, not the day.
