# Research Overview: The Qualia Convergence Framework

### Persistent Homology and Multi-Pathway Essence Determination for Geological Analog Retrieval

**Corey James Hoydic** | Dissertation Research | April 2026

---

## Part 1 -- The Research Problem

Accurate prediction of subsurface geological response to natural and anthropogenic stimuli requires spatial models that faithfully represent multiscale geological variability -- from the connectivity of individual channel bodies at the meter scale to the organization of depositional systems at the kilometer scale. The observational basis for constructing such models is inherently limited: well logs provide high-resolution but spatially sparse vertical profiles, seismic surveys offer broad spatial coverage at reduced resolution, and outcrop observations are geographically constrained. This is the *sparsity problem*.

The natural counterpart to sparsity is the abundance of analog information. Vast repositories of geological analogs exist -- process-based simulations, object-based models, training images from multiple-point geostatistics, real outcrop databases, and interpreted seismic volumes. The challenge is not availability but *selection*: given sparse observations of a target reservoir, which analogs faithfully represent the essential structural properties of the subsurface? Currently, analog selection remains largely subjective and expertise-driven -- difficult to reproduce and lacking principled uncertainty quantification.

The **Qualia Convergence Framework (QCF)** addresses this with a two-pipeline architecture:

- **Pipeline A (Cataloguing)** transforms heterogeneous analog artifacts into a searchable structural representation: analog data $\to$ encode essence $\to$ index analogs $\to$ geologic index.
- **Pipeline B (Retrieval)** maps sparse, incomplete field observations into the same representation space: sparse observations $\to$ encode essence $\to$ compare to index $\to$ retrieve analog(s).

The core coupling requirement is that the essence representation used in Pipeline A must be compatible with the essence representation inferred from sparse data in Pipeline B. Without this compatibility, retrieval is meaningless.

The enabling abstraction connecting both pipelines is **essence** -- defined operationally as *multiscale structural invariance independent of generator artifacts*. This definition is deliberately operational rather than metaphysical, following the pragmatist tradition of Peirce, James, and Dewey. No claim is made about Platonic forms or Aristotelian essences. The claim is that if a structural descriptor remains invariant across multiple independent generative processes, multiple observation modalities, and multiple representational pathways, it has earned the designation "essence" for the practical purposes of analog retrieval. The term "qualia" in the framework's name is used metaphorically (operationalized via the LOGO test), not in the philosophical phenomenology sense.

---

## Part 2 -- The Three-Pathway Architecture

The QCF employs three independent feature-extraction pathways, each representing a distinct epistemological perspective on geological structure. Their convergence provides the epistemic warrant for essence claims.

### Classical Pathway: Variographic Indexing

The classical pathway computes traditional geostatistical descriptors -- directional variograms, fractal dimensions, connectivity functions, facies proportions -- yielding approximately 50 dimensions of features that encode spatial correlation structure. Every feature has a direct physical interpretation: the variogram range quantifies spatial correlation length, the anisotropy ratio characterizes directional fabric, and the fractal dimension quantifies multiscale roughness. The pathway's primary advantage is computational transparency and decades of established theory (Matheron, 1963; Chiles and Delfiner, 2012).

The classical pathway's fundamental limitation is *topological blindness*: variograms measure spatial correlation but are provably insensitive to connectivity topology (see SS4.4 of the dissertation). A braided system with many interconnected channels and a meandering system with a single sinuous channel can produce matching two-point statistics when their spatial correlation lengths coincide. No refinement of classical features can overcome this -- the relevant information (loop topology) is fundamentally higher-order.

### Learned Pathway: Scene Gist and Holistic Pattern Encoding

The learned pathway uses DINOv2-ViT-B/14, a self-supervised vision transformer, with LoRA fine-tuning (Hu et al., 2022) on geological imagery to extract 768-dimensional feature vectors. These capture the holistic "scene gist" -- the rapid, holistic pattern recognition that allows experienced geoscientists to categorize a depositional environment within milliseconds (Oliva and Torralba, 2006). The pathway is intentionally opaque: individual DINOv2 dimensions have no straightforward geological interpretation, but the representations are demonstrably linearly separable for semantic categories across diverse visual domains (Oquab et al., 2023).

The learned pathway lacks formal invariance guarantees -- its features depend on the training data distribution and model architecture. In the confidence hierarchy (SS14.6), DINOv2 residuals enter at Tier 3--4. However, the pathway captures information that neither variograms nor PH compute: texture gradients, facies boundary sharpness, spatial frequency content, and bar morphology.

A critical addition to the learned pathway is **CG-VAE** (Li et al., 2025), a supervised identifiable variational autoencoder trained on paired $(I, \theta)$ data from the principle-based generator. CG-VAE provides theorem-backed identifiability: its learned factors are identifiable up to element-wise invertible transformation against true generative factors. CG-VAE identified factors enter at Tier 1b of the confidence hierarchy, complementing PH at Tier 1a. DINOv2 and CG-VAE are not alternatives but complements with distinct epistemic roles within the learned pathway (see SS6.5).

### Topological Pathway: Persistent Homology

The topological pathway computes persistent homology in dimensions $H_0$ (connected components) and $H_1$ (loops) via Giotto-TDA (Tauzin et al., 2021), producing approximately 20--50 dimensions of topological features. The pathway operates specifically on binary facies images via cubical complexes with a signed Euclidean distance transform (SEDT) filtration (Robins et al., 2016). The SEDT assigns each pixel a signed distance to the nearest facies boundary, providing a geologically meaningful filtration where thick channel cores receive high positive values and thin connections receive values near zero.

The topological pathway's unique strength is the **stability theorem** (Cohen-Steiner, Edelsbrunner, and Harer, 2007):

$$d_B\bigl(\textrm{Dgm}(f), \textrm{Dgm}(g)\bigr) \leq \lVert f - g \rVert_\infty$$

This is a mathematical proof that persistence diagrams are Lipschitz-continuous functions of the input -- a formal invariance guarantee that does not depend on which generators are tested or how many experiments are run. Stability places the topological pathway at Level 1a of the evidence hierarchy.

The central testable hypothesis is the **$H_1$ Hypothesis**: first-dimensional persistent homology discriminates braided from meandering channel architectures even when variogram parameters are matched. Braided systems should exhibit many persistent $H_1$ features (loops around unfilled floodplain islands); meandering systems should exhibit few. Together, stability (mathematical invariance) and the $H_1$ experiment (geological relevance) provide a two-level evidential warrant that no single method provides. Pre-committed thresholds: >70% accuracy on variogram-matched pairs confirms $H_1$; <60% demotes TDA to an ablation study (ADR-S04).

### Why Three Pathways?

The three pathways' failures are *non-overlapping*: the classical pathway fails when topological structure diverges from correlation structure; the topological pathway fails when geological differences are purely metric (two braided systems with different channel widths but identical loop topology); the learned pathway captures both but with no guarantee that any specific feature is geologically meaningful. This complementarity -- not redundancy -- is the architectural rationale.

Fusion is governed by a **convergence regularization loss**:

$$L_{\textrm{conv}} = \sum_{i < j} \lVert f_i(x) - f_j(x) \rVert^2$$

When the three pathways converge, uncertainty is low. When they disagree, the system signals ambiguity. The fused representation is projected into a hyperbolic embedding space (Poincare ball model; Nickel and Kiela, 2017), where hierarchical organization of depositional environments is naturally encoded -- general categories near the origin, specific sub-types near the boundary.

---

## Part 3 -- The Generator (Pillar I)

### Why Build a Generator?

The principle-based generator is not merely a data source -- it is the experimental apparatus that makes the entire framework testable. Without controlled generation (images whose structural properties are known by construction), the demands for cross-generator invariance testing (Level 6), severe adversarial testing (Level 2), and the $H_1$ experiment all remain abstract aspirations rather than executable protocols. Known ground truth is essential for the LOGO test: when a generated image has specified parameters (sinuosity $S = 1.8$, wavelength $\lambda = 12W$, bankfull width $W = 15$ pixels), we know exactly what structural properties it should exhibit.

### Generator Taxonomy

The generator occupies a deliberate epistemic position among three approaches:

| Approach | Key Property | Role in Framework |
|---|---|---|
| **Process-based** (Flumy, BRAHMS) | Highest fidelity; solves governing PDEs | Held-out generator in LOGO test |
| **Statistical** (MPS/SNESIM) | Reproduces spatial patterns from training images | Additional LOGO generator |
| **Principle-based** (this work) | Fast, interpretable, known ground truth | Primary training data |

The design philosophy: *constrain geometry with empirical formulas from the literature, not with physics simulation*. The generator directly implements geometric relationships that governing equations produce at equilibrium -- relationships measured, validated, and published by geomorphologists over decades.

### Three Depositional Environments

**Fluvial** environments implement the Leopold-Wolman (1957) framework, producing meandering (sinuosity $S \in [1.3, 2.5]$, wavelength $\lambda = kW$ with $k \in [10, 14]$, curvature $R_c = mW$ with $m \in [2, 3]$), braided (bifurcation spacing $\Delta x_{\textrm{bif}} = 4$--$5W$, width-to-depth $W/d > 50$), and anastomosing (low-sinuosity $S \in [1.0, 1.3]$, avulsion-driven splitting, 60--90% wetland) architectures.

**Aeolian** environments implement the Werner (1995) cellular automaton framework, producing barchan (crescent-shaped, unidirectional wind), linear/seif (bidirectional wind, high ridge continuity $C_{\textrm{ridge}} \geq 0.7$), and transverse (strong unidirectional wind, crest-parallel ridges) dune morphologies.

**Estuarine** environments implement tidal prism relationships informed by Jiwei et al. (2025), producing tide-dominated (ebb-flood channel pairs, tidal bars), wave-dominated (shoreface-parallel bars, smooth shoreline), and mixed-energy configurations with a tunable dominance slider $\delta \in [0, 1]$.

This three-environment, nine-substyle design provides the morphological diversity required for meaningful cross-environment testing: if PH features trained on fluvial systems transfer to aeolian and estuarine systems, the argument for mathematical universality is substantiated empirically.

---

## Part 4 -- The Evidence Hierarchy

The evidence hierarchy is organized by epistemic strength, from mathematical proof at the top to empirical agreement at the bottom. The convergence of multiple levels provides warranted confidence for essence claims (see SS8 of the dissertation).

| Level | Evidence Type | What It Provides |
|---|---|---|
| **1a** | Stability theorem (Cohen-Steiner et al., 2007) | Mathematical proof: $d_B(\textrm{Dgm}(f), \textrm{Dgm}(g)) \leq \lVert f - g \rVert_\infty$. Protects PH from perturbation noise. |
| **1b** | Identifiability theorems (Khemakhem et al., 2020; Li et al., 2025) | Mathematical proof: learned latents recover true generative factors up to invertible equivalence. Protects learned features from recovering artifact mixtures. |
| **2** | Severe adversarial testing (Mayo, 2018) | Tests designed to *break* invariance claims, not merely challenge them. Five adversarial tests in the Sakshi battery. |
| **3** | Information-theoretic measures | $I(f(X); \theta \mid G)$ for geological content; $I(f(X); G \mid \theta)$ for artifact contamination. |
| **4** | Cross-domain validation | Same PH machinery applied to music, neuroscience, other domains (SS11). |
| **5** | Real-data validation | Testing against field data no generator was designed to reproduce. |
| **6** | Cross-generator validation (LOGO) | Training on $N - 1$ generators, testing on held-out. Necessary but not sufficient. |
| **7** | Expert agreement | Human judgment (Cohen's $\kappa$). Truly generator-independent but subjective. |

### Why LOGO Was Demoted

LOGO was originally the primary evidence for essence. Three independent theoretical results constrain what cross-generator validation can establish:

1. **Ahuja et al. (2023)** proved that invariance alone is insufficient to identify latent causal variables -- passing LOGO across $N$ generators does not prove features capture geological causes rather than shared generator assumptions.
2. **IRM failures** (Arjovsky et al., 2019; Rosenfeld et al., 2021) demonstrated catastrophic failures in nonlinear settings, requiring impractically many environments for formal guarantees.
3. **Wimsatt's independence condition** (1981; Orzack and Sober, 1993) established that convergent results from multiple models provide evidence only if the models are genuinely independent.

LOGO remains a useful necessary-condition check (Level 6), but mathematical invariance (Level 1a--1b) is now the primary evidence anchor. This epistemological restructuring is documented in `EPISTEMOLOGICAL_OVERHAUL.md`.

### The $H_1$ Experiment as Linchpin

The $H_1$ experiment occupies a critical epistemic position. If PH features cannot discriminate braided from meandering architectures on variogram-matched pairs, then Level 1a's mathematical guarantee becomes actively misleading -- certifying the robustness of features encoding no geological content. The hierarchy, designed to privilege mathematical invariance over empirical testing, would privilege precisely the wrong signals. This is why pre-committed decision thresholds exist: below 60% classification accuracy, the topological pathway is demoted regardless of its mathematical elegance.

---

## Part 5 -- The Confidence Hierarchy and Asymmetric Trust

The confidence hierarchy operationalizes the abstract evidence hierarchy at the feature level -- mapping each concrete feature dimension to a confidence tier (see SS14.6).

| Tier | Source | Epistemic Basis |
|---|---|---|
| **1-joint (Doubly Proven)** | PH $\cap$ CG-VAE joint component via SLIDE | Both stability and identifiability theorems apply |
| **1a (Proven -- stability)** | PH features | Stability theorem |
| **1b (Proven -- identifiability)** | CG-VAE factors passing MCC $\geq 0.85$ | Li et al. (2025) Theorem 2 |
| **2 (Corroborated)** | Joint components across three or more pathways | Cross-pathway convergence |
| **3 (Empirically invariant)** | Features passing LOGO but low CKA with PH/CG-VAE | LOGO-validated, no theoretical backing |
| **4 (Uncertain)** | Unique to one pathway | No cross-validation |

### Key Mechanisms

**SLIDE decomposition** (Gaynanova and Li, 2019) partitions multi-view features into joint, partially shared, and individual components:

$$X = X_{\textrm{joint}} + X_{\textrm{partial}} + X_{\textrm{individual}}$$

This directly assigns each feature dimension to a tier. The PH $\cap$ CG-VAE joint component -- features simultaneously aligned with both theorem-backed anchors -- earns the highest confidence.

**Centered Kernel Alignment (CKA)** (Kornblith et al., 2019; Williams et al., 2024) measures cross-pathway alignment. Williams et al. proved CKA, RSA, and CCA are mathematically equivalent under appropriate normalization.

**Dempster-Shafer Theory (DST)** handles evidence combination with asymmetric reliability. Unlike Bayesian fusion (which treats sources symmetrically), DST encodes ignorance via the gap between belief and plausibility functions. Tier 1-joint features have narrow gaps (high confidence); Tier 4 features have wide gaps (high ignorance).

### The Asymmetric Trust Structure

No prior work in multi-modal feature fusion exploits the epistemic asymmetry between theorem-backed and empirically derived features. Standard fusion approaches treat all feature sources as epistemically equivalent. When one source (PH) has provable invariance guarantees and another (CG-VAE) has provable identifiability guarantees, symmetric treatment is epistemically inappropriate. This asymmetric trust structure is a novel contribution of the framework.

### DeCUR Residual Analysis

DeCUR (Wang et al., 2024) demonstrated that the unique (non-shared) components of self-supervised representations carry meaningful information. DINOv2's PH-residual features may encode geological information that is real but not topological: texture gradients, facies boundary sharpness, spatial frequency content. These residuals feed the uncertainty quantification pipeline (SS14.7) rather than being discarded.

---

## Part 6 -- The Essence Thought Experiment

The ellipse degradation thought experiment (Hoydic, 2026) examined the question of how persistent homology relates to "essence" through progressive degradation of a channelized reservoir image.

**Variant A (Occlusion)**: Progressively add ellipses that hide geological features. Information is preserved but inaccessible. **Variant B (Erosion)**: Progressively remove geological features themselves. Information is irreversibly destroyed.

### Five Problems Identified

1. **Occlusion vs. erosion are fundamentally different.** The QCF faces an occlusion problem (sparse observations of full geology), making this distinction critical.
2. **Path dependence.** Different degradation orders yield different "minimal essence" sets. No unique answer exists.
3. **Feature entanglement.** Geological features are physically coupled through constraints like $\lambda = 10$--$14W$ (Leopold-Wolman). Independent feature removal creates geologically impossible states outside the constrained manifold $M$.
4. **Observer-relativity.** Different measurement systems have different essence thresholds. PH ($H_1$) is particularly sensitive to channel connectivity -- even few ellipses at intersections could destroy the homology.
5. **Minimality vs. sufficiency.** Minimality is fragile; sufficiency (redundant features) is more robust for retrieval.

### Resolution: Generator Invariance

Essence is better defined through invariance across generative processes. Formally:

$$\textrm{Essence}(f) = \bigcap_G \lbrace \text{information about } \theta \text{ captured by } f \text{ when trained on } G \rbrace$$

This definition is unique (no path dependence), respects physics (generators enforce the constrained manifold $M$), and is observer-independent (defined by generator agreement). The LOGO test operationalizes this definition. The thought experiment is reframed as a robustness test, not an essence definition.

---

## Part 7 -- Validation Framework (Sakshi)

The Sakshi (Sanskrit: "witness") validation framework operationalizes the Vedantic epistemological principle that a claim about essence must be validated by an observer independent of the representation being evaluated (see SS10).

### Ten Independent Witnesses

| # | Witness | Target |
|---|---|---|
| 1 | Cluster purity (ARI) | > 0.7 |
| 2 | Retrieval precision (P@10) | > 0.8 |
| 3 | LOGO invariance | Degradation < 20% |
| 4 | Transfer prediction | $R^2$ > 0.5 |
| 5 | Expert validation (Cohen's $\kappa$) | > 0.6 |
| 6 | Pathway convergence | Disagreement < 0.2 |
| 7 | Adversarial robustness | Attack success < 30% |
| 8 | Calibration (ECE) | < 0.1 |
| 9 | Mixture handling | Correct high entropy on ambiguous inputs |
| 10 | Process correlation | $r$ > 0.4 with physical parameters |

### The LOGO Protocol

Under the Unifying CRL framework (Yao et al., ICLR 2025), distinct generators are reinterpreted as interventions on a shared data-generating process. LOGO tests which features remain invariant across the intervention space. The reframing changes what a LOGO pass means: it is not merely empirical cross-validation but a test of whether features correspond to provably identifiable factors under the observed intervention structure.

The generator pool ($G_1$: principle-based, $G_2$: GAN, $G_3$: MPS, $G_4$: Flumy process-based) is audited for informativeness in the CRL sense. $G_1$ and $G_4$ supply mechanism variation; $G_2$ and $G_3$ supply distributional variation. A fourth metric applies specifically to CG-VAE: MCC between learned factors and held-out ground-truth parameters (threshold $\geq 0.85$ for Level 1b maintenance).

### Adversarial Tests

Five tests provide Level 2 severe evidence:

1. **Variogram-matched topology swap** (*Sankhya-maya*): identical variograms, different connectivity. Tests the $H_1$ hypothesis directly.
2. **Style transfer attack** (*Rupa-viparyaya*): neural style transfer changes appearance while preserving structure. Tests structural vs. textural discrimination.
3. **Channel skeleton permutation** (*Nadi-krama-parinama*): permuted connectivity with preserved aggregate statistics. Tests genuine topological sensitivity.
4. **Histogram equalization** (*Samya-karana*): equalized intensity distributions. Tests reliance on spatial structure vs. marginal statistics.
5. **Factor-conditioned counterfactual severity** (*Hetu-vyabhicara*) (SS10.4.5): using Chi et al. (2026) flow-matching as a controllable counterfactual generator, tests per-factor pathway response specificity. Pre-committed thresholds: PH specificity ratio $S_k \geq 3$ for connectivity factors; CG-VAE $S_k \geq 2$ for identified factors; DINOv2 serves as entangled control.

### Claim Survival Matrix

All interpretation criteria are fixed before experiments are conducted. The matrix maps evidence configurations to warranted claims: L1 + L2 + L3 + L6 + L7 all passing yields a "strong" essence claim; L6 passing alone yields only a "weak" claim; calibration failure at any level disqualifies the claim entirely because overconfident predictions are worse than no predictions.

---

## Part 8 -- Extensions

### Response Essence via Dynamical Systems

The framework extends essence from static structure to dynamic response (SS14.1--14.5). **Response essence** is the equivalence class of geological configurations producing topologically equivalent dynamic response under a specified class of stimuli. Two configurations share response essence if their Morse-Smale decompositions (Conley, 1978) are combinatorially equivalent -- the same attractors exist and state space is organized identically around them.

The computational pipeline uses **Takens embedding** (Takens, 1981) to reconstruct attractor topology from sparse time series, and **double persistent homology** (Kramar et al., 2016) to track how persistence diagrams themselves evolve over time. Venkataraman et al. (2016) demonstrated that PH of Takens-reconstructed attractors reliably distinguishes dynamical regimes; Moon et al. (2019) showed PH features of pore structure predict macroscopic flow properties, establishing the structural-to-response link.

Formation dynamics as attractor systems suggests that structural PH of the geological record encodes information about the attractor of the formation process itself -- connecting structural and response essence at a deeper level than the retrieval problem requires.

### Uncertainty Quantification Pipeline

The pipeline links PH's mathematical guarantees to calibrated uncertainty in retrieval (SS14.7):

1. PH features provide bounded invariants (stability theorem)
2. **DeCUR** (Wang et al., 2024) separates DINOv2 into PH-aligned and PH-residual components
3. **Kotelevskii et al. (2025)** decompose residual uncertainty into aleatoric and epistemic per feature dimension
4. **Hedged instance embeddings** (Oh et al., 2019) represent analogs as distributions $\mathcal{N}(\mu, \Sigma)$
5. Retrieval uses uncertainty-weighted similarity that downweights high-uncertainty dimensions

This transforms Pipeline A from storing analogs as point estimates to storing analogs *with calibrated confidence about what is known and unknown*.

### Implications for Two-Pipeline Architecture

Pipeline A's index becomes a **tiered descriptor**: core index (Tiers 1--2) for primary retrieval; extended index (Tier 3) for refinement within equivalence classes; uncertainty envelope (Tier 4 + aleatoric) for uncertainty quantification. Pipeline B's Neural Process query encoder uses the structured uncertainty as an informative prior: Tier 1 features receive tight priors, Tier 4 features receive diffuse priors.

---

## Part 9 -- The Identifiability Integration (April 2026)

### Context

On April 13, 2026, a search for methods to distinguish signal essence in latent space surfaced Chi et al. (2026) -- "Disentangled Representation Learning via Flow Matching" (arXiv:2602.05214). Analysis revealed that Chi et al. addresses *disentanglement* (factor independence via orthogonality regularization), not *essence* (structural invariance across generators) as the QCF defines it. The paper does not escape the Locatello et al. (2019) impossibility result for unsupervised disentanglement. This motivated a broader survey of the identifiability frontier.

### Three-Method Strategy

| Role | Method | Purpose |
|---|---|---|
| **Primary** | Li et al. 2025 CG-VAE (arXiv:2503.00639) | Theorem-backed identification of $\theta$; upgrades Learned Pathway to Level 1b |
| **Framework** | Unifying CRL (Yao et al., ICLR 2025, arXiv:2409.02772) | Reframes LOGO as interventional CRL with specified assumption-satisfaction conditions |
| **Adversarial tool** | Chi et al. 2026 (supervised variant) | Counterfactual image generator for Level 2 severe testing (SS10.4.5) |
| **Cite-only** | Brady et al. 2025 (ICLR, arXiv:2411.07784) | Frontier single-view disentanglement (wrong data shape for QCF) |
| **Competitor** | Geological GAN (arXiv:2510.17478) | Adjacent work -- no PH, no identifiability theorem, single-environment scope |

### Why Li et al. 2025 (CG-VAE) is Primary

*Note*: The integration plan originally cited this paper as "Kong et al." -- a factual error. The correct first author is Zijian Li.

Four reasons CG-VAE fits QCF:

1. **Paired $(I, \theta)$ data matches auxiliary structure.** The generator produces images with known parameter vectors, satisfying CG-VAE's conditional independence assumption (A2).
2. **Empirical formulas are sparse mixing.** Leopold-Wolman ($\lambda = 10$--$14W$), Parker ($W/d > 50$), Werner dune parameters encode which parameters affect which image regions -- exactly the sparse mixing structure A4 requires.
3. **Fewer domains needed.** $2\lvert z_a \rvert + 1$ domains for subset $z_a$ instead of iVAE's $2n + 1$ for all $n$ factors. Practical for a 15--30 parameter space.
4. **Automatic fallback.** Corollary 1 recovers iVAE's result in the fully-connected case. If proofs have issues under peer review, fallback requires no re-architecture.

### Level 1a vs. Level 1b: Complementary Guarantees

| Guarantee | Protects Against | Does Not Protect Against |
|---|---|---|
| **Level 1a (stability)** | Perturbation noise: bounded input changes produce bounded diagram changes | Correspondence: features could be stable yet encode generator artifacts |
| **Level 1b (identifiability)** | Entanglement: learned factors recover true generative parameters, not artifact mixtures | Perturbation sensitivity: factors could be correctly identified yet arbitrarily sensitive to noise |

A feature satisfying both is "doubly Level 1" -- robust against perturbation *and* correctly identified. The SLIDE decomposition isolates this joint component as the highest-confidence class in the system.

### The Key Philosophical Shift

**Before**: "PH is uniquely Level 1; the learned pathway is inherently Tier 3--4."

**After**: "PH and supervised-identifiable learned features are both Level 1, protecting against *different* failure modes. The convergence of two complementary Level 1 guarantees provides stronger essence justification than either alone, because they rule out different kinds of wrongness."

### Peer-Review Status

Li et al. 2025 is a preprint (arXiv:2503.00639) as of April 2026. The iVAE fallback (Khemakhem et al., 2020, AISTATS -- peer-reviewed) is automatic via Corollary 1 if proofs do not survive peer review. Quarterly checks are planned for published version.

---

## Part 10 -- Open Questions and Future Work

### Multi-Parameter Persistence

Standard PH uses a single filtration parameter. Geological images exhibit structure at multiple scales simultaneously -- bar spacing, channel sinuosity, floodplain texture. Multi-parameter persistence (Cerri et al., 2013) would track how features at different scales interact. However, vectorization for multi-parameter persistence remains an active research area and computational costs are substantially higher.

### Topological Dictionary Learning

An ambitious extension: learn a set of *topological atoms* -- canonical persistence diagrams -- such that any image's diagram decomposes as a sparse combination of atoms. Each atom would represent a topological primitive ("sinuous channel with one oxbow," "braided network with 3--5 connections"), closing the loop between generative processes, topological representations, and the essence claim.

### Cross-Domain Validation

Applying the identical PH pipeline to musical scores (Alcala-Alvarez and Padilla-Longoria, 2022; Bergomi et al., 2016), neural recordings (Giusti, Ghrist, and Bassett, 2016; Wang et al., 2025), and other structured data. If the same pipeline distinguishes braided from meandering channels and also distinguishes musical genres or neural states, the argument for mathematical universality becomes very strong (Level 4 evidence).

### By-Hand Implementation Tasks

- Read Li et al. 2025 supplementary proofs; verify assumptions A1--A5 against the principle-based generator
- Implement CG-VAE loss ($L_r + \alpha L_s - \beta L_{\textrm{KL}}$ with sparsity penalty $L_s = \sum \lvert \partial \hat{x} / \partial \hat{z} \rvert$) on generator data
- Compute MCC between learned factors and true $\theta$; per-factor disentanglement score
- Build Chi et al. supervised counterfactual generator for SS10.4.5 severity test
- Quarterly peer-review tracking for Li et al. 2025

### Information-Theoretic Quantification

Estimating conditional mutual information using MINE (Belghazi et al., 2018) or similar variational bounds remains untested for this framework. This would populate Level 3 of the evidence hierarchy.

---

## Part 11 -- Document Map

| Document | Role | Status |
|---|---|---|
| `DISSERTATION_OUTLINE.md` | Primary deliverable: full dissertation structural scaffold (~1,400+ lines, 15 sections) | Active; sections vary in depth |
| `IDENTIFIABILITY_INTEGRATION_PLAN.md` | Plan for upgrading the Learned Pathway to Level 1b via CG-VAE | Plan document; SS4 edits complete on main (April 2026) |
| `READING_NOTES.md` | Notes from all source documents; essence thought experiment summary; identifiability paper summaries | Reference |
| `EPISTEMOLOGICAL_OVERHAUL.md` | Blueprint for restructuring the evidence hierarchy (LOGO demotion, mathematical-invariance-primary) | ARCHIVED; core ideas implemented in dissertation SS8 and SS14 |
| `qualia_convergence_COMPLETE_VISION_v5.md` | QCF "north star" -- full intellectual vision | Current (v5.4) |
| `qualia_convergence_IMPLEMENTATION_SPEC_v6.md` | Practical guide with phases and decision points | Current (v6.3) |
| `qualia_convergence_ARCHITECTURE_DECISIONS_v1.md` | Reasoning behind design choices (ADRs) | Current (v1.1) |
| `persistent_homology_writeup_general_research.docx` | Earlier general PH research writeup (~7,000 words) | Superseded by dissertation outline |
| `persistent_homology_writeup_my_research.docx` | Earlier personal PH research writeup (identical to general) | Superseded by dissertation outline |
| `essence_thought_experiment.pdf` | Ellipse degradation thought experiment | Reference |
| `00_DOCUMENT_INDEX.md` | Authoritative document index and relationship diagram | Current |

**Document hierarchy**: The Complete Vision is the "north star"; the Implementation Spec translates vision into phases; the Architecture Decisions record trade-offs. The Dissertation Outline is the primary academic deliverable, drawing on all three QCF documents plus the identifiability integration and epistemological overhaul.

---

## Part 12 -- Bibliography

### Persistent Homology and TDA

- Adams, H., et al. (2017). Persistence images: A stable vector representation of persistent homology. *JMLR*, 18(8), 1--35.
- Atienza, N., Gonzalez-Diaz, R., and Soriano-Trigueros, M. (2020). On the stability of persistent entropy and new summary functions for TDA. *Pattern Recognition*, 107, 107509.
- Bubenik, P. (2015). Statistical topological data analysis using persistence landscapes. *JMLR*, 16(3), 77--102.
- Carlsson, G. (2009). Topology and data. *Bull. AMS*, 46(2), 255--308.
- Cerri, A., et al. (2013). Betti numbers in multidimensional persistent homology are stable functions. *Math. Methods Appl. Sci.*, 36(12), 1543--1557.
- Chazal, F., de Silva, V., Glisse, M., and Oudot, S. (2016). *The Structure and Stability of Persistence Modules*. Springer.
- Cohen-Steiner, D., Edelsbrunner, H., and Harer, J. (2007). Stability of persistence diagrams. *Discrete Comput. Geom.*, 37(1), 103--120.
- Edelsbrunner, H., and Harer, J. (2010). *Computational Topology: An Introduction*. AMS.
- Edelsbrunner, H., Letscher, D., and Zomorodian, A. (2002). Topological persistence and simplification. *Discrete Comput. Geom.*, 28(4), 511--533.
- Kemmea, A. J., and Agyingi, C. A. (2025). Persistent homology: A pedagogical introduction with biological applications. arXiv:2505.06583.
- Otter, N., et al. (2017). A roadmap for the computation of persistent homology. *EPJ Data Science*, 6, Article 17.
- Oudot, S. Y. (2015). *Persistence Theory: From Quiver Representations to Data Analysis*. AMS.
- Tauzin, G., et al. (2021). giotto-tda: A topological data analysis toolkit for machine learning. *JMLR*, 22(39), 1--6.
- Wagner, H., Chen, C., and Vucini, E. (2012). Efficient computation of persistent homology for cubical data. In *Topological Methods in Data Analysis and Visualization II*. Springer.
- Zomorodian, A., and Carlsson, G. (2005). Computing persistent homology. *Discrete Comput. Geom.*, 33(2), 249--274.

### TDA in Geoscience

- Chawshin, K., et al. (2021). U.S. Patent 11,386,143 (topological knowledge representation for well-log interpretation).
- Moon, C., et al. (2019). Statistical inference over persistent homology predicts fluid flow in porous media. *Water Resources Research*, 55(11), 9592--9603.
- Robins, V., et al. (2016). Percolating length scales from topological persistence analysis of micro-CT images. *Water Resources Research*, 52(1), 315--329.
- Thompson, A. B., Mayall, M., and Sherborne, A. (2023). Persistent homology tracks dynamic topological changes in dissolving porous media. *Water Resources Research*, 59(5), e2022WR033750.

### TDA in Music and Neuroscience

- Alcala-Alvarez, A., and Padilla-Longoria, P. (2022). A framework for topological music analysis (TMA). arXiv:2204.09744.
- Bergomi, M. G., Barate, A., and Di Fabio, B. (2016). Towards a topological fingerprint of music. In *CTIC*, LNCS 9667, 88--100. Springer.
- Bergomi, M. G., and Barate, A. (2020). Homological persistence in time series: An application to music classification. *J. Math. Music*, 14(2), 204--221.
- Giusti, C., Ghrist, R., and Bassett, D. S. (2016). Two's company, three (or more) is a simplex. *J. Comput. Neurosci.*, 41(1), 1--14.
- Liu, J., et al. (2021). Persistent homology-based topological analysis on Gestalt patterns during human brain cognition. *J. Healthcare Eng.*, 2021, 2334332.
- Wang, Y., et al. (2025). Topological signatures of brain dynamics. *Frontiers in Human Neuroscience*, 19, 1607941.

### Identifiability and Causal Representation Learning

- Ahuja, K., Hartford, J., and Bengio, Y. (2023). Invariance and causal representation learning: Prospects and limitations. arXiv:2312.03580.
- Brady, J., et al. (2025). Interaction asymmetry: A general principle for learning composable abstractions. *ICLR 2025*. arXiv:2411.07784.
- Brehmer, J., et al. (2022). Weakly supervised causal representation learning. *NeurIPS 35*.
- Chi, J., et al. (2026). Disentangled representation learning via flow matching. arXiv:2602.05214.
- Khemakhem, I., Kingma, D. P., Monti, R. P., and Hyvarinen, A. (2020). Variational autoencoders and nonlinear ICA: A unifying framework. *AISTATS*.
- Li, Z., et al. (2025). Synergy between sufficient changes and sparse mixing procedure for disentangled representation learning. arXiv:2503.00639.
- Locatello, F., et al. (2019). Challenging common assumptions in the unsupervised learning of disentangled representations. *ICML*, 4114--4124.
- Squires, C., et al. (2023). Linear causal disentanglement via interventions. *ICML*.
- Varici, B., et al. (2024). Score-based causal representation learning. *JMLR*.
- von Kugelgen, J., et al. (2021). Self-supervised learning with data augmentations provably isolates content from style. *NeurIPS 34*.
- Yao, D., et al. (2025). Unifying causal representation learning with the invariance principle. *ICLR 2025*. arXiv:2409.02772.

### Invariance, Philosophy of Science, and Severe Testing

- Arjovsky, M., et al. (2019). Invariant risk minimization. arXiv:1907.02893.
- Mayo, D. G. (2018). *Statistical Inference as Severe Testing*. Cambridge University Press.
- Orzack, S. H., and Sober, E. (1993). A critical assessment of Levins's model-building strategy. *Q. Rev. Biol.*, 68(4), 533--546.
- Rosenfeld, E., Ravikumar, P., and Risteski, A. (2021). The risks of invariant risk minimization. *ICLR*.
- Weisberg, M. (2006). Robustness analysis. *Phil. Sci.*, 73(5), 730--742.
- Wimsatt, W. C. (1981). Robustness, reliability, and overdetermination. In *Scientific Inquiry and the Social Sciences*.

### Self-Supervised Learning and Vision Transformers

- Caron, M., et al. (2021). Emerging properties in self-supervised vision transformers. *ICCV 2021*. arXiv:2104.14294.
- Dosovitskiy, A., et al. (2020). An image is worth 16x16 words. *ICLR 2021*. arXiv:2010.11929.
- Hu, E. J., et al. (2022). LoRA: Low-rank adaptation of large language models. *ICLR 2022*. arXiv:2106.09685.
- Oliva, A., and Torralba, A. (2006). Building the gist of a scene. *Prog. Brain Res.*, 155, 23--36.
- Oquab, M., et al. (2023). DINOv2: Learning robust visual features without supervision. arXiv:2304.07193.

### Cross-Pathway Alignment and Uncertainty

- Gaynanova, I., and Li, G. (2019). Structural learning and integrative decomposition of multi-view data. *Biometrics*, 75(4), 1121--1132.
- Kendall, A., and Gal, Y. (2017). What uncertainties do we need in Bayesian deep learning? *NeurIPS 30*.
- Kornblith, S., et al. (2019). Similarity of neural network representations revisited. *ICML 2019*. arXiv:1905.00414.
- Kotelevskii, N., et al. (2025). Uncertainty decomposition in feature space without ensembles. arXiv:2511.12389.
- Kriegeskorte, N., Mur, M., and Bandettini, P. (2008). Representational similarity analysis. *Frontiers in Systems Neuroscience*, 2, Article 4.
- Oh, S., et al. (2019). Hedged instance embedding. *ICLR 2019*. arXiv:1810.00319.
- Wang, Z., et al. (2024). DeCUR: Decoupling common and unique representations for multiview self-supervised learning. *ECCV 2024*. arXiv:2309.05300.
- Williams, A. H., et al. (2024). Generalized shape metrics on neural representations. *Nature Machine Intelligence*, 6, 100--113.

### Dynamical Systems and Response Essence

- Conley, C. (1978). *Isolated Invariant Sets and the Morse Index*. AMS.
- Das, S., Bhattacharya, S., and Bhowmick, S. (2024). Topological analysis of dynamical systems via persistent homology. arXiv:2408.15834.
- He, Q., et al. (2023). Koopman operator-based model reduction for reservoir simulation. *SPE Journal*, 28(4), 2024--2040.
- Kramar, M., et al. (2016). Analysis of Kolmogorov flow and Rayleigh-Benard convection using persistent homology. *Physica D*, 334, 82--98.
- Lipinski, M., Mrozek, M., and Batko, B. (2023). Persistent Conley-Morse graphs. arXiv:2107.02115.
- Shah, P., Mukherjee, S., and Sousbie, T. (2025). Persistent homology detects bifurcation routes to chaos. arXiv preprint.
- Takens, F. (1981). Detecting strange attractors in turbulence. *Lect. Notes Math.*, 898, 366--381.
- Venkataraman, V., Ramamurthy, K. N., and Turaga, P. (2016). Persistent homology of attractors for action recognition. *IEEE ICIP*, 4150--4154.

### Geomorphology and Generator Foundations

- Frascati, A., and Lanzoni, S. (2009). Morphodynamic regime and long-term evolution of meandering rivers. *J. Geophys. Res.*, 114(F2), F02002.
- Fredsoe, J. (1978). Meandering and braiding of rivers. *J. Fluid Mech.*, 84(4), 609--624.
- Hundey, E. J., and Ashmore, P. E. (2009). Length scale of braided river morphology. *Water Resources Research*, 45(8), W08409.
- Jiwei, L., et al. (2025). Characteristics and distribution of interlayers in tidal-dominated estuarine reservoir. *Scientific Reports*, 15, 3591.
- Kleinhans, M. G., and van den Berg, J. H. (2011). River channel and bar patterns explained and predicted. *Earth Surf. Process. Landforms*, 36(6), 721--738.
- Leopold, L. B., and Wolman, M. G. (1957). River channel patterns. *USGS Professional Paper* 282-B.
- Leopold, L. B., and Wolman, M. G. (1960). River meanders. *GSA Bulletin*, 71(6), 769--793.
- Leopold, L. B., Wolman, M. G., and Miller, J. P. (1964). *Fluvial Processes in Geomorphology*. W. H. Freeman.
- Nanson, G. C., and Knighton, A. D. (1996). Anabranching rivers. *Earth Surf. Process. Landforms*, 21(3), 217--239.
- Parker, G. (1976). On the cause and characteristic scales of meandering and braiding in rivers. *J. Fluid Mech.*, 76(3), 457--480.
- Phillips, J. D. (2006). Deterministic chaos and historical geomorphology. *Geomorphology*, 76(1--2), 109--121.
- Stolum, H.-H. (1996). River meandering as a self-organization process. *Science*, 271(5256), 1710--1713.
- Werner, B. T. (1995). Eolian dunes: Computer simulations and attractor interpretation. *Geology*, 23(12), 1107--1110.
- Williams, G. P. (1986). River meanders and channel size. *J. Hydrology*, 88(1--2), 147--164.

### Geostatistics and Subsurface Modeling

- Arnold, D., et al. (2018). Hierarchical benchmark case study for history matching and uncertainty quantification. *Math. Geosci.*, 50(7), 793--826.
- Chiles, J.-P., and Delfiner, P. (2012). *Geostatistics: Modeling Spatial Uncertainty* (2nd ed.). Wiley.
- Guardiano, F. B., and Srivastava, R. M. (1993). Multivariate geostatistics: Beyond bivariate moments. In *Geostatistics Troia '92*. Springer.
- Journel, A. G., and Huijbregts, C. J. (1978). *Mining Geostatistics*. Academic Press.
- Matheron, G. (1963). Principles of geostatistics. *Economic Geology*, 58(8), 1246--1266.
- Scheidt, C., Li, L., and Caers, J. (2018). *Quantifying Uncertainty in Subsurface Systems*. Wiley/AGU.
- Strebelle, S. (2002). Conditional simulation of complex geological structures using multiple-point statistics. *Math. Geol.*, 34(1), 1--21.

### Neural Processes and Retrieval Architecture

- Garnelo, M., et al. (2018). Neural processes. arXiv:1807.01622.
- Jaegle, A., et al. (2021). Perceiver IO. arXiv:2107.14795.
- Johnson, J., Douze, M., and Jegou, H. (2019). Billion-scale similarity search with GPUs. *IEEE Trans. Big Data*, 7(3), 535--547.
- Kim, H., et al. (2019). Attentive Neural Processes. *ICLR 2019*.
- Nickel, M., and Kiela, D. (2017). Poincare embeddings for learning hierarchical representations. *NeurIPS 30*.
- Peng, W., et al. (2022). Hyperbolic deep neural networks: A survey. *IEEE TPAMI*, 44(12), 10023--10044.
- Chami, I., et al. (2019). Hyperbolic graph convolutional neural networks. *NeurIPS 32*.
- Vaughan, A., et al. (2022). Convolutional conditional neural processes for local climate downscaling. *Geosci. Model Dev.*, 15(1), 251--268.

### Geological Generative Models

- Rongier, G., and Peeters, L. (2025). Towards geological inference with process-based and deep generative modeling, part 2. arXiv:2510.17478.

---

*This document synthesizes the full research program from the dissertation outline, identifiability integration plan, epistemological overhaul, reading notes, and QCF source documents. For the authoritative, detailed treatment of any topic, see the dissertation outline (`DISSERTATION_OUTLINE.md`) at the section numbers referenced throughout.*
