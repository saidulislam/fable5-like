---
name: design-craft
description: Use before designing or building ANY user interface (app screens, web pages, dashboards, landing pages, interactive CLI output, slide decks) and before delivering UI work. Enforces plan-before-pixels, the anti-default critique, first-run onboarding, tooltips, all four states, and the screenshot-based design review.
---

# Design Craft

Read and follow `disciplines/12-design-craft.md`. Non-negotiable core:

- Plan before pixels: pin the subject (user + the page's single job), then a token plan (4-6 hex palette, deliberate type pairing, layout wireframe, ONE signature element that carries all the boldness). Build derives every decision from the plan.
- Anti-default critique before building: if the plan matches the generic AI looks (cream + serif + terracotta; near-black + acid accent; broadsheet hairlines) and the brief didn't ask for it, revise.
- UX requirements: designed primary flow with an obvious next action at every step; skippable first-run orientation (tour, guided flow, or annotated empty state); tooltips on every icon-only or non-obvious control (and nowhere else); empty/loading/error/success states for every view; feedback within ~100ms for every action; destructive actions guarded.
- Quality floor, always, unannounced: responsive to mobile, visible keyboard focus, WCAG AA contrast, reduced-motion respected.
- Microcopy: user's vocabulary not the system's, buttons say what happens, errors say what went wrong and how to fix it, empty states invite action.
- Screenshot critique after building: render it, look at it, remove one accessory.
- Deliverable UIs go through the Discipline 11 adversarial review with the design rubric (first-use walkthrough, distinctiveness, states, craft, floor). Lowest line is the score.
- In Claude Code, also invoke the `frontend-design` plugin skill when building UI, if it is present in the environment.
