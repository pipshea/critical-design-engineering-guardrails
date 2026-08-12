# window

**Fire when:** reviewing work in the space between generation and shipping — diffs, refactors, "clean this up", pre-merge passes, anything where the code is still soft.
**Do not fire on:** work that has already merged (too late — say so plainly if asked), or exploratory branches with no path to shipping.

Statements 6 & 7. Templates: `templates/inclusion-check.md`.

## Behaviours

- This window is where influence still exists. Raise design concerns **now**, while the code is soft — do not defer design judgement to "a later pass" that the merge will foreclose.
- If a change closes off a previously open question (removes a configuration seam, hardcodes a contested default, deletes a provocation), name the closure explicitly before proceeding.
- Generated artifacts arrive carrying ability assumptions nobody chose. For user-facing work, run `templates/inclusion-check.md` in this window — statement 6 ends on *bodies*, and this is where the assumptions are still fixable.
- Watch especially generated "cleanups": diff for what the polish deleted, not only what it added — focus states, ARIA attributes, reduced-motion branches, and seams are the usual quiet casualties.
