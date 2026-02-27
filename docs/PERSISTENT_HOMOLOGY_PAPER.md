# Persistent Homology and the Operationalization of Geological Essence

### A Topological Framework for the Qualia Convergence Research Program

**Corey James Hoydic**
February 2026

---

## Abstract

Persistent homology (PH) provides a mathematically rigorous framework for extracting multi-scale topological features from complex data, with provable stability guarantees that make it uniquely suited for problems requiring invariant structural characterization. This paper introduces the core mathematical machinery of persistent homology—simplicial complexes, filtrations, homology groups, Betti numbers, and persistence diagrams—and demonstrates *why* these concepts matter, not merely what they are. We examine persistent homology's role within the Qualia Convergence Framework (QCF), a multi-pathway architecture for depositional analog retrieval that seeks to operationalize the concept of geological "essence." We engage critically with the ellipse degradation thought experiment on the nature of essence, proposing that persistent homology's stability properties provide a *mathematical proof* of invariance that is epistemically stronger than any empirical invariance test. We develop this insight into a restructured evidence hierarchy for essence claims, arguing that the Leave-One-Generator-Out (LOGO) protocol—while a necessary check—faces fundamental limitations rooted in impossibility results from causal representation learning, the independence condition from robustness analysis in philosophy of science, and the problem of induction itself. We further explore how PH's domain-agnostic framework extends to music, auditory structure, and neuroscience, using cross-domain applicability as evidence for mathematical universality rather than domain-specific overfitting. We conclude with an honest assessment of what remains unsolved, centering the philosophical robustness of invariance testing as the central open question for the research program.

---

## 1. Introduction to Persistent Homology

### 1.1 From Topology to Data Analysis

Topology is the branch of mathematics concerned with properties of shapes that are preserved under continuous deformations—stretching, bending, and twisting—but not tearing or gluing. While geometry asks "how far apart are these two points?" topology asks "are these two spaces fundamentally the same shape?" The classical illustration is the homeomorphism between a coffee mug and a doughnut: both possess exactly one hole, making them topologically equivalent despite their obvious geometric dissimilarity (Kemmea & Agyingi, 2025). A homeomorphism $f: X \to Y$ is a bijective continuous function with continuous inverse—a formal way of saying "you can deform one into the other without cutting or gluing."

This focus on *invariant structure* rather than metric detail is precisely what makes topology powerful for data analysis. When a geoscientist examines two reservoir images and recognizes both as "braided fluvial systems" despite different scales, orientations, and noise levels, they are performing an intuitive topological classification—recognizing that both images share a structural property (interconnected channel networks) that persists under geometric transformations. The Qualia Convergence Framework seeks to formalize this intuition mathematically.

Topological Data Analysis (TDA) emerged from the recognition that real-world datasets—point clouds sampled from unknown manifolds, images of complex structures, time series of dynamical systems—possess intrinsic *shape* carrying meaningful information beyond what statistical summaries capture. Conventional machine learning approaches rely primarily on statistical relationships, local density estimations, or distance-based measures within datasets (Carlsson, 2009). These methods effectively capture local structure but often fail to detect global topological features—loops, tunnels, voids—that may encode essential characteristics of the data-generating process.

Consider a concrete geological example. A variogram computed from a braided channel system and a variogram computed from a meandering channel system can be nearly identical if the spatial correlation lengths are similar. Yet the two systems have fundamentally different *connectivity*: the braided system contains multiple interconnected channels forming closed loops, while the meandering system has a single sinuous channel. No amount of two-point statistical analysis will distinguish these configurations—the difference is topological, not statistical. Persistent homology is designed precisely to detect such differences.

### 1.2 Topological Foundations: Spaces, Continuity, and Distance

Before constructing simplicial complexes and computing homology, three foundational concepts establish the mathematical ground we stand on. These are not mere technicalities—each one answers a specific question that arises when we try to move from intuitive shape recognition to rigorous computation.

**What is a topological space?** Informally, topology studies what stays the same when you stretch and bend a shape but don't tear it. A *topological space* $(X, \tau)$ consists of a set $X$ and a collection $\tau$ of subsets called "open sets" satisfying three axioms: (1) the empty set $\emptyset$ and $X$ itself are in $\tau$; (2) $\tau$ is closed under finite intersections; and (3) $\tau$ is closed under arbitrary unions (Kemmea & Agyingi, 2025, Definition 1). These axioms formalize the notion of "nearness" without requiring any concept of distance—they define which points are "close together" in a purely structural sense.

The power of this abstraction is visible in the classification of surfaces by *genus* (the number of holes). Imagine holding everyday objects: a marble has genus 0 (no holes); a doughnut has genus 1 (one hole through the center); a pair of scissors has genus 2 (two finger-holes); a cheese grater, with its many perforations, has genus 3 or more. Objects within each genus class are *homeomorphic*—continuously deformable into one another—regardless of their geometric appearance. This is the same kind of invariance we seek in geological pattern recognition: two reservoir images may look different at the pixel level but share the same topological "type."

**When are two spaces "the same shape"?** Homeomorphism (§1.1) tells us when two spaces are topologically identical, but a softer notion—*homotopy*—tells us when two spaces are equivalent in a way that preserves precisely the features homology detects. A *homotopy* between continuous maps $f, g: X \to Y$ is a continuous function $H: X \times [0,1] \to Y$ satisfying $H(x,0) = f(x)$ and $H(x,1) = g(x)$ (Kemmea & Agyingi, 2025, Definition 3). Intuitively, $H$ is a continuous deformation that smoothly morphs one map into another over a "time" parameter $t \in [0,1]$.

This concept motivates homology directly. Imagine a solid disk: you can continuously contract it to a single point by shrinking it inward—it is *contractible*, with no holes to obstruct the contraction. Now imagine a circle (just the boundary, no interior): any attempt to shrink it to a point must at some moment "jump" across the hole in the middle. No continuous deformation can make the circle contractible. Spaces that are *homotopy equivalent* (continuously deformable into each other) have isomorphic homology groups. This is why homology reliably detects holes—they are homotopy invariants, persisting under any stretching, bending, or reshaping short of filling them in.

**How do we measure closeness in data?** Our geological data begins as discrete measurements—pixels in images, depth readings in well logs, scattered outcrop observations—with no inherent topological structure. To build the combinatorial structures on which homology computation depends, we need a principled notion of distance. A *metric space* $(M, d)$ is a set $M$ equipped with a distance function $d: M \times M \to [0, \infty)$ satisfying four properties:

1. *Identity*: $d(x,y) = 0$ if and only if $x = y$
2. *Positivity*: $d(x,y) > 0$ when $x \neq y$
3. *Symmetry*: $d(x,y) = d(y,x)$
4. *Triangle inequality*: $d(x,z) \leq d(x,y) + d(y,z)$

These properties ensure distance behaves as spatial intuition expects: you cannot take a shortcut that beats the direct path. Metric spaces connect topology to data because they provide the threshold-based construction of simplicial complexes discussed in §1.3: two points are connected by an edge when $d(x,y) \leq \epsilon$. Without a metric, there is no principled way to decide which points should be "neighbors"—and thus no way to build the shape-from-data machinery that follows.

### 1.3 Simplicial Complexes: Building Shapes from Data

The bridge from raw data to topological analysis is the *simplicial complex*, a combinatorial structure that systematically builds higher-dimensional shapes from discrete points.

**Definition** (Abstract Simplicial Complex). An abstract simplicial complex $K$ over a vertex set $V$ is a collection of non-empty subsets of $V$ satisfying:
1. Every single vertex $\lbrace v \rbrace$ with $v \in V$ is in $K$.
2. If a set of vertices $\sigma$ belongs to $K$, then all subsets of $\sigma$ also belong to $K$ (closure property).

The building blocks are $k$-simplices: a 0-simplex is a point, a 1-simplex is an edge connecting two points, a 2-simplex is a filled triangle, and a 3-simplex is a solid tetrahedron. More generally, a $d$-dimensional simplex is the convex hull of its $d+1$ vertices:

$$\sigma = \left\lbrace \sum_{i=0}^{d} t_i v_i \;\mid\; t_i \geq 0, \;\sum_{i=0}^{d} t_i = 1 \right\rbrace$$

The closure property is intuitively necessary: if we claim a triangle exists (3 points mutually connected), then its edges and vertices must also exist.

**Why this matters for our research**: Simplicial complexes provide the mathematical scaffolding that allows us to talk rigorously about "shape" in data that is fundamentally discrete (pixel grids, point clouds). Without this structure, we cannot define concepts like "loop" or "connected component" in a way that admits algebraic computation.

**Constructing complexes from data.** For point cloud data in a metric space $(M, d)$, simplicial complexes are constructed by connecting points based on proximity. Given a threshold distance $\epsilon$, the *Vietoris–Rips complex* $\text{VR}_\epsilon$ includes a $k$-simplex whenever all $\binom{k+1}{2}$ pairwise distances among its vertices are at most $\epsilon$ (Otter et al., 2017). As $\epsilon$ increases from zero, isolated points gradually connect into edges, triangles, and higher-dimensional simplices—the data "fills in" and reveals its underlying shape.

For gridded image data—such as geological facies maps where each pixel has a binary value (channel vs. floodplain)—*cubical complexes* provide a computationally more natural and efficient alternative. Instead of constructing simplices from point-pairs, the cubical approach treats each pixel as an elementary square (2-cube) and builds the filtration by thresholding on pixel values (Kaczynski, Mischaikow, & Mrozek, 2004; Wagner, Chen, & Vuçini, 2012). This distinction—Vietoris–Rips for point clouds, cubical for images—is practically important for the QCF, which works primarily with geological images.

### 1.4 Homology: Detecting Holes Algebraically

Homology translates the geometric question "how many holes does this shape have?" into linear algebra. The key insight is that "holes" can be detected by studying *cycles* (closed loops) that are not *boundaries* (edges of filled-in regions).

**Chain groups.** For each dimension $k$, the $k$-simplices of a complex $K$ generate a vector space $C_k(K)$ called the $k$-th *chain group*, with coefficients in the two-element field:

$$\mathbb{Z}_2 = \lbrace 0, 1 \rbrace$$

An element of this group—a $k$-chain—is a formal sum of $k$-simplices:

$$\gamma = \sum_{\sigma} \gamma_{\sigma} \, \sigma, \quad \gamma_{\sigma} \in \lbrace 0, 1 \rbrace$$

Working over $\mathbb{Z}_2$ means a simplex is either "included" (1) or "not included" (0), with the rule that $1 + 1 = 0$ (including a simplex twice cancels it out).

**Faces of simplices.** Before defining boundary maps, we need the concept of a *face*. The faces of a $k$-simplex are the $(k{-}1)$-simplices obtained by dropping one vertex at a time. For example, the triangle $[v_0, v_1, v_2]$ has three faces (edges): $[v_1, v_2]$, $[v_0, v_2]$, and $[v_0, v_1]$—each formed by removing one of the three vertices. Similarly, each edge $[v_i, v_j]$ has two faces (its endpoints): the vertices $v_i$ and $v_j$. Faces are what boundary maps "sum over."

**Boundary maps.** The *boundary map* $\delta_k: C_k(K) \to C_{k-1}(K)$ sends each $k$-simplex to the formal sum of its $(k-1)$-dimensional faces. Over $\mathbb{Z}_2$, this simplifies to:

$$\delta_k(\sigma) = \sum_{i=0}^{k} \sigma_{-i}$$

where $\sigma_{-i}$ denotes the face obtained by removing vertex $i$ (Kemmea & Agyingi, 2025, Definition 9).

**The fundamental property**: $\delta_{k-1} \circ \delta_k = 0$—the boundary of a boundary is always empty. This is not merely a technical convenience; it expresses a deep geometric truth. The boundary of a filled triangle is a closed loop; a closed loop has no boundary (no endpoints). This property is what allows us to *define* holes: they are the cycles that aren't boundaries of anything.

**Worked example: detecting a hole.** Imagine you are looking at three wells arranged in a triangle—call them $v_0$, $v_1$, $v_2$—with edges connecting each pair. The 1-chain $\gamma = [v_0, v_1] + [v_1, v_2] + [v_0, v_2]$ traces a closed loop through all three edges. Applying the boundary map:

$$\delta_1(\gamma) = (v_0 + v_1) + (v_1 + v_2) + (v_0 + v_2) = 0$$

Each vertex appears exactly twice, and $1 + 1 = 0$ in $\mathbb{Z}_2$, so every vertex cancels. The loop has no boundary—it is a *cycle*. Now the critical question: is this cycle a *boundary* of some filled-in region?

- **If the triangle is filled** (the 2-simplex $[v_0, v_1, v_2]$ exists): then $\gamma = \delta_2([v_0, v_1, v_2])$, and the cycle is a boundary. It represents no hole—the interior fills the loop. This cycle contributes nothing to $H_1$.
- **If the triangle is unfilled** (only edges, no face): then $\gamma$ is a cycle that is *not* a boundary of anything. It detects a genuine 1-dimensional hole—an element of $H_1 \neq 0$.

This is exactly how homology works in practice: cycles that bound filled regions are trivial; cycles that enclose genuine holes survive in the homology group.

This property yields the *chain complex*:

$$0 \to C_k(K) \xrightarrow{\delta_k} C_{k-1}(K) \to \cdots \xrightarrow{\delta_1} C_0(K) \to 0$$

**Homology groups and Betti numbers.** The $k$-th *homology group* is defined as:

$$H_k(K) = \ker(\delta_k) \,/\, \textrm{im}(\delta_{k+1})$$

This quotient captures precisely the *k*-dimensional cycles — elements of the kernel of the boundary map — that are **not** boundaries of higher-dimensional simplices. These non-boundary cycles are the genuine topological "holes" in dimension *k*.

The rank of this group is the *k*-th **Betti number** (denoted $\beta_k$), which provides an interpretable summary:

| Betti Number | What It Counts | Geological Interpretation |
|---|---|---|
| $\beta_0$ | Connected components | Isolated channel bodies, separate sand bodies |
| $\beta_1$ | Loops / 1-dimensional holes | Channel network loops, oxbow lakes, braiding |
| $\beta_2$ | Enclosed voids | 3D enclosed cavities (relevant for pore-space analysis) |

For reference, standard shapes have characteristic Betti numbers: a circle has $(\beta_0, \beta_1) = (1, 1)$; a sphere has $(\beta_0, \beta_1, \beta_2) = (1, 0, 1)$; a torus has $(\beta_0, \beta_1, \beta_2) = (1, 2, 1)$; two disjoint circles have $(\beta_0, \beta_1) = (2, 2)$.

**Why this matters for our research**: For geological images, the critical insight is that $\beta_1$ (loop count) directly corresponds to channel network connectivity. A braided system has many loops ($\beta_1$ large); a meandering system has few ($\beta_1$ small). This topological difference is invisible to variograms and other two-point statistics, but homology detects it directly.

### 1.5 Persistent Homology: Tracking Features Across Scales

A single simplicial complex computed at a fixed threshold captures topology at only one scale. But what threshold should we choose? Too small, and the data is a disconnected scatter of points with no interesting topology. Too large, and everything is connected into a single blob. The answer: *don't choose*. Instead, compute topology at *every* scale and track how features evolve.

**Filtrations.** A *filtration* is a nested sequence of complexes:

$$K_0 \subseteq K_1 \subseteq K_2 \subseteq \cdots \subseteq K_n$$

obtained by gradually increasing the scale parameter $\epsilon$. For point clouds, this means increasing the connection radius. For images with cubical complexes, this means sweeping through pixel-value thresholds.

**Birth and death.** As $\epsilon$ increases, topological features are *born* (a new cycle appears that is not a boundary of any existing simplex) and *die* (a cycle becomes a boundary when a higher-dimensional simplex fills it in, or two components merge). The *persistence* of a feature is the interval $[b, d]$ between its birth time $b$ and death time $d$.

The key interpretive principle: **long-persisting features are genuine structural properties; short-lived features are noise.** A loop that appears at scale $\epsilon = 2$ and dies at scale $\epsilon = 50$ is a robust, large-scale structural feature. A loop that appears at $\epsilon = 10$ and dies at $\epsilon = 11$ is likely an artifact of noise or discretization.

**Visualization.** Birth-death intervals are visualized in two equivalent formats:

- *Persistence barcodes*: Horizontal bars whose length equals persistence $d - b$. Longer bars = more significant features.
- *Persistence diagrams*: Points $(b, d)$ in the plane. The diagonal $y = x$ represents zero persistence. Features far from the diagonal are significant; features near the diagonal are noise.

The *structure theorem* for persistence modules guarantees that the persistent homology of any finite filtered complex is completely characterized by such a multiset of intervals (Chazal et al., 2016; Oudot, 2015). This means persistence diagrams are a *complete* invariant of the filtration's topology—no topological information is lost.

**Vectorization for machine learning.** Persistence diagrams inhabit a metric space (under bottleneck or Wasserstein distances) that is not a Hilbert space, making direct use with many ML algorithms challenging. Several vectorization methods bridge this gap:

- *Persistence landscapes* (Bubenik, 2015): Map diagrams into a Banach space supporting statistical hypothesis testing.
- *Persistence images* (Adams et al., 2017): Apply weighted Gaussian kernels on the birth-persistence plane to produce fixed-dimensional vectors.
- *Persistence entropy* (Atienza et al., 2020): Compress diagrams to a single scalar per homological dimension via Shannon entropy.

These vectorizations are what allow PH features to be combined with classical and learned features in the QCF's fusion architecture.

### 1.6 Stability: The Theoretical Guarantee

The property that makes persistent homology practically viable—and, as we shall argue, theoretically central to the entire research program—is the *stability theorem* of Cohen-Steiner, Edelsbrunner, and Harer (2007):

> **Stability Theorem.** For tame functions $f$ and $g$ on a triangulable space,
> $$d_B\big(\text{Dgm}(f),\, \text{Dgm}(g)\big) \leq \lVert f - g \rVert_\infty$$
> where $d_B$ denotes the bottleneck distance between persistence diagrams and $\lVert \cdot \rVert_\infty$ the supremum norm.

In plain language: **small changes to the input produce small changes to the persistence diagram.** If two geological images differ by at most $\epsilon$ in pixel values (due to noise, measurement error, or different but similar generative processes), their persistence diagrams can differ by at most $\epsilon$ in bottleneck distance.

This guarantee is *mathematical*, not empirical. It does not depend on which generators are used, which dataset is tested, or how many experiments are run. It is a theorem about the mathematical structure of persistent homology itself. As we shall argue in Sections 3 and 6, this makes the stability theorem epistemically stronger than any empirical invariance test—including LOGO.

**Practical significance.** The stability theorem is what distinguishes TDA from methods sensitive to coordinate perturbations. A variogram is also stable (in the sense that small input changes produce small output changes), but the stability of variograms is not *proven*—it is observed empirically. The stability of persistent homology is *proven* from first principles. This distinction matters when the goal is to make robust claims about "essence."

---

## 2. Application to the Qualia Convergence Framework

### 2.1 The Research Problem: What Is the Essence of a Geological Image?

The Qualia Convergence Framework (QCF) addresses a fundamental challenge in subsurface reservoir characterization: given sparse observations (well logs, partial seismic surveys, limited outcrop data), how does a geoscientist retrieve *depositional analogs*—reference geological models that share the essential structural properties of the target reservoir?

The framework was motivated by a colleague's incisive critique:

> "Patterns based on statistical coherence will never solve the essence problem."

This challenge articulates a tension that has haunted quantitative geology: variogram-matching and facies-proportion-matching retrieve statistically similar images that may be structurally (topologically) dissimilar. Two images can have identical variograms, identical facies proportions, identical fractal dimensions—and yet be fundamentally different geological systems. One might be a single sinuous meandering channel; the other might be a complex braided network. The statistics match; the geology doesn't.

### 2.2 Operationalizing Essence

The QCF responds to this challenge with *pragmatic operationalism* (following Peirce, James, Dewey): rather than debating whether "essence" exists metaphysically, we define it by what our tests measure and validate by consequences.

> **Operational Definition**: "Essence" is the invariant structure that remains stable under:
> 1. Multiple independent representation pathways (classical, learned, topological)
> 2. Multiple observation modalities (well logs, seismic, outcrop, images)
> 3. Multiple generative processes (different simulators, real data)

This definition is *epistemic, not metaphysical*. We make no claim about Platonic forms or Aristotelian essences. We claim only that if a structure satisfies these invariance criteria *and* enables prediction of held-out properties, it has earned the designation "essence" for practical purposes.

The use of "Qualia" in the framework name is metaphorical—it signals our ambition to capture something beyond surface statistics, the gestalt quality that experts recognize, while making no claim to access subjective phenomenological experience (Tye, 2021).

### 2.3 Three-Pathway Architecture

The QCF employs three independent feature-extraction pathways, each representing a distinct epistemological perspective:

**The Classical Pathway** computes traditional geostatistical descriptors—variograms, fractal dimensions, connectivity functions—yielding approximately 50 dimensions of features that encode spatial correlation structure. This captures *aparā vidyā* (lower, empirical knowledge) in the framework's Vedantic epistemological framing.

**The Learned Pathway** uses DINOv2-ViT-B/14, a self-supervised vision transformer, with LoRA fine-tuning on geological imagery to extract 768-dimensional feature vectors capturing high-level visual semantics. This captures the holistic "gestalt" that an experienced geoscientist perceives when viewing an image.

**The Topological Pathway**—the focus of this paper—computes persistent homology in dimensions $H_0$ and $H_1$ via Giotto-TDA (Tauzin et al., 2021), producing approximately 20–50 dimensions of topological features. This captures structural connectivity—the skeleton of the geological pattern.

The three pathways are fused through a convergence regularization loss:

$$L_{\text{conv}} = \sum_{i \lt j} \lVert f_i(x) - f_j(x) \rVert^2$$

This loss enforces agreement between pathway representations, encoding a structural analogy to the boundary operator's coherence property $\delta_{k-1} \circ \delta_k = 0$: information extracted at one "dimension" of analysis must be compatible with information at adjacent dimensions. The fused vector is projected into a hyperbolic embedding space (Poincaré ball model) where hierarchical organization of depositional environments is naturally encoded—general categories near the origin, specific sub-types near the boundary.

### 2.4 The $H_1$ Hypothesis

The central testable hypothesis of the topological pathway is:

> **$H_1$ Hypothesis**: First-dimensional persistent homology ($H_1$) discriminates braided from meandering channel architectures even when variogram parameters (range, sill, nugget) are matched.

The physical reasoning is as follows. Braided river systems are characterized by multiple interconnected channels that split and rejoin around bars, creating a network of closed loops in planform view. A braided system should exhibit many persistent $H_1$ features—loops that persist over a wide range of filtration scales. Meandering systems have a single sinuous channel with occasional oxbow cutoffs, yielding few $H_1$ features (primarily at scales corresponding to oxbow-lake formation).

Critically, two-point geostatistics (variograms) *cannot* distinguish these configurations when spatial correlation lengths are similar—they measure correlation structure but are blind to connectivity topology. This is precisely the "essence problem" the colleague's critique identifies, and it is precisely the problem that persistent homology is designed to solve.

The framework establishes a pre-committed decision point: if classification accuracy using only $H_1$ features exceeds 70%, the hypothesis is supported and TDA becomes a core pathway; if it falls below 60%, TDA remains an ablation study (ADR-S04). This pre-commitment follows the Sākṣī (witness) validation philosophy: interpretation thresholds are fixed before data analysis.

### 2.5 Cubical Complexes and the SEDT Filtration

For geological image data, the QCF employs *cubical complexes* with a *signed Euclidean distance transform* (SEDT) filtration, following the methodology established by Robins et al. (2016) for geological pore-space characterization.

The SEDT assigns to each pixel a signed distance to the nearest boundary between facies: positive inside channel bodies, negative inside floodplain. Filtering by increasing SEDT values progressively "erodes" narrow connections, revealing which topological features (connected components, loops) are robust at the core of geobodies versus those that depend on thin, possibly artifactual connections.

This filtration choice is geologically meaningful: features that persist across a wide range of SEDT values correspond to thick, well-connected channel bodies—the kind of structural features that matter for reservoir connectivity and flow simulation. Features that die quickly correspond to thin connections or noise.

### 2.6 Persistence Diagrams and the Hyperbolic Embedding

The persistence diagrams produced by the topological pathway encode hierarchy in a manner that aligns naturally with the QCF's hyperbolic embedding space. In a persistence diagram, the distance of a point from the diagonal (its persistence, $d - b$) reflects the feature's structural importance: long-lived bars correspond to essential, large-scale topological features, while short-lived bars correspond to fine-scale detail or noise.

The Poincaré ball model used by the QCF encodes a depositional hierarchy: general environment types near the origin, specific sub-types near the boundary. There is a natural map between these two hierarchies: an image whose $H_1$ persistence diagram is dominated by many long-lived loops is "more braided" and should sit closer to the hyperbolic boundary near the braided-river prototype; an image with few $H_1$ features but a characteristic distribution of $H_0$ lifetimes (reflecting channel-body isolation) is "more meandering" and sits near the meandering prototype.

This geometric interpretation of persistence diagrams feeding directly into hierarchy-aware embedding represents, to our knowledge, a novel contribution of the QCF.

---

## 3. The Ellipse Degradation Thought Experiment

### 3.1 The Setup

The question of how persistent homology relates to "essence" was examined in a thought experiment (Hoydic, 2026) involving progressive degradation of a channelized reservoir image. Two variants were considered:

**Variant A (Occlusion)**: Progressively add ellipses to the image that hide (but do not destroy) geological features. At 0% coverage, the full image is visible. At 100%, only ellipses remain. The question: at what point is "essence" lost?

**Variant B (Erosion)**: Progressively modify the geological features themselves—straightening channels, removing point bars, eliminating oxbow lakes. The end state is the same (an unrecognizable image), but the path involves destroying information rather than hiding it.

### 3.2 Five Problems with Degradation-Based Essence

This analysis revealed five fundamental problems with defining essence through degradation thresholds:

**1. Occlusion versus erosion.** Occlusion preserves information (the geology is still there, just hidden); erosion destroys it irreversibly. The QCF faces an occlusion problem—sparse observations of full subsurface geology—making this distinction critical. The thought experiment conflates these fundamentally different operations.

**2. Path dependence.** Different degradation orders yield different "minimal essence" sets. Removing sinuosity first, then point bars, versus removing point bars first, then sinuosity, produces different intermediate states and different "essence thresholds." There is no unique answer.

**3. Feature entanglement.** Geological features are not independent—they are physically coupled through constraints like the Leopold-Wolman relationship ($\lambda = 10\text{--}14W$, relating meander wavelength $\lambda$ to channel width $W$) and curvature constraints ($R_c = 2\text{--}3W$, relating radius of curvature to width). Independent feature removal creates geologically *impossible* states—configurations that could never occur in nature because they violate physical constraints. This means the degradation path passes through regions outside the constrained manifold $M$ of valid geological configurations.

**4. Observer-relativity.** Different measurement systems have different essence thresholds. A human sedimentologist might maintain recognition up to 60% ellipse coverage. DINOv2 might fail at 40% or persist to 70% depending on pretraining. Persistent homology ($H_1$ loops) is particularly sensitive to channel connectivity—even a few ellipses placed at channel intersections could destroy the homology, causing apparent "essence loss" at very low coverage. The variogram, integrating information across all pixel pairs, might be robust until very high coverage. Essence is observer-relative, not intrinsic.

**5. Minimality versus sufficiency.** The thought experiment implicitly seeks the "minimal" set of features needed for recognition. But minimality is fragile: if the minimal features are corrupted, recognition fails completely. For retrieval with calibrated uncertainty, we need *sufficient* representations that include redundancy. Over-complete representations can be more stable than minimal ones.

### 3.3 Generator Invariance as an Alternative

The thought experiment's conclusion was that essence is better defined through *invariance across generative processes* rather than degradation thresholds. Formally, let:

- $X$ be the space of possible images
- $\Theta$ be the space of geological parameters (sinuosity, width, wavelength, etc.)
- $G: \Theta \to X$ be a stochastic generator function
- $M \subset \Theta$ be the constrained manifold of physically realizable configurations
- $f: X \to Z$ be a representation function

Then:

$$\text{Essence}(f) = \bigcap_G \lbrace \text{information about } \theta \text{ captured by } f \text{ when trained on } G \rbrace$$

This is operationalized via the *Leave-One-Generator-Out* (LOGO) test: train on generators $\lbrace G_j : j \neq i \rbrace$, test on $G_i$. If retrieval performance degrades by less than 20% for all held-out generators, the features are deemed generator-invariant.

**Why generator invariance is better than degradation**: Invariance is unique (no path dependence), respects physics (generators enforce constraints), is observer-independent (defined by generator agreement), is task-relevant (directly measures retrieval capability), and is operationally testable (LOGO is well-defined).

The stability theorem provides a strong theoretical prediction for LOGO: because persistent homology is provably stable under perturbations of the input function, topological features *should* transfer between generators better than learned features (which may overfit to generator-specific textures) or classical features (which depend on specific correlation-function shapes). This is a testable, pre-committed prediction: per-pathway LOGO degradation should be lowest for the topological pathway.

---

## 4. The Evidence Hierarchy: Mathematical Invariance Over Empirical Testing

### 4.1 The Fundamental Limitation of LOGO

While generator invariance is conceptually superior to degradation thresholds, the LOGO test itself faces a fundamental philosophical challenge: **the invariance claim is only as strong as the diversity and independence of the generator pool.**

This is not a minor caveat. It is a structural limitation supported by three independent theoretical results:

**The Impossibility Result.** Ahuja et al. (2023) proved that invariance alone is insufficient to identify latent causal variables. Even with multiple environments (generators), without additional structural constraints, invariant features may correspond to shared assumptions of the generator family rather than to the causal structure of the data-generating process. Translation: passing LOGO across N generators does not prove that the invariant features capture geological causes.

**The Environment Diversity Problem.** Invariant Risk Minimization (IRM; Arjovsky et al., 2019)—the most studied invariant learning framework—has been shown to fail catastrophically in nonlinear settings and to require an impractically large number of environments for formal guarantees (Rosenfeld et al., 2021). Adding more generators from the same family (all process-based, all rule-based) does not address this; what matters is the genuine *independence* of their assumptions.

**The Independence Condition.** Wimsatt's robustness analysis (1981) establishes that convergent results from multiple models provide evidence only if the models are genuinely independent. If generators share physical assumptions (Leopold-Wolman relationships, process-based sediment transport equations), then "invariance across generators" may reflect invariance to that shared assumption space—producing what Wimsatt calls "illusory robustness." Orzack and Sober (1993) sharpened this critique: robustness analysis is "nonempirical confirmation, effective only under unusual circumstances."

**The degrees-of-freedom concern.** With sufficient control over the generator space, one can engineer a generator pool where LOGO trivially succeeds—not because essence has been captured, but because the definition of invariance has been overfit to the generator family. This is analogous to the well-known problem in generative modeling: systems with sufficient capacity (transformers, diffusion models) can memorize training distributions while appearing to generalize. The analogy is precise: if you control the generators and the invariance test, you control what "essence" means.

### 4.2 The Restructured Evidence Hierarchy

Given these limitations, the QCF restructures its evidence for essence claims into a multi-level hierarchy, ordered by epistemic strength:

**Level 1 — Mathematical Invariance Theorems (Strongest).** The stability theorem provides a *formal proof* that persistent homology features are invariant under bounded perturbations. This is a mathematical guarantee—it does not depend on which generators are tested, which dataset is used, or how many experiments are run. It cannot be "overengineered" because it is a theorem, not a test. For the topological pathway, this is the primary evidence for invariance.

*Limitation*: The stability theorem guarantees that PH features are *invariant*, but does not guarantee they are *relevant*. You could have perfectly stable features that are irrelevant to geological classification. The H₁ hypothesis (Section 2.4) addresses relevance; stability addresses invariance. Together, they provide both.

**Level 2 — Severe Adversarial Testing.** Following Mayo's severe testing framework (2018): a claim passes a severe test if the test was *highly capable of detecting failure* had the claim been false. The key shift: design tests to *break* the invariance claim, not merely challenge it. Specifically: construct generators designed to produce images where topological features are misleading, test whether H₁ features can be manipulated independently of geological meaning, and inject noise at filtration-critical scales. If the claim survives tests designed to destroy it, that is strong evidence.

**Level 3 — Information-Theoretic Measures.** Quantify what representations capture using mutual information: $I(f(X); \theta \mid G)$ measures geological information captured independently of generator; $I(f(X); G \mid \theta)$ measures generator-artifact contamination. High $I(f(X); \theta \mid G)$ and low $I(f(X); G \mid \theta)$ provide continuous, quantitative evidence that the representation captures geology, not generator artifacts.

**Level 4 — Cross-Domain Validation.** If the same topological features that distinguish geological environments also distinguish structurally analogous patterns in music, neuroscience, or other domains, the invariance transcends the generator concept entirely—it is a property of the mathematics, not of any particular application. (See Section 5.)

**Level 5 — Real-Data Validation.** Testing against real geological data that no generator was designed to reproduce. This is the ultimate generator-independent benchmark, but requires data that may not be available in early research phases.

**Level 6 — LOGO (Necessary but Not Sufficient).** LOGO remains a useful check: failure indicates generator-specificity. But passing LOGO alone is insufficient for a strong essence claim. It must be corroborated by evidence from higher levels.

**Level 7 — Expert Agreement.** Human expert judgment (Cohen's κ) provides truly generator-independent assessment, as experts judge geological similarity from experience, not from any computational pipeline.

### 4.3 The Revised Essence Claim

> We claim that a representation captures "essence" when evidence *converges across multiple levels* of this hierarchy. No single level is sufficient. The convergence of mathematical proof (Level 1), survival of severe testing (Level 2), information-theoretic confirmation (Level 3), and empirical validation (Levels 5–7) provides the warranted basis for the essence designation.

This position is both more epistemically honest and more powerful than relying on LOGO alone. It acknowledges the limitations that impossibility results and the independence condition impose, while building a stronger multi-layered argument. Crucially, the topological pathway has a unique advantage: it is the *only* pathway with a Level 1 mathematical guarantee, making it the natural backbone of the framework's essence argument.

---

## 5. Persistent Homology Across Domains: Music, Neuroscience, and Mathematical Universality

### 5.1 The Argument from Domain Agnosticism

One of the most epistemically significant properties of persistent homology is its domain agnosticism: the same mathematical machinery—filtrations, Betti numbers, persistence diagrams, stability theorems—applies to *any* data that can be represented as a topological space. This property is directly relevant to the evidence hierarchy (Level 4, cross-domain validation) and to the broader philosophical claim about the nature of "essence."

If persistent homology captures meaningful invariant structure only in geology, the skeptic can argue that the invariance is an artifact of the geological domain—perhaps all geological generators share biases that topological methods exploit. But if the same framework captures meaningful invariant structure in music, neural data, and other domains built on entirely different physical processes, then the invariance must be a property of the *mathematics*, not of any particular domain.

### 5.2 TDA Applied to Musical Structure

Recent work has demonstrated that persistent homology captures meaningful structure in musical data:

**Topological Music Analysis (TMA).** Alcalá-Alvarez and Padilla-Longoria (2022) developed a framework that converts musical scores to point clouds in Euclidean spaces, computes persistent homology of the resulting simplicial complexes, and uses topological features to compare stylistic properties across composers. They demonstrated that PH can distinguish J.S. Bach's Brandenburg Concertos from compositions by the Mexican composer Armando Luna based on topological fingerprints of their chord sequences—capturing structural differences that spectral analysis alone cannot detect.

**Topological Fingerprints via the Tonnetz.** Bergomi, Baratè, and Di Fabio (2016) proposed interpreting the Tonnetz—a classical music-theoretic lattice relating notes, chords, and keys—as a two-dimensional simplicial complex. By applying persistent homology to this complex deformed by consonance values, they extract invariant harmonic features that characterize musical structure from both melodic and harmonic perspectives.

**Homological Persistence for Genre Classification.** Bergomi and Baratè (2020) applied persistence to musical time series for genre classification, demonstrating that topological features capture structural patterns invisible to spectral analysis alone. Their approach describes time-varying systems through the evolution of geometric and topological properties, using persistent homology to track how these properties change over time.

### 5.3 TDA in Neuroscience and Consciousness Research

The application of persistent homology to neural data provides another line of cross-domain evidence:

**Brain Network Connectivity.** Giusti, Ghrist, and Bassett (2016) applied algebraic-topological tools, including persistent homology, to understand higher-order structure in neural data. They demonstrated that the topology of brain networks—patterns of connectivity between neural populations—contains information about cognitive function that pairwise correlation analysis misses, paralleling the geological case where variograms miss topological structure.

**Brain Dynamics and Individuality.** Wang, Xian, Chen, and Yan (2025) used persistent homology of fMRI time series from approximately 1,000 Human Connectome Project subjects to reveal individual differences in brain dynamics. Topological features exhibited high test-retest reliability and matched or exceeded the predictive performance of traditional features for higher-order cognitive domains, suggesting that PH captures aspects of brain organization invisible to standard methods.

**Gestalt Pattern Recognition.** Liu et al. (2021) applied persistent homology to EEG data during pattern recognition tasks and showed that the persistence entropy of brain signals evoked by ordered Gestalt images differs significantly from that evoked by random patterns—suggesting that human cognition itself has a topological signature.

### 5.4 The Cross-Domain Argument

The parallel between geological and musical applications of PH is more than analogical. In both domains, the fundamental research question is the same: *what features are invariant across different realizations of the same underlying structure?*

| Domain | PH Application | $H_0$ Captures | $H_1$ Captures |
|---|---|---|---|
| Geology | Channel network structure | Isolated channel bodies | Network loops (braiding) |
| Music | Harmonic structure | Separate tonal regions | Harmonic cycles (chord progressions returning to tonic) |
| Neuroscience | Brain connectivity | Isolated neural populations | Feedback loops in neural circuits |

In each case, $H_1$ captures *cyclic structure*—loops, feedback, recurrence—that is invisible to pairwise statistics. The persistence of these features across different realizations (different generators, different performances, different cognitive states) provides a measure of structural robustness that is domain-general.

If the same mathematical framework captures invariant structure in geology, music, *and* neural dynamics, then "essence" as defined by topological invariance may reflect something genuinely fundamental about pattern structure—not a domain-specific artifact that could be explained away by shared generator biases.

---

## 6. Open Questions and the Path Forward

### 6.1 The Central Open Question: Philosophical Robustness of Invariance

The restructured evidence hierarchy (Section 4) does not eliminate the fundamental tension between operational invariance and genuine essence. It acknowledges and addresses the tension more honestly. But several questions remain:

**How do we verify generator independence?** The independence condition (Wimsatt, 1981) is necessary for robust inference, but verifying that generators are genuinely independent—rather than merely superficially different—is itself a non-trivial problem. What constitutes "sufficient diversity" for LOGO to be informative? This question connects to the broader epistemological problem of induction: how can any finite set of tests provide evidence for a universal claim?

**Can causal structure replace empirical invariance?** Instead of testing invariance across generators, one could attempt to identify the *causal structure* that generates geological patterns. If a representation can be shown to capture features that are *causes* of (not merely correlated with) the geological outcome, then invariance follows from the causal graph rather than from empirical testing. This would be the strongest possible evidence—but it requires knowing the causal graph, which is itself a major research challenge.

**What is the relationship between mathematical and geological invariance?** The stability theorem proves that PH features are invariant under bounded perturbations. But does mathematical invariance imply geological invariance? Could there be geological differences that produce unbounded perturbations in the input function, violating the stability theorem's premise? Understanding the relationship between the mathematical bound and the geological reality is essential.

### 6.2 Multi-Parameter Persistence

Standard persistent homology uses a single filtration parameter $\epsilon$. Geological images exhibit structure at multiple scales simultaneously—bar spacing at one scale, channel sinuosity at another, floodplain texture at a third. Multi-parameter persistence (Cerri et al., 2013) would track how topological features at different scales interact—literally the "objects of different dimensions crafting each other" that motivates the research. However, the vectorization problem for multi-parameter persistence remains an active area of research, and computational costs are substantially higher.

### 6.3 Topological Dictionary Learning

An ambitious extension would learn a set of *topological atoms*—canonical persistence diagrams—such that any geological image's persistence diagram decomposes as a sparse combination of these atoms. Each atom would represent a canonical topological primitive ("sinuous channel with one oxbow," "braided network with 3–5 through-going connections"), and the correspondence between generator parameters and these atoms would close the loop between generative processes, topological representations, and the essence claim.

### 6.4 Information-Theoretic Quantification

The information-theoretic measures proposed in the evidence hierarchy (Level 3) have not yet been implemented. Estimating conditional mutual information from finite samples is itself a challenging statistical problem, particularly in high-dimensional representation spaces. The use of variational bounds (MINE; Belghazi et al., 2018) or other neural estimators is a promising but untested direction for this framework.

### 6.5 Cross-Domain Validation as Evidence

The most philosophically compelling line of future work may be systematic cross-domain validation: applying the *identical* PH pipeline used for geological images to musical scores, neural recordings, and other structured data. If the same pipeline that distinguishes braided from meandering channels also distinguishes musical genres or neural states, the argument for mathematical universality becomes very strong. This would provide Level 4 evidence that is not merely "consistent with" but "predicted by" the mathematical theory.

---

## 7. Conclusion

Persistent homology provides a unique combination of mathematical rigor, computational tractability, and domain agnosticism that makes it the natural backbone of the Qualia Convergence Framework's essence claim. The stability theorem provides what no empirical test can: a mathematical *proof* of invariance under bounded perturbations. The H₁ hypothesis provides a specific, falsifiable prediction about the discriminative power of topological features for geological classification. The LOGO protocol provides a necessary (though not sufficient) empirical check on generator-invariance.

The epistemological contribution of this paper is the recognition that mathematical invariance is epistemically *stronger* than empirical invariance, and the consequent restructuring of the evidence hierarchy for essence claims. This restructuring is not merely a philosophical exercise—it changes what experiments are prioritized, how results are interpreted, and what claims are warranted.

The colleague's challenge—"patterns based on statistical coherence will never solve the essence problem"—remains the animating question. Our response is now more nuanced: patterns based on statistical coherence indeed cannot capture topological structure. But patterns based on *topological* coherence, validated by mathematical invariance theorems and severe testing, can approach something worthy of the designation "essence"—with epistemic humility about the gap between operational definitions and deeper truths.

---

## References

Adams, H., Emerson, T., Kirby, M., Neville, R., Peterson, C., Shipman, P., ... & Ziegelmeier, L. (2017). Persistence images: A stable vector representation of persistent homology. *Journal of Machine Learning Research*, 18(8), 1–35.

Ahuja, K., Hartford, J., & Bengio, Y. (2023). Invariance & causal representation learning: Prospects and limitations. *arXiv:2312.03580*.

Alcalá-Alvarez, A., & Padilla-Longoria, P. (2022). A framework for topological music analysis (TMA). *arXiv:2204.09744*.

Arjovsky, M., Bottou, L., Gulrajani, I., & Lopez-Paz, D. (2019). Invariant risk minimization. *arXiv:1907.02893*.

Atienza, N., González-Díaz, R., & Soriano-Trigueros, M. (2020). On the stability of persistent entropy and new summary functions for topological data analysis. *Pattern Recognition*, 107, 107509.

Belghazi, M. I., Barber, A., Balin, O., Dresdner, R., et al. (2018). Mutual information neural estimation. *ICML*.

Bergomi, M. G., Baratè, A., & Di Fabio, B. (2016). Towards a topological fingerprint of music. In *Computational Topology in Image Context*, LNCS 9667, 88–100. Springer.

Bergomi, M. G., & Baratè, A. (2020). Homological persistence in time series: An application to music classification. *Journal of Mathematics and Music*, 14(2), 204–221.

Bubenik, P. (2015). Statistical topological data analysis using persistence landscapes. *Journal of Machine Learning Research*, 16(3), 77–102.

Carlsson, G. (2009). Topology and data. *Bulletin of the American Mathematical Society*, 46(2), 255–308.

Cerri, A., Di Fabio, B., Ferri, M., Frosini, P., & Landi, C. (2013). Betti numbers in multidimensional persistent homology are stable functions. *Mathematical Methods in the Applied Sciences*, 36(12), 1543–1557.

Chazal, F., de Silva, V., Glisse, M., & Oudot, S. (2016). *The Structure and Stability of Persistence Modules*. SpringerBriefs in Mathematics.

Cohen-Steiner, D., Edelsbrunner, H., & Harer, J. (2007). Stability of persistence diagrams. *Discrete & Computational Geometry*, 37(1), 103–120.

Edelsbrunner, H., & Harer, J. (2010). *Computational Topology: An Introduction*. American Mathematical Society.

Edelsbrunner, H., Letscher, D., & Zomorodian, A. (2002). Topological persistence and simplification. *Discrete & Computational Geometry*, 28(4), 511–533.

Giusti, C., Ghrist, R., & Bassett, D. S. (2016). Two's company, three (or more) is a simplex: Algebraic-topological tools for understanding higher-order structure in neural data. *Journal of Computational Neuroscience*, 41(1), 1–14.

Hoydic, C. J. (2026). On the nature of geological essence: A critical analysis of the ellipse degradation thought experiment. Unpublished manuscript.

Kaczynski, T., Mischaikow, K., & Mrozek, M. (2004). *Computational Homology*. Applied Mathematical Sciences, Vol. 157. Springer.

Kemmea, A. J., & Agyingi, C. A. (2025). Persistent homology: A pedagogical introduction with biological applications. *arXiv:2505.06583*.

Liu, J., Wang, J., Liu, B., & Ma, Z. (2021). Persistent homology-based topological analysis on the Gestalt patterns during human brain cognition process. *Journal of Healthcare Engineering*, 2021, 2334332.

Mayo, D. G. (2018). *Statistical Inference as Severe Testing: How to Get Beyond the Statistics Wars*. Cambridge University Press.

Orzack, S. H., & Sober, E. (1993). A critical assessment of Levins's "The strategy of model building in population biology." *Quarterly Review of Biology*, 68(4), 533–546.

Otter, N., Porter, M. A., Tillmann, U., Grindrod, P., & Harrington, H. A. (2017). A roadmap for the computation of persistent homology. *EPJ Data Science*, 6, Article 17.

Oudot, S. Y. (2015). *Persistence Theory: From Quiver Representations to Data Analysis*. Mathematical Surveys and Monographs, Vol. 209. American Mathematical Society.

Robins, V., Saadatfar, M., Delgado-Friedrichs, O., & Sheppard, A. P. (2016). Percolating length scales from topological persistence analysis of micro-CT images of porous materials. *Water Resources Research*, 52(1), 315–329.

Rosenfeld, E., Ravikumar, P., & Risteski, A. (2021). The risks of invariant risk minimization. *ICLR*.

Tauzin, G., Lupo, U., Tunstall, L., et al. (2021). giotto-tda: A topological data analysis toolkit for machine learning and data exploration. *Journal of Machine Learning Research*, 22(39), 1–6.

Tye, M. (2021). Qualia. *Stanford Encyclopedia of Philosophy*. https://plato.stanford.edu/entries/qualia/

Wagner, H., Chen, C., & Vuçini, E. (2012). Efficient computation of persistent homology for cubical data. In *Topological Methods in Data Analysis and Visualization II*. Springer.

Wang, Y., Xian, Y., Chen, X., & Yan, C. (2025). Topological signatures of brain dynamics: Persistent homology reveals individuality and brain–behavior links. *Frontiers in Human Neuroscience*, 19, 1607941.

Weisberg, M. (2006). Robustness analysis. *Philosophy of Science*, 73(5), 730–742.

Wimsatt, W. C. (1981). Robustness, reliability, and overdetermination. In *Scientific Inquiry and the Social Sciences*, ed. Brewer & Collins.

Zomorodian, A., & Carlsson, G. (2005). Computing persistent homology. *Discrete & Computational Geometry*, 33(2), 249–274.
