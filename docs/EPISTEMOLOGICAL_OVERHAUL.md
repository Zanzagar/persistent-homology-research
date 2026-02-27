# Epistemological Overhaul: Restructuring the Evidence Hierarchy for Essence Claims

**Author**: Corey James Hoydic
**Date**: February 2026
**Status**: Draft — Blueprint for updating QCF core documents

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

## 3. Specific Changes to Each Document

### 3.1 Changes to COMPLETE_VISION_v5.md

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

### 3.2 Changes to ARCHITECTURE_DECISIONS_v1.md

| ADR | Change | Rationale |
|-----|--------|-----------|
| ADR-008 (LOGO) | Add "Limitations" section citing impossibility results; revise "Rationale" to position LOGO as necessary-but-insufficient | Currently no limitations |
| New ADR-012 | "Mathematical Invariance as Primary Evidence" — decision to foreground PH stability theorem over empirical LOGO for topological pathway | New architectural decision |
| New ADR-013 | "Severe Testing Protocol" — decision to design adversarial tests for severity (Mayo), not just challenge | New architectural decision |
| New ADR-014 | "Information-Theoretic Validation" — decision to add MI-based assessment of what representations capture | New architectural decision |
| ADR-S04 (TDA as Ablation) | Update to reflect that TDA has *mathematical* invariance guarantees (stability theorem) that other pathways lack — strongest candidate for promotion from ablation to core | Currently frames TDA as unvalidated |
| Open Questions | Add: "How do we verify generator independence for LOGO?" and "What information-theoretic threshold distinguishes essence from artifact?" | Currently missing these questions |

### 3.3 Changes to IMPLEMENTATION_SPEC_v6.md

| Section | Change | Rationale |
|---------|--------|-----------|
| Phase 2 (TDA) | Add step: compute and report stability bounds for topological features | Currently just computes PH; doesn't exploit stability theorem |
| Phase 3 (Validation) | Restructure validation order: (1) mathematical invariance check, (2) severe testing, (3) LOGO, (4) information-theoretic measures | Currently LOGO-first |
| Decision Point 3.3 | Revise: LOGO pass alone insufficient for strong invariance claim; require corroboration from severity and/or mathematical invariance | Currently LOGO alone determines outcome |
| New section | "Severe Testing Protocol" — implementation details for adversarial generator construction and severity assessment | Does not exist |
| New section | "Information-Theoretic Validation" — MINE-based MI estimation implementation | Does not exist |

---

## 4. Impact on the Persistent Homology Paper

The paper draft should be rewritten to reflect the updated framework:

1. **Section 3 (Operationalizing Essence)**: Lead with the philosophical critique of LOGO, present the restructured evidence hierarchy, then show how PH's stability theorem provides the strongest available evidence for the topological pathway
2. **Section 5 (Open Questions)**: Expand significantly — the philosophical robustness of invariance testing is THE central open question, not a footnote
3. **New section**: Cross-domain validation as evidence for mathematical universality
4. **Tone shift**: From "LOGO validates essence" to "mathematical structure provides the strongest evidence; empirical testing provides corroboration; honest acknowledgment of what remains unresolved"

---

## 5. Key References for the Overhaul

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

---

## 6. Summary: What Changes and What Stays

### What Changes
- LOGO demoted from primary to necessary-but-insufficient evidence
- Mathematical invariance (stability theorem) promoted to primary evidence for topological pathway
- New evidence levels added: severe testing, information-theoretic measures, cross-domain validation
- Explicit acknowledgment of impossibility results and independence conditions
- The *tone* of the essence claim: from "LOGO validates essence" to "mathematical + empirical + philosophical evidence converges, with honest limitations"

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
**After**: "We define essence operationally as what satisfies a convergence of evidence: mathematical invariance guarantees, survival of severe testing, information-theoretic confirmation of content, cross-domain universality, generator-independence (LOGO), and expert agreement. No single test is sufficient; the convergence of independent evidence streams is the warrant for the claim."

This is both more honest and more powerful than the original position.
