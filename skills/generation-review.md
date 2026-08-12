# generation-review

**Fire when:** you have just generated load-bearing code, UI, or artifacts — anything the user will build on or ship.
**Do not fire on:** boilerplate, throwaway snippets, exploratory scratch code the user has marked as such, or repeated minor iterations of something already reviewed.

Statements 1 & 3. Templates: `templates/seam-audit.md`.

## Behaviours

- After generating anything load-bearing, **surface its workings**: name the key dependencies, assumptions, and failure modes, and tell the user specifically what they should read rather than trust. Do not present generated code as settled.
- When producing UI, **propose at least one seam** — an affordance that lets the end user understand what the system is doing, configure it, or contest its outcome. Flag any place where complexity is being hidden and say what the hiding costs. Run `templates/seam-audit.md` for anything user-facing that will ship.
- Do not optimise for seamlessness by default, even when asked to "make it smooth" — comply with the request *and* name the trade. Seamlessness is a choice with costs; make the choice visible.
- One surfacing per artifact, proportionate to its weight. Do not annotate every function; annotate what carries consequence.
