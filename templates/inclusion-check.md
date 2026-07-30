# Inclusion Check

<!-- Statement 7: inhabit the space between generation and shipping — and statement 6, which ends on *bodies*. -->
<!-- Generated artifacts arrive carrying ability assumptions nobody chose. Run this check while the code is -->
<!-- still soft, before the merge hardens the assumptions in. -->
<!-- Grounded in public standards: WCAG 2.2 and COGA (W3C), the permanent/temporary/situational impairment -->
<!-- spectrum (Microsoft Inclusive Design Toolkit). The design-layer framing follows MC Dean's -->
<!-- inclusive-design-skills (github.com/Owl-Listener/inclusive-design-skills): accessibility is a design -->
<!-- commitment, not a code review. This check is the statement-7 complement to that work — it audits the -->
<!-- generated artifact in the pre-merge window, where her skills shape the decisions before code exists. -->

## Artifact

What was generated, by what tool, and who is its end user?

## The assumptions it shipped with

Generated defaults encode a default body. Name what this artifact assumes the user can do — see, hear, use a pointer, hold state in memory, read at speed, act within a timeout. Every assumption listed here was made for default bodies; that is why it must be examined by somebody.

## Who is excluded, across the spectrum

For each assumption above, who does it exclude? Work the full spectrum — permanent, temporary, and situational (a blind user; a user with a migraine; a user holding a baby in bright sunlight). Exclusion is rarely intentional and never self-announcing.

## The four checks

- **Perceivable** — does every piece of information reach the user through more than one channel? (Text alternatives, contrast, not colour alone, captions.)
- **Operable** — does everything work by keyboard alone? Is there anything a timeout, a gesture, or a motion effect makes impossible? Is `prefers-reduced-motion` respected?
- **Understandable** — can the user tell where they are, what happened, and how to recover from an error? Is the language plain? Is the cognitive load of the flow proportionate to the task?
- **Robust** — does it hold up under assistive technology, zoom to 200%, and user-set preferences (contrast, colour scheme, text size)?

These compress WCAG 2.2 and COGA; they do not replace them. For anything shipping to production, run the real success criteria.

## Seams for every body (statement 3)

The understand / configure / contest test, asked again for assistive technology: can a screen-reader user *understand* what the system did? Can preferences *configure* it (motion, contrast, text size — respected, not overridden)? Is the recourse for contesting an outcome itself accessible, or does the appeal path assume abilities the main path doesn't?

## Decisions and debt (statements 5 and 9)

- Record what was found and what was fixed, with the why, in a decision record.
- For anything deferred: who is excluded while it waits, what the fix is, and why it was deferred — written down, not implied.
- **Accepted exclusion is a decision, and a named human signs it.** An agent cannot accept accessibility debt on anyone's behalf; deferring a fix means deciding some people wait, and that decision carries a name.

## The merge check

Before this artifact ships: did this window close any seam an earlier version had? Generated "cleanups" quietly remove focus states, ARIA attributes, and reduced-motion branches — diff for what the polish deleted, not only what it added.
