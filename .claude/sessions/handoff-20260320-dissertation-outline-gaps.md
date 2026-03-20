# Session Handoff — 2026-03-20: Dissertation Outline Gap Analysis & Plan

## What Was Done This Session

1. **Synced advisor writeup improvements into dissertation chapter** (commit ac31868):
   - §2.4: Restructured ker/im ordering — definitions before usage, added filled-vs-unfilled geological analogy
   - §3.4: Expanded H₁ argument — stability≠relevance brightness counterexample, variogram-matching eliminates-redundancy argument, two-level warrant table
   - §6: Added "PH as epistemic anchor" framing paragraph

2. **Full gap analysis** comparing `docs/DISSERTATION_CHAPTER_PH.md` against the three QCF source documents (Complete Vision v5.4, Implementation Spec v6.3, Architecture Decisions v1.1)

## Gap Analysis Summary

### Well-covered (no action needed)
- PH mathematical foundations (§2) — strongest section
- H₁ hypothesis with two-level warrant (§3.4) — just expanded
- Ellipse degradation thought experiment (§4)
- Evidence hierarchy, 7 levels (§5)
- System architecture (NP, hyperbolic, Perceiver IO) (§6)
- Cross-domain applications (§7)
- Dynamic essence / response essence (§10.1-10.5)
- Confidence hierarchy / SLIDE / DST (§10.6)
- Uncertainty quantification pipeline (§10.7)

### Major gaps — Priority order

**Gap 1: The Principle-Based Generator** (HIGHEST PRIORITY)
- Source: Complete Vision Chapters 11-16 (~200 lines)
- Missing: why build a generator, taxonomy positioning, fluvial/aeolian/estuarine design, acceptance criteria, validation strategy
- This is the experimental apparatus — without it, everything else is untestable theory
- **Key resource**: `~/projects/analog_image_generator/` has:
  - 5 PRDs: `.taskmaster/docs/prd.txt`, `prd_aeolian.txt`, `prd_estuarine.txt`, `prd_fluvial_demo.txt`, `prd_fluvial_realism.txt`
  - Code structure: `src/analog_image_generator/geologic_generators.py`
  - Tests: `tests/test_fluvial.py`, `test_braided.py`, `test_anastomosing.py`
  - Last commit: 2025-12-04 (~3.5 months ago)
  - **IMPORTANT**: Code is barely implemented and not working. The basic project structure exists but the implementation was never completed. The PRDs and structure are useful as design references for the dissertation chapter, but don't treat the code as a working reference. The generator chapter in the dissertation should be a theoretical treatment of what needs to be built, informed by the PRDs and Complete Vision — not a description of existing working software. The code will need considerable theoretical evaluation and likely a ground-up implementation effort in a future phase.

**Gap 2: Linchpin Framing** (QUICK WIN)
- The advisor writeup states starkly: "if PH features turn out to capture irrelevant invariants, the entire hierarchy inverts. The H₁ experiment is the linchpin."
- Currently implied across §3.4 and §5.1 but never stated as an explicit risk
- Should go in §5.1 (after the "Limitation" note) or §3.4 (after the two-level warrant table)
- ~2-3 sentences, can be done in minutes

**Gap 3: Complete Sākṣī Validation Framework**
- Source: Complete Vision Chapters 21-24
- Currently §6.6 mentions 4 of 10 witnesses in passing
- Missing: full 10-test table with targets, LOGO protocol details, all 4 adversarial tests (only one in §3.7), Claim Survival Matrix with pre-committed interpretations
- Needed for experimental design coherence

**Gap 4: Literature Review / Novelty Positioning**
- Source: Complete Vision Chapters 7-10
- No dedicated literature review section exists
- Missing: 20-query validation results, component-level novelty analysis, "integration gap" argument, competitive positioning
- Needed before any publication but can be deferred during theory-building

**Gap 5: Training Methodology**
- Source: Complete Vision Chapters 25-26
- Missing: 4-phase training procedure, loss function details with pseudocode, hyperparameter specification
- Needed before implementation begins

**Gap 6: Vedantic Framework Depth**
- Source: Complete Vision Chapters 2-3, 5-6
- Aparā/Parā Vidyā, Three Guṇas, Underdetermination as Epistemic Virtue
- Lowest priority — philosophical framing can be layered in last
- Some of this may be cut for a more standard dissertation format

### Minor gaps
- Alternative frameworks engagement (phenomenological, semiotic, TKR) — Complete Vision §4.5
- Architecture decision rationale (why DINOv2, why principle-based generator) — ADR document
- Implementation phasing / decision trees / contingency plans — Impl Spec

## Recommended Execution Plan

### Session 2: Generator Chapter + Linchpin (next session)
1. Quick win: Add linchpin framing to §5.1 (~5 min)
2. Read the 5 PRDs from `~/projects/analog_image_generator/.taskmaster/docs/`
3. Read `geologic_generators.py` to understand current implementation state
4. Compare generator project state to Complete Vision Chapters 11-16
5. Write new dissertation section (probably §X between current §8 and §9, or as a new §3-adjacent section) covering:
   - Why build a generator (vs. using existing simulators)
   - Generator taxonomy positioning
   - Three-environment design (fluvial, aeolian, estuarine) with parameters
   - Acceptance criteria
   - Generator validation strategy (internal + LOGO)
6. Commit

### Session 3: Sākṣī Validation Framework
1. Expand §6.6 into a full section or promote to its own top-level section
2. Include: 10-test table, LOGO protocol, 4 adversarial tests, Claim Survival Matrix
3. Ensure experimental validation design (§8) references the full Sākṣī framework
4. Commit

### Session 4: Literature Review + Training Methodology
1. Add literature review section (or distribute into existing sections)
2. Add training methodology section
3. Consider restructuring the document's section numbering
4. Commit

### Session 5: Vedantic Framework + Final Structure
1. Deepen philosophical framing if desired
2. Final structural pass — renumber sections, update §1.4 chapter overview
3. Add linchpin contingency language where needed

## Current State
- Branch: main
- Last commit: ac31868 (docs: sync advisor writeup improvements into dissertation chapter)
- Working tree: clean except .claude session files
- Dissertation chapter: ~1,010 lines, 11 sections

## Key Files for Next Session
- `docs/DISSERTATION_CHAPTER_PH.md` — target document
- `docs/qualia_convergence_COMPLETE_VISION_v5.md` — source (Chapters 11-16 for generator)
- `~/projects/analog_image_generator/.taskmaster/docs/prd*.txt` — generator PRDs (5 files)
- `~/projects/analog_image_generator/src/analog_image_generator/geologic_generators.py` — current implementation
- This handoff: `.claude/sessions/handoff-20260320-dissertation-outline-gaps.md`

## Start Message for Next Session
```
Read .claude/sessions/handoff-20260320-dissertation-outline-gaps.md and MEMORY.md

Task: Session 2 of dissertation outline gap-filling. Start with the linchpin framing (quick win),
then write the generator design chapter by comparing the Complete Vision (Chapters 11-16),
the generator PRDs in ~/projects/analog_image_generator/.taskmaster/docs/, and the current
implementation in geologic_generators.py. Formal academic voice, full theoretical treatment.
```
