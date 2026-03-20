# Epistemological Overhaul: Restructuring the Evidence Hierarchy for Essence Claims

**Author**: Corey James Hoydic
**Date**: February 2026
**Status**: ARCHIVED — Core ideas implemented in `DISSERTATION_OUTLINE.md` §5 (evidence hierarchy) and §10 (confidence hierarchy, response essence, uncertainty quantification). This document is retained for historical reference only. The dissertation chapter is now the authoritative source.

---

## 1. The Problem: LOGO Is Necessary but Not Sufficient

### 1.1 The Original Framework's Position

The Qualia Convergence Framework (QCF) currently positions the Leave-One-Generator-Out (LOGO) test as the **primary evidence** for generator invariance (ADR-008). The claim structure is:

> If a representation passes LOGO (< 20% degradation across all held-out generators), then it captures **generator-invariant structure**, which operationally defines **essence**.

### 1.2 Why This Is Epistemically Insufficient

The LOGO test has a fundamental limitation that can be stated precisely:

> **LOGO tests invariance within a generator family, not invariance to the underlying geology.**

This is not a minor caveat — it is a structural limitation analogous to known impossibility results in causal representation learning. The argument has three independent threads:

#### Thread 1: The Impossibility Result (Formal)

Ahuja et al. (2023), "Invariance & Causal Representation Learning: Prospects and Limitations" (arXiv:2312.03580), proved that **invariance alone is insufficient to identify latent causal variables**. Even with multiple environments (in our case, generators), without additional structural constraints, you cannot guarantee that learned invariant features correspond to the causal structure of the data-generating process.

**Translation to QCF**: Passing LOGO across 4 generators does not prove that the invariant features capture geological essence. They might capture features invariant to a shared assumption space (e.g., all generators parameterize the Leopold-Wolman relationship, so invariance to generators is really invariance to that parameterization).

#### Thread 2: The Environment Diversity Problem (Statistical)

Invariant Risk Minimization (IRM; Arjovsky et al., 2019) — the most studied invariant learning framework — has been shown to:

- **Fail catastrophically** in nonlinear settings (Rosenfeld et al., 2021, "The Risks of Invariant Risk Minimization")
- Require an **impractically large number of environments** for guarantees
- Be **sensitive to environment diversity** — not just count, but genuine independence

**Translation to QCF**: Adding more generators from the same family (process-based, rule-based, MPS-based) does not fix the problem if they share physical assumptions. You need generators built on **fundamentally different** assumptions — or better yet, real geological data that no generator was designed to reproduce.

#### Thread 3: The Independence Condition (Philosophical)

Wimsatt's robustness analysis (1981) and Weisberg's formalization (2006) established that convergent results from multiple models provide evidence **only if the models are genuinely independent**. Failure of independence produces **illusory robustness**.

Orzack & Sober's critique: robustness analysis is "nonempirical confirmation, effective only under unusual circumstances" — specifically, when model independence can be verified.

**Translation to QCF**: The three pathways (Classical, Learned, Topological) are methodologically independent, which is good. But the generators used in LOGO are **not** independent in the relevant sense — they all attempt to model the same physical processes with similar constraints. "Invariance across generators" may therefore be weaker evidence than the framework claims.

### 1.3 The Degrees-of-Freedom Concern

The user's original intuition: "defining invariance this way creates the same problem that generative models with transformers and diffusion give — basically getting infinite degrees of freedom on a dataset."

This maps onto a known problem in statistics: with sufficient model capacity, you can always find a representation that appears invariant across your training environments while failing to generalize. In the LOGO context:

- If the generator pool is small (4 generators), the representation can overfit to "what these 4 generators agree on" without capturing geology
- If the generator pool is large but homogeneous (many generators, same physical assumptions), invariance is trivial
- If the generator pool is adversarially designed to make LOGO easy, we've engineered our validation

The only escape is either:
1. **Mathematical proof** of invariance (not empirical)
2. **Severe testing** designed to *break* invariance (not confirm it)
3. **Real-data validation** that no generator was designed for
4. **Cross-domain validation** that transcends the generator concept entirely

---

## 2. The Restructured Evidence Hierarchy

### 2.1 New Hierarchy (Strongest → Weakest)

| Rank | Evidence Type | Epistemic Character | Applies To | Status in QCF |
|------|---|---|---|---|
| **1** | Mathematical invariance theorems | Formal proof — no empirical uncertainty | Topological pathway (PH stability theorem) | Mentioned but not foregrounded |
| **2** | Severe adversarial testing | Empirical — designed to break claims | All pathways | Partially exists (Ch. 23) but not systematic |
| **3** | Information-theoretic measures | Formal + empirical hybrid | All pathways | **NEW — not in framework** |
| **4** | Cross-domain validation | Empirical — transcends generator concept | Topological pathway | **NEW — not in framework** |
| **5** | Real-data validation | Empirical — generator-independent benchmark | All pathways | Acknowledged as future work |
| **6** | LOGO across generators | Empirical — bounded by generator diversity | All pathways | Currently primary; **demoted** |
| **7** | Expert agreement | Empirical — independent but subjective | All pathways | One of 10 Sākṣī witnesses |

### 2.2 Detailed Description of Each Level

#### Level 1: Mathematical Invariance Theorems

The stability theorem of Cohen-Steiner, Edelsbrunner, and Harer (2007):

$$d_B(\text{Dgm}(f), \text{Dgm}(g)) \leq \|f - g\|_\infty$$

This is a **mathematical proof** that persistent homology features are invariant under bounded perturbations. Key properties:

- **Does not depend on generators** — it's a property of the mathematical structure of PH
- **Quantifies the invariance bound** — not just "invariant" but "invariant within this epsilon"
- **Applies to any input** — geological, musical, neural, or otherwise
- **Cannot be "overengineered"** — it's a theorem, not a test

**Limitation**: The stability theorem guarantees invariance of *topological* features, but doesn't guarantee those features are the *right* features for capturing geological essence. You could have perfectly stable features that are irrelevant.

**Resolution**: The H₁ hypothesis connects stability to relevance — if H₁ features discriminate channel architectures AND are provably stable, then we have both relevance and invariance.

#### Level 2: Severe Adversarial Testing

Following Mayo's severe testing framework: a claim passes a severe test if the test was **highly capable of detecting failure** had the claim been false.

**Current QCF adversarial tests** (Ch. 23):
- Variogram-matched topology swap
- Style transfer attack
- Channel skeleton permutation
- Histogram equalization

**Proposed additions for severity**:
- **Adversarial generator design**: Construct a generator specifically designed to produce images where topological features are misleading (e.g., matched H₁ but different geological process)
- **Feature disentanglement attack**: Test whether H₁ features can be manipulated independently of geological meaning
- **Noise injection at critical scales**: Add noise specifically at scales where the filtration creates/destroys H₁ features

The key shift: **design tests to break the claim, not confirm it.** If the claim survives, that's severe evidence.

#### Level 3: Information-Theoretic Measures

Quantify what the representation captures using mutual information:

- $I(f(X); \theta \mid G)$ — mutual information between representation $f(X)$ and geological parameters $\theta$, conditioned on generator $G$. High values → representation captures generator-invariant geological information.
- $I(f(X); G \mid \theta)$ — mutual information between representation and generator identity, conditioned on geological parameters. Low values → representation doesn't capture generator artifacts.

**Why this helps**: Information-theoretic measures provide a continuous, quantitative assessment rather than a binary pass/fail. They decompose exactly *what* the representation captures and what it ignores.

**Practical implementation**: Use MINE (Mutual Information Neural Estimation) or similar variational bounds to estimate these quantities from finite samples.

#### Level 4: Cross-Domain Validation

If the same topological features that distinguish geological environments also distinguish structurally analogous patterns in:
- **Music**: Harmonic structure (Bergomi et al., 2016; Alcalá-Alvarez & Padilla-Longoria, 2022)
- **Neuroscience**: Brain connectivity patterns (Giusti, Ghrist, & Bassett, 2016)
- **Other structured domains**

...then the invariance is a property of the **mathematics**, not of the **generators**. This provides evidence that transcends the generator concept entirely.

#### Level 5: Real-Data Validation

Validate against real geological data (well logs, seismic, outcrop photos) that no generator was designed to reproduce. This is the ultimate test of generator-independence, but requires data that may not be available in early phases.

#### Level 6: LOGO (Demoted)

LOGO remains a useful **necessary condition** check:
- If LOGO fails → representation is generator-specific → not essence
- If LOGO passes → representation is invariant within the generator family → *necessary but not sufficient* for essence

**Explicit limitations to document**:
1. LOGO only tests invariance within the generator pool — not beyond it
2. Generator diversity is hard to verify (independence condition)
3. Passing LOGO with N generators provides weaker evidence than mathematical proof
4. The number of generators needed for statistical guarantees may be impractical (IRM impossibility)

#### Level 7: Expert Agreement

Human expert judgment (Cohen's κ) remains valuable as the only **truly generator-independent** witness — experts judge geological similarity based on experience, not on any computational pipeline. However, expert agreement is subjective and may reflect shared training biases.

---

## 3. Operationalizing the Hierarchy: From Evidence Levels to Feature-Level Confidence

### 3.1 The Gap: Evidence Levels Are Abstract; Features Are Concrete

The 7-level evidence hierarchy (§2) tells us *which kinds of evidence are epistemically stronger*. But when the three-pathway architecture produces a concrete feature vector for an analog image — 20–50 PH dimensions, ~50 geostatistical dimensions, 768 DINOv2 dimensions — the evidence hierarchy alone does not tell us *which feature dimensions to trust* or *how much weight each should receive* in retrieval. We need a mechanism that maps the abstract evidence hierarchy onto concrete, per-feature confidence assignments.

### 3.2 The Confidence Hierarchy (Tiers 1–4)

The dissertation chapter (§10.6) develops a four-tier confidence hierarchy that operationalizes the evidence levels at the feature level:

| Tier | Source | Epistemic Basis | Invariance Guarantee |
|------|--------|----------------|---------------------|
| **1 — Proven** | PH features | Stability theorem (Level 1 evidence) | Mathematical proof |
| **2 — Corroborated** | Joint components across all three pathways | Cross-pathway convergence (Levels 1 + 6) | Strong empirical + partial theoretical |
| **3 — Empirically invariant** | Features passing LOGO but low alignment with PH | Empirical testing (Level 6) | LOGO-validated but no theoretical backing |
| **4 — Uncertain** | Unique to one pathway, no cross-pathway support | Single-source | No cross-validation |

**How the tiers map to evidence levels:**
- Tier 1 derives from **Level 1** (mathematical invariance) — only PH features qualify
- Tier 2 derives from **Level 6** (LOGO/cross-generator) corroborated by **Level 1** — features where empirical and mathematical evidence converge
- Tier 3 derives from **Level 6** alone — LOGO passes but no mathematical backing
- Tier 4 has no evidence level support — these are hypothesis-generating, not hypothesis-confirming

### 3.3 The Asymmetric Trust Structure: A Novel Contribution

No prior work in multi-modal feature fusion exploits the epistemic asymmetry between theorem-backed and empirically derived features. Standard fusion approaches — early fusion, late fusion, attention-based fusion — treat all feature sources as epistemically equivalent: each contributes information, and the model learns to weight them. But when one source (PH) has *provable* invariance guarantees and others do not, symmetric treatment is epistemically inappropriate.

This asymmetric trust structure is operationalized through three mechanisms:

1. **Cross-pathway alignment measurement** via Centered Kernel Alignment (CKA; Kornblith et al., 2019). Williams et al. (2024) proved CKA, RSA, and CCA are mathematically equivalent — they measure the same underlying alignment. CKA is preferred for its robustness to dimensionality mismatch (PH: 20–50d vs. DINOv2: 768d).

2. **SLIDE decomposition** (Gaynanova & Li, 2019) partitions multi-view features into joint (shared by all pathways), partially shared (pairwise), and individual (unique to one pathway) components. This directly assigns each feature dimension to a tier.

3. **Dempster-Shafer Theory (DST)** for evidence combination with asymmetric reliability. Unlike Bayesian fusion (which treats sources symmetrically via likelihoods), DST encodes *ignorance* via the gap between belief and plausibility functions. Tier 1 features have narrow gaps (high confidence); Tier 4 features have wide gaps (high ignorance). Dempster's rule combines these into a unified belief structure that appropriately weights mathematical evidence over empirical evidence.

### 3.4 Extension to Response Essence

The original evidence hierarchy applies to *structural* essence — the invariant spatial pattern. The dissertation chapter (§10.1–10.5) extends the essence concept to *response essence*: the equivalence class of geological configurations producing topologically equivalent dynamic response under stimulation.

**Response essence** is defined formally via Morse-Smale decomposition of the basin-of-attraction structure. Two geological configurations share response essence if their dynamical systems have combinatorially equivalent Morse-Smale decompositions.

This extension has a critical implication for the evidence hierarchy: it introduces a **new validation criterion** for the entire retrieval system. Analogs retrieved by Pipeline B (on the basis of structural similarity) should produce similar dynamic responses when simulated. If structural retrieval predicts response similarity, the evidence hierarchy is validated at the deepest possible level — the structural invariants that organize the repository are *causally connected* to the dynamic behavior that the repository exists to predict.

### 3.5 Uncertainty Quantification from Feature Residuals

The SLIDE decomposition produces not only confidence-tiered features but also *residual* features — components of DINOv2's representation not aligned with PH. Rather than discarding these as noise, DeCUR (Wang et al., 2024) proves that unique (non-shared) components of self-supervised representations carry meaningful information. The pipeline:

1. DeCUR separates DINOv2 into PH-aligned and PH-residual components
2. Kotelevskii et al. (2025) decompose residual uncertainty into aleatoric (intra-class variability) and epistemic (data sparsity) per feature dimension
3. Hedged instance embeddings (Oh et al., 2019) represent each analog as a distribution $\mathcal{N}(\mu, \Sigma)$ rather than a point
4. Retrieval uses uncertainty-weighted similarity that downweights high-uncertainty dimensions

This transforms Pipeline A from storing analogs as point estimates to storing analogs *with calibrated confidence about what is known and unknown* — directly implementing the epistemic humility that the evidence hierarchy demands.

---

## 4. Specific Changes to Each Document

### 4.1 Changes to COMPLETE_VISION_v5.md

| Section | Change | Rationale |
|---------|--------|-----------|
| Ch. 4 (Operationalizing Essence) | Add subsection 4.6 "Epistemic Limitations of Operational Invariance" acknowledging that empirical invariance testing has known theoretical bounds | Honest about LOGO's reach |
| Ch. 4 (Operationalizing Essence) | Add subsection 4.7 "Mathematical Invariance as Primary Evidence" foregrounding the stability theorem | Restructured evidence hierarchy |
| Ch. 22 (LOGO Protocol) | Add section 22.4 "Limitations and Epistemic Scope" with explicit discussion of impossibility results, environment diversity, independence condition | Currently no limitations section |
| Ch. 22 (LOGO Protocol) | Revise section 22.1 to position LOGO as "necessary but not sufficient" | Currently positioned as primary |
| Ch. 23 (Adversarial Tests) | Add severity assessment to each test; add new adversarial tests designed to break (not just challenge) the topological pathway | Currently adversarial but not "severe" in Mayo's sense |
| Ch. 24 (Claim Survival Matrix) | Add rows for mathematical invariance and severe testing outcomes; revise interpretations to reflect multi-level evidence | Currently based primarily on LOGO |
| New Chapter | "Evidence Hierarchy for Essence Claims" — the restructured hierarchy with all 7 levels | Does not currently exist |
| TDA sections | Foreground stability theorem as the topological pathway's primary invariance guarantee, ahead of LOGO | Currently stability is background justification |

### 4.2 Changes to ARCHITECTURE_DECISIONS_v1.md

| ADR | Change | Rationale |
|-----|--------|-----------|
| ADR-008 (LOGO) | Add "Limitations" section citing impossibility results; revise "Rationale" to position LOGO as necessary-but-insufficient | Currently no limitations |
| New ADR-012 | "Mathematical Invariance as Primary Evidence" — decision to foreground PH stability theorem over empirical LOGO for topological pathway | New architectural decision |
| New ADR-013 | "Severe Testing Protocol" — decision to design adversarial tests for severity (Mayo), not just challenge | New architectural decision |
| New ADR-014 | "Information-Theoretic Validation" — decision to add MI-based assessment of what representations capture | New architectural decision |
| ADR-S04 (TDA as Ablation) | Update to reflect that TDA has *mathematical* invariance guarantees (stability theorem) that other pathways lack — strongest candidate for promotion from ablation to core | Currently frames TDA as unvalidated |
| Open Questions | Add: "How do we verify generator independence for LOGO?" and "What information-theoretic threshold distinguishes essence from artifact?" | Currently missing these questions |

### 4.3 Changes to IMPLEMENTATION_SPEC_v6.md

| Section | Change | Rationale |
|---------|--------|-----------|
| Phase 2 (TDA) | Add step: compute and report stability bounds for topological features | Currently just computes PH; doesn't exploit stability theorem |
| Phase 3 (Validation) | Restructure validation order: (1) mathematical invariance check, (2) severe testing, (3) LOGO, (4) information-theoretic measures | Currently LOGO-first |
| Decision Point 3.3 | Revise: LOGO pass alone insufficient for strong invariance claim; require corroboration from severity and/or mathematical invariance | Currently LOGO alone determines outcome |
| New section | "Severe Testing Protocol" — implementation details for adversarial generator construction and severity assessment | Does not exist |
| New section | "Information-Theoretic Validation" — MINE-based MI estimation implementation | Does not exist |

---

## 5. Impact on the Persistent Homology Chapter

The dissertation chapter (`DISSERTATION_OUTLINE.md`) has been substantially updated to reflect the restructured framework:

1. **Section 5 (Evidence Hierarchy)**: Restructured evidence hierarchy is fully developed, with mathematical invariance as Level 1 and LOGO demoted to Level 6
2. **Section 9 (Open Questions)**: Expanded to cover philosophical robustness of invariance, multi-parameter persistence, topological dictionary learning, and information-theoretic quantification
3. **Section 7**: Cross-domain validation (music, neuroscience) as evidence for mathematical universality
4. **Section 10 (NEW — Extensions)**: Three major extensions now implemented:
   - §10.1–10.5: Response essence via dynamical systems (Morse-Smale decomposition, Takens embedding, formation dynamics as attractors)
   - §10.6: Confidence hierarchy operationalizing the evidence levels via SLIDE, CKA, and DST
   - §10.7: Uncertainty quantification from feature residuals via DeCUR and aleatoric/epistemic decomposition
   - §10.8: Concrete implications for the two-pipeline architecture (tiered indexing, uncertainty-weighted retrieval)
5. **Tone**: "Mathematical structure provides the strongest evidence; empirical testing provides corroboration; honest acknowledgment of what remains unresolved"

### What Remains to Implement in the QCF Core Documents

The following changes from §4 above have NOT yet been made to the QCF source documents (Vision v5, Architecture Decisions v1, Implementation Spec v6). They remain as planned changes:

- New ADRs (012–014) for mathematical invariance, severe testing, and information-theoretic validation
- LOGO limitations section in Chapter 22
- Severity assessment additions to Chapter 23
- Restructured validation order in Implementation Spec Phase 3
- New evidence hierarchy chapter in Vision document

---

## 6. Key References for the Overhaul

### Impossibility Results and Causal Invariance
- Ahuja, K., Hartford, J., & Bengio, Y. (2023). Invariance & Causal Representation Learning: Prospects and Limitations. arXiv:2312.03580.
- Arjovsky, M., Bottou, L., Gulrajani, I., & Lopez-Paz, D. (2019). Invariant Risk Minimization. arXiv:1907.02893.
- Rosenfeld, E., Ravikumar, P., & Risteski, A. (2021). The Risks of Invariant Risk Minimization. ICLR.

### Philosophy of Science
- Wimsatt, W. C. (1981). Robustness, Reliability, and Overdetermination. In *Scientific Inquiry and the Social Sciences*, ed. Brewer & Collins.
- Weisberg, M. (2006). Robustness Analysis. *Philosophy of Science*, 73(5), 730–742.
- Mayo, D. G. (2018). *Statistical Inference as Severe Testing: How to Get Beyond the Statistics Wars*. Cambridge University Press.
- Popper, K. (1963). *Conjectures and Refutations*. Routledge.
- Orzack, S. H., & Sober, E. (1993). A Critical Assessment of Levins's "The Strategy of Model Building in Population Biology." *Quarterly Review of Biology*, 68(4), 533–546.

### Mathematical Invariance
- Cohen-Steiner, D., Edelsbrunner, H., & Harer, J. (2007). Stability of Persistence Diagrams. *Discrete & Computational Geometry*, 37(1), 103–120.
- Chazal, F., de Silva, V., Glisse, M., & Oudot, S. (2016). *The Structure and Stability of Persistence Modules*. Springer.

### Information Theory
- Belghazi, M. I., et al. (2018). Mutual Information Neural Estimation. ICML.

### Cross-Pathway Alignment and Decomposition
- Kornblith, S., Norouzi, M., Lee, H., & Hinton, G. (2019). Similarity of neural network representations revisited. ICML. arXiv:1905.00414.
- Williams, A. H., Kunz, E., Kornblith, S., & Linderman, S. W. (2024). Generalized shape metrics on neural representations. Nature Machine Intelligence, 6, 100–113.
- Gaynanova, I., & Li, G. (2019). Structural learning and integrative decomposition of multi-view data. Biometrics, 75(4), 1121–1132.
- Kriegeskorte, N., Mur, M., & Bandettini, P. (2008). Representational similarity analysis. Frontiers in Systems Neuroscience, 2, Article 4.

### Confidence Hierarchy and Uncertainty
- Kendall, A., & Gal, Y. (2017). What uncertainties do we need in Bayesian deep learning for computer vision? NeurIPS.
- Kotelevskii, N., et al. (2025). Uncertainty decomposition in feature space without ensembles. arXiv:2511.12389.
- Wang, Z., et al. (2024). DeCUR: Decoupling common and unique representations for multiview self-supervised learning. ECCV. arXiv:2309.05300.
- Oh, S., et al. (2019). Hedged instance embedding. ICLR. arXiv:1810.00319.
- Scheidt, C., Li, L., & Caers, J. (2018). Quantifying Uncertainty in Subsurface Systems. Wiley/AGU.

### Dynamical Systems and Response Essence
- Conley, C. (1978). Isolated Invariant Sets and the Morse Index. AMS.
- Kramar, M., et al. (2016). Analysis of Kolmogorov flow and Rayleigh-Bénard convection using persistent homology. Physica D, 334, 82–98.
- He, Q., et al. (2023). Koopman operator-based model reduction for reservoir simulation. SPE Journal, 28(4), 2024–2040.
- Takens, F. (1981). Detecting strange attractors in turbulence. Lecture Notes in Mathematics, 898, 366–381.

---

## 7. Summary: What Changes and What Stays

### What Changes
- LOGO demoted from primary to necessary-but-insufficient evidence
- Mathematical invariance (stability theorem) promoted to primary evidence for topological pathway
- New evidence levels added: severe testing, information-theoretic measures, cross-domain validation
- Explicit acknowledgment of impossibility results and independence conditions
- The *tone* of the essence claim: from "LOGO validates essence" to "mathematical + empirical + philosophical evidence converges, with honest limitations"
- **NEW**: Confidence hierarchy (Tiers 1–4) operationalizes the evidence levels at the feature level via SLIDE, CKA, and DST
- **NEW**: Essence concept extended from structural invariance to response essence via dynamical systems (Morse-Smale decomposition of basin-of-attraction topology)
- **NEW**: Uncertainty quantification pipeline transforms feature residuals into calibrated aleatoric/epistemic uncertainty via DeCUR decomposition
- **NEW**: Pipeline A stores analogs with tiered confidence and uncertainty envelopes, not flat feature vectors

### What Stays
- Three-pathway architecture (ADR-001) — this is about method independence, not generator independence
- Hyperbolic embedding (ADR-002) — unchanged
- Cubical complexes for geological images — unchanged
- H₁ hypothesis — unchanged (if anything, strengthened by stability theorem emphasis)
- Sākṣī validation philosophy — enhanced, not replaced
- LOGO test itself — still run, just interpreted differently
- Expert validation — still essential, possibly elevated

### The Key Philosophical Shift
**Before**: "We define essence operationally as what passes LOGO."
**After**: "We define essence operationally as what satisfies a convergence of evidence: mathematical invariance guarantees, survival of severe testing, information-theoretic confirmation of content, cross-domain universality, generator-independence (LOGO), and expert agreement. No single test is sufficient; the convergence of independent evidence streams is the warrant for the claim. The confidence hierarchy provides the mechanism for translating this convergence into concrete, per-feature trust levels — with Dempster-Shafer Theory handling the asymmetric reliability that the stability theorem creates between PH and other pathways."

**The deepest extension**: Essence is no longer limited to static structure. Response essence — defined via the topology of basins of attraction — extends the framework to dynamic behavior. If structural retrieval predicts response similarity, the evidence hierarchy is validated at its deepest possible level: the invariants that organize the repository are causally connected to the outcomes the repository exists to predict.

This is both more honest and more powerful than the original position.
