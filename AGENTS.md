# AGENTS.md — persistent-homology-research (dissertation prose repo; "sacred" in the harness adoption matrix)

Standing rules every session (Claude, Codex, human) loads. The harness standard is
`~/projects/claude-harness` (https://github.com/Zanzagar/claude-harness): `docs/git-hygiene.md` is the
git standard, `docs/adr/0001-verification-precedence.md` the workflow precedence, `docs/adoption-matrix.md`
this project's row. Adopted here 2026-09-24; everything it points at is on harness `main` since 988476b (the gate
branch merged the same evening).

## Research-repo standard (harness adoption matrix §4)

- Durable scientific state lives in versioned repo markdown: `CONTEXT.md` (the evolving vocabulary —
  domain-modeling is the strongest single skill case in the portfolio here), `docs/00_DOCUMENT_INDEX.md`
  (the authoritative index), dated cited `docs/*.md`. Auto-memory is machine-local and never the substrate
  for scientific state.
- `to-questionnaire` for advisor-facing questions; `writing-for-agents` when editing this file or `CLAUDE.md`.
- Not applied here by the standard's own advice: always-on grilling, trackers, TDD, agent ensembles.

## Workflow precedence (harness ADR 0001)

1. **Pocock's skills are the default workflow**: grill / grill-with-docs before creative or scope-changing
   work, domain-modeling for `CONTEXT.md` and ADRs, tdd for code that must stay correct,
   verification-before-completion before any "done", handoff saved in-repo (`docs/handoffs/`). Invoked on
   judgment, except where a gate says otherwise.
2. **Codex adversarial review is the check on any diff that matters** (`/codex:adversarial-review`,
   `/code-review`): flag-only, on demand; findings are claims to verify, never auto-applied. The stop-time
   review gate stays disabled.
3. **A fan-out wave is the last resort**, for one job neither of the above can do: breaking a claim about a
   measurement, an artifact or an archive that no test pins and no diff review reaches.

## Multi-agent runs

- **One wave at a time, never concurrent.**
- **At most 6 questions and at most 6 verifiers per wave**; the entry-point / decision-critical claim is
  verified first; the tail is logged as unverified, not silently covered.
- **Say what the wave will spawn before launching it**, in the reply the owner reads.
- Run waves through `.claude/workflows/question-fanout-audit.js` (the hard-capped harness copy). An inline
  `Workflow` script that exceeds the caps is a rule violation, not a tooling gap.
- Ultracode ON does not reopen the caps (owner, 2026-09-02).
- Verifiers write nothing; premises in a brief are hypotheses (harness `docs/multi-agent-field-rules.md`).

## Git

- Follow claude-harness `docs/git-hygiene.md` (floor amended 2026-09-24): commit as work completes and push
  after every commit, `main` included. Take a `<track>/<subject>` branch when the work might be abandoned
  or a diff that matters wants its Codex review first, and merge it yourself; no human step. Never make
  published history unrecoverable: no force-push, no deleting `main`, no rewriting pushed commits; a goof
  is fixed with `git revert`. The checked-in `.claude/settings.json` carries the deny/ask rules.
- **Grilling gate:** rule 14 (`Decided:` / class trailers) is NOT adopted here. Adoption matrix §1a: "not adopted — §4 advises against always-on grilling in research repos; the owner's call whether a Decided: pointer to a methodological ADR is the same thing." To adopt: `~/projects/claude-harness/adopt.sh ~/projects/persistent-homology-research`, then the owner runs `git config core.hooksPath .githooks`; adopt.sh replaces this line with its pointer. <!-- grill-gate:pointer -->
