# Critical Design Engineering Guardrails

```
══════════════════════
  o───o───●───o───▶
══════════════════════
```

Design engineering guardrails for critical collaboration with agentic IDEs. Operationalising the [Critical Design Engineering Manifesto](https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4) (Shea, 2026) — a remix of Oliver, Savičić & Vasiliev's [Critical Engineering Manifesto](https://criticalengineering.org) (2011).

The manifesto states the principles; this repository is their practice layer. The source text stays in [version control as a public gist](https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4) — this repo turns it into working guardrails for design engineers, UX designers, product managers, and anyone shipping software with AI assistance.

The guardrails are plain markdown. They work in any tool that reads markdown instructions.

**What it does:** turns eleven manifesto statements into agent behaviours. The agent records the *why* behind decisions before moving on, surfaces what generated code hides, proposes seams users can understand, configure and contest, raises design concerns while code is still soft, and requires a named human to accept authorship of consequence before anything ships. It creates the seams where human judgement happens; it does not perform critique.

## Layout

```
●──┬──o
   ├──o
   ├──o
   └──o
```

```
AGENTS.md                          — the five conventions; the universal entry point
core/
  critical-design-engineering.md   — the router: stances, and which skill fires at which moment
skills/
  spec-why.md                      — statements 4 & 5: record the why; carry the prototype's question
  generation-review.md             — statements 1 & 3: surface the workings; propose seams
  window.md                        — statements 6 & 7: the pre-merge window; the inclusion check
  merge.md                         — statements 8–10: what closes, who's affected, who signs
  design-contest.md                — statement 8: stage competing cases before consensus
templates/
  decision-record.md               — statement 5: decided / rejected / why / who's affected
  seam-audit.md                    — statement 3: hidden / revealed / understand-configure-contest
  provotype-brief.md               — statements 8 & 10: the question, and how to spot its quiet closure
  inclusion-check.md               — statements 6 & 7: the ability assumptions generated code ships with
references/
  influences.md                    — the scholarship behind each statement
adapters/                          — thin, tool-native pointers to the core
.github/
  pull_request_template.md         — statements 5, 9 & 10 at merge time
  workflows/human-signs.yml        — CI: a PR merges only when a named human signs
testing/
  protocol.md                      — four probes for testing the guardrails per model/IDE
  results.md                       — dated results matrix
```

The router in `core/` is the entry point: it holds the always-on stances and routes each moment to one skill. Adapters are deliberately thin so nothing drifts.

## Install

```
      o
      ↓
o───o───●───▶
```

**Any tool that reads AGENTS.md** (most agentic IDEs now do): copy this repo's files into your project, or copy the conventions block from `AGENTS.md` into your existing one. Done.

**Claude Code:** copy `adapters/claude-code/skills/critical-design-engineering/` into your project's `.claude/skills/` (or `~/.claude/skills/` for all projects — though see the scope note under "Use"), and keep `core/`, `templates/` and `references/` at the repo root where the skill can read them.

**Cursor:** copy `adapters/cursor/critical-design-engineering.mdc` into `.cursor/rules/`.

**GitHub Copilot:** copy the contents of `adapters/github-copilot/copilot-instructions.md` into `.github/copilot-instructions.md`.

**Gemini CLI:** copy the contents of `adapters/gemini-cli/GEMINI.md` into your project's `GEMINI.md`.

**Anything else:** point the tool's context mechanism at `core/critical-design-engineering.md`. It is self-contained.

## Use

```
o───o───o───●───▶
↑   ↑   ↑   ↑
```

The practice fires at four moments: writing specs (record the why), generating (surface the workings, propose seams), the window between generation and shipping (raise concerns while code is soft), and before merge (what does this close, who is affected, which human signs). The templates are meant to be committed to your repo, filled in, next to the code they explain — that is statement 5 working as intended.

Not everything here wants to be always-on, though. The guardrails come in two weights, and matching the weight to the moment is what keeps them useful rather than ritual.

**Always-on: the stances.** The five conventions in `AGENTS.md` — and the thin Cursor rule, which carries the same — are cheap enough to persist. They change how the agent narrates and stops, not what it builds. Leave these on for any repo where the work ships to users.

**At the moments: the practice.** The skills in `skills/` and their templates are deliberate friction, and friction is only the deliverable at decision points. The router matches each moment to one skill — including `design-contest`, summoned when directions compete and consensus is arriving before the alternatives have been argued. Fire them at their moments, not on every autocomplete and trivial refactor. Don't convert the skills into always-on rules: a seam proposal on every keystroke is how you manufacture the over-firing failure described in the note on models, and how a team comes to delete the guardrails. The practice inhabits the space between generation and shipping; summon it when you enter that window.

One note on scope: install per-repo, where the work is user-facing and consequential. Scratch projects, spikes, and one-off scripts don't need seam audits, and a global install that fires everywhere teaches people to ignore it everywhere. The guardrails belong where consequence lives.

And for work that merges: the repo includes a pull request template and a `human-signs` check (see `.github/`) that make the sign-off part of the pipeline itself, independent of any AI tool. Much design engineering work never merges — prototypes and provocations do their job without shipping — so these are there when your work heads for production, not a required starting point.

## A note on models

```
        ┌──▶
o───●───┼──▶
        └──▶
```

These guardrails are a plan, and plans are resources for action, not determinants of it. Every model interprets them differently, and the differences are not the ones the spec sheets advertise. A large context window doesn't help much — the files are tiny; what matters is whether the model still *attends* to them an hour into a session. The failures run in two directions: a model that quietly drops the behaviours under the pressure of the coding task, and a model that performs them as ritual — decision records for every renamed variable, critique as decoration. The second failure looks like compliance and is the one most likely to make you delete the guardrails. Watch especially the stop behaviours: some models will mention the signature requirement while merging anyway.

Statement 1 applies to the tool running these guardrails, too. Don't take any of this on faith — `testing/protocol.md` gives you four probes to measure how your model and IDE actually behave. Run it before trusting the stop behaviours.

## Fork it

```
o───●───o───▶
     \
      o───▶
```

Guardrails are authored context; author them. Edit the behaviours to fit your practice, delete what doesn't serve, and record why in your commit messages. The manifesto's source text lives in [version control](https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4) with an open invitation to fork, and so does this.

## Acknowledgements

The portable-markdown architecture — guidance as plain markdown, with thin per-tool adapters — follows the pattern of MC Dean's [Designpowers](https://github.com/Owl-Listener/designpowers) (MIT), which in turn credits the plugin architecture of Jesse Vincent's [Superpowers](https://github.com/obra/superpowers). The pattern is theirs; the guardrails are ours. Designpowers is also a working demonstration of what these guardrails argue for — a design practice authored in markdown — and is cited in `references/influences.md`. The inclusion check's design-layer framing follows her [inclusive-design-skills](https://github.com/Owl-Listener/inclusive-design-skills) (MIT) — accessibility as a design commitment, not a code review — while drawing its substance from the public standards she also builds on: WCAG 2.2, COGA, and Microsoft's Inclusive Design Toolkit.

## Credit and license

Manifesto: Pip Shea (2026), remixing Julian Oliver, Gordan Savičić & Danja Vasiliev (2011). Published under the [GNU Free Documentation License v1.3](https://www.gnu.org/licenses/fdl-1.3.html), after the original — share alike. See `LICENSE.md`.
