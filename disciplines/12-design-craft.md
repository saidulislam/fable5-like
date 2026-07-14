# Discipline 12: Design Craft (UI/UX)

Applies whenever the work produces an interface: apps, web pages, dashboards,
CLIs with interactive output, slides. "Make it beautiful" is not an
instruction a model can follow; this discipline replaces it with a process,
concrete UX requirements, visual craft rules, and a design-specific review
that plugs into the quality loop (Discipline 11).

The bar, stated operationally: a first-time user completes the primary task
without help, and a designer reviewing screenshots finds deliberate choices
rather than defaults. Both are testable; both are tested below.

## Process: plan before pixels

1. **Pin the subject.** One concrete sentence: who the user is, what the
   page's single job is. If the brief doesn't say, decide and state it.
   Distinctive design comes from the subject's own world (its materials,
   vocabulary, artifacts), not from a style grab-bag.
2. **Design plan first.** Before any code: a compact token system.
   - Palette: 4-6 named hex values.
   - Type: a characterful display face used with restraint, a complementary
     body face, a utility face if data/captions need one. Avoid the
     reflexive default stack. (Exception: for internal utility tools,
     convention and speed may beat novelty; say which you chose and why.)
   - Layout: one-sentence concept plus an ASCII wireframe.
   - **Signature:** the single element this design will be remembered by.
     Spend all the boldness there; keep everything around it quiet.
3. **Anti-default critique.** Review the plan against this question: "would
   I have produced this same plan for a different brief?" AI-generated
   design clusters (a mid-2026 observation; recheck as models change)
   around three looks: warm cream background with
   serif display and terracotta accent; near-black with one acid-green or
   vermilion accent; broadsheet layout with hairline rules and zero
   border-radius. These are defaults, not choices. If the plan matches one
   (and the brief didn't ask for it), revise and say what changed.
4. **Build from the plan exactly.** Every color and type decision derives
   from the tokens. No mid-build improvisation of new colors or faces.
5. **Screenshot critique.** Render and LOOK at it (screenshot tooling where
   available). Then apply Chanel's rule: remove one accessory. Cut any
   decoration that does not serve the brief.

## UX requirements (the checklist an interface must pass)

- **The primary flow is designed, not assumed.** Write out the steps a user
  takes to complete the core task, then walk them in the built product.
  Every step needs an obvious next action.
- **First-run experience.** A first-time user gets orientation: a brief
  guided flow, an annotated empty state, or a 2-4 step tour of what to do
  first. Never a blank screen with 30 unexplained controls. Make onboarding
  skippable and never show it twice.
- **Tooltips where needed, not everywhere.** Any control whose purpose is
  not obvious from its label gets a tooltip (or inline hint). Icon-only
  buttons ALWAYS get one. Self-explanatory controls get none; tooltip spam
  is its own failure.
- **Every state exists.** Empty (an invitation to act, with the first step
  offered), loading (skeleton or progress, never a frozen screen), error
  (what went wrong and how to fix it, specific, no apology theater),
  success (confirmation the action took effect).
- **Feedback for every action.** Click, save, delete, submit: each produces
  a visible response within ~100ms, even if just a pressed state.
- **Destructive actions are guarded** (confirm or undo), frequent actions
  are frictionless. Never the reverse.
- **Consistency is navigation.** An action keeps the same name through the
  whole flow: a "Publish" button produces a "Published" toast. One
  vocabulary, everywhere.
- **Quality floor, unannounced:** responsive down to mobile, visible
  keyboard focus, sufficient color contrast (WCAG AA), reduced-motion
  respected, real focus order. These are not features to mention; they are
  the floor.

## Visual craft

- **Typography carries the personality.** Deliberate pairing, a clear scale,
  intentional weights and spacing. Type is a memorable part of the design,
  not a neutral container.
- **Structure encodes meaning.** Numbering, dividers, labels only where the
  content genuinely has sequence or hierarchy. Decoration pretending to be
  structure reads as template.
- **Motion is deliberate and scarce.** One orchestrated moment (a load
  sequence, a scroll reveal, a hover micro-interaction) lands harder than
  scattered effects. Excess animation is an AI tell. Respect reduced-motion.
- **Match complexity to the vision.** Maximalist directions need elaborate
  execution; minimal directions need precision in spacing and detail.
  Elegance is executing the chosen vision well, at either extreme.

## Microcopy (words inside the interface)

Words in a UI exist to make it easier to use. Rules: name things by what the
user controls, never by how the system is built ("Notifications", not
"Webhook config"); buttons say exactly what happens ("Save changes", not
"Submit"); active voice, sentence case, plain verbs; errors state what
happened and how to fix it, without vagueness or apology; empty states
invite the first action. Discipline 10's ban list applies to UI copy too.

## The design review (feeds Discipline 11's loop)

Deliverable interfaces go through the adversarial review with these rubric
lines added (lowest line is the score, as always):

| Line | Test |
|---|---|
| First-use | A fresh-context reviewer walks the primary flow as a first-time user, from screenshots or the running app. Where would they stall? Every stall is a named defect. |
| Distinctiveness | Could this design be mistaken for the generic default? Which choices are specific to THIS brief? "Looks like every AI page" is a defect with a location. |
| States | Reviewer enumerates empty/loading/error/success for each view; each missing state is a defect. |
| Craft | Spacing rhythm, type scale consistency, alignment, contrast, checked from screenshots, not from the code. |
| Floor | Keyboard walk, mobile width, reduced motion. Pass/fail. |

Claude Code users: the `frontend-design` plugin skill complements this
discipline with the same philosophy; invoke it when building UI. On other
harnesses, this file stands alone.
