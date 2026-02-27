# Plan: Unified Dissertation Chapter — Persistent Homology & Analog Retrieval

## Context

A new document (`docs/ESSENCE_UNDER_CONSTRAINT_CONTEXT.md`) reframes the entire research program by centering the dissertation's operational question: how to organize and retrieve geological analogs under sparse data constraints. The existing PH paper treats essence determination as the primary research question; the context document positions it as the *enabling abstraction* for two coupled pipelines (cataloguing and retrieval).

**Goal:** Create a single dissertation chapter draft that integrates the existing PH paper (~7,000 words, 40 references) with the new Pipeline A/B framing and relevant QCF source material.

**Outcome:** `docs/DISSERTATION_CHAPTER_PH.md` — a ~14,250-word, committee-ready chapter.

**Preservation:** Existing `PERSISTENT_HOMOLOGY_PAPER.md` and all source documents remain untouched.

---

## Chapter Title

"Persistent Homology and the Operationalization of Geological Essence: Topological Foundations for Analog Cataloguing and Retrieval Under Sparse Data Constraints"

---

## Section-by-Section Plan

### Abstract (~350 words) — REWRITE
- Expand current abstract to include the dissertation research question, Pipeline A/B architecture, and PH's role within that architecture
- Sources: PH Paper abstract + Context Doc framing

### §1: The Dissertation Research Problem and System Architecture (~1,500 words) — NEW

**1.1 The Research Question** (~400 words)
- Sparse subsurface prediction problem
- Why analog retrieval is the response
- The operational question: systematic organization, indexing, and retrieval
- Sources: Context Doc §1, §3

**1.2 The Two-Pipeline Architecture** (~500 words)
- Pipeline A: Analog data → encode essence → index → geologic index
- Pipeline B: Sparse observations → encode essence → compare → retrieve
- The coupling requirement: compatible essence representations
- What breaks without compatibility
- Sources: Context Doc §2, §5

**1.3 Essence as the Enabling Abstraction** (~350 words)
- Core structural commitment: "multiscale structural invariance independent of generator artifacts"
- What essence enables vs. what happens without it
- Sources: Context Doc §4–5, §11

**1.4 Chapter Overview** (~250 words)
- Roadmap of the chapter
- How this chapter relates to subsequent dissertation chapters

### §2: Mathematical Foundations of Persistent Homology (~1,850 words) — PRESERVED VERBATIM
- Copy PH Paper §1 with section renumbering (1.x → 2.x)
- Subsections: 2.1–2.6 (topology, simplicial complexes, homology, PH, stability)
- All math, references, and examples intact

### §3: Application to the Qualia Convergence Framework (~1,800 words) — PRESERVED + LIGHT EDITS
- Copy PH Paper §2 with renumbering (2.x → 3.x)
- **Light edits only:**
  - §3.1: Add 1–2 sentences connecting back to §1's pipeline framing
  - §3.3: Add brief note that the three-pathway architecture feeds Pipeline A
- All existing content, math, and references preserved

### §4: The Ellipse Degradation Thought Experiment (~1,050 words) — PRESERVED VERBATIM
- Copy PH Paper §3 with renumbering (3.x → 4.x)
- No changes to content

### §5: The Evidence Hierarchy (~1,200 words) — PRESERVED + ONE NEW SUBSECTION
- Copy PH Paper §4 with renumbering (4.x → 5.x)
- **New §5.3: "Implications for Descriptor Admissibility and Query Validation"** (~350 words)
  - How the evidence hierarchy governs Pipeline A descriptor admissibility
  - How it governs Pipeline B query encoding validation
  - How it governs similarity metric justification
  - Sources: Context Doc §7.2, §8.2, §9, §10

### §6: System Architecture: From Invariants to Analog Retrieval (~3,200 words) — MOSTLY NEW

This is the major new section. It draws extensively from QCF Vision chapters 6, 18–21 and the Context Document, translated into dissertation-level conceptual prose with key equations (no implementation code).

**6.1 Pipeline A: Building the Geologic Index** (~600 words)
- Three-pathway feature extraction feeding index construction
- PH's role: topological descriptors as index entries with Level 1 evidence
- Multimodal analog data types (full-resolution images, 3D models, seismic, core photos, simulations)
- Index unit and granularity questions (entire analog vs. subvolume vs. stratigraphic package)
- Schema design options: metric space + ANN, hyperbolic embedding, knowledge graph, hybrid
- Sources: Context Doc §6–7, Vision Ch. 18–20

**6.2 Pipeline B: The Neural Process Query Encoder** (~800 words)
- The sparse observation problem: real queries have few wells, partial seismic, scattered observations
- Why Neural Processes over alternatives (TKR comparison from Vision §18.5)
- Architecture (conceptual with key equations):
  - Input: context set C = {(x₁,y₁), ..., (xₙ,yₙ)} of location-observation pairs
  - Modality-specific encoders: well log (1D CNN), seismic (2D CNN), outcrop (DINOv2)
  - Permutation-invariant set encoder: per-element MLP → self-attention → aggregation
  - Distribution output: (μ, σ) where σ captures uncertainty from sparsity
- Training objective: L_NP = E_C[KL(q(z|C) || p(z)) + E_z[-log p(targets|z)]]
- Graceful degradation: σ scales monotonically with sparsity (n>10: confident → n=0: prior)
- ADR-003 decision rationale and revision triggers
- The compatibility constraint: query encoder must map to same descriptor space as Pipeline A
- Sources: Vision Ch. 18 (lines 956–1090), ADR-003 (lines 148–195), Context Doc §8

**6.3 The Hyperbolic Embedding Space** (~600 words)
- Why Euclidean fails for hierarchical data: depositional environments are tree-like (environment → style → subtype)
- Poincaré ball model: distance grows exponentially toward boundary, volume grows exponentially with radius → O(log n) dimensions vs. Euclidean O(n)
- Key operations: exponential map (Euclidean → hyperbolic), logarithmic map (reverse), hyperbolic distance
- Hierarchy-aware training loss (key equation from Vision §19):
  - Positive attraction + negative repulsion + hierarchy regularization forcing children near parents
- Expected embedding structure: fluvial hierarchy at boundary (meandering/braided/anastomosing), with aeolian and estuarine as separate branches
- Sources: Vision Ch. 19 (lines 1094–1181), Nickel & Kiela (2017, 2018)

**6.4 Perceiver IO: Handling Variable Modalities** (~400 words)
- The variable-input problem: real queries have variable well counts, variable modalities present/absent, variable spatial coverage
- Perceiver IO architecture (conceptual):
  - Cross-attention (Input → Latent): variable-length inputs update fixed-size latent array
  - Self-attention: process information within fixed-size bottleneck
  - Cross-attention (Latent → Output): generate desired output format
- Output: single embedding vector + distribution parameters (μ, σ) + per-modality attention weights
- Benefits: fixed compute regardless of input complexity, interpretability through attention weights
- Sources: Vision Ch. 20 (lines 1185–1242), Jaegle et al. (2021)

**6.5 Pathway Fusion and the Underdetermination Principle** (~400 words)
- Cross-attention fusion of three pathways: project each to shared hidden dim → self-attention → output projection
- Convergence regularization loss: L_conv = Σ_{i<j} ‖fᵢ(x) - fⱼ(x)‖² — encourages pathways to agree while preserving independent signals
- The underdetermination principle (Vision §6): sparse observations consistent with multiple environments should return a distribution reflecting ambiguity, not a false point estimate
- High uncertainty on ambiguous queries = working as intended; confident prediction on ambiguous = calibration failure
- Sources: Vision Ch. 6 (lines 214–222), Impl Spec §3.4 (lines 369–410)

**6.6 Validation: The Sākṣī Layer** (~200 words)
- Ten independent "witnesses" validate the system end-to-end (Vision §21)
- Key witnesses relevant to this chapter: LOGO invariance (degradation <20%), pathway convergence (disagreement <0.2), calibration (ECE <0.1), adversarial robustness (attack success <30%)
- How the Sākṣī layer connects to the evidence hierarchy: each witness provides evidence at a specific level
- Sources: Vision Ch. 21 (lines 1248–1263)

**6.7 Open Design Questions** (~200 words)
- Similarity metrics under missing invariant dimensions (marginalization? imputation? constraint relaxation?)
- Retrieval format: single analog, top-k ranked set, equivalence class, posterior weights
- Uncertainty propagation from query sparsity through retrieval to output
- Adaptive metric selection based on query completeness
- Sources: Context Doc §8–9

### §7: Cross-Domain Structural Validation (~800 words) — PRESERVED VERBATIM
- Copy PH Paper §5 with renumbering (5.x → 7.x)
- No changes to content

### §8: Proposed Experimental Validation (~1,200 words) — PRESERVED VERBATIM
- Copy PH Paper §7 with renumbering (7.x → 8.x)
- No changes to content

### §9: Open Questions and the Path Forward (~700 words) — PRESERVED VERBATIM
- Copy PH Paper §6 with renumbering (6.x → 9.x)
- No changes to content

### §10: Conclusion (~600 words) — EXPANDED
- Preserve existing conclusion (~440 words)
- Add closing paragraph (~160 words) tying back to the dissertation:
  - PH provides the mathematical backbone for Pipeline A descriptor admissibility
  - The evidence hierarchy governs both pipeline operations
  - The experimental design provides the validation pathway for the next research phase

### References (~48 entries)
- Preserve all 40 existing references
- Add ~8 new references for Pipeline A/B content:
  - Kim et al. (2019) — Attentive Neural Processes
  - Nickel & Kiela (2017) — Poincaré embeddings
  - Nickel & Kiela (2018) — Lorentz model of hyperbolic geometry
  - Johnson, Douze, & Jégou (2019) — FAISS billion-scale similarity search
  - Leopold & Wolman (1957) — River channel patterns (if not cited elsewhere)
  - Additional references as needed during writing

---

## Word Count Summary

| Section | Words | Status |
|---------|-------|--------|
| Abstract | 350 | Rewrite |
| §1: Research Problem & Architecture | 1,500 | NEW |
| §2: Mathematical Foundations | 1,850 | Preserved |
| §3: Application to QCF | 1,800 | Preserved + light edits |
| §4: Ellipse Thought Experiment | 1,050 | Preserved |
| §5: Evidence Hierarchy | 1,200 | Preserved + 350 new |
| §6: System Architecture | 3,200 | MOSTLY NEW (expanded Vision content) |
| §7: Cross-Domain Validation | 800 | Preserved |
| §8: Experimental Validation | 1,200 | Preserved |
| §9: Open Questions | 700 | Preserved |
| §10: Conclusion | 600 | Expanded |
| **Total** | **~14,250** | ~63% preserved from PH paper, ~37% new |

Target: ~22–28 formatted pages (accounting for equations, tables, whitespace).

---

## Implementation Steps

1. Create `docs/DISSERTATION_CHAPTER_PH.md`
2. Write new §1 (research problem & pipeline architecture)
3. Copy §2 from PH Paper §1 (renumber)
4. Copy §3 from PH Paper §2 (renumber, light framing edits)
5. Copy §4 from PH Paper §3 (renumber)
6. Copy + expand §5 from PH Paper §4 (renumber, add §5.3)
7. Write new §6 (system architecture — pipelines, NP encoder, hyperbolic, fusion)
8. Copy §7 from PH Paper §5 (renumber)
9. Copy §8 from PH Paper §7 (renumber)
10. Copy §9 from PH Paper §6 (renumber)
11. Expand §10 from PH Paper §8
12. Write expanded abstract
13. Compile references (existing 40 + new ~8)
14. Full read-through for coherence, cross-references, and LaTeX rendering

---

## Quality Checks

- [ ] Every paragraph traces to PH Paper, Context Doc, or QCF source documents
- [ ] All forward/backward references within the chapter resolve
- [ ] All LaTeX follows GitHub MathJax rules (MEMORY.md)
- [ ] No implementation code — conceptual architecture only
- [ ] No orphaned references
- [ ] Narrative arc reads coherently from §1 through §10 without external documents
- [ ] Existing PH Paper content preserved faithfully
