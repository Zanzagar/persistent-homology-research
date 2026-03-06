# Persistent Homology: Motivation, Framework, and Application to Geological Essence

**Corey James Hoydic**
**Informal Writeup — Advisor Meetings, February–March 2026**

---

This writeup informally introduces the methodology of persistent homology, particularly its motivating epistemic origins, mathematical framework, and how the concepts therein can be applied to our research questions, particularly in how it addresses our fundamental research question: what is the essence of a geologic image? The goal here is to demonstrate a thought process and address any gaps in conceptual understanding or implementation rigor. I have other documents that will more rigorously lay out the theoretical frameworks and address the literature. We recall that, at this point we have defined the essence of a geologic image as the invariant structure that remains stable under multiple independent observation pathways (eg, classical geostatiscs, learned features, topology of geological fields), under multiple observation modalities (diverse data at different scales: well logs, seismic, outcrops, images), and multiple generative processes (synthetic data from different simulators and real data) – this definition is a pragmatic operationalization of the term, meaning that we define it by what our tests measure and validate such essence claims by the consequences of the tests. We will also investigate what makes persistent homology "stable" where traditional machine learning methods fail. Lastly, we will discuss the particular details and design choices of how persistent homology will be leveraged to assert a mathematical invariance in geologic analog data, and how this invariant structural representation can both identify invariant structural descriptors (enabling us to organize a repository of analogs) and to verify that these descriptors are inferable from sparse data (enabling us to retrieve the best analog(s) match given some sparse observations). The proper rigor in defining essence ensures helps us address a core challenge in this research work: are the essence representations of these two pathways, where information asymmetry exists, compatible?

## The Motivating Problem: Why Topology?

To understand why persistent homology is the right tool here, it helps to start with the limitations of existing quantitative approaches—and to be precise about which limitations we mean, because geostatistics is not a monolithic field.

Classical two-point geostatistics—variograms, covariance functions—characterize spatial patterns through pairwise correlation structure. These are powerful and well-understood, but they have a well-known blind spot: they cannot distinguish between patterns that share the same spatial correlation structure but differ in connectivity topology. The geostatistical community recognized this limitation decades ago, and multiple-point statistics (MPS) methods—training image-based approaches like SNESIM (Strebelle, 2002), Direct Sampling, and more recent deep generative approaches—were developed precisely to capture higher-order spatial patterns beyond what two-point statistics encode. MPS methods scan training images for multi-point configurations (templates) and reproduce their frequency in simulated realizations, thereby honoring spatial patterns that variograms alone cannot constrain.

So why not stop at MPS? The issue is that MPS methods, while they do capture higher-order spatial patterns, operate through *empirical pattern matching*—they reproduce the frequency of observed templates without providing any formal, provable guarantee about the structural invariants they preserve. An MPS simulation conditioned on a training image will reproduce the template statistics of that training image, but there is no theorem guaranteeing that topologically meaningful features (like the number of closed channel loops, or the persistence of connectivity across scales) are preserved under perturbation or transfer to a different training image. The invariance of MPS-derived patterns is empirical, contingent on the training image and the template size, and does not generalize with mathematical certainty to unseen configurations. Furthermore, MPS methods are inherently tied to specific training images—they are generative tools, not analytical descriptors. They produce realizations that *look like* the training data, but they do not extract a compact, mathematically rigorous *description* of the structural features that make two images "the same kind of geology." We need not a simulation method but an *analytical framework*—one that extracts invariant structural descriptors from any image, with provable stability guarantees, and produces representations that can be compared, indexed, and retrieved.

The learned feature pathway—in our case, DINOv2-ViT-B/14, a self-supervised vision transformer fine-tuned on geological imagery via LoRA—addresses the geostatistical blind spot from a different direction. Deep learned features capture high-level visual semantics: the holistic "gestalt" that makes an image look like a braided system or a meandering system. DINOv2 produces 768-dimensional feature vectors that encode something closer to what an experienced geoscientist perceives when viewing an image—pattern recognition at a level of abstraction far beyond pairwise correlation. These features can, and often do, capture structural differences invisible to variograms.

But the learned pathway has its own limitations, and they are different in kind from the geostatistical ones. First, learned features are *opaque*. A 768-dimensional embedding vector cannot tell you *which* structural property it has encoded. If DINOv2 distinguishes braided from meandering systems, we cannot point to a specific interpretable feature (like "number of closed loops") and say "this is what the model is using." The representation may be capturing texture, color statistics, or other visual properties correlated with but not identical to the structural topology we care about. Second, learned features have *no provable stability guarantees*. The stability of DINOv2 embeddings under generator shift—when we move from images produced by one simulator to images produced by another—is an empirical question whose answer depends on the pretraining corpus, the fine-tuning data, and the specific domain shift encountered. A model fine-tuned on Flumy-generated meandering channels may learn texture artifacts specific to Flumy's rendering that do not transfer to BRAHMS-generated braided channels. This is a well-documented problem in domain adaptation: deep features that appear robust within a training distribution can fail unpredictably under distribution shift. Third, and most fundamentally for the essence question, learned features face the same epistemic limitation as MPS: their invariance is empirical, not mathematical. We can test whether DINOv2 features are invariant across generators by running LOGO (Leave-One-Generator-Out), but a positive result proves invariance *within the tested generator family*, not invariance in general. There is no theorem guaranteeing that DINOv2 features will remain stable under arbitrary bounded perturbations of the input—the kind of guarantee that the stability theorem provides for persistent homology.

This is why the three-pathway architecture exists: each pathway has complementary strengths and complementary blind spots. Classical geostatistics provides interpretable, well-understood features that are blind to higher-order structure. Learned features capture holistic visual semantics but are opaque and lack formal stability guarantees. Persistent homology provides *interpretable, mathematically stable, structurally explicit* descriptors—you know exactly what $\beta_1$ counts (loops), you know it is provably stable under bounded perturbations, and you can connect it directly to geological meaning (channel connectivity). The convergence of all three pathways—when they agree—provides stronger evidence for essence than any single pathway alone.

Here is a concrete example that sharpens these distinctions. Consider two depositional images, both fluvial: one is a single sinuous meandering channel, the other is a complex braided network of interconnected channels. It is entirely possible to tune the generator parameters such that these two images produce nearly identical variograms—the same range, sill, and nugget. An MPS approach trained on both images would reproduce their respective template statistics faithfully, but the *description* of what makes them structurally different—the braided system's multiple closed loops of channel connectivity versus the meandering system's single sinuous path with at most one oxbow loop—is not something MPS provides as an output. It is implicit in the training image, not extracted as a formal invariant. DINOv2 would likely distinguish them—a vision transformer trained on geological imagery can learn to tell braided from meandering—but we cannot say *why* it distinguishes them or guarantee that its distinction would survive a shift to a different simulator's output. The structural difference we actually care about is topological: the braided system has high $\beta_1$ (many loops); the meandering system has low $\beta_1$. Persistent homology makes this explicit, interpretable, and provably stable. No amount of template matching or learned embedding, at any order or dimensionality, provides that combination of interpretability and mathematical guarantee. This is not an exotic edge case—it is a generic limitation when the goal is *analytical description with formal invariance properties* rather than *conditional simulation or pattern recognition*, and it is precisely the "essence problem" that motivates this work.

The question then becomes: what mathematical framework can *explicitly detect and quantify* these structural differences as formal invariants? The answer is topology—specifically, the branch of topology concerned with detecting "holes" (connected components, loops, voids) in a systematic, algebraically computable way. This is what homology does. And persistent homology extends this by tracking how these topological features evolve across spatial scales, distinguishing robust structural features from noise, with provable stability guarantees that neither two-point statistics nor MPS methods can offer.

## The Mathematical Framework: Building Persistent Homology from Fundamentals

The goal of this section is to construct persistent homology from the ground up—not as a list of definitions, but as a sequential narrative where each concept motivates the next. We begin with the most basic question: what is a topological space? And we build, step by step, to persistence diagrams.

### The Space We Work In

**Topological spaces.** Topology studies what stays the same when you stretch, bend, and deform a shape—but do not tear or glue it. A *topological space* $(X, \tau)$ consists of a set $X$ and a collection $\tau$ of subsets called "open sets" satisfying three axioms: (1) the empty set $\emptyset$ and $X$ itself are in $\tau$; (2) $\tau$ is closed under finite intersections; and (3) $\tau$ is closed under arbitrary unions (Kemmea & Agyingi, 2025).

In plain terms, a topological space is a set of points together with a rule that tells you which groups of points count as "neighborhoods." The collection $\tau$ is that rule—the list of all subsets you have declared to be "open." The three axioms ensure this neighborhood structure is self-consistent: (1) "nothing" and "everything" are valid neighborhoods (the trivial cases); (2) if two neighborhoods overlap, the overlap is also a neighborhood—zooming in (taking the common part of two open sets) gives you something still valid; and (3) gluing any collection of neighborhoods together, even infinitely many, produces a valid neighborhood—zooming out always makes sense. These three axioms are the minimum structure needed to define what "continuous" means, and continuous functions are what topology studies: a function is continuous if it does not tear the space, meaning nearby points stay nearby. Crucially, you do not need distance to define this—you only need to know which sets are open. This is why a topological space is more general than a metric space: it captures the idea of "shape" without requiring any notion of measurement. For our purposes, we do work in metric spaces (images have Euclidean pixel distances), so the topological space definition is the general container that metric spaces sit inside.

These axioms formalize "nearness" without requiring any concept of distance—they define which points are "close together" in a purely structural sense. The power of this abstraction is that it allows us to classify shapes by their invariant properties. A marble has genus 0 (no holes); a doughnut has genus 1 (one hole); a pair of scissors has genus 2 (two finger-holes). Objects within each genus class are topologically equivalent regardless of their geometric appearance. This is precisely the kind of invariance we seek in geological pattern recognition: two reservoir images may look different at the pixel level but share the same topological "type."

**Homeomorphism.** When are two topological spaces "the same"? A *homeomorphism* $f: X \to Y$ is a bijective continuous function with a continuous inverse—formally, a way of saying "you can deform one space into the other without cutting or gluing." The classic example: a coffee mug and a doughnut are homeomorphic because both have exactly one hole, and you can continuously deform one into the other. Homeomorphism is the strictest notion of topological equivalence—it preserves every topological property. But for data analysis, we often need a softer notion that preserves only the features we care about detecting.

**Homotopy and homotopy equivalence.** A *homotopy* between two continuous maps $f, g: X \to Y$ is a continuous function $H: X \times [0,1] \to Y$ satisfying $H(x,0) = f(x)$ and $H(x,1) = g(x)$. Intuitively, $H$ smoothly morphs one map into the other over a "time" parameter $t \in [0,1]$. Two spaces are *homotopy equivalent* if one can be continuously deformed into the other—a weaker condition than homeomorphism. A solid disk is homotopy equivalent to a point (you can shrink it continuously), but a circle is not (any attempt to shrink it to a point must "jump" across the hole). This matters because spaces that are homotopy equivalent have isomorphic homology groups. Homology detects holes precisely because holes are homotopy invariants—they persist under any stretching, bending, or reshaping short of filling them in. This is why homology is the right algebraic tool for our purposes: it captures exactly the structural features (connected components, loops, voids) that survive continuous deformation.

**Metric spaces.** Our geological data begins as discrete measurements—pixels in images, depth readings in well logs, scattered outcrop observations—with no inherent topological structure. To build the combinatorial structures on which homology computation depends, we need a principled notion of distance. A *metric space* $(M, d)$ is a set $M$ equipped with a distance function $d: M \times M \to [0, \infty)$ satisfying four properties: (1) identity: $d(x,y) = 0$ iff $x = y$; (2) positivity: $d(x,y) > 0$ when $x \neq y$; (3) symmetry: $d(x,y) = d(y,x)$; (4) the triangle inequality: $d(x,z) \leq d(x,y) + d(y,z)$. These properties ensure distance behaves as spatial intuition expects: you cannot take a shortcut that beats the direct path. The metric provides the threshold-based construction that follows: two points are connected by an edge when $d(x,y) \leq \epsilon$. Without a metric, there is no principled way to decide which points should be "neighbors"—and thus no way to build shape from data.

**Point clouds.** In practice, our data arrives as a *point cloud*: a finite set of points sampled from some underlying space, equipped with the metric inherited from the ambient space (typically Euclidean distance). A geological image is a point cloud on a regular grid; a set of well log locations is a point cloud in 3D space; outcrop measurements are scattered points on a surface. The fundamental challenge of topological data analysis is to recover the topological properties of the underlying space from the finite, noisy sample that is the point cloud. This is exactly what simplicial complexes and persistent homology are designed to do.

### From Data to Shapes: Simplicial Complexes

**Abstract simplicial complexes.** The bridge from a point cloud to a topological space is the *simplicial complex*—a combinatorial structure that systematically builds higher-dimensional shapes from discrete points. An *abstract simplicial complex* $K$ over a vertex set $V$ is a collection of non-empty subsets of $V$ satisfying two properties: (1) every single vertex $\lbrace v \rbrace$ with $v \in V$ is in $K$; and (2) if a set of vertices $\sigma$ belongs to $K$, then all subsets of $\sigma$ also belong to $K$ (the *closure property*).

The building blocks are $k$-simplices: a 0-simplex is a point, a 1-simplex is an edge connecting two points, a 2-simplex is a filled triangle, and a 3-simplex is a solid tetrahedron. More generally, a $d$-dimensional simplex is the convex hull of $d+1$ vertices. The closure property is intuitively necessary: if we claim a triangle exists (three points mutually connected), then its edges and vertices must also exist. You cannot have a triangle without its sides.

**Building complexes from data.** Given a point cloud in a metric space, we construct a simplicial complex by connecting points based on proximity. Given a threshold distance $\epsilon$, the *Vietoris-Rips complex* includes a $k$-simplex whenever all pairwise distances among its $k+1$ vertices are at most $\epsilon$ (Otter et al., 2017). As $\epsilon$ increases from zero, isolated points gradually connect into edges, triangles, and higher-dimensional simplices—the data "fills in" and reveals its underlying shape. This is the geometric representation that the simplicial complex elucidates: from a discrete scatter of points, we recover an approximation of the continuous shape from which those points were sampled.

For gridded image data—such as our geological facies maps—*cubical complexes* provide a computationally more natural alternative. Instead of constructing simplices from point pairs, the cubical approach treats each pixel as an elementary square (2-cube) and builds the filtration by thresholding on pixel values. This distinction is practically important: cubical complexes respect the grid structure of image data, avoid the quadratic memory cost of Vietoris-Rips, and are computed efficiently by specialized algorithms.

### From Shapes to Algebra: Homology

Now we have a combinatorial shape (the simplicial complex) built from our data. The next question is: how do we detect "holes" in this shape in a way that is algebraically computable? This is the role of homology, and constructing it requires several definitions that build on each other.

**Faces of a simplex.** The *faces* of a $k$-simplex are the $(k{-}1)$-simplices obtained by dropping one vertex at a time. The triangle $[v_0, v_1, v_2]$ has three faces (edges): $[v_1, v_2]$, $[v_0, v_2]$, and $[v_0, v_1]$—each formed by removing one of the three vertices. Each edge $[v_i, v_j]$ has two faces (its endpoints): the vertices $v_i$ and $v_j$. Faces are what boundary maps "sum over."

**Chain groups.** For each dimension $k$, the $k$-simplices of a complex $K$ generate a vector space $C_k(K)$ called the $k$-th *chain group*, with coefficients in the two-element field $\mathbb{Z}_2 = \lbrace 0, 1 \rbrace$. A $k$-chain is a formal sum of $k$-simplices:

$$\gamma = \sum_{\sigma} \gamma_{\sigma} \, \sigma, \quad \gamma_{\sigma} \in \lbrace 0, 1 \rbrace$$

Working over $\mathbb{Z}_2$ means a simplex is either "included" (1) or "not included" (0), with the rule that $1 + 1 = 0$—including a simplex twice cancels it out. A 1-chain, for example, is a collection of edges; a 2-chain is a collection of filled triangles.

**Boundary maps.** The *boundary map* $\partial_k: C_k(K) \to C_{k-1}(K)$ sends each $k$-simplex to the formal sum of its $(k{-}1)$-dimensional faces. Over $\mathbb{Z}_2$:

$$\partial_k(\sigma) = \sum_{i=0}^{k} \sigma_{-i}$$

where $\sigma_{-i}$ denotes the face obtained by removing vertex $i$. The boundary of a triangle is the sum of its three edges. The boundary of an edge is the sum of its two endpoints.

**Chain complexes and the fundamental property.** The chain groups connected by boundary maps form a *chain complex*:

$$0 \to C_k(K) \xrightarrow{\partial_k} C_{k-1}(K) \to \cdots \xrightarrow{\partial_1} C_0(K) \to 0$$

The defining property of a chain complex is:

$$\partial_{k-1} \circ \partial_k = 0$$

The boundary of a boundary is always empty. This is not a technicality; it expresses a deep geometric truth. The boundary of a filled triangle is a closed loop of edges; a closed loop has no boundary (no endpoints). This property is what makes the entire algebraic machinery work: because $\partial_{k-1} \circ \partial_k = 0$, every boundary is automatically a cycle. This guarantees that boundaries are always a subset of cycles, which is what allows us to ask the defining question of homology: which cycles are *not* boundaries?

### From Chains to Homology

We now define two subsets of the chain group that are central to everything that follows. The *kernel* of $\partial_k$, written $\ker(\partial_k)$, is the set of all $k$-chains whose boundary is zero. The *image* of $\partial_{k+1}$, written $\textrm{im}(\partial_{k+1})$, is the set of all $k$-chains that are the boundary of some $(k{+}1)$-chain.

Elements of the kernel are called **$k$-cycles** — chains with no boundary. A 1-cycle, for example, is a collection of edges that forms one or more closed loops: every vertex appears an even number of times, so the boundary (the sum of endpoints) cancels to zero. Elements of the image are called **$k$-boundaries** — chains that bound a filled region of one dimension higher.

Because $\partial_{k} \circ \partial_{k+1} = 0$, every boundary is automatically a cycle (if $\gamma = \partial_{k+1}(\alpha)$, then $\partial_k(\gamma) = \partial_k \circ \partial_{k+1}(\alpha) = 0$). But not every cycle is a boundary — some cycles surround genuine unfilled holes. Distinguishing the genuine holes from the false positives is exactly what homology computes.

**Homology groups.** The $k$-th *homology group* is the quotient:

$$H_k(K) = \ker(\partial_k) \,/\, \textrm{im}(\partial_{k+1})$$

This quotient captures precisely the $k$-dimensional cycles that are *not* boundaries of $(k{+}1)$-dimensional simplices. These non-boundary cycles are the genuine topological "holes" in dimension $k$. Two cycles that differ by a boundary are considered equivalent—they "enclose the same hole."

A worked example makes this concrete. Consider three wells arranged in a triangle—call them $v_0$, $v_1$, $v_2$—with edges connecting each pair. The 1-chain $\gamma = [v_0, v_1] + [v_1, v_2] + [v_0, v_2]$ traces a closed loop through all three edges. Applying the boundary map:

$$\partial_1(\gamma) = (v_0 + v_1) + (v_1 + v_2) + (v_0 + v_2) = 0$$

Each vertex appears exactly twice, and $1 + 1 = 0$ in $\mathbb{Z}_2$, so every vertex cancels. The loop has no boundary—it is a cycle. Now the critical question: is it a boundary?

- If the triangle is filled (the 2-simplex $[v_0, v_1, v_2]$ exists): then $\gamma = \partial_2([v_0, v_1, v_2])$, and the cycle is a boundary. It encloses no hole—the interior fills the loop. This cycle is trivial in $H_1$.
- If the triangle is unfilled (only edges, no face): then $\gamma$ is a cycle that is not a boundary of anything. It detects a genuine 1-dimensional hole—a nontrivial element of $H_1$.

This is exactly how homology works: cycles that bound filled regions are trivial; cycles that enclose genuine holes survive in the homology group.

**Betti numbers.** The homology groups capture the essential topological features of the space. These features are quantified by *Betti numbers*—the rank (dimension) of each homology group, denoted $\beta_k$:

| Betti Number | What It Counts | Geological Interpretation |
|---|---|---|
| $\beta_0$ | Connected components | Isolated channel bodies, separate sand bodies |
| $\beta_1$ | Loops / 1-dimensional holes | Channel network loops, oxbow lakes, braiding |
| $\beta_2$ | Enclosed voids | 3D enclosed cavities (relevant for pore-space analysis) |

For reference, standard shapes have characteristic Betti numbers: a circle has $(\beta_0, \beta_1) = (1, 1)$; a sphere has $(\beta_0, \beta_1, \beta_2) = (1, 0, 1)$; a torus has $(\beta_0, \beta_1, \beta_2) = (1, 2, 1)$.

For our research, the critical Betti number is $\beta_1$—the loop count. A braided system has many $H_1$ features (channel loops); a meandering system has few. This is the topological difference that variograms miss entirely and that MPS methods capture only implicitly through template reproduction, without extracting it as a formal, stable descriptor.

### From Homology to Persistent Homology: Tracking Features Across Scales

A single simplicial complex computed at a fixed threshold captures topology at only one scale. But what threshold should we choose? Too small, and the data is a disconnected scatter of points with no interesting topology. Too large, and everything merges into a single blob. The answer: do not choose. Instead, compute topology at every scale and track how features evolve.

**Filtrations.** A *filtration* is a nested sequence of complexes:

$$K_0 \subseteq K_1 \subseteq K_2 \subseteq \cdots \subseteq K_n$$

obtained by gradually increasing the scale parameter $\epsilon$. For point clouds, this means increasing the connection radius in the Vietoris-Rips construction. For images with cubical complexes, this means sweeping through pixel-value thresholds.

**Birth and death of topological features.** As $\epsilon$ increases, topological features are *born* (a new cycle appears that is not a boundary of any existing simplex) and *die* (a cycle becomes a boundary when a higher-dimensional simplex fills it in, or two connected components merge). The *persistence* of a feature is the interval $[b, d]$ between its birth time $b$ and death time $d$. The key interpretive principle: long-persisting features are genuine structural properties of the data; short-lived features are noise or artifacts of discretization. A loop that appears at scale $\epsilon = 2$ and dies at scale $\epsilon = 50$ is a robust, large-scale structural feature. A loop that appears at $\epsilon = 10$ and dies at $\epsilon = 11$ is likely noise.

**Visualizing persistent homology.** Birth-death intervals are visualized in two equivalent formats:

- *Persistence barcodes*: Horizontal bars whose length equals persistence $d - b$. Longer bars represent more significant features.
- *Persistence diagrams*: Points $(b, d)$ in the plane. The diagonal $y = x$ represents zero persistence. Features far from the diagonal are significant; features near the diagonal are noise.

The structure theorem for persistence modules guarantees that the persistent homology of any finite filtered complex is completely characterized by such a multiset of intervals (Chazal et al., 2016; Oudot, 2015). This means persistence diagrams are a *complete* invariant of the filtration's topology—no topological information is lost.

**Vectorization for machine learning.** Persistence diagrams inhabit a metric space (under bottleneck or Wasserstein distances) that is not a Hilbert space, making direct use with many ML algorithms challenging. Several vectorization methods bridge this gap: *persistence landscapes* (Bubenik, 2015) map diagrams into a Banach space supporting statistical hypothesis testing; *persistence images* (Adams et al., 2017) apply weighted Gaussian kernels to produce fixed-dimensional vectors; *persistence entropy* (Atienza et al., 2020) compresses diagrams to a single scalar per homological dimension via Shannon entropy. These vectorizations produce the 20-50-dimensional topological feature vectors that enter the fusion layer of our architecture.

## Stability: Where Mathematical Proof Replaces Empirical Hope

Now we arrive at the property that, in my view, makes persistent homology not just useful but *epistemically privileged* for this research program: the stability theorem.

Cohen-Steiner, Edelsbrunner, and Harer (2007) proved that for tame functions $f$ and $g$:

$$d_B(\textrm{Dgm}(f), \textrm{Dgm}(g)) \leq \lVert f - g \rVert_\infty$$

where $d_B$ is the bottleneck distance between persistence diagrams and $\lVert f - g \rVert_\infty$ is the supremum norm. In plain language: *small changes to the input produce small, bounded changes to the persistence diagram.* If two geological images differ by at most $\epsilon$ in pixel values—due to noise, measurement error, or generation by different simulators—their persistence diagrams can differ by at most $\epsilon$ in bottleneck distance.

This is a *mathematical theorem*, not an empirical observation. It does not depend on which generators we test, which dataset we use, or how many experiments we run. Contrast this with the stability of variograms or learned features: we can observe empirically that small input perturbations produce small variogram changes, but we cannot *prove* this from first principles for arbitrary perturbations. The stability of DINOv2 embeddings under generator shift is an empirical question, with answers that depend on the particular generators tested. The stability of persistent homology features is proven once and holds universally.

Why does this matter for the essence question? Recall that we defined essence as the invariant structure stable under multiple pathways, modalities, and generative processes. When we ask "is this representation invariant?"—there are two fundamentally different ways to answer:

1. **Empirical invariance testing** (like the LOGO test—Leave-One-Generator-Out): cross-validate across generators, measure degradation. This is useful but structurally limited. Ahuja et al. (2023) proved that invariance across a finite set of environments is insufficient to identify latent causal variables. Passing LOGO across $N$ generators proves invariance *within that generator family*, not geological invariance in general. The generators may share physical assumptions (e.g., Leopold-Wolman scaling), and invariance to those shared assumptions is weaker evidence than we might hope.

2. **Mathematical invariance theorems**: prove from first principles that the representation is stable. This is what the stability theorem provides for persistent homology, and *only* for persistent homology among our three pathways. This distinction elevates the topological pathway from "one of three parallel feature extractors" to "the pathway with the strongest epistemic warrant for invariance."

I want to be precise about what this does and does not establish. The stability theorem guarantees that PH features are *invariant*—that small perturbations cannot change them dramatically. But it does not guarantee they are *relevant*—you could have perfectly stable features that are irrelevant to geological classification. This is where the $H_1$ hypothesis comes in: it connects stability to relevance by predicting that $H_1$ features specifically discriminate braided from meandering architectures. If the $H_1$ hypothesis holds (classification accuracy > 70% on variogram-matched pairs), then we have *both* mathematical invariance *and* geological relevance. That two-level warrant—stability theorem plus empirical discrimination—is the strongest evidence structure available in the evidence hierarchy.

## Application: The Two-Pipeline Architecture

The practical question is: how does persistent homology actually serve the two-pipeline architecture that structures this research?

**Pipeline A (Repository/Cataloguing):** Full-resolution analog images—generated by process-based simulators like Flumy (meandering) or BRAHMS (braided)—are encoded via the topological pathway. The SEDT filtration is applied, cubical persistence is computed in $H_0$ and $H_1$, and the resulting persistence diagrams are vectorized (via persistence images, landscapes, or entropy) into 20–50-dimensional feature vectors. These vectors, combined with classical geostatistical features (~50 dimensions) and learned features from DINOv2 (~768 dimensions), are fused via cross-attention and projected into a hyperbolic embedding space (Poincaré ball model). The result is a geologic index—a structured database of analogs organized by their invariant structural properties. The hyperbolic geometry naturally encodes depositional hierarchy: general categories (e.g., "fluvial") near the origin, specific sub-types (e.g., "high-sinuosity meandering with oxbow cutoffs") near the boundary. The persistence diagram hierarchy maps naturally to this embedding: images with many long-lived $H_1$ loops are "more braided" and sit near the braided prototype at the boundary.

**Pipeline B (Query/Retrieval):** A geoscientist's query consists of sparse observations: a few well logs, a partial seismic survey, scattered outcrop measurements. These are fundamentally different from the complete images in Pipeline A—they are incomplete, multimodal, and defined on different data structures (1D depth profiles vs. 2D images). A Neural Process encoder maps these sparse inputs to a distribution $(\mu, \sigma)$ in the same embedding space—not a point estimate, but a calibrated uncertainty region that degrades gracefully with observation density. More observations tighten the distribution; fewer yield wider bounds.

**The Compatibility Problem.** This is the central architectural challenge, and it is worth stating plainly: the essence representation computed from complete images (Pipeline A) must be compatible with the essence representation inferred from sparse observations (Pipeline B). These two pathways face an information asymmetry. The analog side has complete 2D images from which cubical persistence can be computed directly. The query side has sparse 1D profiles from which $H_1$ features cannot be computed directly—you cannot detect loops in a channel network from three vertical well intersections.

The compatibility question is therefore: *are the essence representations of these two pathways, where information asymmetry exists, compatible?* Persistent homology contributes to this in two ways. First, the stability theorem provides a framework for reasoning about how much information about the persistence diagram can be recovered from partial observations—if the sparse data constrains the underlying function $f$ within an $\epsilon$-band, then the persistence diagram is constrained within an $\epsilon$-band as well. Second, the convergence regularization loss across all three pathways enforces that the topological, classical, and learned representations must agree—so even if the sparse query encoder cannot directly compute $H_1$, the convergence loss during training ensures that the learned representation (which *can* be computed from sparse inputs via the Neural Process encoder) captures information correlated with the topological features. The question of how well this indirect route preserves topological information is empirically testable and is one of the key research questions for the next phase.

## Design Choices: SEDT Filtration and Cubical Complexes

A brief note on two specific design choices that deserve justification.

**Why cubical complexes instead of Vietoris-Rips?** Our input data are regular pixel grids, not scattered point clouds. Cubical complexes respect this grid structure natively—each pixel is an elementary square (2-cube), and the filtration is built by thresholding pixel values. This avoids the quadratic memory cost of constructing a Vietoris-Rips complex from all pairwise distances (which would be prohibitive for $256 \times 256$ images with 65,536 points) and uses algorithms specialized for gridded input. The implementation uses Giotto-TDA, which handles cubical complexes efficiently.

**Why the SEDT filtration?** The SEDT assigns each pixel a signed distance to the nearest facies boundary—positive inside channel bodies, negative inside floodplain. This choice is geologically motivated: filtering by increasing SEDT values progressively erodes narrow connections, revealing which topological features are robust at the core of geobodies versus those that depend on thin, possibly artifactual connections. A loop that persists across a wide range of SEDT values corresponds to a thick, well-connected braided channel network. A loop that dies quickly corresponds to a thin connection that may be an artifact of grid resolution or generator noise. The filtration choice is doing real epistemic work here: it translates the mathematical abstraction of persistence into a geologically interpretable quantity.

## Extensions: Dynamic Essence, Confidence Hierarchy, and Uncertainty

Three extensions have emerged from this work that significantly broaden the framework. I want to sketch each here because they address natural follow-up questions that arose in our last meeting.

### From Structural Essence to Response Essence

Everything above deals with *structural* essence—the invariant spatial pattern of a geological image. But the ultimate purpose of analog retrieval is not to find analogs that *look like* a target reservoir but to find analogs that *behave like* it. If two geological configurations share the same topological structure, do they also produce similar dynamic responses to stimulation?

This is naturally framed as a dynamical systems question. A reservoir under stimulation evolves according to a state-space model: $x_{k+1} = f(x_k, u_k)$, where different geological configurations correspond to different functions $f$, producing different trajectories through the same state space. Classical reservoir simulation *is* state-space modeling—this is not an analogy. He et al. (2023) showed that reservoir dynamics even admit Koopman linearization, connecting attractor geometry to spectral properties.

The key idea is that we can apply PH to these trajectories. Takens' embedding theorem guarantees that the attractor topology can be reconstructed from a single time series, and Venkataraman et al. (2016) demonstrated that persistence diagrams of reconstructed attractors reliably distinguish different dynamical regimes. There is already direct evidence for this link: Moon et al. (2019) showed that PH features of pore structure predict macroscopic flow properties—topological invariants of static geometry carry information about dynamic behavior. So the pipeline would be: run simulations on different geological configurations under identical forcing, embed the production time series via Takens, compute PH of the attractor, and ask whether structural PH predicts response PH.

I define *response essence* formally via the Morse-Smale decomposition: two geological configurations share response essence if their basin-of-attraction structures are combinatorially equivalent. This is currently intractable for high-dimensional reservoir systems, but Lipinski et al. (2023) developed persistent Conley-Morse graphs for tracking how Morse decompositions change under parameter variation, and Koopman-based dimension reduction (He et al., 2023) may make the problem tractable.

An especially intriguing observation: geological formations themselves are frozen signatures of dynamical processes. Meandering rivers exhibit self-organized criticality (Stolum, 1996); the Leopold-Wolman braided/meandering threshold is a bifurcation boundary; delta lobe switching is a limit cycle. The PH computation of §8.1—distinguishing braided from meandering via $H_1$ features—is therefore detecting *which side of a dynamical bifurcation* the formation process occupied. This suggests structural PH of the geological record may encode information about the attractor of the formation process, connecting structural and response essence at a deeper level.

A complicating factor is *equifinality*—the well-documented phenomenon whereby fundamentally different geological processes can produce landforms with similar structural signatures (Phillips, 2006). Two depositional environments governed by different dynamical systems could converge on similar topological structures through different attractor mechanisms. This means the mapping from formation dynamics to structural PH may be many-to-one: identical $H_1$ signatures could arise from different formation processes. Equifinality does not invalidate the structural-to-response link, but it constrains the inference—shared structural PH is necessary but may not be sufficient for shared response essence.

### The Confidence Hierarchy: PH as Epistemic Anchor

The three-pathway architecture extracts features of fundamentally *different epistemic status*—and this is a distinction that, as far as I can determine, no prior work in multi-modal feature fusion has exploited.

Here is the core insight. PH features have a *mathematical proof* of invariance (the stability theorem). Geostatistical descriptors have no analogous theorem—they depend on stationarity assumptions that geological data routinely violate. DINOv2 features depend on training data distribution and model architecture—no theorem guarantees their behavior under domain shift. This creates what I am calling an *asymmetric trust structure*:

- **Tier 1 (Proven)**: PH features — mathematically invariant via stability theorem
- **Tier 2 (Corroborated)**: Features where all three pathways converge (joint component in SLIDE decomposition)
- **Tier 3 (Empirically invariant)**: Features passing LOGO but with low alignment to PH
- **Tier 4 (Uncertain)**: Features unique to one pathway, no cross-pathway support

To operationalize this, I adopt three tools from representation learning theory. First, CKA (Centered Kernel Alignment; Kornblith et al., 2019) measures global agreement between pathway pairs—Williams et al. (2024) proved CKA, RSA, and CCA are mathematically equivalent, so the choice of metric does not matter. Second, SLIDE (Gaynanova & Li, 2019) decomposes multi-view features into joint, partially-shared, and individual components—directly assigning each feature dimension to a tier. Third, Dempster-Shafer Theory (DST) provides the formal framework for combining evidence of asymmetric reliability: each pathway contributes a belief function (lower bound on probability) and a plausibility function (upper bound), with the gap encoding ignorance. PH gets a narrow gap (high confidence); single-pathway unique features get a wide gap (high ignorance).

The practical pipeline: compute features from all three pathways → CKA pairwise alignment → SLIDE decomposition into joint/partial/individual → linear probes and T-CAV (Kim et al., 2018) from DINOv2 → PH concepts → assign tiers → DST-weighted evidence combination for retrieval scoring.

### From Feature Residuals to Uncertainty Quantification

The SLIDE decomposition identifies DINOv2 features *not* aligned with PH—the PH-residual component. A natural temptation is to discard these as noise. But DeCUR (Wang et al., 2024) proved that unique (non-shared) components of self-supervised representations carry *meaningful* information—they encode view-specific structure genuinely present in the data. For our setting, PH-residual DINOv2 features may encode texture gradients, facies boundary sharpness, or spatial frequency content that PH's topological abstraction deliberately ignores.

The question is whether these residual features represent *aleatoric* uncertainty (genuine intra-class variability—different braided systems have different textures) or *epistemic* uncertainty (model ignorance). Kotelevskii et al. (2025) showed this decomposition can be performed per feature dimension without ensembles, using density estimation in representation space.

The pipeline composes these methods into a chain from PH's mathematical guarantees to calibrated uncertainty in retrieval:

1. PH features provide bounded invariants (stability theorem)
2. DeCUR separates DINOv2 into PH-aligned and PH-residual components
3. Kotelevskii density model decomposes residual into aleatoric/epistemic per dimension
4. Hedged instance embeddings (Oh et al., 2019): represent each analog as a distribution $\mathcal{N}(\mu, \Sigma)$, not a point
5. Uncertainty-weighted similarity for retrieval
6. Neural Process encoder's $(\mu, \sigma)$ outputs receive structured priors from steps 3–5

This connects directly to Scheidt, Li, and Caers (2018), who developed distance-based subsurface uncertainty methods using feature-space distances for scenario probabilities. Our contribution is grounding those distances in features with *known* epistemic status.

### Implications for the Two-Pipeline Architecture

These three extensions change what both pipelines store and compute:

**Pipeline A**: Each analog's index entry becomes tiered—a core index (Tiers 1–2: PH + corroborated features), extended index (Tier 3: empirically invariant), and uncertainty envelope (Tier 4 + aleatoric variability). The repository stores analogs *with calibrated confidence about what is known and unknown*.

**Pipeline B**: The Neural Process encoder produces posteriors with structured priors—tight on Tier 1 dimensions (PH constrains them), diffuse on Tier 4 dimensions. Sparse queries naturally receive wider confidence intervals where warranted.

**Coupling layer**: Retrieval returns not just a ranked list but a *posterior distribution* over candidate analogs with calibrated confidence intervals. Response essence validation provides the ultimate test: retrieved analogs should not only look similar but behave similarly.

## What Remains Open

Several questions remain unresolved, and intellectual honesty requires naming them.

**Multi-parameter persistence.** Standard persistent homology uses a single filtration parameter. But geological images have structure at multiple scales simultaneously—bar spacing at one scale, channel sinuosity at another, floodplain texture at a third. Multi-parameter persistence would track how topological features at different scales interact, but the vectorization problem for multi-parameter persistence is still an active area of research, and computational costs are substantially higher.

**The relationship between mathematical and geological invariance.** The stability theorem proves that PH features are invariant under *bounded* perturbations. But does mathematical invariance imply geological invariance? Could there be geological differences that produce *unbounded* perturbations in the input function? Understanding this relationship—between the abstract mathematical bound and the physical reality of geological variation—is essential for knowing the limits of the approach.

**Information recovery from sparse data.** The compatibility question between Pipeline A and Pipeline B is ultimately empirical: how much topological information about a complete image can be inferred from a handful of well logs? The stability theorem provides a theoretical ceiling on the possible error, but the actual information recovery depends on the geometry of the well placement, the dimensionality of the topological features, and the capacity of the Neural Process encoder.

**Cross-domain validation.** If the same PH machinery that distinguishes geological environments also distinguishes structurally analogous patterns in music (harmonic cycles), neuroscience (neural feedback loops), and other domains, the invariance transcends geology entirely—it becomes a property of the mathematics. This represents perhaps the most philosophically compelling line of future work, because it addresses the concern that any domain-specific validation might simply reflect shared biases of our geological generators.

**Tractability of response essence.** Computing Morse-Smale decompositions for high-dimensional reservoir state spaces is currently intractable. The Koopman linearization + PH pipeline proposed above is a promising direction, but whether reduced-order attractor topology is sufficiently informative for geological classification remains an open empirical question.

**Validation of the asymmetric trust structure.** The confidence hierarchy assumes PH features deserve higher trust because of the stability theorem. But if PH features turn out to capture irrelevant invariants (stable but not discriminative), the entire hierarchy inverts. The $H_1$ experiment is the linchpin: it tests whether mathematical invariance connects to geological relevance.
