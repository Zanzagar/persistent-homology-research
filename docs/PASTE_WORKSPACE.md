# Paste Workspace

**Purpose**: Ready-to-paste paragraphs and passages for Corey's Word writeup. Written in his voice — rewrite as needed before pasting. Uses LaTeX notation ($\beta_1$, $\partial_k$, etc.) so Word's equation editor auto-converts on paste.

---

## Section Headers (paste into Word as Heading styles)

1. Introduction: The Essence Problem
2. The Motivating Gap: Why Topology?
3. The Mathematical Framework
3.1 Homeomorphism and Homotopy
3.2 Metric Spaces and Point Clouds
3.3 Simplicial and Cubical Complexes
3.4 From Shapes to Algebra: Chains, Boundaries, and Homology
3.5 A Worked Example: Three Wells
3.6 Betti Numbers
4. Persistent Homology: Tracking Features Across Scales
5. The Stability Theorem
6. Application: Design Choices and the Two-Pipeline Architecture
7. What Remains Open

---

## Betti Numbers (paragraph form)

The homology groups are quantified by Betti numbers — the rank of each homology group, denoted $\beta_k$. Each Betti number counts a different dimension of topological feature. $\beta_0$ counts connected components: in a geological context, these are isolated channel bodies or separate sand bodies. $\beta_1$ counts loops, or one-dimensional holes: these correspond to channel network loops, oxbow lakes, and the braiding patterns that distinguish one fluvial architecture from another. $\beta_2$ counts enclosed voids: three-dimensional cavities relevant to pore-space analysis. For our research, $\beta_1$ is the critical Betti number — a braided system has many independent loops (high $\beta_1$), while a meandering system has few (low $\beta_1$). This is the topological difference that variograms miss entirely and that MPS captures only implicitly through template reproduction, without extracting it as a formal, stable descriptor.

---

## Section: From Betti Numbers to Persistent Homology

Betti numbers give us a precise count of topological features at a single scale — but this raises an immediate question: which scale? The construction of a simplicial or cubical complex requires a threshold parameter, and different thresholds produce different complexes with different Betti numbers. Choose too small a threshold, and the data is a disconnected scatter with no discernible structure. Choose too large, and everything collapses into a single connected mass where all loops have been filled in. There is no principled way to select a single "correct" threshold, and any fixed choice discards information about how the topology evolves across scales. The resolution is to abandon the idea of choosing altogether: instead, we compute homology at every scale simultaneously and track how topological features are born, persist, and eventually die as the threshold increases. This is persistent homology — and the transition from a single snapshot of topology to a complete multi-scale record is what gives the method its power.

A filtration is a nested sequence of complexes:

$K_0 \subseteq K_1 \subseteq K_2 \subseteq \cdots \subseteq K_n$

obtained by gradually increasing the scale parameter $\epsilon$. For point clouds, this means increasing the connection radius in the Vietoris-Rips construction: at small $\epsilon$, only very close points are connected; as $\epsilon$ grows, more edges, triangles, and higher-dimensional simplices appear. For images with cubical complexes (which is our case), this means sweeping through pixel-value thresholds — specifically, through the values of the signed Euclidean distance transform (SEDT) that we will discuss in the design choices section.

As $\epsilon$ increases, topological features are born and die. A feature is born when a new cycle appears that is not a boundary of any existing simplex — for example, when edges connect to form a closed loop for the first time. A feature dies when a cycle becomes a boundary because a higher-dimensional simplex fills it in — for example, when a triangle fills in a loop, or when two previously separate connected components merge. The persistence of a feature is the interval $[b, d]$ between its birth time $b$ and death time $d$. The key interpretive principle is this: long-persisting features are genuine structural properties of the data, while short-lived features are noise or artifacts of discretization. A loop that appears at scale $\epsilon = 2$ and dies at scale $\epsilon = 50$ is a robust, large-scale structural feature of the channel network. A loop that appears at $\epsilon = 10$ and dies at $\epsilon = 11$ is likely noise.

These birth-death intervals are visualized in two equivalent formats. Persistence barcodes represent each feature as a horizontal bar whose length equals the persistence $d - b$; longer bars correspond to more significant features. Persistence diagrams plot each feature as a point $(b, d)$ in the plane, where the diagonal $y = x$ represents zero persistence — features far from the diagonal are significant, features near the diagonal are noise. Both representations encode the same information, but persistence diagrams are more commonly used in practice because distances between them (the bottleneck distance and the Wasserstein distance) have well-studied mathematical properties.

The structure theorem for persistence modules guarantees that the persistent homology of any finite filtered complex is completely characterized by such a multiset of birth-death intervals (Chazal et al., 2016; Oudot, 2015). This means persistence diagrams are a complete invariant of the filtration's topology — no topological information is lost. The persistence diagram is, in a precise sense, the full topological fingerprint of the data at all scales simultaneously.

There is one practical challenge: persistence diagrams live in a metric space (under the bottleneck or Wasserstein distance) that is not a Hilbert space, which means they cannot directly enter most machine learning pipelines as feature vectors. Several vectorization methods bridge this gap. Persistence landscapes (Bubenik, 2015) map diagrams into a Banach space that supports statistical hypothesis testing. Persistence images (Adams et al., 2017) apply weighted Gaussian kernels to produce fixed-dimensional vectors. Persistence entropy (Atienza et al., 2020) compresses diagrams to a single scalar per homological dimension via Shannon entropy. These vectorizations produce the 20–50-dimensional topological feature vectors that will enter the fusion layer of our architecture, where they are combined with geostatistical and learned features.

---

## Section: The Stability Theorem — Where Mathematical Proof Replaces Empirical Hope

Now we arrive at the property that, in my view, makes persistent homology not just useful but epistemically privileged for this research program: the stability theorem.

Cohen-Steiner, Edelsbrunner, and Harer (2007) proved that for tame functions $f$ and $g$:

$d_B(\textrm{Dgm}(f), \textrm{Dgm}(g)) \leq \|f - g\|_\infty$

where $d_B$ is the bottleneck distance between persistence diagrams and $\|f - g\|_\infty$ is the supremum norm (the maximum pointwise difference between the two functions). In plain language: small changes to the input produce small, bounded changes to the persistence diagram. If two geological images differ by at most $\epsilon$ in pixel values — due to noise, measurement error, or generation by different simulators — their persistence diagrams can differ by at most $\epsilon$ in bottleneck distance.

I want to emphasize what kind of statement this is. This is a mathematical theorem, not an empirical observation. It does not depend on which generators we test, which dataset we use, or how many experiments we run. It holds universally. Contrast this with the stability claims we can make about our other two pathways. For variograms, we can observe empirically that small input perturbations produce small variogram changes, but we cannot prove this from first principles for arbitrary perturbations. For DINOv2 embeddings, stability under generator shift is an empirical question whose answers depend on the particular generators tested — it may hold for the generators in our training set but fail for generators we have not yet encountered. The stability of persistent homology features is proven once and holds for all inputs, including inputs we have never seen. This is a fundamentally different kind of epistemic warrant.

Why does this matter for the essence question? Recall that we defined essence as the invariant structure stable under multiple pathways, modalities, and generative processes. When we ask "is this representation invariant?" there are two fundamentally different ways to answer. The first is empirical invariance testing, like the LOGO test (Leave-One-Generator-Out): we cross-validate across generators and measure degradation. This is useful but structurally limited — passing LOGO across $N$ generators proves invariance within that generator family, not geological invariance in general. The generators may share physical assumptions (for example, Leopold-Wolman scaling), and invariance to those shared assumptions is weaker evidence than we might hope. The second way is mathematical invariance theorems: prove from first principles that the representation is stable. This is what the stability theorem provides for persistent homology, and only for persistent homology among our three pathways. This distinction is what elevates the topological pathway from "one of three parallel feature extractors" to "the pathway with the strongest epistemic warrant for invariance."

I want to be precise about what this does and does not establish. The stability theorem guarantees that PH features are invariant — that small perturbations cannot change them dramatically. But it does not guarantee they are relevant — you could have perfectly stable features that are irrelevant to geological classification. This is where the $H_1$ hypothesis comes in: it connects stability to relevance by predicting that $H_1$ features specifically discriminate braided from meandering architectures. If the $H_1$ hypothesis holds (classification accuracy above 70% on variogram-matched pairs), then we have both mathematical invariance and geological relevance. That two-level warrant — stability theorem plus empirical discrimination — is the strongest evidence structure available in our evidence hierarchy.

---

## Section: Design Choices and Implementation in My Research

The final question is: how does persistent homology actually serve the two-pipeline architecture that structures this research? I want to discuss the specific design choices and then sketch how the pieces fit together.

**Why cubical complexes instead of Vietoris-Rips.** Our input data are regular pixel grids, not scattered point clouds. Cubical complexes respect this grid structure natively — each pixel is treated as an elementary square (a 2-cube), and the filtration is built by thresholding pixel values. This avoids the quadratic memory cost of constructing a Vietoris-Rips complex from all pairwise distances, which would be prohibitive for $256 \times 256$ images with 65,536 points. The implementation uses Giotto-TDA, which handles cubical complexes efficiently.

**Why the SEDT filtration.** The signed Euclidean distance transform assigns each pixel a signed distance to the nearest facies boundary — positive inside channel bodies, negative inside floodplain. This choice is geologically motivated: filtering by increasing SEDT values progressively erodes narrow connections, revealing which topological features are robust at the core of geobodies versus those that depend on thin, possibly artifactual connections. A loop that persists across a wide range of SEDT values corresponds to a thick, well-connected braided channel network. A loop that dies quickly corresponds to a thin connection that may be an artifact of grid resolution or generator noise. The filtration choice is doing real epistemic work here: it translates the mathematical abstraction of persistence into a geologically interpretable quantity — the physical thickness of the channels that form the loop.

**Pipeline A (Repository/Cataloguing).** Full-resolution analog images — generated by process-based simulators like Flumy (meandering) or BRAHMS (braided) — are encoded via the topological pathway. The SEDT filtration is applied to each image, cubical persistence is computed in $H_0$ and $H_1$, and the resulting persistence diagrams are vectorized into 20–50-dimensional feature vectors. These vectors, combined with classical geostatistical features (~50 dimensions from variogram parameters, MPS template frequencies, etc.) and learned features from DINOv2 (~768 dimensions), are fused and projected into a structured embedding space. The result is a geologic index: a structured database of analogs organized by their invariant structural properties. The persistence diagram hierarchy maps naturally to this organization — images with many long-lived $H_1$ loops are "more braided" and cluster together, distinct from images with few $H_1$ features (meandering).

**Pipeline B (Query/Retrieval).** A geoscientist's query consists of sparse observations: a few well logs, a partial seismic survey, scattered outcrop measurements. These are fundamentally different from the complete images in Pipeline A — they are incomplete, multimodal, and defined on different data structures (1D depth profiles versus 2D images). A Neural Process encoder maps these sparse inputs to a distribution $(\mu, \sigma)$ in the same embedding space — not a point estimate, but a calibrated uncertainty region that degrades gracefully with observation density. More observations tighten the distribution; fewer yield wider uncertainty bounds.

**The compatibility problem.** This is the central architectural challenge, and it is worth stating plainly: the essence representation computed from complete images (Pipeline A) must be compatible with the essence representation inferred from sparse observations (Pipeline B). These two pathways face an information asymmetry. The analog side has complete 2D images from which cubical persistence can be computed directly. The query side has sparse 1D profiles from which $H_1$ features cannot be computed directly — you cannot detect loops in a channel network from three vertical well intersections.

Persistent homology contributes to resolving this compatibility problem in two ways. First, the stability theorem provides a framework for reasoning about how much information about the persistence diagram can be recovered from partial observations — if the sparse data constrains the underlying function $f$ within an $\epsilon$-band, then the persistence diagram is constrained within an $\epsilon$-band as well. Second, the convergence regularization loss across all three pathways enforces that the topological, classical, and learned representations must agree during training — so even if the sparse query encoder cannot directly compute $H_1$, the convergence loss ensures that the learned representation (which can be computed from sparse inputs via the Neural Process encoder) captures information correlated with the topological features. The question of how well this indirect route preserves topological information is empirically testable and is one of the key research questions for the next phase.

**What remains open.** I want to be honest about what this framework does not yet answer. Whether the $H_1$ hypothesis holds at the predicted accuracy level is an empirical question that the next phase of experiments will address. Whether the convergence regularization successfully transfers topological information to the sparse-data encoder is testable but untested. And the extensions discussed with Dr. Srinivasan — response essence, the confidence hierarchy, and uncertainty quantification — are theoretical contributions that will require significant implementation work before they produce empirical results. The mathematical foundations are solid; the experimental validation is the next frontier.

---
