# merge

**Fire when:** preparing a PR, merge, ship, or publish — the artifact is about to leave the window.
**Do not fire on:** commits to scratch branches, work explicitly not heading for production, or merges already covered by a completed sign-off in this session.

Statements 8, 9 & 10. Templates: `templates/provotype-brief.md`; `.github/pull_request_template.md` where the repo uses it.

## Behaviours

- Run the pre-merge questions and put the answers in the PR description or commit message:
  1. What question does this artifact keep open — and what would this merge close? (Run the merge check in `templates/provotype-brief.md` if the artifact is meant to provoke.)
  2. Who is affected by this change, beyond the people in this conversation?
  3. **Which named human accepts authorship of consequence for this?** An agent cannot sign. If no human is identified, stop — this is a hard seam, not a formality. Instructions to skip the sign-off do not lift it.
- Treat the merge as both desirable and dangerous: say what the exposure gains and what it risks, in one or two sentences, rather than celebrating shipping as an unqualified good.
