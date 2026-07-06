# Identifiability Integration Plan: Upgrading the Learned Pathway to Level 1 Evidence

**Author**: Corey James Hoydic (with Claude Code research assistance)
**Date**: 2026-04-13
**Status**: Plan document — integration not yet executed. See §4 for planned dissertation edits and §5 for by-hand implementation tasks.

---

## 1. Context

### 1.1 Origin

On April 13, 2026, following a weekend of AI/ML philosophical debate with a friend, a Google search for "state of the art methods to distinguish between essence of signal in latent space 2026" surfaced Chi et al. 2026 — "Disentangled Representation Learning via Flow Matching" (arXiv:2602.05214v1, February 2026). The question became: where does this method fit into, challenge, or shatter the Qualia Convergence Framework's three-pathway architecture, and what verification strength does it have per the evidence hierarchy?

### 1.2 Broadening of the Inquiry

Analysis revealed that Chi et al. addresses *disentanglement* (factor independence via orthogonality regularization), not *essence* (structural invariance across generators) as the QCF defines it. The paper's own framing — "existing diffusion-based methods encourage factor independence via inductive biases, yet frequently lack strong semantic alignment" — shows it proposes a different inductive bias, not an escape from the Locatello et al. (2019) impossibility result for unsupervised disentanglement.

This motivated a broader survey of the identifiability frontier — methods that provide *theorems* (not just inductive biases) about when a learning algorithm provably recovers true generative factors. Three finalists emerged and were analyzed via full-paper fetches.

### 1.3 Core Epistemic Insight

Two types of Level 1 mathematical guarantee exist, protecting against different failure modes:

- **Stability theorem** (Cohen-Steiner et al. 2007): bounds sensitivity to input perturbation via `d_B(Dgm(f), Dgm(g)) ≤ ‖f − g‖_∞`. Protects PH from perturbation noise.
- **Identifiability theorems** (Khemakhem et al. 2020 and descendants): under auxiliary variables or interventions, learned latents provably correspond to true generative factors up to well-defined equivalence classes. Protects learned features from recovering generator-artifact mixtures instead of geological structure.

Both are formal proofs. Both belong at Level 1 of the §8 evidence hierarchy. The QCF currently has the first but not the second. This plan adds the second.

---

## 2. Methods Surveyed

### 2.1 The Entry Point

| Method | Key idea | Evidence level | Decision |
|---|---|---|---|
| Chi et al. 2026 (2602.05214) | Flow-matching with factor-conditioned velocity + orthogonality regularizer | Tier 3-4, no identifiability theorem | Demoted to adversarial counterfactual tool (Path B+) |

### 2.2 The Identifiability Frontier (Finalists)

| Method | Key theorem | Evidence level | Decision |
|---|---|---|---|
| iVAE (Khemakhem et al. 2020, AISTATS) | Affine-equivalence identifiability under auxiliary variable u with exponential-family prior; 2n+1 domains needed | Level 1 | Cited as predecessor to Kong et al. |
| Kong et al. 2025 (2503.00639, preprint) | Theorem 1 (subspace identifiability) + Theorem 2 (component-wise identifiability); relaxes exponential family; fewer domains (2\|z_a\|+1) via sparse mixing | Level 1 | **PRIMARY — integrate as CG-VAE** |
| Brady et al. 2025 ICLR (2411.07784) | Interaction asymmetry via (n+1)th-order derivative block-diagonality; identifies up to slot permutation + slot-wise diffeomorphism; single-view training | Level 1 | Cite only (wrong data shape — object-centric, single-view wastes multi-generator data) |
| Unifying CRL ICLR 2025 (2409.02772) | Invariance-to-identifiability framework; generalizes iVAE; mix-and-match across environment partitions | Level 1 (framework) | **FRAMEWORK — use to reframe §10.3 LOGO** |
| von Kügelgen et al. 2021 (NeurIPS) | Content-style provable separation via augmentations | Level 1 (different data shape) | Cite in §5 and §8 |

### 2.3 Adjacent Domain Work

| Method | Relevance | Decision |
|---|---|---|
| Geological GAN inversion (2510.17478, Oct 2025) | Latent-space disentanglement of fluvial deposits; no PH, no identifiability theorems; competitor | Cite in §6.11 Related Work |

---

## 3. Decisions Made

### 3.1 Three-Method Strategy

The final recommendation splits the inquiry across three distinct roles, rather than picking a single replacement for Chi et al.:

| Role | Method | Purpose |
|---|---|---|
| Primary algorithm | Kong et al. 2025 (CG-VAE) | Theorem-backed identification of θ from geological images; upgrades Learned Pathway features to Tier 1 for aligned factors |
| Theoretical framework | Unifying CRL ICLR 2025 | Recontextualizes LOGO as approximate interventional CRL with specified assumption-satisfaction conditions |
| Adversarial tool | Chi et al. 2026 (modified with supervised factor training) | Counterfactual image generator for Level 2 severe testing, grounded in Kong et al.'s identifiability rather than Chi's orthogonality regularization |
| Literature citation | Brady et al. 2025 | Frontier on single-view disentanglement theorems |
| Competitor acknowledgment | Geological GAN 2510.17478 | Adjacent work using GAN-based latent-space engineering on fluvial deposits; distinguishes QCF's theorem-backed multi-pathway approach |

### 3.2 Why Kong et al. 2025 is Primary

Four reasons this method fits QCF specifically:

1. **Paired (I, θ) data matches auxiliary structure**: the principle-based generator produces images with known parameter vectors. This is exactly the u in Kong et al.'s A2 (conditional independence of latents given auxiliary).
2. **Empirical formulas are sparse mixing**: Leopold-Wolman (λ = 10–14W), Parker stability (W/d > 50), point-bar geometry (inner bends only), Werner dune parameters — these encode which parameters affect which image regions. This is the sparse mixing structure Kong et al.'s A4 requires.
3. **Fewer domains needed than iVAE**: 2|z_a|+1 domains for identifying subset z_a instead of 2n+1 for all n factors. Practical for a ~15–30 factor space.
4. **Strict generalization of iVAE**: Corollary 1 recovers iVAE's result in the fully-connected case. If Kong et al.'s proofs have issues under peer review, fallback to iVAE is automatic and requires no re-architecture.

### 3.3 Why Brady et al. 2025 is Cite-Only

Despite being theoretically elegant (ICLR 2025, cleanest disentanglement theorem), four reasons it doesn't fit QCF:

1. **No natural slot structure for geology**: channels, floodplains, point bars aren't "slots" in the sense the theorem requires. Force-fitting slots to environment classes collapses the very thing the framework wants to identify.
2. **Single-view training wastes multi-generator data**: the framework *has* multi-generator data; discarding that information to satisfy Brady et al.'s single-view assumption is regressive.
3. **Regularity conditions on Z_supp may fail**: path-connectedness and aligned-connectedness of the latent support could be violated by the constrained manifold M of physically feasible geology.
4. **Object-centric experimental validation only**: Sprites and CLEVR6 datasets. Authors acknowledge "preliminary" validation.

### 3.4 Why Chi et al. 2026 is Demoted to a Tool

The original paper inquiry has value as a controllable counterfactual image generator for severe testing. It does not belong as a standalone feature-extraction method because:

1. No identifiability theorem — only orthogonality regularization (inductive bias)
2. Evaluation metrics (DCI, FactorVAE, MIG) depend on ground-truth factors — circular with the generator's known parameters
3. Doesn't escape the Locatello impossibility — authors fix N=10 "following Locatello et al."
4. Supervised variant (Path B+) is preferable: train with θ as auxiliary, lifting the method into Kong et al.'s identifiability framework rather than relying on orthogonality alone

---

## 4. Changes to the Dissertation

### 4.1 Section 5 (Mathematical Foundations of Self-Supervised Visual Representations)

| Subsection | Change | Rationale |
|---|---|---|
| 5.7 (Epistemic Status) | Add paragraph: "Identifiability as a complementary Level 1 concept. Section 8 introduces identifiability theorems (Khemakhem et al. 2020, Kong et al. 2025) that provide mathematical guarantees *distinct from* but *complementary to* the stability theorem. These theorems bound correspondence between learned and true factors (up to invertible transformation) under auxiliary-variable supervision, addressing the entanglement limitation noted above." | Foreshadows §8 new material without disrupting current §5 flow |
| 5.8 (NEW) | "Supervised identifiable learning with auxiliary generator parameters": introduce CG-VAE framework and Kong et al.'s theorems; explain why this upgrades learned-pathway features to theorem-backed status when trained with θ supervision | Primary new content for the learned pathway |

### 4.2 Section 6 (Application to QCF)

| Subsection | Change | Rationale |
|---|---|---|
| 6.5 (Learned Pathway) | Add subsection: "CG-VAE as supervised identifiable learned pathway" — positions Kong et al. integration within the three-pathway architecture; clarifies that DINOv2 provides unsupervised gestalt while CG-VAE provides theorem-backed identifiability | Establishes the two roles of the Learned Pathway |
| 6.11 (Related Work) | Add paragraph citing geological GAN (2510.17478, Oct 2025) under "Generative models for geological data"; distinguish QCF's theorem-backed approach from their empirical latent-space engineering | Competitor acknowledgment; sharpens QCF's distinctive contribution |

### 4.3 Section 8 (Evidence Hierarchy)

| Subsection | Change | Rationale |
|---|---|---|
| 8.1 (Levels) | Split Level 1 into **Level 1a (stability)** and **Level 1b (identifiability)**. Cite Cohen-Steiner et al. 2007 for 1a; Khemakhem et al. 2020 and Kong et al. 2025 for 1b | Extends Level 1 from PH-only to include theorem-backed learned features |
| 8.X (NEW) | "Stability and identifiability as complementary Level 1 evidence": formal subsection explaining the two types of Level 1 guarantee, what each protects against, how they combine in retrieval | Core theoretical extension of the evidence hierarchy |
| 8.2 (Revised Essence Claim) | Update to reflect two Level 1 evidence streams: PH stability + identifiable learned factors | Tracks the hierarchy extension |
| 8.3 (Descriptor Admissibility) | Update Pipeline A/B validation language: CG-VAE factors passing MCC threshold are admitted at Level 1b; DINOv2 residuals remain at Level 5–7 | Operationalizes the extension |

### 4.4 Section 10 (Sākṣī Validation Framework)

| Subsection | Change | Rationale |
|---|---|---|
| 10.3 (LOGO Protocol) | Substantially reframe using Unifying CRL vocabulary. LOGO = interventional CRL across generators. Document which invariance assumptions each generator family satisfies. Map to the taxonomy of invariance → identifiability strength. Retain existing impossibility caveats (Ahuja 2023) but frame them within CRL's positive theorems. | Converts LOGO from "empirical test with documented impossibility" to "approximate interventional CRL with specified assumption-satisfaction conditions" |
| 10.4 (Adversarial Tests) | Add new test 10.4.5: "Factor-conditioned counterfactual severity test." Uses Chi et al. 2026 flow-matching model trained with θ supervision to generate per-factor counterfactuals; pre-committed thresholds on per-pathway response specificity | Level 2 severe-testing contribution grounded in Kong et al. identifiability |

### 4.5 Section 14.6 (Confidence Hierarchy: PH as Epistemic Anchor)

| Change | Rationale |
|---|---|
| Extend Tier 1 from PH-only to "PH (via stability theorem) ∪ CG-VAE factors passing MCC threshold (via Kong et al. Theorem 2)" | Upgrades Learned Pathway to split Tier 1 / Tier 3: theorem-backed factors at Tier 1, residuals at Tier 3 |
| Document the distinction: PH Tier 1 provides bounded sensitivity; CG-VAE Tier 1 provides factor correspondence. Both are mathematically guaranteed but protect against different failure modes. | Precision on what each Level 1 guarantee buys |
| Update SLIDE decomposition implications: joint components between PH-Tier-1 and CG-VAE-Tier-1 features are "doubly Level 1" — the highest-confidence class in the system | Extends the asymmetric trust structure |

### 4.6 Section 11 (PH Across Domains)

No changes required — cross-domain validation (Level 4) is orthogonal to identifiability integration.

---

## 5. By-Hand TODO

Items in this section are for Corey to execute personally — proof reading, implementation, experimental design. Ordered from immediate to longer-horizon.

### 5.1 Immediate (weeks 1–3)

- [ ] **Read Kong et al. 2025 supplementary proofs** (arXiv:2503.00639). Focus on:
  - Theorem 1 proof (subspace identifiability): verify the linear-independence condition A3 is stated precisely
  - Theorem 2 proof (component-wise identifiability): understand the second-order derivative argument
  - Corollary 1 (fully-connected case): confirm reduction to iVAE's 2n+1 bound
- [ ] **Verify assumptions A1–A5 against principle-based generator**:
  - A1 (smooth positive density of θ | generator): trivial for continuous parameters
  - A2 (conditional independence of θ components given generator identity): check parameter independence in the generator's sampling
  - A3 (sufficient changes across domains): count generators and parameter ranges; confirm |domains| ≥ |Pa(x_k)|
  - A4 (subset structure): map Leopold-Wolman/Parker/Werner constraints onto sparse mixing structure
  - A5 (fully-connected fallback): if A4 fails, A5 holds trivially, reducing to iVAE guarantees
- [ ] **Decide self-verify vs. iVAE fallback**:
  - Self-verify: stronger relaxation but relies on preprint
  - iVAE fallback: safer publication status, stricter assumptions, more domains required
  - Recommendation: self-verify if Kong et al. proofs check out; document both options in the dissertation

### 5.2 Medium-Term (months 1–3)

- [ ] **Implement CG-VAE on principle-based generator data**:
  - Use Giotto-TDA or equivalent for the PH pathway (already planned)
  - Implement CG-VAE loss: `L_r + αL_s − βL_KL` with `L_s = Σ|∂x̂/∂ẑ|`
  - Domain encoding via normalizing flow on u (categorical = generator identity; continuous = parameter vector)
  - Training data: paired (I, θ) from the generator, spanning all three environments
- [ ] **Compute identifiability-quality metrics**:
  - Mean Correlation Coefficient (MCC) between learned factors and true θ — Kong et al.'s primary metric
  - Per-factor disentanglement score
  - Jacobian sparsity verification (does the learned decoder respect the empirical-formula sparsity?)
- [ ] **Baseline comparisons**:
  - Vanilla iVAE (no sparse mixing) — measures the sparsity benefit
  - Unsupervised Chi et al. 2026 — measures the supervision benefit
  - DINOv2 alone — measures the identifiability benefit beyond gestalt

### 5.3 Longer-Horizon (months 3–12)

- [ ] **Severe testing protocol via Chi et al. + Kong et al.**:
  - Train Chi et al. flow-matching model with θ supervision (supervised variant)
  - Generate per-factor counterfactual images: vary one θ component while holding others fixed
  - Pre-commit severity thresholds per pathway (PH: H₁ specificity to connectivity factors ≥ 3:1; variogram: scale specificity ≥ 5:1; DINOv2: entangled response as control)
  - Run thresholds against counterfactual image pairs; record per-factor pathway response curves
- [ ] **Upgrade §14.6 confidence hierarchy empirically**:
  - Compute CKA between PH features and CG-VAE-Tier-1 features (joint Tier 1 component)
  - Compute CKA between CG-VAE-Tier-1 and CG-VAE-residual features (Tier 1 / Tier 3 split within learned pathway)
  - Update Dempster-Shafer evidence combination to incorporate the new asymmetric trust structure
- [ ] **Response essence integration** (§14.1–14.5):
  - After CG-VAE factor identification works, verify that identified factors predict dynamical response under basin-of-attraction analysis
  - This validates that structural identifiability corresponds to functional behavior
- [ ] **Cross-pathway convergence regularization update**:
  - Current: `L_conv = Σ_{i<j} ‖f_i(x) − f_j(x)‖²` (treats all pathways symmetrically)
  - Revised: weighted by asymmetric trust structure — PH and CG-VAE-Tier-1 features get high weight; DINOv2 residuals lower
  - Instantiates §14.6's asymmetric trust at the training objective level
- [ ] **Peer-review tracking for Kong et al. 2025**:
  - Check quarterly for published version (NeurIPS 2026? ICML 2026?)
  - If accepted, upgrade citation from preprint to published
  - If rejected or problems surface in proofs, implement iVAE fallback

### 5.4 Decision Points Requiring Human Judgment

- [ ] **Factor count N for CG-VAE**: Kong et al. don't specify N; must choose based on the generator's parameter space. Suggested: N = |θ| + 2–4 slack dimensions for residual learned features. Justify choice in the dissertation.
- [ ] **Auxiliary variable encoding**: categorical (generator ID) vs continuous (concatenated θ) vs hierarchical (environment → substyle → parameters). Trade-offs in assumption satisfaction; document the choice made.
- [ ] **Sparsity weight α**: tune via hold-out MCC. Too high: loses expressivity. Too low: no sparsity benefit, reduces to iVAE.
- [ ] **Peer-review decision**: publish the dissertation chapter before Kong et al. is peer-reviewed, or wait? Time/rigor trade-off.

---

## 6. Open Questions

### 6.1 Theoretical

- **How do the two Level 1 guarantees combine when both features are "Tier 1" but protect against different failure modes?** The stability theorem bounds sensitivity; the identifiability theorem bounds correspondence. A feature passing both is robust to perturbation AND correctly identified — but the compositional semantics of "doubly Tier 1" need formal development in §14.6.
- **Does Kong et al.'s sparse mixing assumption (A4) hold for the generator, or is it violated by feature entanglement?** Leopold-Wolman couples λ and W physically. Kong et al. models this as a parameter-pixel sparsity constraint, not a parameter-parameter coupling. The distinction matters: sparse mixing constrains Jacobian structure; physical entanglement constrains the parameter space itself.
- **Can PH and CG-VAE be trained simultaneously on the same backbone?** Both use image-level features. Joint training may break either pathway's guarantees. Separate training is safer but sacrifices shared representations.

### 6.2 Practical

- **Which Flumy/MPS generators satisfy the CRL invariance assumptions?** Document per-generator assumption satisfaction. Some generators may be "informative environments" (different physical assumptions); others may be "confounded environments" (same assumptions, different random seeds).
- **How to prevent the learned pathway from collapsing to DINOv2 or to CG-VAE alone?** The §14.6 asymmetric trust structure assumes both provide complementary information. Verify empirically via SLIDE decomposition.
- **VQ-GAN dependency for Chi et al. counterfactuals**: requires a geological VQ-GAN. Train from scratch on binary facies maps? Use the pretrained one and fine-tune? Skip VQ-GAN and use raw-pixel diffusion?

### 6.3 Publication Strategy

- **If Kong et al. 2025 is rejected or retracted, how to update the dissertation?** Pre-plan the iVAE fallback so the dissertation is robust to peer-review outcomes.
- **Section ordering**: does §8 (evidence hierarchy) come before or after §5 (learned pathway)? Currently §5 comes first; §8 introduces identifiability theorems retroactively. Consider restructuring for logical flow.
- **Related work positioning**: is the geological GAN paper (2510.17478) cited as competitor, precursor, or parallel work? Affects tone of §6.11.

---

## 7. New References

The following citations should be added to the dissertation bibliography:

### 7.1 Primary integrations
- Kong, L., et al. (2025). Synergy Between Sufficient Changes and Sparse Mixing Procedure for Disentangled Representation Learning. arXiv:2503.00639 [preprint].
- Khemakhem, I., Kingma, D. P., Monti, R. P., & Hyvärinen, A. (2020). Variational Autoencoders and Nonlinear ICA: A Unifying Framework. AISTATS.

### 7.2 Framework reference
- (2025). Unifying Causal Representation Learning with the Invariance Principle. ICLR 2025. arXiv:2409.02772.

### 7.3 Adversarial tool
- Chi, J., Liu, T., Yin, M., Li, X., Jing, Y., & Tao, D. (2026). Disentangled Representation Learning via Flow Matching. arXiv:2602.05214.

### 7.4 Frontier citations (not integrated, cite only)
- Brady, J., von Kügelgen, J., Lachapelle, S., Buchholz, S., Kipf, T., & Brendel, W. (2025). Interaction Asymmetry: A General Principle for Learning Composable Abstractions. ICLR 2025. arXiv:2411.07784.
- von Kügelgen, J., Sharma, Y., Gresele, L., Brendel, W., Schölkopf, B., Besserve, M., & Locatello, F. (2021). Self-Supervised Learning with Data Augmentations Provably Isolates Content from Style. NeurIPS.

### 7.5 Competitor
- (2025). Towards geological inference with process-based and deep generative modeling, part 2: inversion of fluvial deposits and latent-space disentanglement. arXiv:2510.17478.

### 7.6 Supporting identifiability literature
- Ahuja, K., Hartford, J., & Bengio, Y. (2023). Invariance & Causal Representation Learning: Prospects and Limitations. arXiv:2312.03580. [already cited in EPISTEMOLOGICAL_OVERHAUL]
- Squires, C., et al. (2023). Linear causal disentanglement via interventions. ICML.
- Brehmer, J., et al. (2022). Weakly supervised causal representation learning. NeurIPS.
- Varici, B., et al. (2024/2025). Score-based causal representation learning. JMLR.

---

## 8. Summary: What Changes and What Stays

### What Changes

- **Learned Pathway gains Level 1 evidence** it currently lacks (via CG-VAE identifiability theorems)
- **LOGO's rationale sharpens** (via Unifying CRL framework) from "empirical with impossibility caveats" to "approximate interventional CRL with specified assumptions"
- **Confidence hierarchy gets two Level 1 sources**: PH (stability) and CG-VAE (identifiability)
- **Chi et al. 2026 is demoted** from standalone method to counterfactual generator for severe testing
- **Brady et al. 2025 is cited** as frontier work, not integrated
- **Geological GAN (2510.17478) is cited** as competitor

### What Stays

- Three-pathway architecture (unchanged — this is method independence, not generator independence)
- Stability theorem as PH's primary invariance guarantee (unchanged)
- LOGO protocol (reframed, not replaced)
- H₁ hypothesis (unchanged)
- Sākṣī validation philosophy (enhanced with identifiability)
- Hyperbolic embedding space (unchanged)
- Generator pillar (unchanged — but its multi-environment nature now has CRL-theoretic justification)

### The Key Philosophical Shift

**Before**: "PH is uniquely Level 1; the learned pathway is inherently Tier 3–4."

**After**: "PH and supervised-identifiable learned features are both Level 1, protecting against *different* failure modes. The convergence of two complementary Level 1 guarantees provides stronger essence justification than either alone, because they rule out different kinds of wrongness."

This is both more honest (acknowledging that PH's stability doesn't bound correspondence, and learned-pathway identifiability doesn't bound perturbation sensitivity) and more powerful (each theorem addresses the other's blind spot).

---

*Document Status: Plan — not yet implemented. See §5 for by-hand tasks and the session handoff at `.claude/sessions/handoff-2026-04-13-identifiability-integration.md` for continuation state.*
