# Project: Persistent Homology Research

Academic research on applying persistent homology (TDA) to the qualia convergence framework.

## Tech Stack

- No code — research and writing only
- Markdown for output documents

## Structure

```
docs/              # Source documents and output papers
```

## Project-Specific Patterns

- All source documents are in `docs/`
- Output documents go in `docs/` with descriptive names
- Academic tone, precise mathematical notation (LaTeX-style)

## Key Decisions & Constraints

- Research-only project — no TDD, no linting, no code
- Read ALL source documents before conducting external research
- Every claim must trace to source documents or cited references

## Gotchas & Watch-outs

- The term "qualia" is used metaphorically (operationalized via the LOGO test), not in the philosophical phenomenology sense
- Source docs include deprecated versions — only use the three current documents listed in `docs/00_DOCUMENT_INDEX.md`
- `.docx` files in `docs/` contain the persistent homology writeups (general research + personal research)

## Research Workflow

### Daily Loop
1. Read source documents relevant to the current research task
2. Conduct external research if needed (WebSearch, WebFetch)
3. Write/revise output documents
4. Small, focused commits

## Current Focus

- [ ] ~5-page persistent homology writeup for professor meeting

## Source Documents

See `docs/00_DOCUMENT_INDEX.md` for the authoritative document index. Key files:

| Document | Purpose |
|----------|---------|
| `qualia_convergence_COMPLETE_VISION_v5.md` | Full intellectual vision (north star) |
| `qualia_convergence_IMPLEMENTATION_SPEC_v6.md` | Practical guide with phases and decision points |
| `qualia_convergence_ARCHITECTURE_DECISIONS_v1.md` | Reasoning behind design choices |
| `persistent_homology_writeup_general_research.docx` | General PH research writeup |
| `persistent_homology_writeup_my_research.docx` | Personal PH research writeup |
| `essence_thought_experiment.pdf` | Essence thought experiment |
