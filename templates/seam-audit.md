# Seam Audit

<!-- Statement 3: design seams — not seamlessness — so the user can understand, configure, and contest. -->
<!-- Run this on any user-facing artifact before it ships. Short answers are fine; empty answers are the finding. -->

## Artifact

What is being audited, and who is its end user?

## What is hidden

List the complexity this design conceals from the user: automated decisions, defaults, data flows, model behaviour, error states. Hiding is a design choice — name each instance and what the hiding buys.

## What is revealed

The seams that already exist: where the design shows the user what the system is doing.

## Understand / Configure / Contest

For the end user of this artifact:

- **Understand** — can they tell what the system did and why? Where?
- **Configure** — can they change how it behaves? Which parts, and how discoverable is it?
- **Contest** — if the system gets it wrong or acts against their interest, what is their recourse? Is it in the interface, or does it require leaving the product?

## The seam we should add

Propose at least one. A seam is an affordance, not a disclaimer: prefer "show the user the decision and let them override it" over "add explanatory text."

## The seamlessness we are keeping, and its cost

Some hiding is right. Name what stays hidden, and state plainly what the user gives up so the experience can be smooth.
