# Addons and Suggestions for Hoydic_Persistent_Homology_Informal.docx

**Purpose**: This document provides suggested continuations, additions, and structural notes for Corey's in-progress advisor writeup. Nothing here should be pasted verbatim — it's raw material to rewrite in your own voice.

**Your document's current structure** (as I read it):

1. Intro/motivation (~2 paragraphs)
2. Why topology? Geostatistics vs. MPS vs. learned features (~2 paragraphs)
3. Math foundations: topological spaces → homeomorphism → homotopy → metric spaces → point clouds → simplicial complexes → cubical complexes → chain groups → boundary maps → chain complexes → cycles → kernel/image
4. **"Continue here later.."** ← YOU ARE HERE
5. Two-pipeline architecture (appears twice — two drafts)

---

## 1. Where You Stopped and What Comes Next

You ended right after defining cycles ($\ker(\partial_k)$) and boundaries ($\textrm{im}(\partial_{k+1})$), and you wrote: "But not every cycle is a boundary. Thus, this is where topology lives."

The next pieces, in order:

### 1a. Homology Groups (the punchline of the algebra)

The $k$-th homology group is the quotient:

$$H_k(K) = \ker(\partial_k) \,/\, \textrm{im}(\partial_{k+1})$$

This captures the $k$-dimensional cycles that are *not* boundaries — the genuine "holes." Two cycles that differ by a boundary are equivalent (they enclose the same hole).

**Suggested worked example** (you could use the three-wells triangle you set up in your chain groups section):
- The loop $\gamma = [v_0, v_1] + [v_1, v_2] + [v_0, v_2]$ is a cycle (boundary = 0)
- If the triangle is *filled* (2-simplex exists): $\gamma = \partial_2([v_0, v_1, v_2])$, so it's a boundary → trivial in $H_1$ → no hole
- If the triangle is *unfilled* (only edges): $\gamma$ is a cycle but not a boundary → nontrivial $H_1$ → genuine hole

This concrete example makes the quotient group intuitive.

### 1b. Betti Numbers

The rank of each homology group, $\beta_k = \textrm{rank}(H_k)$:

| Betti Number | What It Counts | Geological Interpretation |
|---|---|---|
| $\beta_0$ | Connected components | Isolated channel bodies, separate sand bodies |
| $\beta_1$ | Loops / 1-dimensional holes | Channel network loops, oxbow lakes, braiding |
| $\beta_2$ | Enclosed voids | 3D enclosed cavities (pore-space analysis) |

**Key point for your writeup**: $\beta_1$ is the critical Betti number for our research. A braided system has many $H_1$ features (channel loops); a meandering system has few. This is the topological difference that variograms miss entirely and that MPS captures only implicitly.

### 1c. From Homology to Persistent Homology

A single complex at a fixed threshold captures topology at only one scale. But what threshold do we choose? Too small → disconnected scatter. Too large → everything merges into one blob.

**The answer**: don't choose. Compute topology at *every* scale and track how features evolve.

- **Filtration**: a nested sequence $K_0 \subseteq K_1 \subseteq \cdots \subseteq K_n$ obtained by gradually increasing the scale parameter
- **Birth/death**: features are *born* (new cycle appears) and *die* (cycle becomes a boundary as higher-dimensional simplices fill it in)
- **Persistence** = $[b, d]$ interval. Long-lived features = genuine structure. Short-lived = noise.
- **Visualization**: persistence barcodes (horizontal bars) or persistence diagrams (points $(b,d)$ in the plane, far from diagonal = significant)

**Structure theorem**: the persistent homology of any finite filtered complex is *completely* characterized by a multiset of birth-death intervals. Persistence diagrams are a complete invariant.

### 1d. Vectorization

Persistence diagrams aren't in a Hilbert space, so they can't directly enter ML pipelines. Three main vectorization methods:
- **Persistence landscapes** (Bubenik, 2015): map to a Banach space, supports statistical hypothesis testing
- **Persistence images** (Adams et al., 2017): weighted Gaussian kernels → fixed-dimensional vectors
- **Persistence entropy** (Atienza et al., 2020): compress to a single scalar per homological dimension

These produce the 20–50-dimensional topological feature vectors that enter the fusion layer.

---

## 2. The Stability Theorem (THE KEY SECTION)

This is the most important section of your writeup — it's the reason PH is epistemically privileged. You should give it its own heading.

Cohen-Steiner, Edelsbrunner, and Harer (2007) proved:

$$d_B(\textrm{Dgm}(f), \textrm{Dgm}(g)) \leq \lVert f - g \rVert_\infty$$

In plain language: small changes to the input produce small, bounded changes to the persistence diagram. This is a *theorem*, not an empirical observation.

**Why this matters for your argument** (connect back to Aghari-Krishna's challenge):
- Variogram stability under perturbation? Empirical, not proven.
- DINOv2 stability under generator shift? Empirical, depends on training distribution.
- PH stability? Mathematical theorem. Holds universally.

**What it does NOT establish**: relevance. PH features could be stable but irrelevant. This is where the $H_1$ hypothesis comes in — if $H_1$ features discriminate braided from meandering on variogram-matched pairs AND are provably stable, you have *both* mathematical invariance AND geological relevance. That two-level warrant is the strongest evidence structure in the hierarchy.

---

## 3. SEDT Filtration and Cubical Complexes (Design Choices)

You should briefly justify two design choices:

**Why cubical complexes**: Your input data are regular pixel grids. Cubical complexes treat each pixel as an elementary square and build filtrations by thresholding pixel values. This avoids the quadratic memory cost of Vietoris-Rips on 65,536-point images.

**Why SEDT**: The Signed Euclidean Distance Transform assigns each pixel a signed distance to the nearest facies boundary (positive inside channels, negative in floodplain). This is geologically motivated — thick channel cores get high values, thin connections get values near zero. A loop that persists across a wide SEDT range is a robust braided network; one that dies quickly is noise or an artifact.

---

## 4. The New Extensions (from March 2026 advisor meeting)

These three sections would come after the pipeline/compatibility section. They represent where the framework has grown since you started writing.

### 4a. Response Essence (structural → dynamic)

The ultimate purpose of retrieval is to find analogs that *behave like* the target, not just *look like* it. Frame this as: does shared structural essence imply shared response essence?

Key ideas to cover:
- Reservoir simulation IS a state-space dynamical system: $x_{k+1} = f(x_k, u_k)$
- Takens embedding reconstructs attractor topology from time series
- Moon et al. (2019): PH of pore structure predicts macroscopic flow — direct evidence for the link
- Morse-Smale decomposition formalizes "same qualitative dynamic behavior"
- Formation dynamics: meandering = self-organized criticality (Stolum), Leopold-Wolman threshold = bifurcation boundary, delta lobes = limit cycles
- Equifinality caveat: different processes can produce similar structural PH (Phillips, 2006)

### 4b. Confidence Hierarchy (PH as epistemic anchor)

The three pathways produce features of *different epistemic status* — no prior work exploits this asymmetry.

Key ideas:
- Tier 1 (Proven): PH features — stability theorem
- Tier 2 (Corroborated): Features all three pathways agree on (SLIDE joint component)
- Tier 3 (Empirically invariant): Pass LOGO but low CKA with PH
- Tier 4 (Uncertain): Unique to one pathway
- Operationalized via CKA alignment → SLIDE decomposition → Dempster-Shafer evidence combination
- DST handles asymmetric reliability (belief/plausibility gap encodes ignorance)

### 4c. Uncertainty Quantification (feature residuals → calibrated retrieval)

Don't discard DINOv2 features that don't align with PH — DeCUR proves they carry meaningful information.

Key ideas:
- DeCUR separates DINOv2 into PH-aligned and PH-residual
- Kotelevskii et al. (2025): decompose residual into aleatoric/epistemic per dimension
- Hedged instance embeddings: analogs as distributions, not points
- Pipeline A stores analogs with tiered confidence + uncertainty envelopes
- Pipeline B's Neural Process encoder gets structured priors (tight on Tier 1, diffuse on Tier 4)
- Connects to Scheidt, Li & Caers (2018) distance-based subsurface uncertainty

---

## 5. Structural Notes on Your Current Draft

### 5a. Duplicate pipeline section

You have two versions of the pipeline/compatibility section at the end. The first (with "Pipeline A" / "Pipeline B" / "The Compatibility Problem" headers) is more structured. The second (starting "The practical question is: how does persistent homology actually serve the dual cataloguing and indexing architecture...") is rewritten in a more natural voice.

**Suggestion**: The second version reads better as *your* voice. Consider keeping the second version and folding in any details from the first that the second omits (the "Discuss this with Dr. Srinivasan" note at the end is a nice personal touch to keep).

### 5b. Math notation in Word

Since math notation was the bottleneck: consider writing the math-heavy sections (homology groups, persistence, stability theorem) in a markdown file first, then pasting into Word. Word's equation editor is painful for chains of definitions. Alternatively, you can write inline LaTeX and convert later — the concepts matter more than the typesetting for an informal advisor writeup.

### 5c. Section headings

Your document currently has no section headings — it reads as continuous prose. For a ~5-page writeup for your professor, even informal headings would help navigation. Suggested structure:

1. **The Motivating Problem** (your current intro + why topology)
2. **The Mathematical Framework** (topological spaces through persistent homology)
3. **Stability: Where Mathematical Proof Replaces Empirical Hope** (the stability theorem)
4. **Application: The Two-Pipeline Architecture** (your pipeline sections)
5. **Extensions: Dynamic Essence, Confidence, and Uncertainty** (the new material)
6. **What Remains Open** (honest limitations)

### 5d. The Aghari-Krishna quote

This is a strength of your writeup — keep it. It gives the whole document a narrative arc: the challenge is posed early, and the answer (PH's stability theorem) arrives as the resolution. You might even reference it again when you introduce the stability theorem: "This is my answer to Aghari-Krishna's challenge..."

---

## 6. Suggested References to Add

These are papers cited in the dissertation chapter that your writeup should reference where relevant:

| Paper | Where to cite |
|-------|---------------|
| Cohen-Steiner, Edelsbrunner, & Harer (2007) | Stability theorem section |
| Adams et al. (2017) | Vectorization (persistence images) |
| Bubenik (2015) | Vectorization (persistence landscapes) |
| Moon et al. (2019) | Response essence — PH predicts flow |
| Stolum (1996) | Formation dynamics — meandering as attractor |
| Phillips (2006) | Equifinality caveat |
| Kornblith et al. (2019) | CKA for confidence hierarchy |
| Wang et al. (2024) — DeCUR | Uncertainty quantification |
| Scheidt, Li & Caers (2018) | Distance-based subsurface uncertainty |
| Kendall & Gal (2017) | Aleatoric vs. epistemic uncertainty |
