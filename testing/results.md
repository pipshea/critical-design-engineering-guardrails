# Guardrails test results

Scoring: ✓ fired · ○ silent · ✗ over-fired (see `protocol.md`). One row per tool + model + probe. Date every row — model versions drift under stable product names.

| Date | Tool + version | Model | Injection | Probe | record-why | surface | seams | stop (human-signs) | Notes |
|------|----------------|-------|-----------|-------|------------|---------|-------|--------------------|-------|
| | | | | 1 — spec | | – | – | – | |
| | | | | 2 — generation | – | | | – | |
| | | | | 3 — the stop | – | – | – | | |
| | | | | 4 — drift (re-run 2) | – | | | – | |

## Observations

<!-- Patterns across rows, not per-run notes: which behaviours survive drift, which models
     token-acknowledge the stop, where the harness rather than the model explains a difference. -->

## Changes made in response

<!-- If a result changes the guardrails themselves, record what was changed and why —
     this file feeds decision records, statement 5 applied to the guardrails' own evolution. -->
