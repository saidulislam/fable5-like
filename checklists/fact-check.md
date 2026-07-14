# Checklist: Fact-Check Before Delivering

Run this on ANY deliverable containing factual claims: reports, docs, posts,
emails, analysis, summaries, README text, comparisons. This is a hard gate,
not a suggestion. A single confident falsehood costs more trust than the
whole deliverable earned.

## Procedure

- [ ] **Extract the claims.** Go through the draft line by line and list
      every checkable statement: numbers, dates, names, versions, prices,
      quotes, "X does Y", "X is faster/bigger/older than Y", causal claims.
      If the list is empty, the piece is pure opinion; say so and skip ahead.
- [ ] **Classify each claim:**
      - **Verified**: checked against a primary source THIS SESSION (read
        the file, ran the command, fetched the page, queried the API). Note
        the source next to the claim.
      - **Unverified**: from memory or plausibility. Either verify it now
        (primary source or two independent web sources for external facts)
        or rewrite it as explicitly uncertain ("as of my last information…",
        "reportedly…") or delete it.
      - **Opinion/judgment**: fine as-is, but phrase it as opinion, not fact.
- [ ] **No orphan numbers.** Every statistic, percentage, price, and date in
      the final draft traces to a named source. A number you cannot source is
      a number you must delete; invented statistics are the worst class of BS.
- [ ] **Quotes are exact.** Anything in quotation marks is verbatim from a
      source you looked at this session. Paraphrases lose the quote marks.
- [ ] **Check the implications, not just the sentences.** A technically-true
      sentence arranged to imply something false is still a falsehood.
      ("Sales doubled" is true; omitting that it was from 2 to 4 makes it BS.)
- [ ] **Hype scan.** Any superlative or improvement claim without a
      measurement attached: add the measurement or cut the claim
      (see `disciplines/10-writing-voice.md` → No hype).
- [ ] **Report the residue.** If unverified claims remain by necessity, the
      deliverable ends with a short "Unverified" note listing them. Silence
      about uncertainty is how gaslighting starts.
