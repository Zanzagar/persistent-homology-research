# Qualia Convergence Framework — Document Index

**Last Updated**: January 2026 (Post-Critical Review)

---

## Current Documents (Three-Document Architecture)

These are the authoritative, current documents:

| Document | Purpose | Version | File |
|----------|---------|---------|------|
| **Complete Vision** | The "north star" — full intellectual vision | v5.4 | `qualia_convergence_COMPLETE_VISION_v5.md` |
| **Implementation Specification** | Practical guide with phases and decision points | v6.3 | `qualia_convergence_IMPLEMENTATION_SPEC_v6.md` |
| **Architecture Decisions** | Reasoning behind design choices | v1.1 | `qualia_convergence_ARCHITECTURE_DECISIONS_v1.md` |

### Document Relationships

```
┌─────────────────────────────────────────────────────────┐
│           COMPLETE VISION (v5)                          │
│           "What we're building"                         │
│           The north star - no compromise                │
│           ~70KB, 1,470 lines                           │
└────────────────────────┬────────────────────────────────┘
                         │
         ┌───────────────┴───────────────┐
         │                               │
         ▼                               ▼
┌─────────────────────────┐   ┌─────────────────────────┐
│ IMPLEMENTATION SPEC (v6)│   │ ARCHITECTURE DECISIONS  │
│ "How we build it"       │   │ "Why these choices"     │
│ Phases, decisions,      │   │ Trade-offs, triggers,   │
│ contingencies           │   │ evidence                │
│ ~32KB, 650 lines        │   │ ~23KB, 470 lines        │
└─────────────────────────┘   └─────────────────────────┘
```

---

## Deprecated Documents (Historical Reference Only)

These documents have been **superseded** by the current three-document architecture. They are retained for historical reference but should not be used for active development.

### Superseded Consensus Documents

| File | Status | Superseded By |
|------|--------|---------------|
| `qualia_convergence_FINAL_v5.2.md` | DEPRECATED | Complete Vision v5 + Implementation Spec v6 |
| `qualia_convergence_FINAL_v5.1.md` | DEPRECATED | Complete Vision v5 + Implementation Spec v6 |
| `qualia_convergence_FINAL_v5.md` | DEPRECATED | Complete Vision v5 + Implementation Spec v6 |

### Superseded Appendix Documents

| File | Status | Superseded By |
|------|--------|---------------|
| `qualia_convergence_FULL_VISION_appendix_v4.md` | DEPRECATED | Complete Vision v5 |
| `qualia_convergence_FULL_VISION_appendix_v3.md` | DEPRECATED | Complete Vision v5 |
| `qualia_convergence_FULL_VISION_appendix_v2.md` | DEPRECATED | Complete Vision v5 |

### Merged Documents

| File | Status | Content Merged Into |
|------|--------|---------------------|
| `02_anticipated_questions.md` | MERGED | Implementation Spec v6 (Q&A as decision points) |
| `full_vision_vs_staged_comparison.md` | SUPERSEDED | Architecture Decisions v1 |

---

## What Changed in the Reorganization

### Before (Multiple Overlapping Documents)
- Consensus document (practical focus)
- Full Vision appendix (theoretical focus)
- Anticipated questions (Q&A format)
- Comparison document (staging analysis)

**Problems**:
- Overlapping content
- Orphaned cross-references
- Unclear which document was authoritative
- References to "see other document" that didn't exist

### After (Clean Three-Document Architecture)
- **Complete Vision**: Single authoritative source for the full system
- **Implementation Spec**: Single authoritative source for how to build it
- **Architecture Decisions**: Single authoritative source for why

**Benefits**:
- No overlapping content
- Self-contained documents (no orphaned references)
- Clear purpose for each document
- Complete reference lists in each document

---

## Literature Validation Status

All 20 queries from January 2026 literature validation are integrated into the Complete Vision document.

| Query Range | Topic | Status |
|-------------|-------|--------|
| 1-3 | Core components (Hyperbolic, NP, TDA) | ✅ Integrated |
| 4-6 | Retrieval systems and foundation models | ✅ Integrated |
| 7-10 | DINOv2, domain adaptation, UQ, validation | ✅ Integrated |
| 11-13 | Sparse methods, multimodal, classification | ✅ Integrated |
| 14-16 | Generator taxonomy and positioning | ✅ Integrated |
| 17-18 | Interpretable generators, synthetic data gaps | ✅ Integrated |
| 19-20 | Aeolian/estuarine simulators, deep generative models | ✅ Integrated |

**Key Findings from Queries 17-20**:
- Rule-based generators "indispensable" for interpretability (validates our approach)
- Major documented gap: lack of standardized geological benchmarks
- Aeolian/estuarine simulators less mature than fluvial; CA and process-based dominate
- Deep generative models (GANs/VAEs/diffusion) focus on surrogate simulation, not training data
- Our principle-based generator fills a distinct niche (fast, interpretable, multi-environment, known ground truth)

---

## Critical Epistemic Review Response (January 2026)

An external critical review examined the framework's philosophical coherence, literature gaps, and engagement with alternative frameworks.

### Changes Made in Response

| Concern Raised | Response | Document Updated |
|----------------|----------|------------------|
| **"Qualia" terminology** | Added explicit scope limitations; metaphorical use documented | Complete Vision Ch. 4.5, ADR-009 |
| **What we do NOT claim** | Added explicit disclaimers (phenomenology, semiotics, intrinsic essence) | Complete Vision Ch. 4.5.1 |
| **Alternative frameworks** | Engaged with phenomenological, semiotic, graph-based approaches | Complete Vision Ch. 4.5.3, ADR-010 |
| **Literature gaps: TKR** | Cited Chawshin et al. TKR patent; noted as potential pathway | Complete Vision refs [84], ADR-010 |
| **Literature gaps: Semiotics** | Cited Parcell & Parcell (2009) | Complete Vision refs [82-83] |
| **Literature gaps: Qualia** | Cited Tye (2021), Block (1995) | Complete Vision refs [86-87] |

### Concerns Addressed by Existing Framework

| Concern Raised | Existing Coverage |
|----------------|-------------------|
| **Operational definition of essence** | LOGO test (Complete Vision Ch. 4, ADR-008) |
| **Expert validation** | Sākṣī framework with Cohen's κ (Ch. 12, ADR-007) |
| **Similarity metrics** | NMI, ECE, Pearson r in Sākṣī tests |
| **GANs/VAEs/Diffusion** | Addressed in Query 20; different use case |
| **Sparse data handling** | Neural Process query encoder (ADR-003) |

### Concerns Acknowledged but Out of Scope

| Concern | Rationale |
|---------|-----------|
| **Eye-tracking studies** | Out of scope for PhD; κ-based validation sufficient |
| **Full semiotic framework** | Different research direction; noted as future work |
| **Phenomenological primary framing** | Computationally intractable; operationalism preferred |

---

## Generator PRD Integration Status

All three generator PRDs are integrated into the Complete Vision document.

| Environment | PRD File | Status |
|-------------|----------|--------|
| Fluvial | `prd.txt` | ✅ Complete parameters in Ch. 13 |
| Aeolian | `prd_aeolian.txt` | ✅ Complete parameters in Ch. 14 |
| Estuarine | `prd_estuarine.txt` | ✅ Complete parameters in Ch. 15 |

---

## Recommended Actions

1. **For new work**: Use only the three current documents
2. **For historical reference**: Old documents available but marked deprecated
3. **For advisor meetings**: Use Complete Vision for scope, Implementation Spec for planning
4. **For implementation**: Use Implementation Spec decision trees and phase guides

---

*Document Index — January 2026*
