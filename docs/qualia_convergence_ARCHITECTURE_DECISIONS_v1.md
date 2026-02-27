# Qualia Convergence Framework
## Architecture Decision Record

### Documentation of Design Choices, Trade-offs, and Revision Triggers

---

**Document Purpose**: This document records the **reasoning behind architectural decisions** in the Qualia Convergence Framework. For each major decision, it documents: what alternatives were considered, why the chosen approach was selected, and under what conditions the decision should be revisited.

**Document Type**: Architecture Decision Record (3 of 3)
- **Complete Vision**: What we are building
- **Implementation Specification**: How we build it
- **This document**: Why we made these choices

**Version**: 1.1 — January 2026 (Updated with critical review response)

---

# Part I: Decision Record Format

Each decision follows this structure:

```
## ADR-XXX: [Decision Title]

**Status**: [Proposed | Accepted | Deprecated | Superseded]
**Date**: [Decision date]
**Context**: [What situation led to this decision?]
**Decision**: [What was decided?]
**Alternatives Considered**: [What other options were evaluated?]
**Rationale**: [Why was this option chosen?]
**Consequences**: [What are the implications?]
**Literature Evidence**: [What research supports this?]
**Revision Triggers**: [When should we reconsider?]
```

---

# Part II: Core Architecture Decisions

## ADR-001: Three-Pathway Feature Architecture

**Status**: Accepted  
**Date**: January 2026

### Context

The framework requires feature extraction from geological patterns. The central question: Should we use a single feature extraction approach or multiple independent approaches?

### Decision

Use **three independent pathways** that operate on the same input:
1. **Classical Pathway**: Variogram, fractal dimension, connectivity (interpretable, established)
2. **Learned Pathway**: DINOv2 with LoRA fine-tuning (powerful, data-driven)
3. **Topological Pathway**: Persistent homology via Giotto-TDA (structural, shape-aware)

### Alternatives Considered

| Alternative | Description | Why Rejected |
|-------------|-------------|--------------|
| **Single learned pathway** | DINOv2 only | Lacks interpretability; can't validate convergence across viewpoints |
| **Classical + learned only** | Skip TDA | Misses structural hypothesis (H₁ for channel types) |
| **End-to-end learned** | Train everything from scratch | Loses interpretability; higher data requirements |
| **Ensemble of similar models** | Multiple DINOv2 variants | No true independence; same biases |

### Rationale

1. **Philosophical grounding**: The Sākṣī principle requires independent witnesses. If three fundamentally different approaches (statistics, deep learning, topology) agree, the evidence for essence capture is stronger.

2. **Ablation capability**: Three pathways enable rigorous ablation studies to determine which features matter.

3. **Failure isolation**: If one pathway fails (e.g., TDA hypothesis not supported), others can compensate.

4. **Interpretability gradient**: Classical → interpretable; Learned → powerful; Topological → structural. Different audiences value different pathways.

### Consequences

- **Positive**: Enables convergence analysis, ablation studies, interpretability
- **Negative**: Higher implementation complexity; fusion required
- **Neutral**: ~3× feature computation cost (acceptable for offline embedding)

### Literature Evidence

- Query 7: DINOv2 validated for geological imagery ("near-perfect accuracy")
- Query 3: TDA exists in geology but not integrated with DL
- Classical geostatistics: Established practice (Journel, Caers)

### Revision Triggers

- If pathway convergence is consistently low (disagreement > 0.4), reconsider independence assumption
- If one pathway consistently dominates ablation, consider simplifying to that pathway
- If computational cost becomes prohibitive for real-time applications, consider pathway selection

---

## ADR-002: Hyperbolic vs. Euclidean Embedding Geometry

**Status**: Accepted (with Euclidean fallback)  
**Date**: January 2026

### Context

Embeddings must be placed in a geometric space for similarity computation. Depositional environments have a natural hierarchical structure (Environment → Style → Subtype).

### Decision

Use **hyperbolic geometry (Poincaré ball model)** as the primary embedding space, with Euclidean as a baseline for ablation.

### Alternatives Considered

| Alternative | Description | Why Not Primary |
|-------------|-------------|-----------------|
| **Euclidean** | Standard L2 distance | Distorts hierarchical structure; O(n) dimensions needed |
| **Spherical** | Cosine similarity on unit sphere | Good for direction, not magnitude; no hierarchy benefit |
| **Product manifold** | Hyperbolic × Euclidean | Higher complexity; save for Phase 3+ |
| **Mixed-curvature** | Learned curvature per dimension | Research-level; too experimental |

### Rationale

1. **Hierarchy representation**: Hyperbolic space represents tree structures with O(log n) distortion vs. O(n) in Euclidean. Depositional hierarchies map naturally.

2. **Novelty**: Query 1 confirms no prior hyperbolic embeddings in geoscience. Strong novelty claim.

3. **Mature implementation**: `geoopt` library provides stable Riemannian optimization.

4. **Natural interpretation**: Center = general (e.g., "fluvial"); boundary = specific (e.g., "high-sinuosity meandering").

### Consequences

- **Positive**: Better hierarchy preservation; strong novelty claim; interpretable structure
- **Negative**: More complex optimization (Riemannian SGD); potential stability issues
- **Mitigation**: Euclidean fallback if hyperbolic doesn't improve metrics

### Literature Evidence

- Query 1: "Applications still emerging" in geoscience — confirms novelty
- Nickel & Kiela (2017): Foundational work on Poincaré embeddings
- Chami et al. (2019): 63.1% error reduction with hyperbolic GCNs

### Revision Triggers

- If hyperbolic shows < 5% improvement over Euclidean in ablation → use Euclidean
- If optimization instability persists after tuning → use Euclidean
- If product manifolds show significant gains in research → consider upgrade

---

## ADR-003: Neural Process Query Encoder

**Status**: Accepted  
**Date**: January 2026

### Context

Real queries are sparse: a few wells, partial seismic, scattered observations. The database contains complete patterns. How do we match sparse queries to complete analogs while maintaining calibrated uncertainty?

### Decision

Use **Neural Process (NP) architecture** as the query encoder, outputting a distribution (μ, σ) rather than a point estimate.

### Alternatives Considered

| Alternative | Description | Why Rejected |
|-------------|-------------|--------------|
| **Deterministic encoder** | SetEncoder → point estimate | No principled uncertainty; can't distinguish "confident wrong" from "appropriately uncertain" |
| **MC Dropout** | Post-hoc uncertainty via dropout at inference | Uncertainty reflects model uncertainty, not data sparsity |
| **Deep Ensembles** | Multiple models, variance as uncertainty | Computational cost; uncertainty still model-based |
| **Bayesian Neural Network** | Full posterior over weights | Intractable; approximations may not calibrate well |

### Rationale

1. **Principled uncertainty**: NP uncertainty reflects **data sparsity**, not just model uncertainty. Few observations → high σ; many observations → low σ.

2. **Amortized inference**: Single forward pass, no MCMC sampling at inference time.

3. **Variable input handling**: Naturally handles variable numbers of observations via set encoding.

4. **Novelty**: Query 2 confirms NPs used for interpolation, not retrieval. Novel application.

### Consequences

- **Positive**: Calibrated uncertainty from data sparsity; graceful degradation; novelty
- **Negative**: Training complexity (ELBO, reconstruction vs. KL balance)
- **Mitigation**: Start with simple NP; upgrade to Attentive NP if calibration poor

### Literature Evidence

- Query 2: NPs used for interpolation in geoscience, not retrieval
- Garnelo et al. (2018): Original NP paper
- Kim et al. (2019): Attentive Neural Processes

### Revision Triggers

- If ECE > 0.2 after tuning → upgrade to Attentive NP or explore alternatives
- If graceful degradation fails (σ not monotonic with sparsity) → debug or replace
- If computational cost prohibitive → consider deterministic with post-hoc calibration

---

## ADR-004: DINOv2 as Learned Pathway Backbone

**Status**: Accepted  
**Date**: January 2026

### Context

The learned pathway requires a vision backbone. Many options exist: ResNet, ViT, CLIP, DINOv2, domain-specific models.

### Decision

Use **DINOv2-ViT-B/14** with **LoRA fine-tuning** (rank 8).

### Alternatives Considered

| Alternative | Description | Why Rejected |
|-------------|-------------|--------------|
| **ResNet-50** | Classic CNN | Lower performance on diverse imagery; less transferable features |
| **ViT (supervised)** | ImageNet-supervised ViT | Features less robust to domain shift than self-supervised |
| **CLIP** | Contrastive language-image | Text modality unnecessary; DINOv2 features richer for visual similarity |
| **Domain-specific CNN** | Trained on geological data | Requires large labeled dataset; may overfit to specific geology |
| **GEM 3D features** | Foundation model for 3D geological data | Generation-focused; not designed for retrieval |

### Rationale

1. **Empirical validation**: Query 7 directly validates DINOv2: "near-perfect accuracy" on geological imagery, "visually better than ground truth" segmentation.

2. **Self-supervised pretraining**: Features learned without labels are more robust to domain shift.

3. **Transfer capability**: DINOv2 excels on out-of-distribution samples (critical for LOGO).

4. **Parameter efficiency**: LoRA enables fine-tuning with ~0.5% trainable parameters.

### Consequences

- **Positive**: Validated architecture; strong transfer; efficient fine-tuning
- **Negative**: Fixed input size (224×224 or 518×518); may miss fine-grained details
- **Mitigation**: Use highest resolution feasible; consider multi-scale if needed

### Literature Evidence

- Query 7: Brondolo & Beaussant (2024) — DINOv2 for geological analysis
- Oquab et al. (2023): DINOv2 paper

### Revision Triggers

- If domain-specific foundation model (e.g., GEM 3D encoder) released with retrieval capability → evaluate
- If fine-grained details consistently missed → consider multi-scale or higher resolution
- If ViT-L significantly outperforms ViT-B → upgrade (with compute cost trade-off)

---

## ADR-005: Principle-Based Generator Architecture

**Status**: Accepted  
**Date**: January 2026

### Context

The framework requires training data with known ground truth. Options: real data, process-based simulation, principle-based generation.

### Decision

Build a **principle-based generator** using empirical geomorphic formulas (Leopold-Wolman for fluvial, Werner for aeolian, Tidal Prism for estuarine).

### Alternatives Considered

| Alternative | Description | Why Rejected |
|-------------|-------------|--------------|
| **Real data only** | Curate existing datasets | Unknown true parameters; limited diversity; expensive |
| **Process-based (Flumy)** | Solve physical equations | Computationally expensive; limited to fluvial; use for LOGO only |
| **GAN-generated** | Learn to generate from examples | Unknown parameters; may perpetuate dataset biases |
| **MPS (SNESIM)** | Statistical replication | Requires quality TIs; no explicit parameters |

### Rationale

1. **Known ground truth**: We KNOW the generating parameters by construction. Essential for LOGO test and transfer prediction.

2. **Multi-environment**: Single framework covers fluvial + aeolian + estuarine. No existing system does this.

3. **Interpretable parameters**: Geomorphic formulas (sinuosity, wavelength ratios) are physically meaningful.

4. **Computational efficiency**: Fast generation enables large training sets.

5. **Distinct category**: Queries 14-16 confirm this is a distinct category from process-based (Flumy) and MPS.

6. **Validated approach** (Query 17): Literature confirms rule-based generators are "indispensable for scenarios where interpretability and strict adherence to expert geological rules are paramount."

7. **Addresses documented gap** (Query 18): Literature explicitly identifies lack of standardized benchmarks as a major limitation. Our multi-environment generator addresses this gap.

### Consequences

- **Positive**: Known ground truth; multi-environment; fast; interpretable; addresses benchmark gap
- **Negative**: Lower physical fidelity than process-based
- **Mitigation**: Use Flumy in LOGO test to validate transfer across generator types

### Literature Evidence

- Query 14: Three categories identified (process-based, principle-based, MPS)
- Query 15: Flumy = process-based; Ours = principle-based (different categories)
- Query 16: Commercial tools (Petrel) use similar parameterization for different purpose
- **Query 17**: Rule-based generators validated as "indispensable" for interpretability
- **Query 18**: Documented gap in standardized geological benchmarks; our generator addresses this
- **Query 19**: Aeolian/estuarine dominated by CA (Werner) and process-based (Delft3D); principle-based fills niche for ML training
- **Query 20**: Deep generative models (GANs/VAEs/diffusion) focus on surrogate simulation, not training data; confirms our distinct use case

### Revision Triggers

- If LOGO fails with Flumy held-out → generator may encode artifacts, need diversification
- If process-based becomes computationally feasible at scale → consider as primary
- If real data becomes available in quantity → incorporate for validation

---

## ADR-006: Fusion Architecture Selection

**Status**: Accepted (Cross-Attention, with Perceiver IO option)  
**Date**: January 2026

### Context

Three pathways produce features of different dimensions and semantics. How should they be combined?

### Decision

Use **cross-attention fusion** as primary approach, with **Perceiver IO** as full-vision upgrade path.

### Alternatives Considered

| Alternative | Description | Trade-offs |
|-------------|-------------|------------|
| **Simple concatenation + MLP** | Concat → Linear layers | Simplest; no learned interaction |
| **Cross-attention** | Attention over pathway tokens | Learned interactions; interpretable weights |
| **Perceiver IO** | Variable-length latent bottleneck | Maximum flexibility; highest complexity |
| **Gated fusion** | Learnable gates per pathway | Good for on/off; less nuanced |
| **Tensor fusion** | Outer product of features | Captures interactions; expensive |

### Rationale

1. **Learned interactions**: Cross-attention learns which pathways matter for which queries.

2. **Interpretability**: Attention weights show pathway contributions.

3. **Manageable complexity**: More powerful than concatenation, simpler than Perceiver IO.

4. **Upgrade path**: If variable observation counts become important, Perceiver IO is available.

### Consequences

- **Positive**: Learns pathway interactions; interpretable; proven architecture
- **Negative**: Fixed number of pathways; fixed input structure
- **Upgrade**: Perceiver IO if variable-length inputs become critical

### Literature Evidence

- Vaswani et al. (2017): Attention mechanisms
- Jaegle et al. (2021): Perceiver IO for flexible multi-modal fusion

### Revision Triggers

- If variable observation counts (3 wells vs. 30 wells) become critical → Perceiver IO
- If attention weights show one pathway always dominates → consider simplifying
- If cross-attention unstable → fall back to concatenation

---

## ADR-007: Sākṣī Validation Framework Design

**Status**: Accepted  
**Date**: January 2026

### Context

Claims about "essence" require rigorous validation independent of the representation itself. Standard ML validation (train/test split) is insufficient.

### Decision

Implement **10-test Sākṣī validation framework** with **pre-committed claim survival matrix**.

### Alternatives Considered

| Alternative | Description | Why Rejected |
|-------------|-------------|--------------|
| **Standard ML validation** | Train/test/val splits | Doesn't test generator invariance or interpretability |
| **Domain adaptation benchmarks** | CORAL, MMD metrics | Tests shift but not essence |
| **Human-only evaluation** | Expert judgment | Expensive; hard to scale; still need quantitative |
| **Single metric focus** | Optimize one metric | Misses multi-faceted essence claims |

### Rationale

1. **Independent witnesses**: Each test examines a different aspect of "essence" independently.

2. **Pre-commitment**: Claim survival matrix fixed before experiments prevents cherry-picking.

3. **Comprehensive coverage**: Tests address invariance, transfer, calibration, adversarial, expert agreement.

4. **Novelty**: Query 10 confirms Sākṣī is more comprehensive than existing validation methods.

### Consequences

- **Positive**: Rigorous; pre-committed; multi-faceted; novel
- **Negative**: Expensive to run all tests; some tests require external resources (experts)
- **Mitigation**: Prioritize tests; run critical tests (LOGO, transfer) first

### Literature Evidence

- Query 10: General validation methods exist; Sākṣī more comprehensive
- Philosophical grounding: Sākṣī principle from Vedantic epistemology

### Revision Triggers

- If claim survival matrix produces unexpected edge cases → refine matrix
- If expert validation logistically infeasible → document limitation
- If new validation methods emerge → evaluate for inclusion

---

## ADR-008: LOGO as Necessary (Not Sufficient) Invariance Test

**Status**: Revised — February 2026 (originally "Accepted" January 2026)
**Date**: January 2026 (revised February 2026)

### Context

The central claim is that representations capture geological essence, not generator artifacts. How do we test this?

### Decision

Use **Leave-One-Generator-Out (LOGO)** as a **necessary but not sufficient** test for generator invariance. LOGO must be corroborated by evidence from higher levels of the evidence hierarchy (see Complete Vision, Section 4.7).

### Alternatives Considered

| Alternative | Description | Why Rejected |
|-------------|-------------|--------------|
| **Standard domain adaptation** | CORAL, gradient reversal | Assumes partial overlap; not complete exclusion |
| **Cross-validation** | Standard CV | Doesn't test generator shift |
| **Real-data validation only** | Test on real data | Real data limited; doesn't isolate generator effect |
| **Synthetic noise injection** | Add noise to test robustness | Tests robustness, not invariance |
| **LOGO as sole evidence** | Rely on LOGO alone for essence claim | **Insufficient** — see Limitations section |

### Rationale

1. **Complete exclusion**: LOGO completely excludes one generator type, not just partial domain shift.

2. **Necessary condition**: If LOGO fails, the representation is generator-specific — this is strong negative evidence.

3. **Interpretable failure**: If LOGO fails, we know exactly which generator caused the problem.

4. **Multiple generators**: Testing across process-based (Flumy), principle-based (ours), MPS, and GAN provides coverage.

### Limitations (Added February 2026)

LOGO has fundamental epistemic limitations that constrain the strength of claims derived from it:

1. **Generator-Family Boundedness**: LOGO tests invariance *within the generator pool*, not invariance to geology in general. Generators sharing physical assumptions (Leopold-Wolman, process-based sediment transport) may produce illusory invariance.

2. **Impossibility Results**: Ahuja et al. (2023, arXiv:2312.03580) proved that invariance alone is insufficient to identify latent causal variables. Passing LOGO does not guarantee that invariant features correspond to geological causes.

3. **Independence Condition**: Wimsatt's robustness analysis (1981) requires genuine model independence. If generators are not genuinely independent in their assumptions, convergence provides weak evidence — "illusory robustness."

4. **IRM Failures**: Invariant Risk Minimization (Arjovsky et al., 2019; Rosenfeld et al., 2021) fails catastrophically in nonlinear settings and requires impractically large environment counts for formal guarantees.

5. **Degrees-of-Freedom Risk**: With sufficient control over the generator space, LOGO can be made to trivially succeed without capturing essence.

### Epistemic Status of LOGO Results

| LOGO Outcome | Interpretation |
|---|---|
| **Fails** (Δ > 0.3) | Strong evidence against essence claim |
| **Passes with diverse generators** | Necessary evidence; requires corroboration from mathematical invariance (ADR-012) and severe testing (ADR-013) |
| **Passes with homogeneous generators** | Weak evidence; may be illusory |

### Consequences

- **Positive**: Stringent negative test; interpretable; addresses core concern
- **Negative**: Insufficient alone for positive essence claims; requires multiple generators; computationally expensive
- **Mitigation**: Combine with evidence hierarchy (ADR-012, ADR-013, ADR-014)

### Literature Evidence

- Query 8: Standard domain adaptation less stringent than LOGO
- Ahuja et al. (2023): Invariance alone insufficient for causal identification
- Rosenfeld et al. (2021): IRM fails in nonlinear settings
- Wimsatt (1981): Independence condition for robustness

### Revision Triggers

- If all generators produce similar results (no diversity) → LOGO uninformative, need more diverse generators
- If LOGO consistently fails → pivot to "what causes generator artifacts?" research
- If real data becomes available → add real-data LOGO test
- If mathematical invariance (ADR-012) provides stronger evidence → LOGO may be further demoted

---

## ADR-012: Mathematical Invariance as Primary Evidence (Topological Pathway)

**Status**: Accepted
**Date**: February 2026

### Context

The topological pathway (persistent homology) has a unique property among the three pathways: the stability theorem provides a **mathematical proof** of invariance, independent of any empirical test.

### Decision

Foreground the PH stability theorem as the **primary evidence** for the topological pathway's invariance claims. Position LOGO as corroborative, not primary.

### Rationale

The stability theorem (Cohen-Steiner, Edelsbrunner, & Harer, 2007): $d_B(\text{Dgm}(f), \text{Dgm}(g)) \leq \|f - g\|_\infty$.

Properties:
1. **Generator-independent**: A property of the mathematics, not of any particular test
2. **Quantitative**: Provides explicit bounds on invariance, not just pass/fail
3. **Universal**: Applies to any input domain (geological, musical, neural)
4. **Cannot be "overengineered"**: It is a theorem, not an empirical finding

**Limitation**: Stability guarantees that topological features are *invariant*, but does not guarantee they are *relevant*. The H₁ hypothesis (ADR-S04) addresses relevance; stability addresses invariance. Together, they provide both relevance and invariance — stronger than either alone.

### Consequences

- **Positive**: Strongest possible invariance evidence; unfalsifiable by generator manipulation
- **Negative**: Applies only to topological pathway; classical and learned pathways lack equivalent mathematical guarantees
- **Implication**: The topological pathway has a unique epistemological status in the framework — the only pathway with formal invariance proof

---

## ADR-013: Severe Testing Protocol

**Status**: Accepted
**Date**: February 2026

### Context

Standard adversarial tests (Chapter 23) challenge the representation but are not designed with maximum *severity* — they test robustness, not the system's ability to detect its own failure.

### Decision

Design adversarial tests following Mayo's severe testing framework (2018): tests are severe when they are **highly capable of detecting failure** had the claim been false.

### Severe Testing Criteria

For each adversarial test, document:
1. **The claim being tested** (what would it mean if this fails?)
2. **The severity assessment** (how likely is failure if the claim is false?)
3. **The severity score** (0-1, where 1 = maximally capable of detecting failure)

### Proposed Severe Tests (Beyond Chapter 23)

| Test | Target Claim | Severity Mechanism |
|---|---|---|
| **Adversarial generator design** | H₁ captures geological essence | Construct a generator producing matched H₁ but different geological process |
| **Feature disentanglement attack** | H₁ features are not independently manipulable | Try to change H₁ without changing geological meaning |
| **Noise at critical scales** | PH features are robust at meaningful scales | Add noise specifically at filtration-critical scales |
| **Cross-domain transfer** | PH invariance is mathematical, not domain-specific | Apply same PH pipeline to music/neural data; if it fails to capture structure, mathematical universality claim is weakened |

### Literature Evidence

- Mayo, D. G. (2018). *Statistical Inference as Severe Testing*.
- Popper, K. (1963). *Conjectures and Refutations*: A theory is corroborated by passing tests that were genuinely risky.

---

## ADR-014: Information-Theoretic Validation

**Status**: Proposed
**Date**: February 2026

### Context

Neither LOGO (pass/fail) nor the stability theorem (mathematical) tells us *what information* the representation captures. Information-theoretic measures provide a continuous, quantitative assessment.

### Decision

Add mutual information-based assessment to the validation protocol:

- $I(f(X); \theta \mid G)$ — geological information captured, independent of generator
- $I(f(X); G \mid \theta)$ — generator-artifact contamination

### Implementation

Use Mutual Information Neural Estimation (MINE; Belghazi et al., 2018) or similar variational bounds to estimate these quantities from finite samples.

### Interpretation

| Measure | High | Low |
|---|---|---|
| $I(f(X); \theta \mid G)$ | ✅ Captures geological information | ❌ Representation uninformative |
| $I(f(X); G \mid \theta)$ | ❌ Contaminated by generator artifacts | ✅ Generator-independent |

### Status

Proposed — requires implementation in Phase 3. See Implementation Spec for details.

---

## ADR-009: Framework Terminology ("Qualia Convergence")

**Status**: Accepted with documented limitations  
**Date**: January 2026

### Context

The framework name "Qualia Convergence" uses terminology from philosophy of mind. "Qualia" technically refers to subjective experiential qualities—what it is like to perceive something. This may invite philosophical scrutiny the framework cannot fully satisfy.

### Decision

Retain "Qualia Convergence" as the framework name, with explicit documentation of:
1. What we do NOT claim (subjective experience capture)
2. Why the term is used (metaphorical, signaling ambition beyond surface statistics)
3. Alternative names if confusion persists

### Alternatives Considered

| Alternative | Description | Assessment |
|-------------|-------------|------------|
| **Retain as-is** | Keep "Qualia Convergence" without clarification | Invites misunderstanding |
| **Rename entirely** | "Essence Convergence" or similar | Loses evocative power; breaks continuity |
| **Retain with documentation** | Keep name, add explicit scope limitations | Chosen approach |

### Rationale

1. The term "Qualia" signals ambition to capture something deeper than surface statistics
2. The "Convergence" component is essential and accurately describes the methodology
3. Explicit documentation (Chapter 4.5 in Complete Vision) prevents misinterpretation
4. Philosophical terminology in framework names is common (cf. "attention," "memory," "reasoning" in ML)

### Consequences

- **Positive**: Evocative name; clear documentation prevents overreach claims
- **Negative**: Requires upfront clarification in any presentation
- **Mitigation**: Chapter 4.5 provides standard language for scope statements

### Revision Triggers

- If reviewers consistently misinterpret the claim despite documentation → consider renaming
- If "Qualia" becomes a distraction in publications → use alternative names in papers

---

## ADR-010: Engagement with Alternative Frameworks

**Status**: Accepted  
**Date**: January 2026

### Context

An external critical review identified several alternative epistemological frameworks that could address similar research goals: phenomenological, semiotic/structuralist, and graph-based approaches. The review questioned whether our approach adequately engages with these alternatives.

### Decision

Acknowledge alternative frameworks in documentation (Chapter 4.5) but do NOT adopt them as primary framing. Instead:
1. Cite relevant prior work (Parcell & Parcell semiotics, TKR patent)
2. Explain why our approach differs
3. Note potential complementarity for future work

### Alternatives Considered

| Alternative | Description | Why Not Adopted |
|-------------|-------------|-----------------|
| **Phenomenological primary** | Ground framework in Husserl's eidetic reduction | Requires introspection; computationally intractable |
| **Semiotic primary** | Build explicit symbol systems for geological signs | Different research direction; complementary not competing |
| **Graph-based (TKR)** | Represent images as topological graphs | Legitimate alternative; could be additional pathway |
| **Ignore alternatives** | No engagement with other frameworks | Intellectually incomplete; invites criticism |

### Rationale

1. **Pragmatic operationalism** is our core stance—define essence by what tests measure
2. Alternative frameworks address different questions (subjective experience, symbolic meaning)
3. Engagement demonstrates awareness without scope creep
4. TKR specifically noted as potential future pathway (graph-based analog retrieval)

### Consequences

- **Positive**: Intellectually honest engagement; clear positioning; identifies future work
- **Negative**: Some may wish for deeper philosophical treatment
- **Mitigation**: Framework makes testable claims; philosophical depth can be added in future work

### Literature Evidence

- Parcell & Parcell (2009): Semiotic analysis applied to stratigraphy
- Chawshin et al. (2021): TKR patent demonstrates graph-based alternative
- Frodeman (1995): Geological reasoning as interpretive science

### Revision Triggers

- If TKR-style graph features prove valuable in ablation → integrate as fourth pathway
- If semiotic framing gains traction in geoscience ML → reconsider positioning

---

# Part III: Simplification Decisions

## ADR-S01: Phase 1 Simplification — Frozen DINOv2

**Status**: Accepted for Phase 1  
**Date**: January 2026

### Decision

Start Phase 1 with **frozen DINOv2** (no fine-tuning).

### Rationale

- Query 7 shows "near-perfect accuracy" without fine-tuning
- Faster iteration in Phase 1
- Establishes baseline before adding complexity

### Upgrade Trigger

- If cluster purity < 0.5 with frozen features → add LoRA fine-tuning

---

## ADR-S02: Phase 1 Simplification — Euclidean Baseline

**Status**: Accepted for Phase 1  
**Date**: January 2026

### Decision

Implement **Euclidean embeddings first**, hyperbolic as Phase 3 addition.

### Rationale

- Simpler optimization
- Establishes baseline for hyperbolic comparison
- Reduces Phase 1 complexity

### Upgrade Trigger

- Phase 2 complete → add hyperbolic
- If hierarchy preservation critical early → accelerate

---

## ADR-S03: Phase 1 Simplification — Deterministic Query Encoding

**Status**: Accepted for Phase 1  
**Date**: January 2026

### Decision

Start with **deterministic SetEncoder**, Neural Process as Phase 3 addition.

### Rationale

- Simpler training
- Establishes retrieval baseline
- NP complexity deferred until retrieval working

### Upgrade Trigger

- Phase 2 complete → add Neural Process
- If uncertainty quantification critical early → accelerate

---

## ADR-S04: TDA as Ablation Study (with Mathematical Invariance Note)

**Status**: Accepted (with February 2026 addendum)
**Date**: January 2026 (addendum February 2026)

### Decision

Treat TDA pathway as **ablation study component**, not core claim, until H₁ hypothesis validated.

### Rationale

- H₁ hypothesis (discriminates channel types) unvalidated
- If hypothesis fails, TDA becomes liability not asset
- Ablation framing protects core claims

### Upgrade Trigger

- If H₁ hypothesis validated → TDA becomes core pathway
- If H₁ hypothesis fails → document as negative result

### Addendum (February 2026): Unique Epistemic Status of TDA

Regardless of the H₁ hypothesis outcome, the topological pathway has a **unique epistemic property** among the three pathways: the stability theorem (ADR-012) provides a mathematical proof of invariance that the classical and learned pathways lack. This means:

1. **Even if H₁ fails as a discriminator**, the topological pathway still provides the strongest invariance guarantee in the framework
2. **The ablation question is about relevance (does H₁ discriminate?), not invariance (are PH features stable?)** — relevance is empirical, invariance is proven
3. **If H₁ fails**, the pathway may still be valuable for other reasons: invariance under LOGO, robustness characterization, or as a regularizer that encourages the learned pathway toward topologically stable features

The TDA pathway is the only pathway where the invariance claim rests on mathematical proof rather than empirical testing. This makes it the natural "backbone" for the framework's essence argument, independent of the H₁ classification result.

---

# Part IV: Decision Dependencies

```
ADR-001 (Three Pathways)
    │
    ├── ADR-004 (DINOv2) ← Learned pathway architecture
    │       └── ADR-S01 (Frozen first)
    │
    ├── ADR-S04 (TDA Ablation) ← Topological pathway framing
    │
    └── ADR-006 (Fusion) ← How to combine pathways

ADR-002 (Hyperbolic)
    │
    └── ADR-S02 (Euclidean first)

ADR-003 (Neural Process)
    │
    └── ADR-S03 (Deterministic first)

ADR-005 (Generator)
    │
    └── ADR-008 (LOGO) ← Generator enables LOGO test

ADR-007 (Sākṣī)
    │
    └── ADR-008 (LOGO) ← LOGO is primary Sākṣī test
```

---

# Part V: Literature Evidence Summary

| Decision | Supporting Queries | Key Finding |
|----------|-------------------|-------------|
| ADR-001 (Three Pathways) | 3, 7 | TDA exists, DINOv2 validated |
| ADR-002 (Hyperbolic) | 1 | No geological implementation exists |
| ADR-003 (Neural Process) | 2 | Used for interpolation, not retrieval |
| ADR-004 (DINOv2) | 7 | "Near-perfect accuracy" on geology |
| ADR-005 (Generator) | 14, 15, 16, **17, 18, 19, 20** | Distinct category; interpretable; fills gap; different from deep generative |
| ADR-006 (Fusion) | — | Standard ML practice |
| ADR-007 (Sākṣī) | 10 | More comprehensive than existing |
| ADR-008 (LOGO) | 8 | More stringent than domain adaptation |
| ADR-009 (Terminology) | External critique | Metaphorical use of "qualia" documented |
| ADR-010 (Alternative Frameworks) | External critique | Parcell & Parcell, TKR patent engaged |

---

# Part VI: Revision History

| Date | Decision | Change | Reason |
|------|----------|--------|--------|
| 2026-01 | All | Initial record | Framework consolidation |
| 2026-01 | ADR-005 | Added Queries 17-18 | Validates generator approach; addresses benchmark gap |
| 2026-01 | ADR-005 | Added Query 19 | Confirms distinct niche in aeolian/estuarine simulator landscape |
| 2026-01 | ADR-005 | Added Query 20 | Deep generative models solve different problem (surrogate simulation) |
| 2026-01 | ADR-009 | Added | Address terminology concerns from critical review |
| 2026-01 | ADR-010 | Added | Engage with alternative frameworks (semiotic, TKR) |
| 2026-02 | ADR-008 | Revised | Demoted LOGO from primary to necessary-but-insufficient; added limitations citing impossibility results |
| 2026-02 | ADR-012 | Added | Mathematical invariance as primary evidence for topological pathway |
| 2026-02 | ADR-013 | Added | Severe testing protocol following Mayo's framework |
| 2026-02 | ADR-014 | Added | Information-theoretic validation (MI-based) |
| 2026-02 | ADR-S04 | Addendum | Unique epistemic status of TDA pathway via stability theorem |

---

# Part VII: Open Questions

1. **Product manifolds**: When does hyperbolic × Euclidean become worth the complexity?

2. **Multi-scale TDA**: Should we use multi-scale persistent homology?

3. **Real data integration**: How much real data is needed for validation?

4. **Generator independence verification**: How do we formally verify that generators in the LOGO pool are genuinely independent in their assumptions? What constitutes "sufficient diversity" for LOGO to be informative? (See ADR-008 limitations)

5. **Information-theoretic thresholds**: What values of $I(f(X); \theta \mid G)$ and $I(f(X); G \mid \theta)$ distinguish essence-capturing from artifact-contaminated representations? (See ADR-014)

6. **Causal structure of geological features**: Can we construct a causal graph relating geological parameters to observable features, such that invariance follows from causal structure rather than empirical testing? This would transcend both LOGO and the stability theorem.

7. **Cross-domain universality**: If PH features capture invariant structure in geology AND music/neuroscience, what does this tell us about the nature of "essence"? Is mathematical universality evidence for domain-specific relevance?

8. **Computational scaling**: How does the system scale to 1M+ analogs?

9. **3D extension**: What changes for volumetric geological patterns?

10. **Graph-based pathway**: Should TKR-style graph features be integrated as a fourth pathway?

---

*Architecture Decision Record — Version 1.1*
*January 2026*

**Document Purpose**: Document reasoning behind architectural choices.
**Companion Documents**: Complete Vision (what to build), Implementation Specification (how to build it)
