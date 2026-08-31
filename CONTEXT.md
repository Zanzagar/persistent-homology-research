# Qualia Convergence Framework (Writing Arm)

Framework and writing-side vocabulary for the dissertation's research/writing twin repo.
For the mathematical/TDA and statistical-methodology terms (SEDT, persistence floor, seed
null, MC null, distinguishable, …) see the sibling repo's glossary:
`../persistent-homology/CONTEXT.md` — cross-reference it, do not fork those definitions here.

## Language

### Framework core

**Qualia (operational sense)**:
Used metaphorically and operationalized via the LOGO test — *not* in the philosophical
phenomenology sense. This is the repo's standing gotcha: no phenomenological, semiotic, or
intrinsic-essence claim is made anywhere in the framework.
_Avoid_: qualia as subjective experience, phenomenal character
Source: `CLAUDE.md` (Gotchas); Complete Vision Ch. 4.5 / ADR-009.

**Qualia Convergence Framework (QCF)**:
The dissertation's two-pipeline architecture for geological analog retrieval under sparse
data: Pipeline A catalogues analogs into a geologic index, Pipeline B maps sparse
observations into the same representation space.
_Avoid_: "the framework" in ambiguous contexts, QC framework
Source: `docs/RESEARCH_OVERVIEW.md` Part 1.

**Essence**:
Operationally: multiscale structural invariance independent of generator artifacts —
formally the intersection over generators G of the information about θ captured by a
feature f. Deliberately pragmatist; unique, physics-respecting, observer-independent.
_Avoid_: Platonic form, Aristotelian/intrinsic essence, "true nature"
Source: `docs/RESEARCH_OVERVIEW.md` Parts 1 and 6.

**Sparsity problem**:
The observational limitation motivating everything: wells are dense vertically but sparse
laterally, seismic is broad but coarse, outcrops are geographically constrained — so
complete subsurface structure is never directly observed.
Source: `docs/RESEARCH_OVERVIEW.md` Part 1; `DISSERTATION_OUTLINE.md` §1.

**Pipeline A**:
The cataloguing pipeline: analog data → encode essence → index analogs → geologic index.
Operates on *complete* analogs; PH runs here, never on raw sparse data.
_Avoid_: pathway (see Pathway)
Source: `docs/RESEARCH_OVERVIEW.md` Part 1; `DISSERTATION_OUTLINE.md` §9.1.

**Pipeline B**:
The retrieval pipeline: sparse observations → encode essence (Neural Process query encoder)
→ compare to index → retrieve analog(s). Its essence representation must be compatible with
Pipeline A's, or retrieval is meaningless.
_Avoid_: pathway
Source: `docs/RESEARCH_OVERVIEW.md` Part 1; `DISSERTATION_OUTLINE.md` §9.2.

**Pathway**:
One of the three independent feature-extraction routes whose convergence warrants essence
claims: classical (variographic), learned (DINOv2 + CG-VAE), topological (persistent
homology). A pathway is not a pipeline — pipelines are the A/B system architecture;
pathways are feature extractors used inside them.
_Avoid_: pipeline (for feature extraction), modality (unqualified)
Source: `docs/RESEARCH_OVERVIEW.md` Part 2.

**Geologic index**:
Pipeline A's searchable structural representation of the analog corpus — a tiered
descriptor: core index (Tiers 1–2), extended index (Tier 3), uncertainty envelope (Tier 4 +
aleatoric).
_Avoid_: database, catalog (unqualified)
Source: `docs/RESEARCH_OVERVIEW.md` Parts 1 and 8.

**Principle-based generator**:
The synthetic geological image generator constrained by empirical geomorphological formulas
(Leopold-Wolman, Werner, tidal prism) rather than physics simulation: fast, interpretable,
known ground truth. The experimental apparatus of the dissertation (Pillar I) and primary
training data; distinct from process-based (Flumy) and statistical (MPS) generators, which
serve as LOGO hold-outs.
_Avoid_: simulator, process model
Source: `docs/RESEARCH_OVERVIEW.md` Part 3; `DISSERTATION_OUTLINE.md` §2.

**CG-VAE**:
The supervised identifiable VAE of Li et al. 2025 (arXiv:2503.00639), trained on paired
(image, θ) generator data; its factors are identifiable up to element-wise invertible
transformation, anchoring confidence Tier 1b. Note: originally miscited as "Kong et al." —
the correct first author is Zijian Li.
_Avoid_: Kong et al., "the identifiable VAE" without citing Li
Source: `docs/RESEARCH_OVERVIEW.md` Parts 2 and 9; commit 098aaeb.

**Scene gist**:
The holistic, milliseconds-fast pattern recognition the learned pathway (DINOv2) is meant
to capture — the expert geoscientist's rapid environment categorization (Oliva & Torralba
2006).
Source: `docs/RESEARCH_OVERVIEW.md` Part 2; `DISSERTATION_OUTLINE.md` §5.6.

### Epistemics and validation

**Evidence hierarchy**:
The per-claim ordering of evidence types by epistemic strength, Levels 1a–7: stability
theorem (1a), identifiability theorems (1b), severe adversarial testing (2),
information-theoretic measures (3), cross-domain (4), real-data (5), LOGO (6), expert
agreement (7). Mathematical invariance is the primary anchor; LOGO was demoted to Level 6.
_Avoid_: confidence hierarchy (that is the feature-level structure — see Confidence tier)
Source: `docs/RESEARCH_OVERVIEW.md` Part 4; `DISSERTATION_OUTLINE.md` §8.

**Level 1a / Level 1b**:
The two theorem-backed evidence levels: 1a = PH's stability theorem (protects against
perturbation noise, not against encoding artifacts); 1b = identifiability (protects against
artifact entanglement, not perturbation sensitivity). A feature satisfying both is "doubly
Level 1" — the two-Level-1 structure.
_Avoid_: treating 1a and 1b as interchangeable, "Level 1" without the letter
Source: `docs/RESEARCH_OVERVIEW.md` Part 9; commit 2174f4f.

**Confidence tier**:
The feature-level operationalization of the evidence hierarchy (§14.6): 1-joint (PH ∩
CG-VAE joint component via SLIDE — doubly proven), 1a (PH features), 1b (CG-VAE factors at
MCC ≥ 0.85), 2 (corroborated across ≥3 pathways), 3 (empirically invariant via LOGO), 4
(unique to one pathway). Tiers grade *features*; Levels grade *evidence for claims*.
_Avoid_: conflating tier with level
Source: `docs/RESEARCH_OVERVIEW.md` Part 5; commit cca8049.

**LOGO test**:
Leave-One-Generator-Out: train on N−1 generators, test on the held-out one. Once the
primary essence evidence, now a necessary-condition check at Level 6, reframed under
Unifying CRL (Yao et al. 2025) as a test over an intervention space. It operationalizes the
generator-invariance definition of essence and the operational sense of "qualia".
_Avoid_: cross-validation (unqualified), LOGO as sufficient proof of essence
Source: `docs/RESEARCH_OVERVIEW.md` Parts 4 and 7; `EPISTEMOLOGICAL_OVERHAUL.md`.

**H₁ Hypothesis**:
The central testable claim and linchpin: first-dimensional persistent homology
discriminates braided from meandering channel architectures even when variogram parameters
are matched. Pre-committed thresholds: >70% accuracy confirms; <60% demotes the topological
pathway to an ablation study (ADR-S04).
_Avoid_: softening into "PH helps classification"
Source: `docs/RESEARCH_OVERVIEW.md` Parts 2 and 4; `DISSERTATION_OUTLINE.md` §6.6, §12.2.

**Sākṣī framework**:
The validation framework (Sanskrit "witness"): ten independent witnesses with pre-committed
targets, five geology-specific adversarial tests (Level 2 severe evidence), and the Claim
Survival Matrix. A claim about essence must be validated by an observer independent of the
representation being evaluated.
_Avoid_: "the validation suite" (loses the independence principle), Sakshi without diacritics in formal text
Source: `docs/RESEARCH_OVERVIEW.md` Part 7; `DISSERTATION_OUTLINE.md` §10.

**Claim Survival Matrix**:
The pre-committed mapping from evidence configurations to warranted claims, fixed before
experiments: e.g. L1+L2+L3+L6+L7 passing → "strong" essence claim; L6 alone → "weak";
calibration failure anywhere disqualifies the claim entirely.
Source: `docs/RESEARCH_OVERVIEW.md` Part 7; `DISSERTATION_OUTLINE.md` §10.5.

**Asymmetric trust**:
The framework's novel fusion posture: theorem-backed features (Tiers 1a/1b) and empirically
derived features are not epistemically equivalent, so evidence combination uses
Dempster-Shafer theory (belief/plausibility gaps encode ignorance) instead of symmetric
Bayesian fusion.
Source: `docs/RESEARCH_OVERVIEW.md` Part 5.

**SLIDE decomposition**:
Gaynanova & Li (2019) partition of multi-view features into joint, partially shared, and
individual components — the mechanism that assigns feature dimensions to confidence tiers;
the PH ∩ CG-VAE joint component earns Tier 1-joint.
Source: `docs/RESEARCH_OVERVIEW.md` Part 5.

**Response essence**:
The dynamic extension of essence: the equivalence class of geological configurations
producing topologically equivalent dynamic response — combinatorially equivalent
Morse-Smale decompositions — under a specified stimulus class. Computed via Takens
embedding and PH of reconstructed attractors.
_Avoid_: dynamic essence (older phrasing), response similarity
Source: `docs/RESEARCH_OVERVIEW.md` Part 8; `DISSERTATION_OUTLINE.md` §14.1–14.5.

**Ellipse degradation thought experiment**:
The essence-probing exercise (Hoydic 2026): Variant A occludes features (information
preserved but inaccessible), Variant B erodes them (information destroyed). Its five
identified problems led to redefining essence by generator invariance; the experiment is
reframed as a robustness test, *not* an essence definition.
_Avoid_: citing it as the definition of essence
Source: `docs/RESEARCH_OVERVIEW.md` Part 6; `docs/essence_thought_experiment.pdf`; READING_NOTES Doc 3.

### Writing conventions

**Three-document architecture**:
The rule that only three QCF documents are authoritative — Complete Vision (v5, north
star), Implementation Spec (v6), Architecture Decisions (v1) — per `00_DOCUMENT_INDEX.md`.
Deprecated FINAL/appendix versions exist in `docs/` for history only; never source claims
from them.
_Avoid_: citing `qualia_convergence_FINAL_*.md` or appendix versions
Source: `docs/00_DOCUMENT_INDEX.md`; `CLAUDE.md` (Gotchas).

**§ numbering**:
Bare §N.M references in this repo's docs (also written "SSN.M" in ASCII contexts) point to
`DISSERTATION_OUTLINE.md`'s 15 numbered sections — renumbered when the generator chapter
moved to §2 (commit 495c0aa). Do not confuse with the *sibling repo's* § numbers, which
refer to notebook sections.
_Avoid_: unqualified § references when the target document is ambiguous
Source: `docs/RESEARCH_OVERVIEW.md` (SS-style refs throughout); commit 495c0aa.

**Paste workspace**:
`docs/PASTE_WORKSPACE.md` — the staging document of ready-to-paste writeup paragraphs for
the Word advisor writeup, deliberately kept in LaTeX notation for Word's equation
auto-convert.
Source: commits c8d1dd9, f70b937.

**Stable volumes**:
Obayashi 2023's noise-robust variant of volume-optimal cycles for PH inverse analysis
(identifying which input geometry a birth-death pair corresponds to); implemented in
HomCloud. An open investigation note in READING_NOTES, not yet adopted in the pipeline.
Source: `docs/READING_NOTES.md` Document 15; commit e5dd344 (docs: stable volumes note).

## Unresolved (needs Corey)

- **Sanskrit adversarial-test names** (*Sankhya-maya*, *Rupa-viparyaya*,
  *Nadi-krama-parinama*, *Samya-karana*, *Hetu-vyabhicara*) — the test-to-name mapping is
  clear in `RESEARCH_OVERVIEW.md` Part 7, but the intended literal glosses are not stated
  in-repo; confirm before using the names with translations in the dissertation text.
