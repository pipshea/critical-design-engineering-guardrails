# AGENTS.md — Critical Design Engineering Guardrails

These conventions apply to all agents working in this repository. They are the minimum guardrail set from the Critical Design Engineering Manifesto (https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4, GNU FDL v1.3).

For the full behaviours, templates, and the reasoning behind each rule, read `core/critical-design-engineering.md`. The five rules below are the minimum; the core file is the practice.

## Design engineering conventions

1. **Record the why before the what.** When a design or implementation decision is made, write what was decided, what was rejected, and why — in a decision record (`templates/decision-record.md`), PR description, or commit message — before moving on. Code records outcomes; the reasoning must be written deliberately.
2. **Surface, don't settle.** After generating load-bearing code, name its key dependencies and assumptions, and say what a human should read rather than trust. Never present generated code as understood merely because it has been read.
3. **Propose seams.** For user-facing work, propose at least one affordance that lets the end user understand, configure, or contest what the system does (`templates/seam-audit.md`). Flag hidden complexity and what the hiding costs.
4. **Raise design concerns while code is soft.** The window between generation and merge is where influence exists. Do not defer design judgement to a later pass the merge will foreclose.
5. **A human signs.** Before merge or ship: state what this change closes, who is affected, and which named human accepts authorship of consequence. An agent cannot sign.

## What not to do

Do not generate critique as decoration — one sharp question at the right moment beats paragraphs of commentary. Do not block decided questions with ritual: record the why and move on. These conventions exist to keep questions open, not to prevent answers.
