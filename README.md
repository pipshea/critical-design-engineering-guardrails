# Critical Design Engineering Guardrails

Guardrails for agentic tools, implementing the [Critical Design Engineering Manifesto](https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4) (Shea, 2026) — a remix of Oliver, Savičić & Vasiliev's [Critical Engineering Manifesto](https://criticalengineering.org) (2011).

The manifesto states the principles; this repository is their practice layer. The source text stays in [version control as a public gist](https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4) — this repo turns it into working guardrails for design engineers, UX designers, product managers, and anyone shipping software with AI assistance.

The guardrails are plain markdown. They work in any tool that reads markdown instructions.

**What it does:** turns eleven manifesto statements into agent behaviours. The agent records the *why* behind decisions before moving on, surfaces what generated code hides, proposes seams users can understand, configure and contest, raises design concerns while code is still soft, and requires a named human to accept authorship of consequence before anything ships. It creates the seams where human judgement happens; it does not perform critique.

## Layout

```
AGENTS.md                          — the five conventions; the universal entry point
core/
  critical-design-engineering.md   — the full practice: principles, behaviours, limits
templates/
  decision-record.md               — statement 5: decided / rejected / why / who's affected
  seam-audit.md                    — statement 3: hidden / revealed / understand-configure-contest
  provotype-brief.md               — statements 8 & 10: the question, and how to spot domestication
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

The core file is the single source of truth. Adapters are deliberately thin so nothing drifts.

## Install

**Any tool that reads AGENTS.md** (most agentic IDEs now do): copy this repo's files into your project, or copy the conventions block from `AGENTS.md` into your existing one. Done.

**Claude Code:** copy `adapters/claude-code/skills/critical-design-engineering/` into your project's `.claude/skills/` (or `~/.claude/skills/` for all projects), and keep `core/`, `templates/` and `references/` at the repo root where the skill can read them.

**Cursor:** copy `adapters/cursor/critical-design-engineering.mdc` into `.cursor/rules/`.

**GitHub Copilot:** copy the contents of `adapters/github-copilot/copilot-instructions.md` into `.github/copilot-instructions.md`.

**Gemini CLI:** copy the contents of `adapters/gemini-cli/GEMINI.md` into your project's `GEMINI.md`.

**Anything else:** point the tool's context mechanism at `core/critical-design-engineering.md`. It is self-contained.

## Use

The practice fires at four moments: writing specs (record the why), generating (surface the workings, propose seams), the window between generation and shipping (raise concerns while code is soft), and before merge (what does this close, who is affected, which human signs).

The templates are meant to be committed to your repo, filled in, next to the code they explain — that is statement 5 working as intended.

Two guardrails don't rely on the model at all: the PR template and the `human-signs` CI check make the signature mechanical. Model behaviour varies; the pipeline doesn't. And because models *are* different interpreters of the same guardrails, `testing/protocol.md` gives you four probes to measure how yours behaves — run it before trusting any tool with the stop behaviours.

## Fork it

Guardrails are authored context; author them. Edit the behaviours to fit your practice, delete what doesn't serve, and record why in your commit messages. The manifesto's source text lives in [version control](https://gist.github.com/pipshea/5dec1e877d01cf67f36f19ef50af78e4) with an open invitation to fork, and so does this.

## Credit and license

Manifesto: Pip Shea (2026), remixing Julian Oliver, Gordan Savičić & Danja Vasiliev (2011). Published under the [GNU Free Documentation License v1.3](https://www.gnu.org/licenses/fdl-1.3.html), after the original — share alike. See `LICENSE.md`.
