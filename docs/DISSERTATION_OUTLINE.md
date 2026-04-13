# Dissertation Outline: The Qualia Convergence Framework

### Multi-Pathway Essence Determination and Analog Retrieval for Subsurface Modeling Under Sparse Data Constraints

**Corey James Hoydic**
March 2026

> **Document status:** This is a *dissertation outline* — a detailed structural and argumentative scaffold for the full dissertation. Sections vary in depth: some (particularly persistent homology) are near chapter-ready; others (classical geostatistics, learned representations, generator mechanisms) require expansion to comparable depth and rigor. The three pillars of the dissertation are: (I) the principle-based generator, (II) essence determination and categorization via three independent pathways, and (III) essence retrieval under sparse data constraints.

---

## Abstract

Accurate prediction of subsurface geological response to natural and anthropogenic stimuli requires spatial models that faithfully represent multiscale geological variability—yet available field observations are invariably sparse and incomplete. This dissertation addresses the operational question: how can large cyber-repositories of geological analog data be systematically organized, indexed, and retrieved to support defensible subsurface modeling under sparse data constraints? We propose the Qualia Convergence Framework (QCF), a two-pipeline architecture in which Pipeline A encodes complete analog patterns into a searchable geologic index and Pipeline B maps sparse field observations into the same representation space for retrieval. The enabling abstraction connecting both pipelines is *essence*—defined operationally as multiscale structural invariance independent of generator artifacts.

The framework rests on three pillars. First, a *principle-based geological image generator* produces synthetic depositional analogs with known structural parameters across fluvial, aeolian, and estuarine environments, providing the controlled experimental apparatus for invariance testing. Second, *essence determination and categorization* employs three independent feature-extraction pathways—persistent homology for topological structure, classical geostatistics for spatial correlation, and self-supervised visual representations (DINOv2) for holistic pattern recognition—whose convergence, governed by a structured evidence hierarchy, provides the epistemic warrant for essence claims. Third, *essence retrieval* maps sparse field observations into the same representation space via a Neural Process query encoder with calibrated uncertainty, organized in a hyperbolic embedding space that encodes the natural hierarchy of depositional environments.

We develop each pillar with mathematical rigor: the stability theorem for persistent homology, variogram theory and connectivity functions for the classical pathway, vision transformer architecture and self-supervised pretraining for the learned pathway, and empirical geomorphological formulas for the generator. We propose a comprehensive validation protocol—the Sākṣī framework—comprising ten independent witnesses, four geology-specific adversarial tests, and a pre-committed Claim Survival Matrix. We further develop extensions to dynamic response essence, a confidence hierarchy exploiting epistemic asymmetry across pathways, and an uncertainty quantification pipeline. We conclude with a proposed experimental validation design and an honest assessment of what remains unsolved.

---

## Contents

**1. The Dissertation Research Problem and System Architecture**
&ensp; 1.1 The Research Question · 1.2 The Two-Pipeline Architecture · 1.3 Essence as the Enabling Abstraction · 1.4 Dissertation Overview

**2. The Principle-Based Generator: Experimental Apparatus for Invariance Testing**
&ensp; 2.1 Why Build a Generator? · 2.2 Generator Taxonomy and Design Philosophy · 2.3 Three Depositional Environments · 2.4 Fluvial Environment: The Leopold-Wolman Framework · 2.5 Aeolian Environment: The Werner Dune Framework · 2.6 Estuarine Environment: The Tidal Prism Framework · 2.7 Validation Strategy · 2.8 Current Implementation Status

**3. Mathematical Foundations of Persistent Homology**
&ensp; 3.1 From Topology to Data Analysis · 3.2 Topological Foundations · 3.3 Simplicial Complexes · 3.4 Homology: Detecting Holes Algebraically · 3.5 Persistent Homology: Tracking Features Across Scales · 3.6 Stability: The Theoretical Guarantee

**4. Mathematical Foundations of Classical Geostatistics**
&ensp; 4.1 From Spatial Statistics to Pattern Description · 4.2 Stationarity · 4.3 The Variogram · 4.4 Beyond the Variogram: Connectivity and Higher-Order Statistics · 4.5 Fractal Dimensions · 4.6 Kriging · 4.7 Epistemic Status and Limitations

**5. Mathematical Foundations of Self-Supervised Visual Representations**
&ensp; 5.1 From Hand-Crafted to Learned Features · 5.2 The Vision Transformer Architecture · 5.3 Self-Supervised Pretraining: DINO and DINOv2 · 5.4 Domain Adaptation: LoRA Fine-Tuning · 5.5 Representation Geometry and Interpretability · 5.6 The Scene Gist Connection · 5.7 Epistemic Status and Limitations

**6. Application to the Qualia Convergence Framework**
&ensp; 6.1 The Research Problem · 6.2 Operationalizing Essence · 6.3 Three-Pathway Architecture · 6.4 Classical Pathway: Variographic Indexing · 6.5 Learned Pathway: Scene Gist and Holistic Pattern Encoding · 6.6 The H₁ Hypothesis · 6.7 Cubical Complexes and the SEDT Filtration · 6.8 Persistence Diagrams and the Hyperbolic Embedding · 6.9 The Adversarial Validation · 6.10 Scope and Limitations · 6.11 Related Work

**7. The Ellipse Degradation Thought Experiment**
&ensp; 7.1 The Setup · 7.2 Five Problems with Degradation-Based Essence · 7.3 Generator Invariance as an Alternative

**8. The Evidence Hierarchy: Mathematical Invariance Over Empirical Testing**
&ensp; 8.1 A Multi-Level Evidence Structure · 8.2 The Revised Essence Claim · 8.3 Implications for Descriptor Admissibility and Query Validation

**9. System Architecture: From Invariants to Analog Retrieval**
&ensp; 9.1 Pipeline A: Building the Geologic Index · 9.2 Pipeline B: The Neural Process Query Encoder · 9.3 The Hyperbolic Embedding Space · 9.4 Perceiver IO · 9.5 Pathway Fusion and the Underdetermination Principle · 9.6 Validation: The Sākṣī Layer · 9.7 Open Design Questions

**10. The Sākṣī Validation Framework**
&ensp; 10.1 The Witness Principle · 10.2 The Ten Witnesses · 10.3 The LOGO Protocol · 10.4 Adversarial Tests (10.4.1–10.4.4) · 10.5 The Claim Survival Matrix · 10.6 Integration with the Evidence Hierarchy

**11. Persistent Homology Across Domains: Music, Neuroscience, and Mathematical Universality**
&ensp; 11.1 The Argument from Domain Agnosticism · 11.2 TDA Applied to Musical Structure · 11.3 TDA in Neuroscience · 11.4 The Cross-Domain Argument

**12. Proposed Experimental Validation**
&ensp; 12.1 The PH Computation Pipeline · 12.2 The H₁ Hypothesis Experiment · 12.3 Validation Through the Evidence Hierarchy · 12.4 What Success and Failure Look Like · 12.5 Classical Pathway Experimental Design · 12.6 Learned Pathway Experimental Design · 12.7 Cross-Pathway Fusion and Ablation

**13. Open Questions and the Path Forward**
&ensp; 13.1 Philosophical Robustness of Invariance · 13.2 Multi-Parameter Persistence · 13.3 Topological Dictionary Learning · 13.4 Information-Theoretic Quantification · 13.5 Cross-Domain Validation as Evidence

**14. Extensions: Dynamic Essence, Confidence Hierarchy, and Uncertainty**
&ensp; 14.1 From Structural Essence to Response Essence · 14.2 PH of Dynamical Systems · 14.3 Response Essence via Basin-of-Attraction Topology · 14.4 Formation Dynamics as Attractor Systems · 14.5 State Space Models · 14.6 The Confidence Hierarchy: PH as Epistemic Anchor · 14.7 From Feature Residuals to Uncertainty Quantification · 14.8 Implications for the Two-Pipeline Architecture

**15. Conclusion**

**References**

---

## 1. The Dissertation Research Problem and System Architecture

### 1.1 The Research Question

The foundational research problem of this dissertation is: *how can we predict the response of subsurface geological formations to natural and anthropogenic stimuli when available observations are sparse and incomplete?* Accurate prediction requires spatial models that faithfully represent the multiscale geological variability of the subsurface—from the connectivity of individual channel bodies at the meter scale to the organization of depositional systems at the kilometer scale. Yet the observational basis for constructing such models is inherently limited: well logs provide high-resolution but spatially sparse vertical profiles, seismic surveys offer broad spatial coverage at reduced resolution, and outcrop observations are geographically constrained and often difficult to integrate with subsurface data.

This sparsity problem has a natural counterpart in the abundance of analog information. Vast repositories of geological analog data exist—process-based simulations, object-based models, training images from multiple-point geostatistics, real outcrop databases, and interpreted seismic volumes. These repositories encode the geological knowledge of decades of research into concrete, spatially explicit realizations of depositional systems. The challenge is not the *availability* of analogs but the *selection* of appropriate ones: given a geoscientist's sparse observations of a target reservoir, which analogs from this vast repository faithfully represent the essential structural properties of the subsurface?

Currently, analog selection remains largely subjective and expertise-driven—a process that depends on individual experience, is difficult to reproduce, and provides no principled uncertainty quantification. The operational research question of this dissertation therefore becomes:

> How can large cyber-repositories of geological analog data be systematically organized, indexed, and retrieved to support defensible subsurface modeling under sparse data constraints?

This dissertation establishes the mathematical and architectural foundations for addressing this question, centering three independent feature-extraction pathways—persistent homology, classical geostatistics, and self-supervised visual representations—as the core tools for operationalizing the concept of geological "essence" that underpins the entire retrieval system.

### 1.2 The Two-Pipeline Architecture

To address the operational research question, the project is organized as two coupled pipelines that together form a complete analog retrieval system.

**Pipeline A — the Repository/Cataloguing Pipeline** transforms heterogeneous analog artifacts into a searchable structural representation:

$$\text{Analog data} \;\to\; \text{encode essence} \;\to\; \text{index analogs} \;\to\; \text{geologic index (database)}$$

This pipeline answers three fundamental questions. First, how do we transform heterogeneous analog artifacts—full-resolution geological images, 3D reservoir models, seismic volumes, core photographs, and simulation outputs—into a unified structural representation? Second, what constitutes an "index entry" for an analog—a single feature vector, a hierarchical descriptor, a set of topological invariants? Third, how do we organize the repository such that retrieval is both computationally fast and scientifically defensible?

**Pipeline B — the Query/Retrieval Pipeline** maps sparse, incomplete field observations into the same representation space as the database for comparison and retrieval:

$$\text{Sparse observations} \;\to\; \text{encode essence} \;\to\; \text{compare to index} \;\to\; \text{retrieve analog(s)}$$

This pipeline faces a fundamentally different challenge: the query data are sparse, multimodal, and incomplete. A typical query might consist of three well logs, a partial seismic section, and a handful of interpreted facies labels—from which the system must infer enough about the subsurface structure to identify compatible analogs. Pipeline B must answer: how do sparse observations become a query in the same "essence space" as the database? How is similarity computed when some invariant dimensions are missing or unobservable? And what retrieval object is returned—a single best analog, a ranked set, an equivalence class, or a posterior distribution over candidate analogs?

The core coupling requirement binding the two pipelines is:

> The essence representation used in Pipeline A must be compatible with the essence representation inferred from sparse data in Pipeline B.

Without this compatibility, the system cannot function: if the cataloguing pipeline organizes analogs by one set of structural descriptors and the query pipeline infers a different set, retrieval becomes meaningless. Ensuring compatibility under asymmetric information—Pipeline A sees complete patterns while Pipeline B sees only sparse samples—is one of the central architectural challenges of this dissertation.

### 1.3 Essence as the Enabling Abstraction

For this phase of the research, *essence* is defined as:

> Multiscale structural invariance independent of generator artifacts.

This definition is deliberately operational rather than metaphysical (following the pragmatist tradition of Peirce, James, and Dewey). We make no claim about Platonic forms or Aristotelian essences. We claim only that if a structural descriptor remains invariant across multiple independent generative processes, multiple observation modalities, and multiple representational pathways, it has earned the designation "essence" for the practical purposes of analog retrieval. Response invariance—whether analogs sharing the same structural essence also produce similar dynamic responses to stimulation—is deferred to future work.

The purpose of determining essence is therefore twofold: to identify invariant structural descriptors that can organize analog repositories (Pipeline A) and to verify that these same descriptors are inferable, at least partially, from sparse observations (Pipeline B). If structural invariants can be formally identified and validated, then Pipeline A can organize the repository around scientifically justified equivalence classes and Pipeline B can query the repository using structurally meaningful constraints rather than subjective matching. Without a rigorous essence definition, Pipeline A collapses into heuristic clustering and Pipeline B collapses into ad hoc similarity judgments. Essence determination is the bridge that makes both pipelines principled.

### 1.4 Dissertation Overview

This dissertation develops the mathematical and architectural foundations for the two-pipeline system, organized around three pillars: the generator (experimental apparatus), essence determination (three-pathway feature extraction and validation), and essence retrieval (sparse-to-dense inference and analog matching).

**Pillar I — The Generator.** Section 2 presents the design of the principle-based geological image generator—the experimental apparatus that produces controlled training data with known structural properties for invariance testing across three depositional environments (fluvial, aeolian, estuarine). The generator provides the controlled data on which all subsequent validation depends.

**Pillar II — Essence Determination and Categorization.** Sections 3–5 develop the mathematical foundations for the three independent feature-extraction pathways: persistent homology (topological spaces, simplicial complexes, homology groups, persistence, and the stability theorem), classical geostatistics (variogram theory, connectivity functions, fractal dimensions, kriging), and self-supervised visual representations (vision transformers, DINO self-distillation, LoRA fine-tuning, representation geometry). Section 6 examines how all three pathways are applied within the Qualia Convergence Framework, including the three-pathway feature extraction architecture, the $H_1$ hypothesis for channel discrimination, limitations of the topological pathway, and a literature review identifying the integration gap that constitutes the framework's primary novelty. Section 7 engages critically with the ellipse degradation thought experiment, revealing problems with degradation-based definitions and motivating generator invariance. Section 8 develops a structured evidence hierarchy for essence claims organized by epistemic strength, governing both pipeline operations. Section 10 develops the Sākṣī validation framework—ten independent witnesses, the LOGO protocol, geology-specific adversarial tests, and a pre-committed Claim Survival Matrix. Section 11 explores cross-domain applications as evidence for mathematical universality.

**Pillar III — Essence Retrieval.** Section 9 presents the system architecture connecting invariant descriptors to analog retrieval: the Neural Process query encoder, the hyperbolic embedding space, the Perceiver IO fusion module, and the pathway fusion layer. Section 12 describes the proposed experimental validation design.

**Extensions and Synthesis.** Section 13 discusses open questions and the path forward. Section 14 develops three extensions: dynamic response essence via basin-of-attraction topology, a confidence hierarchy exploiting epistemic asymmetry across pathways, and an uncertainty quantification pipeline grounded in feature residual decomposition. Section 15 concludes with an assessment of the framework's contributions and limitations.

---

## 2. The Principle-Based Generator: Experimental Apparatus for Invariance Testing

Before developing the mathematical machinery for each feature-extraction pathway, we establish the experimental apparatus that makes systematic testing possible. This section describes the design of a *principle-based geological image generator* that produces synthetic depositional analogs with known generating parameters, providing the controlled data necessary to test the $H_1$ hypothesis, execute the LOGO (Leave-One-Generator-Out) protocol, and populate the evidence hierarchy with empirical results.

The generator is not merely a data source. It is the instrument that makes the entire framework *testable*. Without controlled generation—images whose structural properties are known by construction—the demands for cross-generator invariance testing (Level 6), severe adversarial testing (Level 2), and the linchpin $H_1$ experiment all remain abstract aspirations rather than executable protocols. By presenting the generator first, we establish the experimental context within which the mathematical foundations (Sections 3–5), the three-pathway architecture (Section 6), and the validation framework (Section 10) are to be understood.

### 2.1 Why Build a Generator?

Three approaches exist for obtaining geological image data with the properties required for systematic invariance testing:

| Approach | Advantages | Limitations | Role in Framework |
|---|---|---|---|
| **Real data** (outcrop photos, seismic interpretations) | Highest fidelity; generator-independent by definition | Limited availability; unknown true structural parameters; expensive acquisition | Validation only (Level 5 evidence) |
| **Process-based simulation** (e.g., Flumy, BRAHMS) | Physically realistic; solves governing PDEs | Computationally expensive; typically single-environment; parameters interact nonlinearly | Held-out generator in LOGO test |
| **Principle-based generation** (this work) | Fast; interpretable; multi-environment; known ground truth | Lower physical fidelity than process-based | Primary training data |

The principle-based approach is chosen as the primary data source for a specific epistemic reason: *known ground truth is essential for the LOGO test*. When we generate an image using specified parameters—a meandering channel with sinuosity $S = 1.8$, wavelength $\lambda = 12W$, and bankfull width $W = 15$ pixels—we know exactly what structural properties the image should exhibit. This allows rigorous testing of whether PH features capture those properties invariantly across generator families. If representations trained on principle-based, GAN-generated, and MPS-generated images transfer successfully to process-based (Flumy) images, the invariance claim is strengthened because the generators employ fundamentally different mechanisms: empirical formulas, adversarial training, statistical pattern reproduction, and physics simulation, respectively.

### 2.2 Generator Taxonomy and Design Philosophy

Our generator occupies a deliberate position in the geological image generation landscape, distinguished by its epistemic function rather than its physical fidelity.

**Process-based generators** (Flumy, BRAHMS, Delft3D) solve partial differential equations governing sediment transport, fluid flow, and morphodynamic evolution. They produce the most physically realistic outputs but at significant computational cost—a single Flumy realization may require hours of simulation time. More critically for our purposes, their generating parameters interact through physical processes in ways that make the relationship between input parameters and output structural properties opaque: adjusting one parameter (e.g., discharge) cascades through the physics to alter multiple structural features simultaneously. This opacity makes them unsuitable as primary training data but ideal as held-out generators in the LOGO test, precisely because their fundamentally different generation mechanism provides the strongest test of cross-generator invariance.

**Statistical generators** (Multiple-Point Statistics methods: SNESIM, Direct Sampling) reproduce spatial patterns from training images without an explicit physical model. They are fast and flexible but inherit whatever structural properties their training images contain, creating a circularity risk: if invariance is tested across statistical generators trained on similar training images, apparent invariance may reflect shared training data rather than genuine structural properties.

**Principle-based generators** (this work) implement empirical geomorphological formulas—quantitative relationships between observable parameters (channel width, sinuosity, meander wavelength) derived from field measurements and published in the sedimentological literature. They are intermediate in fidelity: more physically grounded than statistical generators (because the formulas encode real physics, albeit approximately) but less physically realistic than process-based generators (because they apply equilibrium relationships rather than solving dynamical equations). Their key advantage is *transparency*: every structural property of the output is traceable to a specific input parameter and a specific empirical relationship, making them ideal for systematic invariance testing.

The design philosophy can be summarized: *constrain geometry with empirical formulas from the literature, not with physics simulation*. The generator does not solve the Saint-Venant equations for shallow water flow or the Exner equation for sediment continuity. Instead, it directly implements the geometric relationships that these equations produce at equilibrium—relationships that have been measured, validated, and published by geomorphologists over decades of field work. This approach sacrifices physical realism in exchange for interpretability, computational speed, and known ground truth.

### 2.3 Three Depositional Environments

The generator encompasses three major depositional environments, each with multiple sub-styles that span the morphological diversity observed in natural systems:

**Fluvial**: Channel systems governed by the Leopold-Wolman (1957) classification, producing meandering, braided, and anastomosing architectures. **Aeolian**: Dune fields governed by the Werner (1995) cellular automaton framework, producing barchan, linear/seif, and transverse morphologies. **Estuarine**: Coastal systems governed by tidal prism relationships, producing tide-dominated, wave-dominated, and mixed-energy configurations informed by recent work from Jiwei et al. (2025).

This three-environment, nine-substyle design provides the morphological diversity required for meaningful cross-environment testing: if PH features trained on fluvial systems transfer to aeolian and estuarine systems, the argument for mathematical universality (Section 11) is substantiated empirically, not merely by analogy.

### 2.4 Fluvial Environment: The Leopold-Wolman Framework

The fluvial generator implements three channel styles based on the Leopold-Wolman (1957) classification of alluvial channels, supplemented by subsequent quantitative work from Leopold and Wolman (1960), Leopold, Wolman, and Miller (1964), Williams (1986), Parker (1976), Fredsøe (1978), Hundey and Ashmore (2009), and Nanson and Knighton (1996).

**Meandering channels.** The meandering sub-generator applies the empirical relationships for single-thread sinuous channels. The fundamental geometric constraint is the wavelength-width coupling:

$$\lambda = k \times W, \quad k \in [10, 14]$$

where $\lambda$ is the meander wavelength (distance between successive bend apexes on the same side of the channel) and $W$ is the bankfull channel width. The original regression of Leopold & Wolman (1960) yielded $\lambda = 10.9 W^{1.01}$, effectively linear; the range $k \in [10, 14]$ reflects the practical scatter documented by Leopold, Wolman, and Miller (1964). The radius of curvature at bend apexes is similarly constrained:

$$R_c = m \times W, \quad m \in [2, 3]$$

where $R_c$ is the radius of curvature at the tightest part of each bend (Williams, 1986). These relationships ensure that generated meander forms respect the dimensional scaling observed in natural rivers rather than producing geometrically arbitrary sinusoidal patterns.

The generation sequence proceeds through a defined depositional hierarchy: (1) channel belt boundary definition; (2) arc-based centerline generation with curvature-constrained bends (not sinusoidal approximations, which are geometrically incorrect for natural meanders); (3) curvature-driven bankfull width variation ($\pm 15\text{--}30\%$ of mean width, wider in bends than straights, reflecting the velocity reduction in curved flow); (4) exponential-decay levees following $h(x) = h_0 \exp(-x / L_d)$, where the decay length $L_d$ is $5\text{--}15$ times the channel width; (5) point bar deposition exclusively on inner bends, with lateral extent scaling to $1.5\text{--}2 \times W$ and intensity modulated by local curvature; (6) arcuate scroll bars confined to point bar regions, recording lateral accretion history through concentric ridges that follow the bend shape; (7) oxbow lakes generated deterministically at neck cutoff locations (where the neck distance between upstream and downstream limbs falls below $W$), with shapes tracing the abandoned meander loop rather than geometric placeholders; and (8) floodplain texture with sedimentary overlays including cross-bedding, ripple marks, fining-upward sequences, and lateral accretion surfaces.

The complete parameter specification for the three fluvial channel styles:

| Parameter | Symbol | Meandering | Braided | Anastomosing |
|---|---|---|---|---|
| Bankfull width | $W$ | 6–20 px | 12–28 px | 8–14 px |
| Sinuosity | $S$ | 1.3–2.5 | N/A | 1.0–1.3 |
| Wavelength multiplier | $k$ | 10–14 | N/A | N/A |
| Curvature multiplier | $m$ | 2–3 | N/A | N/A |
| Thread/branch count | $N$ | 1 | 3–9 | 2–6 |
| Bifurcation spacing | $\Delta x_{\textrm{bif}} / W$ | N/A | 4–5 | N/A |
| Bar aspect ratio | $L/W$ | N/A | $\sim 5:1$ | N/A |
| Marsh/wetland fraction | $f_{\textrm{marsh}}$ | N/A | N/A | 0.2–0.7 |
| Levee decay length | $L_d / W$ | 5–15 | N/A | 5–15 |
| Oxbow mechanism | — | Deterministic cutoff | N/A | N/A |
| Crevasse fan length | $L_{\textrm{fan}}$ | N/A | N/A | 15–60 px |

*Note on sinuosity range.* The classical threshold for "meandering" channels is $S \geq 1.5$ (Leopold & Wolman, 1957); below this, channels are considered transitional or low-sinuosity. The generator deliberately extends the meandering range down to $S = 1.3$ to include transitional channels that occupy the ambiguous zone between straight and fully meandering. This choice is epistemically motivated: transitional channels are the hardest cases for classification, and including them in the training database tests whether the topological pathway can discriminate channel architecture in exactly the regime where classical features are most likely to fail. The lower bound of the anastomosing range ($S \in [1.0, 1.3]$) creates a deliberate overlap zone at $S = 1.3$, reflecting the genuine ambiguity in the field between low-sinuosity meandering and high-sinuosity anastomosing systems.

**Braided channels.** The braided sub-generator implements a bifurcation-confluence network model. The key physical constraint is the confluence-bifurcation spacing:

$$\Delta x_{\textrm{bif}} = k \times W, \quad k \in [4, 5]$$

where $\Delta x_{\textrm{bif}}$ is the downstream distance between successive bifurcation or confluence events. Parker (1976) provided the theoretical stability analysis showing that alternate bar instability scales with channel width; Hundey and Ashmore (2009) empirically measured the confluence-bifurcation unit length in physical models and aerial photographs of braided rivers, establishing the $k \in [4, 5]$ range. Channels must split and merge around bars, not run in parallel—the fundamental topological distinction between braided and meandering systems that the $H_1$ hypothesis is designed to detect. Bars form at bifurcation points with aspect ratios of approximately $5:1$ (length-to-width in the downstream direction), creating the characteristic diamond-shaped mid-channel bars that force flow splitting. The braiding threshold is defined by a width-to-depth ratio $W/d > 50$ (Parker, 1976; Fredsøe, 1978), derived from stability analysis of alternate bar formation rather than from the slope-discharge discriminant of Leopold and Wolman (1957).

**Anastomosing channels.** The anastomosing sub-generator produces multiple narrow, low-sinuosity channels ($S \in [1.0, 1.3]$) with cohesive banks that prevent lateral migration (Nanson & Knighton, 1996). Channel splitting occurs through avulsion rather than bar-forced bifurcation: when levee aggradation causes the channel bed to rise above the surrounding floodplain (superelevation), the channel abandons its current course and establishes a new path at a lower elevation. The floodplain is dominated by wetland environments (60–90% coverage), with crevasse splay fans at levee breach points recording overbank flooding events.

**Fluvial acceptance criteria.** Each generated realization must satisfy environment-specific quality gates before entering the training database:

| Metric | Meandering | Braided | Anastomosing |
|---|---|---|---|
| $\beta_{\textrm{iso}}$ | 0.65–1.1 | 0.35–0.9 | 0.5–1.0 |
| Anisotropy ratio | $\leq 1.2$ | $\leq 1.5$ | $\leq 1.3$ |
| Point-bar compactness | 0.35–0.65 | N/A | 0.4–0.7 |
| Thread connectivity | N/A | $\geq 0.8$ | $\geq 0.6$ |

where $\beta_{\textrm{iso}}$ is the isotropic variogram power-law slope, anisotropy ratio is $\max(\beta_{\textrm{dir}}) / \min(\beta_{\textrm{dir}})$ across directional variograms, compactness is $4\pi A / P^2$ for point bar polygons, and connectivity is $1 - \chi / A$ ($\chi$ = Euler characteristic) for channel network masks. Realizations failing any criterion are rejected and regenerated.

### 2.5 Aeolian Environment: The Werner Dune Framework

The aeolian generator implements three dune morphologies based on the Werner (1995) cellular automaton model of dune self-organization, parameterized by wind regime and sand supply.

**Barchan dunes** form under unidirectional wind with moderate sand supply, producing crescent-shaped bodies with characteristic horns extending downwind from a steep slip face. **Linear (seif) dunes** form under bidirectional or seasonally varying wind, producing elongate ridges with high continuity indices ($C_{\textrm{ridge}} \geq 0.7$) and Y-junction branching. **Transverse dunes** form under strong unidirectional wind with high sand supply, producing crest-parallel ridges orthogonal to the prevailing wind direction with regular spacing.

The key parameters and their ranges:

| Parameter | Symbol | Range | Default |
|---|---|---|---|
| Wind azimuth | $\theta$ | $[0°, 180°]$ | $60°$ |
| Dune height | $H$ | $[5, 40]$ px | 18 px |
| Crest spacing | $\lambda_{\textrm{crest}}$ | $[20, 120]$ px | 60 px |
| Interdune fraction | $f_{\textrm{inter}}$ | $[0.1, 0.6]$ | 0.3 |
| Slip face angle | $\alpha_{\textrm{slip}}$ | $[28°, 34°]$ | $32°$ |
| Ridge continuity | $C_{\textrm{ridge}}$ | $[0.3, 0.9]$ | 0.7 |

Acceptance criteria require that crest orientation error $|\theta_{\textrm{PSD}} - \theta_{\textrm{wind}}| \leq 15°$, ridge continuity falls within morphology-specific bands (barchan: 0.3–0.5; linear: $\geq 0.7$; transverse: 0.4–0.6), and spacing regularity (coefficient of variation) satisfies $\textrm{CV} \leq 0.3$ for barchan, $\leq 0.25$ for linear, and $\leq 0.2$ for transverse morphologies.

### 2.6 Estuarine Environment: The Tidal Prism Framework

The estuarine generator implements three dominance regimes governed by the interplay of tidal prism and wave energy, informed by classical tidal prism relationships and recent work from Jiwei et al. (2025) on tidal-dominated estuary reservoir modeling.

**Tide-dominated estuaries** are characterized by high tidal prism and protected shoreline conditions, producing ebb-flood channel pairs, elongate tidal bars, and extensive mudflats. The key geometric constraint is the ebb-flood separation angle ($\Delta\theta \geq 25°$), reflecting the bipolar flow that drives sediment redistribution. **Wave-dominated estuaries** are characterized by high wave energy and exposed shoreline, producing shoreface-parallel bars, smooth shoreline profiles, and distributary mouth bars with high aspect ratios ($\textrm{AR}_{\textrm{mouth}} = 2.0\text{--}4.0$). **Mixed-energy estuaries** exhibit blended morphologies, with a tunable dominance slider $\delta \in [0, 1]$ controlling the transition between tidal and wave end-members.

The key parameters:

| Parameter | Symbol | Range | Default |
|---|---|---|---|
| Tidal prism index | $P_{\textrm{tide}}$ | $[0.1, 1.0]$ | 0.5 |
| Wave energy index | $E_{\textrm{wave}}$ | $[0.0, 1.0]$ | 0.4 |
| Dominance slider | $\delta$ | $[0, 1]$ | 0.5 |
| Channel sinuosity | $S_{\textrm{chan}}$ | $[1.0, 1.8]$ | 1.4 |
| Bar wavelength | $\lambda_{\textrm{bar}}$ | $[20, 150]$ px | 60 px |
| Mouth-bar aspect ratio | $\textrm{AR}_{\textrm{mouth}}$ | $[1.2, 4.0]$ | 2.5 |
| Mudflat fraction | $f_{\textrm{mud}}$ | $[0.1, 0.5]$ | 0.25 |

A distinctive contribution of the estuarine generator is the incorporation of interlayer statistics from Jiwei et al. (2025), whose seismic facies analysis of tidal-dominated reservoirs identified three interlayer types with characteristic proportions:

| Interlayer Type | Description | Proportion | Mean Thickness |
|---|---|---|---|
| Type I | Thick interlayers | 61% | $\sim 0.3$ m |
| Type II | Thin interlayers | 33% | $< 0.5$ m |
| Type III | Zero thickness | 6% | 0 m |

These statistics constrain the fine-scale heterogeneity of generated estuarine images, ensuring that internal reservoir architecture reflects observed distributions rather than arbitrary assumptions.

### 2.7 Validation Strategy: Internal and External

The generator validation strategy operates at two levels that correspond to different positions in the evidence hierarchy.

**Internal validation (per-realization).** Each generated image undergoes automated acceptance testing against the metric bands specified in Sections 2.4–2.6. Images failing any criterion are rejected and regenerated with a new random seed, producing a quality-controlled ensemble in which every realization satisfies environment-specific structural constraints. The target acceptance rate with reasonable parameters is $\geq 90\%$; rates significantly below this threshold indicate that the generator's parameter space is misspecified relative to the empirical relationships it implements.

**External validation (LOGO test).** The generator's primary validation is its role in the Leave-One-Generator-Out test, which provides Level 6 evidence (cross-generator validation) in the evidence hierarchy. The LOGO protocol trains representations on images from multiple generator families—principle-based (this work), statistical (MPS), and learned (GAN)—and evaluates transfer to a held-out process-based generator (Flumy):

$$\textrm{Train:} \; \lbrace \textrm{Principle-based, MPS, GAN} \rbrace \;\;\to\;\; \textrm{Test:} \; \lbrace \textrm{Flumy (process-based)} \rbrace$$

If representations trained on the first three generators transfer successfully to Flumy—a fundamentally different generative process that solves physics equations rather than applying empirical formulas—the invariance claim is strengthened. The epistemic force of this test depends on the *diversity* of the training generators: our principle-based generator, which implements empirical scaling laws, provides a qualitatively different generation mechanism from both statistical reproduction (MPS) and adversarial learning (GAN), maximizing the diversity of the training pool and thereby strengthening the LOGO test's evidential force.

### 2.8 Current Implementation Status and Path Forward

Intellectual honesty requires acknowledging the gap between the generator design presented above and its current implementation. The fluvial environment is substantially implemented, with both physics-based and legacy generation algorithms available for meandering, braided, and anastomosing channel systems. The physics-based variants implement the quantitative constraints from the sedimentological literature detailed in Section 2.4, including arc-based meander centerlines, curvature-driven width variation, point bar deposition, and bifurcation-confluence braided networks. Sedimentary overlays—channel-fill textures, cross-bedding, ripple marks, lateral accretion surfaces, and fining-upward sequences—are implemented and produce per-realization petrology metadata.

The aeolian and estuarine environments exist only as design specifications. Detailed product requirement documents with parameter tables, acceptance criteria, and generation algorithms have been developed, but code implementation has not yet begun. This sequencing is deliberate: the fluvial environment provides the data for the $H_1$ experiment (Section 12.2), which is the linchpin test that must be resolved before investment in additional environments is warranted. If $H_1$ features do not discriminate braided from meandering architectures on variogram-matched pairs, the framework requires revision before expanding the generator scope.

The path forward is therefore experimentally driven: (1) validate the existing fluvial generator outputs against the acceptance criteria of Section 2.4, (2) execute the $H_1$ experiment using fluvial data, (3) if the $H_1$ hypothesis is confirmed, implement the aeolian and estuarine environments to enable the full cross-environment testing described in Section 2.3, and (4) execute the LOGO test with all three environments to provide Level 6 evidence for the invariance claim.

---

## 3. Mathematical Foundations of Persistent Homology

### 3.1 From Topology to Data Analysis

Topology is the branch of mathematics concerned with properties of shapes that are preserved under continuous deformations—stretching, bending, and twisting—but not tearing or gluing. While geometry asks "how far apart are these two points?" topology asks "are these two spaces fundamentally the same shape?" The classical illustration is the homeomorphism between a coffee mug and a doughnut: both possess exactly one hole, making them topologically equivalent despite their obvious geometric dissimilarity (Kemmea & Agyingi, 2025). A homeomorphism $f: X \to Y$ is a bijective continuous function with continuous inverse—a formal way of saying "you can deform one into the other without cutting or gluing."

This focus on *invariant structure* rather than metric detail is precisely what makes topology powerful for data analysis. When a geoscientist examines two reservoir images and recognizes both as "braided fluvial systems" despite different scales, orientations, and noise levels, they are performing an intuitive topological classification—recognizing that both images share a structural property (interconnected channel networks) that persists under geometric transformations. The Qualia Convergence Framework seeks to formalize this intuition mathematically.

Topological Data Analysis (TDA) emerged from the recognition that real-world datasets—point clouds sampled from unknown manifolds, images of complex structures, time series of dynamical systems—possess intrinsic *shape* carrying meaningful information beyond what statistical summaries capture. Conventional machine learning approaches rely primarily on statistical relationships, local density estimations, or distance-based measures within datasets (Carlsson, 2009). These methods effectively capture local structure but often fail to detect global topological features—loops, tunnels, voids—that may encode essential characteristics of the data-generating process.

Consider a concrete geological example. A variogram computed from a braided channel system and a variogram computed from a meandering channel system can be nearly identical if the spatial correlation lengths are similar. Yet the two systems have fundamentally different *connectivity*: the braided system contains multiple interconnected channels forming closed loops, while the meandering system has a single sinuous channel. No amount of two-point statistical analysis will distinguish these configurations—the difference is topological, not statistical. Persistent homology is designed precisely to detect such differences.

### 3.2 Topological Foundations: Spaces, Continuity, and Distance

Before constructing simplicial complexes and computing homology, three foundational concepts establish the mathematical ground we stand on. These are not mere technicalities—each one answers a specific question that arises when we try to move from intuitive shape recognition to rigorous computation.

**What is a topological space?** Informally, topology studies what stays the same when you stretch and bend a shape but don't tear it. A *topological space* $(X, \tau)$ consists of a set $X$ and a collection $\tau$ of subsets called "open sets" satisfying three axioms: (1) the empty set $\emptyset$ and $X$ itself are in $\tau$; (2) $\tau$ is closed under finite intersections; and (3) $\tau$ is closed under arbitrary unions (Kemmea & Agyingi, 2025, Definition 1). These axioms formalize the notion of "nearness" without requiring any concept of distance—they define which points are "close together" in a purely structural sense.

The power of this abstraction is visible in the classification of surfaces by *genus* (the number of holes). Imagine holding everyday objects: a marble has genus 0 (no holes); a doughnut has genus 1 (one hole through the center); a pair of scissors has genus 2 (two finger-holes); a cheese grater, with its many perforations, has genus 3 or more. Objects within each genus class are *homeomorphic*—continuously deformable into one another—regardless of their geometric appearance. This is the same kind of invariance we seek in geological pattern recognition: two reservoir images may look different at the pixel level but share the same topological "type."

**When are two spaces "the same shape"?** Homeomorphism (§3.1) tells us when two spaces are topologically identical, but a softer notion—*homotopy*—tells us when two spaces are equivalent in a way that preserves precisely the features homology detects. A *homotopy* between continuous maps $f, g: X \to Y$ is a continuous function $H: X \times [0,1] \to Y$ satisfying $H(x,0) = f(x)$ and $H(x,1) = g(x)$ (Kemmea & Agyingi, 2025, Definition 3). Intuitively, $H$ is a continuous deformation that smoothly morphs one map into another over a "time" parameter $t \in [0,1]$.

This concept motivates homology directly. Imagine a solid disk: you can continuously contract it to a single point by shrinking it inward—it is *contractible*, with no holes to obstruct the contraction. Now imagine a circle (just the boundary, no interior): any attempt to shrink it to a point must at some moment "jump" across the hole in the middle. No continuous deformation can make the circle contractible. Spaces that are *homotopy equivalent* (continuously deformable into each other) have isomorphic homology groups. This is why homology reliably detects holes—they are homotopy invariants, persisting under any stretching, bending, or reshaping short of filling them in.

**How do we measure closeness in data?** Our geological data begins as discrete measurements—pixels in images, depth readings in well logs, scattered outcrop observations—with no inherent topological structure. To build the combinatorial structures on which homology computation depends, we need a principled notion of distance. A *metric space* $(M, d)$ is a set $M$ equipped with a distance function $d: M \times M \to [0, \infty)$ satisfying four properties:

1. *Identity*: $d(x,y) = 0$ if and only if $x = y$
2. *Positivity*: $d(x,y) > 0$ when $x \neq y$
3. *Symmetry*: $d(x,y) = d(y,x)$
4. *Triangle inequality*: $d(x,z) \leq d(x,y) + d(y,z)$

These properties ensure distance behaves as spatial intuition expects: you cannot take a shortcut that beats the direct path. Metric spaces connect topology to data because they provide the threshold-based construction of simplicial complexes discussed in §3.3: two points are connected by an edge when $d(x,y) \leq \epsilon$. Without a metric, there is no principled way to decide which points should be "neighbors"—and thus no way to build the shape-from-data machinery that follows.

### 3.3 Simplicial Complexes: Building Shapes from Data

The bridge from raw data to topological analysis is the *simplicial complex*, a combinatorial structure that systematically builds higher-dimensional shapes from discrete points.

**Definition** (Abstract Simplicial Complex). An abstract simplicial complex $K$ over a vertex set $V$ is a collection of non-empty subsets of $V$ satisfying:
1. Every single vertex $\lbrace v \rbrace$ with $v \in V$ is in $K$.
2. If a set of vertices $\sigma$ belongs to $K$, then all subsets of $\sigma$ also belong to $K$ (closure property).

The building blocks are $k$-simplices: a 0-simplex is a point, a 1-simplex is an edge connecting two points, a 2-simplex is a filled triangle, and a 3-simplex is a solid tetrahedron. More generally, a $d$-dimensional simplex is the convex hull of its $d+1$ vertices:

$$\sigma = \left\lbrace \sum_{i=0}^{d} t_i v_i \;\mid\; t_i \geq 0, \;\sum_{i=0}^{d} t_i = 1 \right\rbrace$$

The closure property is intuitively necessary: if we claim a triangle exists (3 points mutually connected), then its edges and vertices must also exist.

**Why this matters for our research**: Simplicial complexes provide the mathematical scaffolding that allows us to talk rigorously about "shape" in data that is fundamentally discrete (pixel grids, point clouds). Without this structure, we cannot define concepts like "loop" or "connected component" in a way that admits algebraic computation.

**Constructing complexes from data.** For point cloud data in a metric space $(M, d)$, simplicial complexes are constructed by connecting points based on proximity. Given a threshold distance $\epsilon$, the *Vietoris–Rips complex* $\textrm{VR}_\epsilon$ includes a $k$-simplex whenever all $\binom{k+1}{2}$ pairwise distances among its vertices are at most $\epsilon$ (Otter et al., 2017). As $\epsilon$ increases from zero, isolated points gradually connect into edges, triangles, and higher-dimensional simplices—the data "fills in" and reveals its underlying shape.

For gridded image data—such as geological facies maps where each pixel has a binary value (channel vs. floodplain)—*cubical complexes* provide a computationally more natural and efficient alternative. Instead of constructing simplices from point-pairs, the cubical approach treats each pixel as an elementary square (2-cube) and builds the filtration by thresholding on pixel values (Kaczynski, Mischaikow, & Mrozek, 2004; Wagner, Chen, & Vuçini, 2012). This distinction—Vietoris–Rips for point clouds, cubical for images—is practically important for the QCF, which works primarily with geological images.

### 3.4 Homology: Detecting Holes Algebraically

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

**The fundamental property**: $\delta_{k-1} \circ \delta_k = 0$—the boundary of a boundary is always empty. This is not merely a technical convenience; it expresses a deep geometric truth. The boundary of a filled triangle is a closed loop; a closed loop has no boundary (no endpoints). This property guarantees a critical containment: every boundary is automatically a cycle, but not every cycle is a boundary—and it is this gap that homology detects.

The chain groups connected by boundary maps form a *chain complex*:

$$0 \to C_k(K) \xrightarrow{\delta_k} C_{k-1}(K) \to \cdots \xrightarrow{\delta_1} C_0(K) \to 0$$

**From chains to homology.** The fundamental property $\delta \circ \delta = 0$ allows us to define two subsets of the chain group that are central to everything that follows. The *kernel* of $\delta_k$, written $\ker(\delta_k)$, is the set of all $k$-chains whose boundary is zero. The *image* of $\delta_{k+1}$, written $\textrm{im}(\delta_{k+1})$, is the set of all $k$-chains that are the boundary of some $(k{+}1)$-chain.

Elements of the kernel are called **$k$-cycles** — chains with no boundary. A 1-cycle, for example, is a collection of edges that forms one or more closed loops: every vertex appears an even number of times, so the boundary (the sum of endpoints) cancels to zero. Elements of the image are called **$k$-boundaries** — chains that bound a filled region of one dimension higher.

Because $\delta_{k} \circ \delta_{k+1} = 0$, every boundary is automatically a cycle (if $\gamma = \delta_{k+1}(\alpha)$, then $\delta_k(\gamma) = \delta_k \circ \delta_{k+1}(\alpha) = 0$). But not every cycle is a boundary — some cycles surround genuine unfilled holes. A closed loop of edges around an unfilled region has no boundary (it is a cycle) and is not the boundary of any filled surface (nothing fills the hole) — this is a genuine topological feature. The same loop around a filled triangle *is* a boundary, and thus a false positive: the "hole" was already filled in. Distinguishing the genuine holes from the false positives is exactly what homology computes.

The algebraic tool for this distinction is the quotient group: we take all cycles and collapse those that differ only by a boundary into the same equivalence class. What remains are the genuine holes. The $k$-th *homology group* formalizes this:

$$H_k(K) = \ker(\delta_k) \,/\, \textrm{im}(\delta_{k+1})$$

This quotient captures precisely the $k$-dimensional cycles that are *not* boundaries of $(k{+}1)$-dimensional chains. Two cycles that differ by a boundary are considered equivalent — they enclose the same hole. The non-boundary cycles that survive this collapsing are the genuine topological "holes" in dimension $k$.

**Worked example: detecting a hole.** A concrete example makes the abstraction tangible. Consider three wells arranged in a triangle—call them $v_0$, $v_1$, $v_2$—with edges connecting each pair. The 1-chain $\gamma = [v_0, v_1] + [v_1, v_2] + [v_0, v_2]$ traces a closed loop through all three edges. Applying the boundary map:

$$\delta_1(\gamma) = (v_0 + v_1) + (v_1 + v_2) + (v_0 + v_2) = 0$$

Each vertex appears exactly twice, and $1 + 1 = 0$ in $\mathbb{Z}_2$, so every vertex cancels. The loop has no boundary—it is a 1-cycle. Now the critical question: is this cycle a boundary?

- **If the triangle is filled** (the 2-simplex $[v_0, v_1, v_2]$ exists): then $\gamma = \delta_2([v_0, v_1, v_2])$, and the cycle is a boundary. It encloses no hole—the interior fills the loop. This cycle is trivial in $H_1$.
- **If the triangle is unfilled** (only edges, no face): then $\gamma$ is a cycle that is not a boundary of anything. It detects a genuine 1-dimensional hole—a nontrivial element of $H_1$.

This is exactly how homology works: cycles that bound filled regions are trivial; cycles that enclose genuine holes survive in the homology group. The quotient $H_k = \ker / \textrm{im}$ is doing precisely this classification — it takes every cycle and asks "is this the boundary of something filled?" If yes, it collapses to zero (false positive). If no, it survives as a genuine topological feature. The same geometric loop gets a different algebraic answer depending on what fills its interior, and this is exactly the discriminating power we need.

Consider the geological analogy: in a braided channel system, channels form loops around unfilled floodplain islands — these are genuine $H_1$ features because nothing fills the interior. In a meandering system, an oxbow lake might close a loop, but the interior is typically filled with deposited sediment — that loop dies in homology because the filled region makes it a boundary. The same geometric shape (a closed path of channels) carries different homological meaning depending on what occupies its interior. This is why $\beta_1$ — the count of surviving loops — discriminates braided from meandering architectures in a way that variograms, which see only pairwise correlation, fundamentally cannot.

**Betti numbers.** The homology groups capture the essential topological features of the space. These features are quantified by *Betti numbers*—the rank (dimension) of each homology group, denoted $\beta_k$:

| Betti Number | What It Counts | Geological Interpretation |
|---|---|---|
| $\beta_0$ | Connected components | Isolated channel bodies, separate sand bodies |
| $\beta_1$ | Loops / 1-dimensional holes | Channel network loops, oxbow lakes, braiding |
| $\beta_2$ | Enclosed voids | 3D enclosed cavities (relevant for pore-space analysis) |

For reference, standard shapes have characteristic Betti numbers: a circle has $(\beta_0, \beta_1) = (1, 1)$; a sphere has $(\beta_0, \beta_1, \beta_2) = (1, 0, 1)$; a torus has $(\beta_0, \beta_1, \beta_2) = (1, 2, 1)$; two disjoint circles have $(\beta_0, \beta_1) = (2, 2)$.

**Why this matters for our research**: The braided-versus-meandering geological analogy above is not merely illustrative — it is the core of the $H_1$ hypothesis developed in §6.6. The topological difference between braided and meandering systems (the number and persistence of surviving loops) is invisible to variograms and other two-point statistics. Homology detects it directly, providing the structural discrimination that motivates persistent homology's role in the Qualia Convergence Framework.

### 3.5 Persistent Homology: Tracking Features Across Scales

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

### 3.6 Stability: The Theoretical Guarantee

The property that makes persistent homology practically viable—and, as we shall argue, theoretically central to the entire research program—is the *stability theorem* of Cohen-Steiner, Edelsbrunner, and Harer (2007):

> **Stability Theorem.** For tame functions $f$ and $g$ on a triangulable space,
> $$d_B\big(\textrm{Dgm}(f),\, \textrm{Dgm}(g)\big) \leq \lVert f - g \rVert_\infty$$
> where $d_B$ denotes the bottleneck distance between persistence diagrams and $\lVert \cdot \rVert_\infty$ the supremum norm.

In plain language: **small changes to the input produce small changes to the persistence diagram.** If two geological images differ by at most $\epsilon$ in pixel values (due to noise, measurement error, or different but similar generative processes), their persistence diagrams can differ by at most $\epsilon$ in bottleneck distance.

This guarantee is *mathematical*, not empirical. It does not depend on which generators are used, which dataset is tested, or how many experiments are run. It is a theorem about the mathematical structure of persistent homology itself. As we shall argue in Sections 7–8, this makes the stability theorem epistemically stronger than any empirical invariance test.

**Practical significance.** The stability theorem is what distinguishes TDA from methods sensitive to coordinate perturbations. A variogram is also stable (in the sense that small input changes produce small output changes), but the stability of variograms is not *proven*—it is observed empirically. The stability of persistent homology is *proven* from first principles. This distinction matters when the goal is to make robust claims about "essence."

---

## 4. Mathematical Foundations of Classical Geostatistics

*[Note: Sections 3–5 present the mathematical foundations for the three pathways as parallel chapters. In the final dissertation, these may be reorganized into a unified Mathematical Foundations part.]*

### 4.1 From Spatial Statistics to Pattern Description

Classical geostatistics provides the mathematical framework for the QCF's classical pathway—the oldest and most operationally established of the three feature-extraction approaches. Where persistent homology asks "what is the *shape* of this data?", geostatistics asks "what is the *spatial correlation structure* of this data?" The two questions are complementary: correlation structure captures how similar nearby locations tend to be, while topology captures how those locations are *connected*.

The foundational object in geostatistics is the *regionalized variable*—a spatially distributed quantity $Z(\mathbf{x})$ defined at every location $\mathbf{x} \in D \subset \mathbb{R}^d$ in a spatial domain $D$ (Matheron, 1963). In geological applications, $Z(\mathbf{x})$ may represent facies type (channel vs. floodplain), porosity, permeability, seismic amplitude, or any spatially varying property. The key insight of geostatistics is to model $Z(\mathbf{x})$ as a *realization of a random field*—a collection of random variables indexed by spatial location—allowing probabilistic inference about unobserved locations from sparse observations.

This probabilistic framing is directly relevant to the retrieval problem. Pipeline A must characterize the spatial correlation structure of complete analogs, producing descriptors that capture how geological properties covary across space. Pipeline B must infer these same descriptors from sparse observations—a task for which geostatistics was explicitly designed (kriging is literally optimal spatial interpolation under specific assumptions). The classical pathway thus provides not only features for indexing but a theoretical foundation for the sparse-to-dense inference that Pipeline B requires.

### 4.2 Stationarity: The Foundation and Its Limits

Geostatistical inference relies on *stationarity assumptions*—the requirement that the statistical properties of the random field do not change across the spatial domain. Three levels of stationarity are commonly distinguished, each progressively weaker:

**Strict stationarity** requires that the full joint probability distribution of $\lbrace Z(\mathbf{x}_1), \ldots, Z(\mathbf{x}_n) \rbrace$ is invariant under spatial translation: shifting all locations by the same vector $\mathbf{h}$ does not change the distribution. This is almost never satisfied by geological data—a channel belt has different statistical properties than its floodplain margin.

**Second-order (weak) stationarity** requires only that the mean $E[Z(\mathbf{x})] = \mu$ is constant across the domain and that the covariance $C(\mathbf{h}) = \textrm{Cov}(Z(\mathbf{x}), Z(\mathbf{x} + \mathbf{h}))$ depends only on the separation vector $\mathbf{h}$, not on the absolute location $\mathbf{x}$. This is the standard assumption underlying variogram-based analysis.

**Intrinsic stationarity** requires only that the *increments* $Z(\mathbf{x} + \mathbf{h}) - Z(\mathbf{x})$ have constant mean (zero, for unbiased increments) and that their variance depends only on $\mathbf{h}$. This is the weakest assumption that supports variogram estimation and is the formal requirement for the variogram to be well-defined (Chilès & Delfiner, 2012).

**Why stationarity matters for the QCF.** The stationarity assumption is simultaneously the power and the Achilles' heel of the classical pathway. Under stationarity, the variogram provides a complete second-order characterization of spatial structure from a single realization—enabling feature extraction from individual geological images. Without stationarity, the variogram is at best a local average of a non-stationary structure, and at worst a misleading summary that conflates distinct spatial regimes.

Geological data routinely violates stationarity. A fluvial depositional system contains channel belts, levees, crevasse splays, and floodplain fines—each with different statistical properties. The boundary between a channel and its floodplain is a non-stationary transition. Stratigraphic layering introduces vertical non-stationarity. The QCF handles this through domain-specific preprocessing (computing variograms within geologically homogeneous windows) and through the multi-pathway architecture itself: when stationarity violations cause the classical pathway to produce misleading features, the topological and learned pathways—which make no stationarity assumption—provide independent characterizations that the fusion layer can use to detect and compensate for the classical pathway's failure.

### 4.3 The Variogram: Measuring Spatial Correlation

The variogram is the central tool of geostatistics—a function that quantifies how spatial correlation decays with distance. The *experimental variogram* at lag $\mathbf{h}$ is estimated from data as:

$$\hat{\gamma}(\mathbf{h}) = \frac{1}{2 \lvert N(\mathbf{h}) \rvert} \sum_{(i,j) \in N(\mathbf{h})} \left[ Z(\mathbf{x}_i) - Z(\mathbf{x}_j) \right]^2$$

where $N(\mathbf{h})$ is the set of all data pairs separated by approximately $\mathbf{h}$ and $\lvert N(\mathbf{h}) \rvert$ is its cardinality. The theoretical variogram $\gamma(\mathbf{h})$ is related to the covariance function (under second-order stationarity) by:

$$\gamma(\mathbf{h}) = C(\mathbf{0}) - C(\mathbf{h})$$

where $C(\mathbf{0}) = \textrm{Var}(Z(\mathbf{x}))$ is the *sill* (total variance) and $C(\mathbf{h})$ is the covariance at lag $\mathbf{h}$.

Three parameters characterize the variogram's behavior and constitute the primary classical features extracted by Pipeline A:

| Parameter | Symbol | Interpretation | Geological Meaning |
|---|---|---|---|
| **Nugget** | $c_0$ | Discontinuity at the origin: $\gamma(0^+)$ | Measurement error + micro-scale variability below sampling resolution |
| **Sill** | $c_0 + c_1$ | Asymptotic variance as $\lVert \mathbf{h} \rVert \to \infty$ | Total variability of the regionalized variable |
| **Range** | $a$ | Distance at which $\gamma$ reaches the sill | Characteristic spatial correlation length — the "reach" of spatial dependence |

**Common variogram models.** The experimental variogram must be fitted to a *valid* (conditionally negative definite) model before use in spatial inference. The three most common isotropic models are:

*Spherical model:*
$$\gamma(h) = c_0 + c_1 \left[ \frac{3h}{2a} - \frac{1}{2}\left(\frac{h}{a}\right)^3 \right] \text{ for } h \leq a; \quad \gamma(h) = c_0 + c_1 \text{ for } h > a$$

*Exponential model:*
$$\gamma(h) = c_0 + c_1 \left[ 1 - \exp\left(-\frac{3h}{a}\right) \right]$$

*Gaussian model:*
$$\gamma(h) = c_0 + c_1 \left[ 1 - \exp\left(-\frac{3h^2}{a^2}\right) \right]$$

The choice of model is not arbitrary—it encodes geological assumptions. The spherical model, with its finite range, implies that spatial correlation ceases beyond a definite distance. The exponential model, which reaches its sill asymptotically, implies gradually fading correlation with no sharp cutoff. The Gaussian model, with its parabolic behavior near the origin, implies extreme spatial smoothness—appropriate for slowly varying properties but inappropriate for geological boundaries.

**Directional variograms and anisotropy.** Geological systems are inherently anisotropic: a meandering channel system has different correlation structure along the channel axis than perpendicular to it. Directional variograms $\gamma(\mathbf{h})$ computed along multiple azimuths reveal this anisotropy. The QCF extracts anisotropy ratios—the ratio of directional ranges—as features that encode depositional geometry. A high anisotropy ratio signals elongated structures (channels, dune ridges); a ratio near unity signals isotropic patterns (tidal flats, lacustrine deposits).

### 4.4 Beyond the Variogram: Connectivity and Higher-Order Statistics

The variogram, as a *two-point statistic*, captures only pairwise spatial correlation. This is a fundamental limitation—one that motivates the QCF's multi-pathway architecture. Two critical aspects of geological structure escape variogram characterization.

**Connectivity functions.** The *connectivity function* $\tau(h)$ measures the probability that two points separated by distance $h$ belong to the same connected component of a binary field (e.g., the same continuous channel body). Unlike the variogram, which measures *correlation* (how similar are values at two points?), the connectivity function measures *connection* (can you walk from one point to the other through the same facies?). This distinction is critical for reservoir engineering: two reservoir models with identical variograms can have dramatically different connectivity—one with well-connected channel bodies enabling fluid flow, the other with isolated sand lenses that trap hydrocarbons.

Connectivity is related to *percolation theory* (Stauffer & Aharony, 1994): a random field exhibits a percolation transition at a critical facies proportion $p_c$ above which a connected pathway spans the domain. The percolation threshold depends on the spatial correlation structure in ways that the variogram alone cannot predict. The connectivity function, while richer than the variogram, remains a two-point statistic in a generalized sense—it is computed between pairs of points. True multi-point structure (three or more points simultaneously) requires further tools.

**Multiple-Point Statistics (MPS).** Multiple-point geostatistics (Guardiano & Srivastava, 1993; Strebelle, 2002) extends beyond two-point statistics by considering the joint probability of facies configurations at multiple spatial locations simultaneously. The *multiple-point probability density function* $f(z_1, z_2, \ldots, z_n; \mathbf{x}_1, \mathbf{x}_2, \ldots, \mathbf{x}_n)$ captures spatial patterns—such as channel sinuosity, branching geometry, or bar morphology—that are invisible to two-point statistics. The SNESIM algorithm (Strebelle, 2002) and its successors generate realizations that reproduce these multi-point patterns by scanning a *training image* for local spatial templates.

MPS partially addresses the variogram's topological blindness: multi-point patterns can encode connectivity and branching structure. However, MPS has limitations relevant to the QCF. First, MPS requires a *training image* that exemplifies the desired spatial patterns—introducing a circularity concern when the training image comes from the same generator family used for testing. Second, MPS captures patterns up to a finite template size but may miss global topological features (such as system-wide connectivity) that exceed the template window. Third, MPS has no stability theorem—the relationship between training image perturbation and output perturbation is empirical, not proven.

### 4.5 Fractal Dimensions and Multiscale Characterization

Geological patterns exhibit structure at multiple scales—from pore-scale heterogeneity to basin-scale depositional architecture. *Fractal geometry* (Mandelbrot, 1982) provides tools for characterizing this multiscale structure through power-law scaling relationships.

The *box-counting fractal dimension* $D_B$ of a binary geological image is computed by covering the image with boxes of side length $\epsilon$ and counting the number $N(\epsilon)$ that contain at least one channel pixel:

$$D_B = \lim_{\epsilon \to 0} \frac{\log N(\epsilon)}{\log(1/\epsilon)}$$

For a perfectly one-dimensional channel, $D_B \approx 1$; for a space-filling network, $D_B \approx 2$. Natural channel networks typically have $D_B \in [1.1, 1.8]$, with braided systems showing higher values (more space-filling due to multiple threads) than meandering systems (less space-filling due to a single sinuous thread).

*Lacunarity* (Plotnick et al., 1996) complements the fractal dimension by measuring the *texture* of the spatial pattern at each scale—specifically, the variability in the distribution of gap sizes. Two patterns with the same fractal dimension can have very different lacunarities: a clustered pattern has high lacunarity (large variation in gap sizes) while a regular pattern has low lacunarity. In geological terms, high lacunarity may indicate isolated channel bodies separated by variable-width floodplain, while low lacunarity may indicate a more uniform spatial distribution of channel material.

The variogram power-law slope $\beta_{\textrm{iso}}$ is related to the fractal dimension: for intrinsically stationary fields, $\beta = 2(2 - D_B)$ in two dimensions (Turcotte, 1997). This relationship connects variogram analysis (§4.3) to multiscale characterization and provides an additional classical feature for the QCF's Pipeline A.

### 4.6 Kriging: Optimal Spatial Prediction Under Stationarity

*Kriging* is the minimum-variance linear unbiased estimator for spatial prediction under second-order stationarity—the "gold standard" for spatial interpolation in geostatistics (Journel & Huijbregts, 1978). Given observations $Z(\mathbf{x}_1), \ldots, Z(\mathbf{x}_n)$ at known locations, the kriging estimate at an unobserved location $\mathbf{x}_0$ is:

$$\hat{Z}(\mathbf{x}_0) = \sum_{i=1}^{n} \lambda_i Z(\mathbf{x}_i)$$

where the weights $\lambda_i$ are determined by solving the kriging system:

$$\sum_{j=1}^{n} \lambda_j \gamma(\mathbf{x}_i - \mathbf{x}_j) + \mu = \gamma(\mathbf{x}_i - \mathbf{x}_0), \quad i = 1, \ldots, n$$

$$\sum_{i=1}^{n} \lambda_i = 1$$

with Lagrange multiplier $\mu$ enforcing unbiasedness. The kriging variance—the expected squared error—is:

$$\sigma^2_K(\mathbf{x}_0) = \sum_{i=1}^{n} \lambda_i \gamma(\mathbf{x}_i - \mathbf{x}_0) + \mu$$

**Why kriging matters for the QCF.** Kriging is relevant to the retrieval architecture in two ways. First, the kriging variance provides a *model-based* uncertainty estimate for spatial prediction from sparse data—a natural comparison point for the Neural Process query encoder's learned uncertainty (§9.2). The NP's advantage is that it learns to perform inference without assuming stationarity or specifying a variogram model; its disadvantage is that it provides no theoretical optimality guarantee. Second, the kriging framework makes explicit the *information content* of different observation configurations: widely separated wells reduce kriging variance more than clustered wells, providing an information-theoretic rationale for observation placement that the NP should learn to replicate.

### 4.7 Epistemic Status and Limitations

The classical geostatistical pathway has a distinctive epistemic profile that differs fundamentally from both the topological and learned pathways:

| Property | Classical (Geostatistics) | Topological (PH) | Learned (DINOv2) |
|---|---|---|---|
| **Theoretical foundation** | Random field theory (Matheron, 1963) | Algebraic topology | Representation learning |
| **Invariance guarantee** | None — empirical stability only | Stability theorem (mathematical proof) | None — distribution-dependent |
| **Stationarity requirement** | Yes (second-order or intrinsic) | No | No |
| **Interpretability** | High — direct physical meaning | Moderate — topological invariants | Low — opaque features |
| **Sensitivity to topology** | None — variograms are topologically blind | Full — designed for topology | Partial — captures some topology implicitly |
| **Operational maturity** | Highest — decades of industry use | Moderate — active research | Low — recent (2023+) |

The classical pathway's most critical limitation for the QCF is its **topological blindness**: the variogram cannot distinguish braided from meandering channel architectures when spatial correlation lengths are matched (§6.6). This is not a failure of implementation but a mathematical property of two-point statistics—they are provably insensitive to connectivity topology.

However, the classical pathway provides information that neither PH nor DINOv2 captures directly. The variogram range quantifies *how far* spatial correlation extends—a continuous measure of depositional scale that PH's discrete topological invariants do not encode. Anisotropy ratios characterize *directional* structure that isotropic PH computations ignore (unless directional filtrations are used). Fractal dimensions quantify *multiscale roughness* in a way that persistence diagrams do not directly capture. These complementary strengths are why the QCF uses all three pathways rather than relying on PH alone.

The classical pathway also lacks any analog to the stability theorem. The empirical observation that "small changes to geological images produce small changes to variograms" is well-supported in practice but has no formal proof. This places classical features at a lower tier in the confidence hierarchy (§14.6): they enter Pipeline A's index as empirically validated but not mathematically guaranteed descriptors—Tier 3 as individual features, though the subset corroborated across all three pathways via the SLIDE decomposition (§14.6) may be promoted to Tier 2.

---

## 5. Mathematical Foundations of Self-Supervised Visual Representations

### 5.1 From Hand-Crafted to Learned Features

The QCF's learned pathway represents a fundamentally different approach to geological pattern recognition than either persistent homology or classical geostatistics. Where PH extracts mathematically defined topological invariants and geostatistics computes theoretically grounded spatial statistics, the learned pathway allows a neural network to *discover* relevant features from data—features that are optimized for discriminative power rather than mathematical elegance.

The evolution from hand-crafted to learned features parallels a broader shift in computer vision. Classical descriptors like SIFT (Lowe, 2004), HOG (Dalal & Triggs, 2005), and Local Binary Patterns (Ojala, Pietikäinen, & Mäenpää, 2002) compute fixed mathematical transformations of image patches—gradient histograms, texture patterns, corner responses. These features are interpretable and well-understood but limited: they capture only the patterns their designers anticipated. Convolutional neural networks (LeCun et al., 1998; Krizhevsky, Sutskever, & Hinton, 2012) demonstrated that *learned* features—optimized end-to-end for a downstream task—dramatically outperform hand-crafted alternatives across virtually all visual recognition benchmarks.

For geological image analysis, this distinction is especially significant. Hand-crafted geological features (variograms, fractal dimensions, connectivity functions) capture well-understood spatial properties but may miss the gestalt—the holistic pattern that an experienced geoscientist recognizes intuitively when viewing a depositional image. The learned pathway aims to capture this gestalt computationally.

### 5.2 The Vision Transformer Architecture

The QCF employs DINOv2-ViT-B/14 (Oquab et al., 2023) as its learned feature extractor. Understanding what this model computes—and what its features represent—requires unpacking the Vision Transformer (ViT) architecture (Dosovitskiy et al., 2020).

**Patch embedding.** A ViT does not process an image as a grid of pixels. Instead, it divides the input image into a regular grid of non-overlapping square patches. For ViT-B/14, each patch is $14 \times 14$ pixels; a $224 \times 224$ geological image (the standard ViT input size) yields $16 \times 16 = 256$ patches. Each patch is flattened into a vector and linearly projected to a $D$-dimensional embedding ($D = 768$ for ViT-B):

$$\mathbf{z}_i^{(0)} = \mathbf{W}_p \cdot \textrm{flatten}(\textrm{patch}_i) + \mathbf{e}_{\textrm{pos}}(i), \quad i = 1, \ldots, N$$

where $\mathbf{W}_p \in \mathbb{R}^{D \times (P^2 \cdot C)}$ is the patch projection matrix, $P = 14$ is the patch size, $C$ is the number of input channels, and $\mathbf{e}_{\textrm{pos}}(i)$ is a learned positional embedding encoding the patch's spatial location within the image. A special learnable [CLS] token $\mathbf{z}_{\textrm{cls}}^{(0)}$ is prepended to the sequence.

**Self-attention.** The core operation of the transformer is *multi-head self-attention* (Vaswani et al., 2017), which allows each patch to attend to every other patch—capturing long-range spatial relationships that convolutional architectures access only through deep stacking. For each attention head $h$, the input embeddings are projected into queries, keys, and values:

$$\mathbf{Q}_h = \mathbf{Z} \mathbf{W}_h^Q, \quad \mathbf{K}_h = \mathbf{Z} \mathbf{W}_h^K, \quad \mathbf{V}_h = \mathbf{Z} \mathbf{W}_h^V$$

Attention weights are computed as:

$$\textrm{Attention}_h(\mathbf{Z}) = \textrm{softmax}\left(\frac{\mathbf{Q}_h \mathbf{K}_h^\top}{\sqrt{d_k}}\right) \mathbf{V}_h$$

where $d_k = D / H$ is the per-head dimension and $H = 12$ is the number of attention heads for ViT-B. The outputs of all heads are concatenated and projected:

$$\textrm{MSA}(\mathbf{Z}) = \textrm{Concat}(\textrm{Attention}_1, \ldots, \textrm{Attention}_H) \mathbf{W}^O$$

Each transformer block applies multi-head self-attention followed by a feed-forward network with residual connections and layer normalization:

$$\mathbf{Z}' = \textrm{LN}(\mathbf{Z} + \textrm{MSA}(\mathbf{Z}))$$

$$\mathbf{Z}^{(\ell+1)} = \textrm{LN}(\mathbf{Z}' + \textrm{FFN}(\mathbf{Z}'))$$

ViT-B stacks $L = 12$ such blocks. The [CLS] token's final representation $\mathbf{z}_{\textrm{cls}}^{(L)} \in \mathbb{R}^{768}$ aggregates global information across all patches via self-attention, serving as a holistic image-level feature vector—the output that enters the QCF's fusion layer.

**Why this matters for geological images.** The self-attention mechanism has a specific advantage for geological pattern recognition: it can detect long-range spatial relationships—such as the downstream correlation between point bars in a meandering system, or the network-wide connectivity of a braided system—without requiring deep convolutional stacks. Each attention head can learn to attend to different types of spatial relationships, and the multi-head structure allows the model to simultaneously capture local texture, medium-scale geometry, and global pattern organization.

### 5.3 Self-Supervised Pretraining: DINO and DINOv2

DINOv2's power comes not from the ViT architecture alone but from its pretraining strategy—*self-supervised learning without labels* on a curated dataset of 142 million images (LVD-142M).

**The self-distillation framework.** DINO (Caron et al., 2021) and its successor DINOv2 (Oquab et al., 2023) employ a teacher-student self-distillation paradigm. Two networks share the same architecture: the *student* receives a locally cropped view of an image, and the *teacher* receives a global view. The training objective forces the student's output distribution to match the teacher's:

$$\mathcal{L}_{\textrm{DINO}} = - \sum_{x \in \lbrace \textrm{global views} \rbrace} \sum_{x' \in \lbrace \textrm{local views} \rbrace} H(P_t(x), P_s(x'))$$

where $H$ is the cross-entropy loss, $P_t$ is the teacher's output probability distribution (computed with a sharpened softmax and centering), and $P_s$ is the student's distribution. The teacher's weights are updated as an exponential moving average of the student's weights—not through gradient descent—creating a slowly evolving target that stabilizes training.

This training paradigm has a remarkable emergent property: the resulting representations are *linearly separable* for semantic categories without any labeled data during training. Oquab et al. (2023) demonstrated that linear probes on frozen DINOv2 features achieve performance competitive with fully supervised methods on ImageNet classification, object detection, and semantic segmentation.

**What DINOv2 learns.** Visualization of DINOv2's attention maps reveals that the model learns to segment objects and discriminate structural patterns purely from self-supervised objectives. Different attention heads attend to different scales and types of structure: some capture fine-grained texture boundaries, others capture large-scale object contours, and others capture spatial relationships between distant image regions. For geological images, this multi-scale attention is potentially powerful: the model can simultaneously attend to channel boundaries (local), meander geometry (medium-scale), and system-wide connectivity patterns (global).

### 5.4 Domain Adaptation: LoRA Fine-Tuning

DINOv2 is pretrained on natural images—photographs of objects, scenes, and activities—not geological data. While its representations demonstrate remarkable cross-domain transferability (the model captures general visual structure that transcends specific image categories), fine-tuning for geological imagery improves performance on domain-specific discrimination tasks.

**Low-Rank Adaptation (LoRA).** Hu et al. (2022) introduced LoRA as a parameter-efficient fine-tuning method. Rather than updating all $\sim$86 million parameters of ViT-B, LoRA freezes the pretrained weights $\mathbf{W}_0$ and adds a low-rank perturbation:

$$\mathbf{W} = \mathbf{W}_0 + \mathbf{B}\mathbf{A}$$

where $\mathbf{A} \in \mathbb{R}^{r \times d_{\textrm{in}}}$ and $\mathbf{B} \in \mathbb{R}^{d_{\textrm{out}} \times r}$ are trainable matrices with rank $r \ll \min(d_{\textrm{in}}, d_{\textrm{out}})$. For the QCF, LoRA is applied to the query and value projection matrices in each attention layer with $r = 8$, adding only $\sim$300K trainable parameters while preserving the pretrained representation's general visual understanding.

**Why LoRA rather than full fine-tuning.** Full fine-tuning risks *catastrophic forgetting*—the pretrained representations, which capture general visual structure useful for geological pattern recognition, may be overwritten by domain-specific features that overfit to the training distribution. LoRA's low-rank constraint acts as an implicit regularizer: the fine-tuned model can only deviate from the pretrained representation along a low-dimensional subspace, preserving the general visual features while learning domain-specific adaptations.

This is epistemically important for the QCF. The DINOv2 pathway's value lies partly in its *independence* from geological domain knowledge—it captures visual patterns that a human geoscientist might recognize intuitively but that neither variograms nor PH encode. Aggressive fine-tuning risks making the learned pathway less independent from the other two, weakening the convergence argument (§6.3).

### 5.5 Representation Geometry and Interpretability

Understanding *what* DINOv2 representations encode is essential for the QCF's evidence hierarchy, which requires knowing the epistemic status of each pathway's features.

**The manifold hypothesis.** High-dimensional neural representations typically lie on or near low-dimensional manifolds within the ambient 768-dimensional space (Bengio, Courville, & Vincent, 2013). For geological images, this means that the set of all DINOv2 representations of, say, meandering channel systems traces out a low-dimensional surface in $\mathbb{R}^{768}$—a surface whose geometry encodes the continuous variation in sinuosity, channel width, point bar development, and other parameters that distinguish meandering configurations from one another.

**Linear probing.** A *linear probe* (Alain & Bengio, 2016) trains a linear classifier $f(\mathbf{z}) = \mathbf{W}\mathbf{z} + \mathbf{b}$ on frozen DINOv2 representations to predict target labels (depositional environment, channel architecture, generator identity). High linear probe accuracy indicates that the relevant information is *linearly accessible* in the representation—a strong form of structure that downstream components (the fusion layer, the embedding projection) can easily exploit. Oquab et al. (2023) showed that DINOv2 representations are remarkably linearly separable, suggesting that the representation geometry naturally organizes images by semantic category.

**Attention map analysis.** For geological images specifically, the spatial attention maps $\alpha_{ij}$ (the softmax weights in the self-attention computation) reveal which image regions the model considers informative. Preliminary analysis suggests that DINOv2 attention maps on geological images highlight channel boundaries, confluence points, and structural discontinuities—features that are geologically meaningful and partially overlap with the structural features that PH captures. This overlap is precisely what the SLIDE decomposition (§14.6) is designed to quantify: how much of DINOv2's representation is shared with PH (joint component), unique to DINOv2 (individual component), or partially shared with one other pathway (partial component)?

### 5.6 The Scene Gist Connection

The DINOv2 [CLS] token provides what cognitive science calls *scene gist*—the rapid, holistic perception of a scene's category and layout that occurs within the first 100–200 milliseconds of visual exposure, before conscious analysis of individual features (Oliva & Torralba, 2006). Experimental evidence shows that human observers can categorize natural scenes (forest, beach, city) from extremely brief exposures (as short as 20ms), suggesting that scene gist is computed from global image statistics—spatial frequency content, texture gradients, and layout geometry—rather than from identified objects.

The analogy to geological image analysis is direct. An experienced geoscientist, shown a depositional image for a fraction of a second, can typically identify the general environment (fluvial, aeolian, estuarine) before consciously analyzing individual features. This gestalt recognition—rapid, holistic, and difficult to articulate—is precisely what the learned pathway aims to capture computationally. The DINOv2 [CLS] token, which aggregates global information via self-attention across all patches, provides an architectural analog to this cognitive process.

### 5.7 Epistemic Status and Limitations

The learned pathway occupies a distinctive position in the QCF's epistemic framework—high discriminative power but low interpretability and no formal guarantees:

**No stability theorem.** Unlike PH, DINOv2 features have no proven invariance under input perturbation. Empirically, ViT representations are more robust to common corruptions than CNNs (Bhojanapalli et al., 2021), but this robustness is observed, not proven. A small, adversarially crafted perturbation could produce a large change in the 768-dimensional representation—a vulnerability that the adversarial tests of §10.4 are designed to probe.

**Distribution dependence.** DINOv2 is pretrained on 142 million natural images. Its representations encode the statistical structure of this training distribution. Geological images—binary facies maps, seismic sections, core photographs—may lie outside the distribution the model has learned to represent well. LoRA fine-tuning partially addresses this, but the resulting features remain dependent on the fine-tuning data distribution. If the fine-tuning data comes from a single generator, the learned features may encode generator-specific artifacts rather than geological structure—a risk that the LOGO protocol (§10.3) is designed to detect.

**Opacity.** The 768-dimensional representation is not directly interpretable in geological terms. We cannot point to a specific dimension and say "this encodes sinuosity" or "this captures net-to-gross ratio." The directed probing methods of §14.6 (linear probes and T-CAV) provide partial interpretability by identifying directions in DINOv2 space that correlate with known geological or topological concepts, but the representation remains fundamentally opaque compared to variogram parameters or Betti numbers.

**Entanglement.** DINOv2 features may encode multiple geological properties in entangled ways—a single dimension might capture a mixture of texture, scale, connectivity, and generator artifacts. The DeCUR decomposition (§14.7) addresses this by separating DINOv2's representation into PH-aligned and PH-residual components, but full disentanglement of geological content from artifacts remains an open problem.

**Identifiability as a complementary Level 1 concept.** The four limitations above—particularly entanglement and distribution dependence—motivate a distinct line of theoretical guarantee that the stability theorem alone cannot provide: *identifiability theorems*. In brief, identifiability theorems (Khemakhem et al., 2020; Kong et al., 2025) bound the correspondence between learned latent factors and true generative parameters (up to well-defined invertible equivalence classes), given access to auxiliary-variable supervision—precisely what the principle-based generator provides through paired image-parameter data $(I, \theta)$. These guarantees are *distinct from* but *complementary to* the stability theorem: stability bounds how features respond to input perturbation, while identifiability bounds whether features recover true generative structure rather than generator-specific artifacts. Section 5.8 develops the framework formally; the epistemic upgrade it provides is then integrated into the evidence hierarchy (§8) and the confidence hierarchy (§14.6), where supervised-identifiable factors join PH at the Level 1 / Tier 1 anchor, while DINOv2's unsupervised representations remain at the lower tiers characterized below.

These limitations are why DINOv2 features enter the confidence hierarchy at Tier 3 or 4 (§14.6)—empirically powerful but lacking the theoretical guarantees of PH (Tier 1) or the cross-pathway corroboration of the joint component (Tier 2). The QCF's architecture treats this epistemic asymmetry as a feature, not a bug: DINOv2's unique contribution—the holistic pattern recognition that neither PH nor geostatistics provides—is most valuable precisely because it is independent of the other pathways' assumptions and methods.

### 5.8 Supervised Identifiable Learning with Auxiliary Generator Parameters

The limitations of §5.7 admit two responses: one can hope they are benign in practice (an empirical gamble), or one can seek theoretical guarantees that bound specific failure modes. This subsection pursues the second response, introducing a supervised variant of the learned pathway whose features carry a distinct form of Level 1 mathematical guarantee—*identifiability*—that complements the stability theorem of §3.6 and enters the evidence hierarchy of §8 alongside it.

**The impossibility result that motivates supervision.** Locatello et al. (2019) proved that purely unsupervised disentanglement of generative factors is impossible without inductive biases: for any model recovering the true factors there exists an observationally equivalent model—related by an entangling invertible transformation—with identical likelihood. Identifiability guarantees therefore require either structural assumptions on the data-generating process or auxiliary supervision beyond the observed images. The QCF's principle-based generator (§2) naturally provides the latter: each synthetic image $I$ is paired with its generating parameter vector $\theta$, containing Leopold-Wolman sinuosity and channel width, Parker stability number, Werner dune parameters, and the other quantities documented in §2.4–2.6.

**iVAE: auxiliary-variable identifiability.** Khemakhem, Kingma, Monti, and Hyvärinen (2020) established the foundational identifiability result for variational autoencoders. An *identifiable variational autoencoder* (iVAE) assumes a generative process

$$x = f(z) + \varepsilon, \qquad p(z \mid u) \in \textrm{Exp}\bigl(\eta(u)\bigr),$$

where $z \in \mathbb{R}^n$ is the latent factor vector, $u$ is an auxiliary variable (environment label, class index, or continuous covariate), and the conditional prior $p(z \mid u)$ belongs to an exponential family with auxiliary-dependent natural parameter $\eta(u)$. Under smoothness and non-degeneracy conditions—specifically, that $2n + 1$ distinct values of $u$ produce linearly independent $\eta(u)$—any two models matching the observed joint distribution of $(x, u)$ must relate their latent variables by an affine transformation $\hat{z} = A z + b$ for some invertible $A$ and translation $b$. This guarantee is weaker than full element-wise disentanglement but strictly stronger than anything unsupervised methods can provide: the learned latent space contains the true factors up to a known, well-characterized ambiguity class.

**Kong et al. 2025: sparse mixing and auxiliary-variation synergy.** Kong, Xie, Jiang, et al. (2025, arXiv:2503.00639) strengthen the iVAE result by relaxing the exponential-family assumption and exploiting sparse structure in the mixing function $f$. Under their assumptions A1–A5—smooth positive density of $\theta$ conditional on generator identity (A1); conditional independence of $\theta$ components given the generator (A2); sufficient changes across domains (A3); sparse mixing structure constraining which latent components affect which image regions (A4); and a fully-connected fallback (A5)—two theorems follow:

- **Theorem 1 (subspace identifiability).** For any subset $z_a \subseteq z$ whose parents in the sparse mixing graph lie within the observed support, $z_a$ is identifiable up to an invertible function of $z_a$ alone, using only $2 \lvert z_a \rvert + 1$ distinct auxiliary values rather than the $2n + 1$ that iVAE requires over the full latent vector.
- **Theorem 2 (component-wise identifiability).** Under an additional second-order derivative condition on the mixing Jacobian, individual components $z_i$ are identifiable up to element-wise invertible transformation—the strongest guarantee currently available in the identifiable causal representation learning literature.

**Why this fits the principle-based generator.** Four features of the QCF's experimental apparatus align with the Kong et al. assumption structure:

1. *Paired $(I, \theta)$ data satisfies A2 by construction.* The generator samples each parameter independently before rendering its image, so the conditional independence structure that Theorem 2 requires holds without further assumption.
2. *Empirical formulas encode sparse mixing (A4).* The Leopold-Wolman wavelength-width coupling (§2.4) applies to fluvial meander geometry without affecting aeolian dune texture; the Parker stability criterion $W / d > 50$ selects channel patterns without dictating fine-scale variogram structure; Werner dune parameters affect only aeolian images. These physical separations are exactly the sparse decoder-Jacobian pattern A4 describes.
3. *Fewer domains suffice.* For a parameter space of $\sim 15$–$30$ quantities across three environments, the reduction from $2n + 1$ to $2 \lvert z_a \rvert + 1$ is the difference between practical and impractical identification.
4. *Corollary 1 of Kong et al. recovers iVAE* when A4 degenerates to fully-connected mixing. If empirical verification of sparse mixing fails on specific generators, the framework reduces to the published iVAE guarantees at the cost of additional auxiliary domains—no architectural change required.

**The CG-VAE training objective.** The supervised variant of the learned pathway—hereafter CG-VAE, the *conditional-generator* variant of the Kong et al. framework adapted to the principle-based generator—trains an encoder $q_\phi(z \mid x, u)$ and decoder $p_\psi(x \mid z)$ against

$$\mathcal{L}_{\textrm{CG-VAE}} \;=\; \mathcal{L}_{r} \;+\; \alpha \, \mathcal{L}_{s} \;-\; \beta \, \mathcal{L}_{\textrm{KL}},$$

where $\mathcal{L}_{r}$ is the image reconstruction loss, $\mathcal{L}_{s} = \sum_{i, k} \lvert \partial \hat{x}_i / \partial \hat{z}_k \rvert$ is a sparsity penalty on the decoder Jacobian that promotes assumption A4 directly in the objective, and $\mathcal{L}_{\textrm{KL}}$ is the evidence-lower-bound regularizer between $q_\phi(z \mid x, u)$ and the auxiliary-conditioned prior $p(z \mid u)$. The auxiliary encoding $u$ admits three principled forms—categorical generator identity, continuous parameter vector, or hierarchical environment-substyle-parameters nesting—with trade-offs in assumption satisfaction that §6.5 discusses. Identifiability quality is evaluated against the ground-truth $\theta$ via Mean Correlation Coefficient (MCC), Kong et al.'s primary metric.

**What CG-VAE upgrades, and what it does not replace.** CG-VAE does not displace DINOv2 in the learned pathway; the two serve distinct epistemic roles. DINOv2 provides unsupervised, gestalt-level pattern recognition without generator-specific bias—its value is precisely its *independence* from the parameterization, which anchors the cross-pathway convergence argument (§6.3). CG-VAE provides theorem-backed identifiability for factors that align with the generator's parameterization—its value is the Level 1 guarantee absent from DINOv2. Section 6.5 positions these as complementary learned-pathway components; §14.6 then separates CG-VAE-aligned factors (which join PH at Tier 1 of the confidence hierarchy) from DINOv2 residuals (which remain at Tier 3–4 as characterized in §5.7).

**Peer-review status and fallback.** Kong et al. (2025) is an arXiv preprint (2503.00639) as of April 2026; its peer-review trajectory remains to be established. The dissertation's integration is robust to this uncertainty: if Theorems 1–2 survive peer review, the CG-VAE guarantees hold in their sharper form; if gaps emerge, Corollary 1 provides automatic fallback to Khemakhem et al.'s published iVAE result, with the identifiability claim downgraded from "$2 \lvert z_a \rvert + 1$ auxiliary values suffice for subspace-identifiable $z_a$" to "$2 n + 1$ values suffice for affine-identifiable $z$"—still a Level 1 guarantee, over a stricter assumption set.

---

## 6. Application to the Qualia Convergence Framework

### 6.1 The Research Problem: What Is the Essence of a Geological Image?

The Qualia Convergence Framework (QCF) addresses a fundamental challenge in subsurface reservoir characterization: given sparse observations (well logs, partial seismic surveys, limited outcrop data), how does a geoscientist retrieve *depositional analogs*—reference geological models that share the essential structural properties of the target reservoir?

The framework was motivated by a colleague's incisive critique:

> "Patterns based on statistical coherence will never solve the essence problem."

This challenge articulates a tension that has haunted quantitative geology: variogram-matching and facies-proportion-matching retrieve statistically similar images that may be structurally (topologically) dissimilar. Two images can have identical variograms, identical facies proportions, identical fractal dimensions—and yet be fundamentally different geological systems. One might be a single sinuous meandering channel; the other might be a complex braided network. The statistics match; the geology doesn't. This challenge connects directly to the two-pipeline architecture introduced in Section 1: Pipeline A must organize analogs by structural properties that transcend statistical summaries, and Pipeline B must infer those same properties from sparse observations—a task that is impossible if "essence" is reducible to two-point statistics.

The QCF addresses this through an analog retrieval system. A database of complete depositional patterns—full images generated by process-based simulators with known parameters—is organized in a hyperbolic embedding space. A geoscientist's query consists of *sparse observations*: a handful of well logs, a partial seismic survey, scattered outcrop measurements. A Neural Process encoder (Garnelo et al., 2018) maps these sparse inputs to a distribution $(\mu, \sigma)$ in the embedding space—not a point estimate but a calibrated uncertainty region. Retrieval via $k$-nearest neighbors returns similar analogs with uncertainty that degrades gracefully: more observations tighten the distribution; fewer yield appropriately wider bounds.

### 6.2 Operationalizing Essence

The QCF responds to this challenge with *pragmatic operationalism* (following Peirce, James, Dewey): rather than debating whether "essence" exists metaphysically, we define it by what our tests measure and validate by consequences.

> **Operational Definition**: "Essence" is the invariant structure that remains stable under:
> 1. Multiple independent representation pathways (classical, learned, topological)
> 2. Multiple observation modalities (well logs, seismic, outcrop, images)
> 3. Multiple generative processes (different simulators, real data)

This definition is *epistemic, not metaphysical*. We make no claim about Platonic forms or Aristotelian essences. We claim only that if a structure satisfies these invariance criteria *and* enables prediction of held-out properties, it has earned the designation "essence" for practical purposes.

The use of "Qualia" in the framework name is metaphorical—it signals our ambition to capture something beyond surface statistics, the gestalt quality that experts recognize, while making no claim to access subjective phenomenological experience (Tye, 2021).

### 6.3 Three-Pathway Architecture

The three-pathway feature extraction architecture forms the core of Pipeline A's essence encoding mechanism, transforming heterogeneous analog data into the structural representations that populate the geologic index. The QCF employs three independent feature-extraction pathways, each representing a distinct epistemological perspective:

**The Classical Pathway** computes traditional geostatistical descriptors—variograms, fractal dimensions, connectivity functions—yielding approximately 50 dimensions of features that encode spatial correlation structure. This captures *aparā vidyā* (lower, empirical knowledge) in the framework's Vedantic epistemological framing.

**The Learned Pathway** uses DINOv2-ViT-B/14, a self-supervised vision transformer, with LoRA fine-tuning on geological imagery to extract 768-dimensional feature vectors capturing high-level visual semantics. This captures the holistic "gestalt" that an experienced geoscientist perceives when viewing an image.

**The Topological Pathway** computes persistent homology in dimensions $H_0$ and $H_1$ via Giotto-TDA (Tauzin et al., 2021), producing approximately 20–50 dimensions of topological features. This captures structural connectivity—the skeleton of the geological pattern.

Importantly, the topological pathway operates specifically on *binary facies images* (channel = 1, floodplain = 0). Different observation modalities receive specialized encoders: well logs are processed by 1D CNNs over depth sequences, seismic amplitudes by 2D CNNs over spatial patches, and outcrop photographs by the DINOv2 backbone. Persistent homology serves as the topological encoder for *gridded image data*—a complementary, not universal, role within the multi-modal architecture.

After independent feature extraction, the three pathway representations are projected to a common dimensionality and fused via cross-attention, with Perceiver IO (Jaegle et al., 2021) planned as an extension for handling variable-length multi-modal inputs. Fusion is governed by a convergence regularization loss:

$$L_{\text{conv}} = \sum_{i \lt j} \lVert f_i(x) - f_j(x) \rVert^2$$

This loss encourages the three pathways to agree. When they converge—when classical statistics, learned semantics, and topological structure all indicate the same depositional environment—the representation is robust and uncertainty is low. When they disagree, the system produces higher uncertainty, signaling that the available evidence is ambiguous. Agreement across independent epistemic perspectives constitutes stronger evidence than any single pathway alone, instantiating the framework's Sākṣī (independent witness) validation philosophy.

The topological pathway's unique contribution within this architecture is *structural discrimination under statistical degeneracy*: when two images share identical variograms and similar learned features but differ in connectivity topology, only the topological pathway registers the difference. This complementarity—not redundancy—is the architectural rationale for including PH alongside powerful classical and learned encoders.

The fused representation is projected into a hyperbolic embedding space (Poincaré ball model) where hierarchical organization of depositional environments is naturally encoded—general categories near the origin, specific sub-types near the boundary.

### 6.4 Classical Pathway: Variographic Indexing and Its Structural Boundary

The classical pathway transforms each geological analog into an approximately 50-dimensional feature vector encoding its spatial correlation structure, directional fabric, connectivity, and multiscale roughness. The mathematical foundations are established in Section 4; here we describe how those foundations are applied within the QCF's retrieval architecture and where the pathway reaches its structural limits.

**Feature composition.** The classical feature vector comprises four families of descriptors, each computed from the binary facies map or its continuous geostatistical properties:

| Feature Family | Dimensions | What It Encodes |
|---|---|---|
| Directional variogram parameters | ~12 | Nugget ($c_0$), sill ($c_0 + c_1$), and range ($a$) estimated from four directional variograms (0°, 45°, 90°, 135°) |
| Anisotropy descriptors | ~4 | Range ratio (max/min directional range), orientation of principal anisotropy axis, ellipse eccentricity |
| Connectivity and percolation | ~8 | Connectivity function parameters at multiple lag distances, estimated percolation threshold, connected component size distribution moments |
| Multiscale texture | ~6–10 | Box-counting fractal dimension $D_B$, lacunarity at 3–5 scales, variogram power-law slope $\beta_{\textrm{iso}}$ |
| Facies proportions | ~2–4 | Net-to-gross ratio, facies interface density, mean channel-body thickness |

The exact dimensionality depends on implementation choices—the number of directional azimuths (4 in the minimal configuration above, up to 8 or more for finer angular resolution), the number of lag distances at which connectivity is evaluated, and the number of scales for lacunarity. The minimal configuration yields ~32 dimensions; a full configuration with 8 azimuths and additional connectivity lags reaches ~50. All references to "approximately 50 dimensions" elsewhere in this document reflect the full configuration.

These descriptors are computed deterministically from each analog image—no learning is involved, no training data required. This computational transparency is the classical pathway's primary epistemic advantage: every feature has a direct physical interpretation. The variogram range tells you the spatial correlation length. The anisotropy ratio tells you whether the depositional pattern is elongated or isotropic. The fractal dimension tells you the space-filling complexity. A geoscientist can examine any classical feature value and understand what it means for the geology.

**Role in Pipeline A.** Classical features enter the geologic index as mid-tier descriptors (Tier 3 as individual features in the confidence hierarchy of §14.6; those corroborated across all three pathways are promoted to Tier 2 via SLIDE decomposition). They provide information that neither PH nor DINOv2 captures directly: the variogram range quantifies *how far* spatial correlation extends—a continuous measure of depositional scale that PH's discrete topological invariants do not encode. Anisotropy ratios characterize *directional* structure that isotropic PH computations ignore. Fractal dimensions quantify *multiscale roughness* in a way that persistence diagrams capture only indirectly through the distribution of feature lifetimes.

In the embedding space, classical features contribute to positioning analogs along dimensions that PH cannot distinguish. Two geological images might share identical $H_1$ persistence diagrams (same number of loops, same persistence values) while differing substantially in variogram range—one is a large-scale braided system with correlation lengths of hundreds of meters, the other a small-scale braided system with correlation lengths of tens of meters. Classical features discriminate these cases, providing scale information that refines the topological classification.

**Connection to Pipeline B.** The classical pathway provides a natural bridge to the sparse-data regime of Pipeline B. Kriging (§4.6), the minimum-variance linear unbiased estimator under stationarity, offers a well-understood baseline for spatial prediction from sparse observations. When a geoscientist provides well log data at a handful of locations, the variogram estimated from those sparse observations—though necessarily less reliable than a variogram computed from a complete image—provides a first-order characterization of the depositional scale and anisotropy. The Neural Process query encoder (§9.2) should reproduce kriging's performance as a lower bound: when stationarity holds and observations are sufficient, the NP's uncertainty estimates should be at least as good as kriging variance. When stationarity is violated or observations are too sparse for reliable variogram estimation, the NP's learned inference should outperform kriging—this performance crossover is itself a diagnostic for the NP's value-added.

**The structural boundary.** The classical pathway's fundamental limitation is topological blindness: variograms measure spatial correlation but are provably insensitive to connectivity topology (§4.4). This is not a failure of implementation but a mathematical property of two-point statistics. Two images can have identical variograms, identical fractal dimensions, identical connectivity functions computed at individual lag distances—and yet differ fundamentally in channel architecture. A braided system with many interconnected channels and a meandering system with a single sinuous channel can produce matching two-point statistics when their spatial correlation lengths coincide. No refinement of classical features—no additional variogram directions, no higher-order moments of the variogram—can overcome this blindness, because the relevant information (loop topology) is fundamentally higher-order.

This structural boundary is not merely a theoretical concern—it is the empirical motivation for the entire multi-pathway architecture. If classical features alone could reliably distinguish depositional environments, the QCF would not need topological or learned pathways. The variogram-matched pairs experiment (§6.9) is designed precisely to demonstrate this boundary: matched pairs where classical features are identical by construction, forcing discrimination to rely on the other pathways.

### 6.5 Learned Pathway: Scene Gist and Holistic Pattern Encoding

The learned pathway extracts a 768-dimensional feature vector from each geological image using DINOv2-ViT-B/14, a self-supervised vision transformer. The mathematical foundations are established in Section 5; here we describe the pathway's specific role within the QCF and why its epistemic independence from domain-specific assumptions makes it uniquely valuable despite—and because of—its opacity.

**Feature extraction pipeline.** Each analog image (resized to $224 \times 224$ pixels for ViT compatibility, or $256 \times 256$ with padding) is processed through the frozen DINOv2 backbone with LoRA fine-tuning adapters (§5.4). The image is divided into $14 \times 14$-pixel patches, each embedded with positional encoding, and processed through 12 transformer blocks of multi-head self-attention and feed-forward layers. The [CLS] token's final-layer representation—a single 768-dimensional vector aggregating information from all patches via learned attention—serves as the pathway's output feature.

This single vector is the learned pathway's analog to the classical pathway's ~50-dimensional variogram-based descriptor and the topological pathway's 20–50-dimensional persistence features. The dimensionality difference is significant: DINOv2's 768 dimensions encode far richer information than either structured pathway, but this richness comes at the cost of interpretability. Where a variogram parameter has direct physical meaning and a Betti number counts topological features, individual DINOv2 dimensions have no straightforward geological interpretation.

**What the learned features encode.** Despite their opacity, DINOv2 features capture information that is demonstrably relevant to geological classification. Three lines of evidence support this claim.

First, *linear separability*. Oquab et al. (2023) demonstrated that DINOv2 features are linearly separable for semantic categories across diverse visual domains without any fine-tuning. For geological images, this implies that a simple linear classifier applied to frozen DINOv2 features should achieve competitive accuracy for depositional environment classification—a prediction that the linear probe experiments of §12.6 are designed to test.

Second, *attention map alignment*. The spatial attention maps of DINOv2's self-attention layers reveal which image regions the model considers informative. For geological images, preliminary evidence suggests that attention concentrates on channel boundaries, confluence points, and structural transitions—features that are geologically meaningful and partially overlap with what PH captures through topology. The attention map analysis protocol of §12.6 will quantify this alignment systematically.

Third, *the scene gist hypothesis* (§5.6). An experienced geoscientist shown a depositional image for a fraction of a second can typically identify the general environment before consciously analyzing individual features. DINOv2's [CLS] token provides a computational analog to this rapid holistic recognition. The hypothesis predicts that DINOv2 classification accuracy should be highest for broad environment discrimination (fluvial vs. aeolian) and progressively lower for finer distinctions (high-sinuosity vs. low-sinuosity meandering)—a prediction testable through hierarchical linear probing.

**Role in Pipeline A.** Learned features enter the geologic index at Tier 3–4 in the confidence hierarchy (§14.6), reflecting their high discriminative power but low interpretability and absence of formal invariance guarantees. Their unique contribution is capturing the holistic pattern gestalt that neither variograms (which decompose images into pairwise spatial statistics) nor PH (which abstracts to topological invariants) preserves. A DINOv2 representation encodes texture gradients, facies boundary sharpness, spatial frequency content, bar morphology, and other visual properties that experienced geoscientists recognize intuitively but that neither structured pathway explicitly computes.

This complementarity is the architectural rationale for including a learned pathway alongside two mathematically principled ones. The classical pathway fails when topological structure diverges from correlation structure (variogram-matched pairs). The topological pathway fails when geological differences are purely metric (two braided systems with different channel widths but identical loop topology). The learned pathway captures both kinds of information—and more—but with no guarantee that any specific feature is geologically meaningful rather than an artifact of the training distribution. The three pathways' failures are non-overlapping, which is precisely the condition under which multi-pathway convergence is most informative.

**Independence and the LOGO protocol.** The learned pathway's epistemic value depends critically on its *independence* from the other two pathways. If DINOv2 features merely encode a noisy version of variogram parameters or a compressed version of persistence diagrams, the three-pathway architecture gains little from including them. True independent information—visual patterns that neither classical statistics nor topology captures—is what makes the convergence argument epistemically powerful.

Independence is threatened by two mechanisms. First, *feature entanglement*: DINOv2's 768 dimensions may encode topological information alongside non-topological information, creating correlation with PH features that is not independence failure but natural overlap. The SLIDE decomposition (§14.6) separates genuine overlap from artificial correlation. Second, *generator dependence*: if DINOv2 features encode generator-specific visual artifacts (texture patterns characteristic of Flumy output, say) rather than geological structure, the pathway's contribution to the essence claim is undermined. The LOGO (Leave-One-Generator-Out) protocol, formalized as Sākṣī Witness 3 (§10.3), tests for this by training on $N - 1$ generators and evaluating on the held-out generator. If DINOv2 classification accuracy drops substantially under LOGO, the features are generator-dependent and enter the confidence hierarchy at Tier 4 (uncertain) rather than Tier 3 (empirically invariant).

**The representational geometry hypothesis.** A deeper question, which the experimental validation of §12.6 begins to address, is whether DINOv2's representation space has *geometric structure* that aligns with geological similarity. If the manifold of meandering-system representations in $\mathbb{R}^{768}$ is smoothly parameterized by sinuosity, channel width, and point-bar development—and the manifold of braided-system representations is similarly parameterized by braiding index, bar spacing, and channel-to-floodplain ratio—then DINOv2 is not merely discriminating environments but encoding a continuous geological parameter space. This would make the learned pathway's contribution to the hyperbolic embedding (§9.3) particularly valuable: the continuous parameterization within each branch of the depositional hierarchy would complement the topological pathway's discrete structural invariants and the classical pathway's correlation-based descriptors.

**CG-VAE as supervised identifiable learned pathway.** The preceding treatment characterizes the learned pathway as DINOv2 + LoRA producing a 768-dimensional [CLS] representation. Section 5.8 introduced a second, complementary component: CG-VAE, a supervised identifiable variational autoencoder trained on paired $(I, \theta)$ data from the principle-based generator. Within the three-pathway architecture, CG-VAE and DINOv2 are not alternatives but complements with distinct epistemic roles.

*DINOv2 provides unsupervised gestalt.* Its representations are trained on 142 million natural images with no geological labels or parameter information. Their value is their *independence* from domain-specific assumptions. DINOv2 features enter Pipeline A at Tier 3–4 of the confidence hierarchy (§14.6): empirically powerful but without formal guarantees.

*CG-VAE provides theorem-backed identifiability.* Trained with the generator's parameter vector $\theta$ as auxiliary supervision, its learned factors $\hat{z}$ satisfy Kong et al. (2025) Theorem 2 under assumptions A1–A5 verifiable on the principle-based generator. The subset of $\hat{z}$ aligned with the sparse mixing structure A4 prescribes is identifiable up to element-wise invertible transformation—in correspondence with true generative factors, not merely correlated with them. These identified factors enter Pipeline A at Tier 1 of the confidence hierarchy, joining PH-derived topological features at the theoretical anchor.

*Auxiliary encoding choice.* The auxiliary variable $u$ admits three principled forms with distinct assumption-satisfaction consequences. *Categorical generator identity* treats each generator and sub-generator as a discrete domain—minimal supervision, cleanest iVAE fallback (§5.8), but may fail Kong et al.'s A3 (sufficient changes) for fine-grained variation within a single generator. *Continuous parameter vector* $u = \theta$ maximizes information content but introduces overfitting risk: learned factors may encode generator-specific artifacts rather than geological structure. *Hierarchical nesting* $u = (\textrm{environment}, \textrm{substyle}, \theta_{\textrm{local}})$ matches the depositional hierarchy encoded in the hyperbolic embedding (§9.3) and supports the causal representation learning reframing of LOGO in §10.3; it is the expected default pending experimental verification (§12.6).

*Independence implications.* CG-VAE is, by construction, *less* independent from the generator than DINOv2—its supervision is exactly the generator's parameter vector. This is not a weakness but a different kind of evidence contribution. DINOv2 supplies generator-independent gestalt, corroborating essence through convergence across unaligned representations; CG-VAE supplies generator-aligned identifiability, corroborating essence through recovery of factors that survive the interventional conditions analyzed in §10.3. The LOGO protocol (§10.3) retains distinct roles for each: for DINOv2, testing gestalt generalization; for CG-VAE, testing whether the identifiability guarantees hold out-of-distribution by evaluating MCC on a held-out generator against a pre-committed threshold.

This two-component structure preserves the three-pathway architecture (classical, learned, topological) while refining the learned pathway into an internal tier split: DINOv2 residuals at the lower tiers, CG-VAE identified factors at Tier 1. Section 14.6 operationalizes this refinement at the confidence-hierarchy level; §8 documents its implications for the evidence hierarchy.

### 6.6 The $H_1$ Hypothesis

The central testable hypothesis of the topological pathway is:

> **$H_1$ Hypothesis**: First-dimensional persistent homology ($H_1$) discriminates braided from meandering channel architectures even when variogram parameters (range, sill, nugget) are matched.

The physical reasoning is as follows. Braided river systems are characterized by multiple interconnected channels that split and rejoin around bars, creating a network of closed loops in planform view. A braided system should exhibit many persistent $H_1$ features—loops that persist over a wide range of filtration scales, corresponding to channels encircling unfilled floodplain islands (genuine $H_1$ features, as developed in §3.4). Meandering systems have a single sinuous channel with occasional oxbow cutoffs, yielding few $H_1$ features—and those that do form tend to enclose sediment-filled regions, dying quickly in homology because the filled interior makes them boundaries rather than genuine holes.

It is important to distinguish *invariance* from *relevance*. The stability theorem (§3.6) guarantees that PH features are invariant under bounded perturbations—but invariance alone does not guarantee geological usefulness. A perfectly stable feature might capture nothing meaningful; for instance, the average pixel brightness of an image is also stable under small perturbations but tells you nothing about channel architecture. The $H_1$ hypothesis is what connects mathematical invariance to geological meaning: it claims that topologically stable features are also geologically discriminative.

The variogram-matched pairs design is what makes this test epistemically powerful. Critically, two-point geostatistics (variograms) cannot distinguish braided from meandering configurations when spatial correlation lengths are similar—they measure correlation structure but are blind to connectivity topology. Without variogram matching, a skeptic could object: "perhaps your PH-based classifier is simply picking up on differences in spatial correlation structure, redundantly encoding information that a variogram already captures." By constructing image pairs where the variograms are identical, we eliminate this explanation entirely. Any discriminating power that $H_1$ features exhibit on variogram-matched pairs *must* come from higher-order structural information—specifically, the connectivity and loop topology—that the variogram is provably blind to.

The specific prediction: braided systems should exhibit significantly more long-lived $H_1$ features (persistent loops around unfilled floodplain islands) than meandering systems (where loops, if they form at all, tend to enclose filled sediment and die quickly in homology), even when the two are constructed to have identical variograms. If a classifier trained only on vectorized $H_1$ persistence diagrams achieves greater than 70% accuracy on these variogram-matched pairs, the $H_1$ hypothesis is confirmed: PH features are not only stable but geologically discriminative in a way that geostatistical features fundamentally cannot be.

This gives us a two-level evidential warrant that no single method provides:

| Level | What it establishes | How |
|---|---|---|
| **Stability theorem** | PH features are *invariant* (bounded sensitivity to perturbation) | Mathematical proof — holds universally |
| **$H_1$ on variogram-matched pairs** | PH features are *relevant* (capture real geological differences) | Empirical experiment — testable and falsifiable |

Neither level alone is sufficient. Stability without relevance gives us features that are robust but useless. Relevance without stability gives us features that discriminate on the datasets we have tested but might break on unseen data from a new basin or generator. Together, they constitute the strongest evidence structure available in the hierarchy: mathematically guaranteed robustness *plus* empirically demonstrated geological meaning.

The framework establishes a pre-committed decision point: if classification accuracy using only $H_1$ features exceeds 70%, the hypothesis is supported and TDA becomes a core pathway; if it falls below 60%, TDA remains an ablation study (ADR-S04). This pre-commitment follows the Sākṣī (witness) validation philosophy: interpretation thresholds are fixed before data analysis.

### 6.7 Cubical Complexes and the SEDT Filtration

For geological image data, the QCF employs *cubical complexes* with a *signed Euclidean distance transform* (SEDT) filtration, following the methodology established by Robins et al. (2016) for geological pore-space characterization.

The SEDT assigns to each pixel a signed distance to the nearest boundary between facies: positive inside channel bodies, negative inside floodplain. Filtering by increasing SEDT values progressively "erodes" narrow connections, revealing which topological features (connected components, loops) are robust at the core of geobodies versus those that depend on thin, possibly artifactual connections.

This filtration choice is geologically meaningful: features that persist across a wide range of SEDT values correspond to thick, well-connected channel bodies—the kind of structural features that matter for reservoir connectivity and flow simulation. Features that die quickly correspond to thin connections or noise.

### 6.8 Persistence Diagrams and the Hyperbolic Embedding

The persistence diagrams produced by the topological pathway encode hierarchy in a manner that aligns naturally with the QCF's hyperbolic embedding space. In a persistence diagram, the distance of a point from the diagonal (its persistence, $d - b$) reflects the feature's structural importance: long-lived bars correspond to essential, large-scale topological features, while short-lived bars correspond to fine-scale detail or noise.

The Poincaré ball model used by the QCF encodes a depositional hierarchy: general environment types near the origin, specific sub-types near the boundary. There is a natural map between these two hierarchies: an image whose $H_1$ persistence diagram is dominated by many long-lived loops is "more braided" and should sit closer to the hyperbolic boundary near the braided-river prototype; an image with few $H_1$ features but a characteristic distribution of $H_0$ lifetimes (reflecting channel-body isolation) is "more meandering" and sits near the meandering prototype.

This geometric interpretation of persistence diagrams feeding directly into hierarchy-aware embedding represents, to our knowledge, a novel contribution of the QCF.

### 6.9 The Adversarial Validation: Variogram-Matched Topology Swap

The strongest direct test of PH's value within the QCF is the *Sankhyā-māyā* ("statistical illusion") adversarial test, formalized as §10.4.1 in the Sākṣī validation battery. The test constructs matched pairs of images—one braided, one meandering—with *identical* variogram parameters (range, sill, nugget). Classical geostatistical features cannot distinguish these pairs by construction. If the system still correctly classifies them using topological features alone, the $H_1$ pathway demonstrably captures structural information invisible to two-point statistics.

This test design instantiates a broader validation philosophy drawn from Mayo's (2018) severe testing framework: a hypothesis is supported only when it passes a test that it would likely fail if false. A classification test using images that are *designed* to fool the classical pathway but should be distinguishable by $H_1$ loop structure provides precisely this kind of severe evidence. The experimental protocol is detailed in the proposed validation design (Section 12.2).

### 6.10 Scope and Limitations of the Topological Pathway

Intellectual honesty requires acknowledging what persistent homology *cannot* do within this framework. First, PH does not address the *sparsity problem*—it requires complete images as input. The Neural Process query encoder handles sparse observations; PH operates downstream on complete database analogs. Second, PH applied to 2D images captures only $H_0$ (connected components) and $H_1$ (loops); $H_2$ (voids) would require 3D volumetric data not yet available in the current pipeline. Third, topological evidence alone is insufficient for a strong essence claim. The stability theorem guarantees mathematical invariance of PH features under bounded perturbations, but the QCF's multi-level evidence hierarchy (Section 8) requires convergence of mathematical, adversarial, empirical, and expert evidence. PH provides one essential strand in that convergence—not the whole rope.

### 6.11 Related Work: Component Technologies and the Integration Gap

The Qualia Convergence Framework draws upon several established research directions—topological data analysis in geoscience, hyperbolic representation learning, neural processes, and self-supervised visual features—while combining them in a manner not attempted in prior work. This section surveys the relevant literature for each component technology and identifies the integration gap that constitutes the framework's primary novelty claim.

**Topological data analysis in geoscience.** Persistent homology has an established track record in geological and materials science applications, though primarily for structural characterization rather than retrieval. Robins et al. (2016) applied PH to micro-CT images of porous materials, developing the SEDT filtration methodology adopted by the present framework (Section 6.7). Moon et al. (2019) demonstrated that statistical inference over persistence diagrams predicts fluid flow properties from pore structure, establishing that topological features capture geologically consequential information beyond what conventional descriptors provide. Thompson et al. (2023) extended PH to dynamic settings, tracking topological changes in dissolving carbonate pore networks over time—work that connects to the dynamic extensions discussed in Section 14. In an industry context, Chawshin et al. (2021) employed topological representations for well-log interpretation and depositional facies classification. However, all existing TDA applications in geoscience operate as standalone analytical tools: no prior work integrates topological features with learned representations within a retrieval architecture, and no prior work tests the specific hypothesis that $H_1$ features discriminate channel architectures under variogram-matched conditions.

**Hyperbolic embeddings.** Hyperbolic representation learning has demonstrated substantial advantages for hierarchically structured data across domains. The foundational Poincaré embedding model of Nickel and Kiela (2017) was extended to graph-structured data by Chami et al. (2019), who reported a 63.1% reduction in embedding distortion for hierarchical graphs compared to Euclidean baselines. Peng et al. (2022) provide a comprehensive survey of hyperbolic deep neural networks, documenting applications in computer vision, natural language processing, social network analysis, and molecular modeling. Despite this breadth of application, hyperbolic embeddings have not been applied to geological facies classification or depositional environment retrieval—the survey characterizes geoscience applications as "still emerging." The QCF's use of the Poincaré ball to encode the natural hierarchy of depositional environments (Section 9.3) represents, to our knowledge, the first such application.

**Neural Processes in earth sciences.** Neural Processes have been applied to earth science problems, but exclusively for interpolation and prediction tasks rather than retrieval. Vaughan et al. (2022) employed Convolutional Conditional Neural Processes for climate downscaling, leveraging the architecture's ability to handle variable-density observational inputs. Physics-informed Attentive Neural Processes have been applied to ground-motion prediction from seismological data. These applications exploit the same architectural properties—set-valued inputs, principled uncertainty quantification, graceful degradation under data sparsity—that motivate the QCF's adoption of NPs as a query encoder (Section 9.2). The critical distinction is that all existing NP applications in geoscience frame the problem as *spatial prediction* (estimating values at unobserved locations), whereas the QCF uses NPs for *similarity-based retrieval* (mapping sparse observations to a distribution in embedding space and retrieving structurally similar analogs). This reformulation—from prediction to retrieval—is novel.

**Self-supervised visual features for geological data.** The DINOv2 architecture (Oquab et al., 2023) provides the learned pathway's feature extractor. Recent empirical studies have validated DINOv2's pre-trained representations for geological image analysis, demonstrating competitive or superior performance to task-specific architectures for rock type classification and geological segmentation, even without domain-specific fine-tuning. This robustness aligns with the cognitive science concept of "scene gist"—the rapid, holistic pattern recognition that allows human experts to categorize a depositional environment within milliseconds before consciously analyzing individual features (Oliva & Torralba, 2006). The DINOv2 [CLS] token, which aggregates global image information via self-attention across all patches, provides an architectural analog to this gestalt perception. Within the QCF, however, DINOv2 features are not used in isolation; they serve as one of three independent epistemic perspectives, and their contribution is adjudicated by the evidence hierarchy (Section 8) and the Sākṣī validation framework (Section 10).

**Generative models for geological data.** Recent work has applied deep generative modeling to geological image analysis with objectives adjacent to but distinct from the QCF's learned pathway. Most relevant is the recent study on inversion of fluvial deposits via process-based and deep generative modeling (arXiv:2510.17478, October 2025), which trains a GAN on process-based fluvial simulations and engineers its latent space to expose directions the authors characterize as semantically meaningful—channel sinuosity, width, bifurcation frequency—for interactive geological editing. Three differences separate this work from the QCF's approach. First, *no persistent homology*: the inversion operates entirely in GAN latent space with no topological component, so the topological information that §6.9's variogram-matched experiment targets is not extracted. Second, *no identifiability theorem*: latent-space directions are identified via empirical probing and orthogonality-inducing regularizers—the same inductive-bias approach Locatello et al. (2019) proved insufficient for unsupervised disentanglement. No theorem bounds the correspondence between learned directions and true generative factors. The QCF's CG-VAE integration (§5.8, §6.5) specifically addresses this gap via Kong et al. (2025) Theorem 2. Third, *single-environment scope*: the prior work treats fluvial deposits only and does not address cross-environment invariance or cross-generator LOGO-style validation (§10.3), whereas the QCF's multi-environment generator (§2) is designed for precisely those cross-generator invariance claims. These distinctions are not criticisms of the prior work—which addresses a different problem (interactive editing under geological constraint)—but clarifications of the QCF's distinctive contribution: theorem-backed identifiability, multi-environment cross-generator validation, and convergence with topological evidence.

**The synthetic benchmark gap.** A documented limitation in geological machine learning is the absence of widely accepted benchmark datasets for geological image classification. Without standardized benchmarks, comparing the efficacy of different methodologies requires each research group to generate its own synthetic datasets, introducing inconsistencies across studies. Existing synthetic data tools—GemPy for 3D structural modeling, geostatistical simulation (SGS/SIS) for spatial realization, coupled flow simulators for reservoir prediction—serve purposes distinct from ML training data generation. Recent deep generative models (GANs, VAEs, diffusion models) have been applied primarily to *surrogate simulation*—replacing expensive numerical solvers for forward prediction—rather than producing labeled training datasets with known ground truth parameters. The principle-based generator described in Section 2 directly addresses this gap: it produces multi-environment geological images with known generating parameters, acceptance-criteria-verified structural properties, and the explicit purpose of providing standardized, reproducible training data for representation learning.

**The integration gap.** The preceding review establishes that each component technology has precedent in isolation. No prior work, however, combines these components into an integrated retrieval system. Specifically, no existing framework embeds geological analogs in hyperbolic space to encode depositional hierarchy, encodes sparse observations via Neural Process query encoders with calibrated uncertainty, discriminates structural topology via persistent homology integrated with learned features, validates invariance claims through a formal pre-committed evidence hierarchy, or generates training data via principle-based simulators designed for cross-generator invariance testing. Each component addresses a limitation that the others cannot resolve alone: PH provides mathematical invariance but requires complete images; NPs handle sparsity but provide no structural guarantees; hyperbolic geometry encodes hierarchy but is blind to topology; DINOv2 captures visual semantics but lacks interpretability. The framework's contribution is not any single component but the epistemically principled architecture that combines them—with the evidence hierarchy (Section 8) and Sākṣī validation framework (Section 10) providing the meta-scientific discipline that governs when the resulting claims are warranted.

---

## 7. The Ellipse Degradation Thought Experiment

### 7.1 The Setup

The question of how persistent homology relates to "essence" was examined in a thought experiment (Hoydic, 2026) involving progressive degradation of a channelized reservoir image. Two variants were considered:

**Variant A (Occlusion)**: Progressively add ellipses to the image that hide (but do not destroy) geological features. At 0% coverage, the full image is visible. At 100%, only ellipses remain. The question: at what point is "essence" lost?

**Variant B (Erosion)**: Progressively modify the geological features themselves—straightening channels, removing point bars, eliminating oxbow lakes. The end state is the same (an unrecognizable image), but the path involves destroying information rather than hiding it.

### 7.2 Five Problems with Degradation-Based Essence

This analysis revealed five fundamental problems with defining essence through degradation thresholds:

**1. Occlusion versus erosion.** Occlusion preserves information (the geology is still there, just hidden); erosion destroys it irreversibly. The QCF faces an occlusion problem—sparse observations of full subsurface geology—making this distinction critical. The thought experiment conflates these fundamentally different operations.

**2. Path dependence.** Different degradation orders yield different "minimal essence" sets. Removing sinuosity first, then point bars, versus removing point bars first, then sinuosity, produces different intermediate states and different "essence thresholds." There is no unique answer.

**3. Feature entanglement.** Geological features are not independent—they are physically coupled through constraints like the Leopold-Wolman relationship ($\lambda = 10\text{--}14W$, relating meander wavelength $\lambda$ to channel width $W$) and curvature constraints ($R_c = 2\text{--}3W$, relating radius of curvature to width). Independent feature removal creates geologically *impossible* states—configurations that could never occur in nature because they violate physical constraints. This means the degradation path passes through regions outside the constrained manifold $M$ of valid geological configurations.

**4. Observer-relativity.** Different measurement systems have different essence thresholds. A human sedimentologist might maintain recognition up to 60% ellipse coverage. DINOv2 might fail at 40% or persist to 70% depending on pretraining. Persistent homology ($H_1$ loops) is particularly sensitive to channel connectivity—even a few ellipses placed at channel intersections could destroy the homology, causing apparent "essence loss" at very low coverage. The variogram, integrating information across all pixel pairs, might be robust until very high coverage. Essence is observer-relative, not intrinsic.

**5. Minimality versus sufficiency.** The thought experiment implicitly seeks the "minimal" set of features needed for recognition. But minimality is fragile: if the minimal features are corrupted, recognition fails completely. For retrieval with calibrated uncertainty, we need *sufficient* representations that include redundancy. Over-complete representations can be more stable than minimal ones.

### 7.3 Generator Invariance as an Alternative

The thought experiment's conclusion was that essence is better defined through *invariance across generative processes* rather than degradation thresholds. Formally, let:

- $X$ be the space of possible images
- $\Theta$ be the space of geological parameters (sinuosity, width, wavelength, etc.)
- $G: \Theta \to X$ be a stochastic generator function
- $M \subset \Theta$ be the constrained manifold of physically realizable configurations
- $f: X \to Z$ be a representation function

Then:

$$\textrm{Essence}(f) = \bigcap_G \lbrace \text{information about } \theta \text{ captured by } f \text{ when trained on } G \rbrace$$

Essence, on this definition, is what survives across *all* generators—the information that no generative process can remove. This definition is unique (no path dependence), respects physics (generators enforce the constrained manifold $M$), and is observer-independent (defined by agreement across generators rather than by any single measurement system).

**Two modes of assessing invariance.** The critical question becomes: *how do we verify that a representation captures this invariant intersection?* There are two fundamentally different approaches, distinguished by epistemic strength:

1. **Empirical invariance testing**: Cross-validate across generators—train on some, test on others, measure degradation. This approach is intuitive and directly measures retrieval capability. However, as we argue in Section 8, any finite set of empirical tests faces structural limitations rooted in the problem of induction: passing $N$ tests does not guarantee passing $N+1$.

2. **Mathematical invariance theorems**: Prove from first principles that a representation is stable under bounded perturbations. The stability theorem (§3.6) provides exactly this for persistent homology—and uniquely for persistent homology among the QCF's three pathways. Mathematical proof is not defeasible by additional evidence; it does not depend on which generators are tested, how many are used, or how "diverse" the test pool is.

The stability theorem thus makes a strong prediction: because persistent homology is provably stable under perturbations of the input function, topological features *should* transfer between generators better than learned features (which may overfit to generator-specific textures) or classical features (which depend on specific correlation-function shapes). This is a testable prediction, pre-committed before data analysis: the topological pathway should show the least degradation under generator shift.

---

## 8. The Evidence Hierarchy: Mathematical Invariance Over Empirical Testing

### 8.1 A Multi-Level Evidence Structure

What evidence warrants calling a representation "essence"? No single test is sufficient. We propose a hierarchy organized by epistemic strength—from mathematical proof at the top to empirical agreement at the bottom—where the convergence of multiple levels provides warranted confidence:

**Level 1 — Mathematical Invariance Theorems (Strongest).** Level 1 comprises two *complementary* classes of mathematical guarantee, each protecting against a distinct failure mode. The framework admits both at the same epistemic tier: each is a formal proof, not an empirical claim, and each provides warranted confidence that no quantity of downstream testing can supply. Section 8.2 develops the complementary-evidence structure formally.

**Level 1a — Stability (sensitivity to perturbation).** The stability theorem (Cohen-Steiner, Edelsbrunner, & Harer, 2007) provides a formal proof that persistent homology features are invariant under bounded perturbations of the input function:

$$d_B\bigl(\textrm{Dgm}(f), \textrm{Dgm}(g)\bigr) \leq \lVert f - g \rVert_\infty.$$

This is a mathematical guarantee—it does not depend on which generators are tested, which dataset is used, or how many experiments are run. It cannot be "overengineered" because it is a theorem, not a test. Stability protects against perturbation noise: bounded input changes produce bounded diagram changes. For the topological pathway, stability is the primary invariance guarantee.

*Limitation (Level 1a).* The stability theorem guarantees that PH features are *invariant under perturbation*, but does not guarantee they are *relevant to geology* or that they *correspond to true generative factors*. One could have perfectly stable features that are geologically irrelevant; one could also have perfectly stable features that encode generator-specific artifacts stably rather than geological structure stably. The $H_1$ hypothesis (§6.6) addresses relevance through empirical testing; Level 1b addresses correspondence through a second theorem class.

This limitation deserves a sharper formulation: *the $H_1$ experiment is the linchpin of the Level 1a guarantee.* If PH features prove unable to discriminate braided from meandering architectures on variogram-matched pairs—if topological invariants capture nothing geologically meaningful—then Level 1a's mathematical guarantee becomes actively misleading rather than merely incomplete. The stability theorem would certify the robustness of features that encode no geological content, and the hierarchy, designed to privilege mathematical invariance over empirical testing, would privilege precisely the wrong signals. The research program's pre-committed decision thresholds (§6.6; ADR-S04) reflect this centrality: below 60% classification accuracy, the topological pathway is demoted to an ablation study regardless of how elegant its mathematical foundations may be.

**Level 1b — Identifiability (correspondence with generative factors).** Identifiability theorems (Khemakhem et al., 2020; Kong et al., 2025) provide a formal proof that learned latent factors recover true generative parameters up to well-defined invertible equivalence classes, under auxiliary-variable supervision. Khemakhem et al.'s iVAE result (§5.8) establishes affine-equivalence identifiability when $2n + 1$ distinct auxiliary values produce linearly independent natural-parameter vectors of an exponential-family conditional prior. Kong et al.'s Theorem 2 strengthens this to component-wise identifiability—up to element-wise invertible transformation—under sparse-mixing structure A4 and a second-order derivative condition on the mixing Jacobian. Section 5.8 contains the theorem statements and their relationship to the CG-VAE architecture introduced there.

Level 1b is also a mathematical guarantee—it does not depend on empirical test passes—but it protects against a *different* failure mode than stability. Where Level 1a bounds sensitivity to input perturbation, Level 1b bounds correspondence: the guarantee that learned factors recover true generative structure rather than generator-artifact mixtures that happen to fit the observed data distribution.

*Limitation (Level 1b).* Identifiability guarantees require auxiliary-variable supervision and the assumption set A1–A5 (iVAE variant: exponential-family prior and $2n + 1$ auxiliary values over the full latent vector). The QCF's principle-based generator (§2) satisfies the supervision requirement by construction through paired $(I, \theta)$ data, but A4 (sparse mixing) must be verified empirically per generator; A5 provides an automatic fallback to iVAE's result if A4 fails on a specific generator. Identifiability guarantees, like stability guarantees, are conditional on their assumption sets holding. The empirical analog of the $H_1$ linchpin for Level 1b is the Mean Correlation Coefficient (MCC) threshold documented in §10.3 and §14.6—a pre-committed check that Level 1b's correspondence claim is not vacuous in practice.

**Level 2 — Severe Adversarial Testing.** Following Mayo's severe testing framework (2018): a claim passes a severe test if the test was *highly capable of detecting failure* had the claim been false. The key shift: design tests to *break* the invariance claim, not merely challenge it. Specifically: construct generators designed to produce images where topological features are misleading, test whether $H_1$ features can be manipulated independently of geological meaning, and inject noise at filtration-critical scales. If the claim survives tests designed to destroy it, that is strong evidence.

**Level 3 — Information-Theoretic Measures.** Quantify what representations capture using mutual information: $I(f(X); \theta \mid G)$ measures geological information captured independently of generator; $I(f(X); G \mid \theta)$ measures generator-artifact contamination. High $I(f(X); \theta \mid G)$ and low $I(f(X); G \mid \theta)$ provide continuous, quantitative evidence that the representation captures geology, not generator artifacts.

**Level 4 — Cross-Domain Validation.** If the same topological features that distinguish geological environments also distinguish structurally analogous patterns in music, neuroscience, or other domains, the invariance transcends the generator concept entirely—it is a property of the mathematics, not of any particular application. (See Section 11.)

**Level 5 — Real-Data Validation.** Testing against real geological data that no generator was designed to reproduce. This is the ultimate generator-independent benchmark, but requires data that may not be available in early research phases.

**Level 6 — Cross-Generator Validation (Necessary but Not Sufficient).** Testing invariance across generators—training on some, testing on others—provides a practical check: failure indicates generator-specificity. However, passing such tests alone is insufficient for a strong essence claim. Three independent theoretical results constrain what cross-generator validation can establish. Ahuja et al. (2023) proved that invariance alone is insufficient to identify latent causal variables—passing cross-validation across $N$ generators does not prove that invariant features capture geological causes rather than shared assumptions of the generator family. Invariant Risk Minimization (Arjovsky et al., 2019; Rosenfeld et al., 2021) has been shown to fail in nonlinear settings and require impractically many environments for formal guarantees—adding more generators from the same family does not help if they share physical assumptions. And Wimsatt's robustness analysis (1981) requires genuinely independent models for convergent results to be evidential; Orzack and Sober (1993) sharpened this to "nonempirical confirmation, effective only under unusual circumstances." These limitations are structural, not merely practical—they constrain what any finite empirical invariance test can demonstrate. Cross-generator protocols remain a valuable diagnostic (failure is informative), but their positive results must be corroborated by higher levels of evidence.

**Level 7 — Expert Agreement.** Human expert judgment (Cohen's $\kappa$) provides truly generator-independent assessment, as experts judge geological similarity from experience, not from any computational pipeline.

### 8.2 Stability and Identifiability as Complementary Level 1 Evidence

The two Level 1 theorem classes introduced in §8.1 are *complementary*, not redundant. Each provides mathematical certainty about a specific invariance; each leaves the other's domain unprotected. A feature that satisfies both is *doubly* Level 1—robust against perturbation and correctly identified against true generative factors—and §14.6 elevates such features to the top of the confidence hierarchy. Understanding the complementarity precisely requires naming what each theorem protects against, and what each does not.

**What stability protects against, and what it does not.** The stability theorem bounds

$$d_B\bigl(\textrm{Dgm}(f + \delta f), \, \textrm{Dgm}(f)\bigr) \leq \lVert \delta f \rVert_\infty$$

for any perturbation $\delta f$ of the input function. This is a sensitivity guarantee: small input changes produce correspondingly small persistence-diagram changes. Stability does *not* say anything about whether the features of $\textrm{Dgm}(f)$ correspond to true generative factors of the geological system that produced $f$. A persistence diagram could be maximally stable and yet encode only generator-specific artifacts—properties that survive perturbation but carry no geological meaning. Level 1a answers "does the feature respond smoothly to input noise?" but not "does the feature recover what produced the input?"

**What identifiability protects against, and what it does not.** The identifiability theorems bound

$$\hat{z} = h(z)$$

for known, structured $h$ (affine in iVAE; element-wise invertible in Kong et al.'s Theorem 2). This is a correspondence guarantee: learned factors are in known relationship with true generative factors. Identifiability does *not* bound response to input perturbation. A learned factor $\hat{z}_k$ could satisfy Theorem 2 perfectly—identifying the true $z_k$ up to invertible transformation—and still be arbitrarily sensitive to small image noise that happens to fall outside the training distribution. Level 1b answers "does the feature recover the generative factor it claims to?" but not "is the feature robust to perturbation?"

**Why both matter in retrieval.** Pipeline A (§9.1) indexes geological analogs by descriptor vectors; Pipeline B (§9.2) maps sparse observations into the same descriptor space. Each pipeline can fail in ways that a Level 1 theorem protects against, but no single theorem protects against both failure modes simultaneously:

| Failure mode | Countered by | Mechanism |
|---|---|---|
| Sparse observation is a bounded perturbation of the full analog it should retrieve, but the perturbed descriptor lies far from the full-analog descriptor in the index metric | Level 1a (stability) | Bottleneck distance bounded by sup-norm of perturbation |
| Descriptor indexes generator-specific texture or artifact that happens to correlate with environment label in the training data | Level 1b (identifiability) | Kong et al. Theorem 2 bounds learned factor away from non-generative artifact via auxiliary supervision |
| Both simultaneously: noisy sparse observation whose descriptor indexes a generator artifact | Level 1a AND Level 1b jointly on the same feature | Joint feature passes both tests — robust *and* correctly identified |

The QCF's retrieval claim rests on the convergence of these two guarantees. PH features provide Level 1a naturally, from the topological pathway's mathematical structure. CG-VAE features provide Level 1b naturally, from the auxiliary-supervised learned pathway's mathematical structure. The SLIDE decomposition (§14.6) isolates the joint component—features simultaneously aligned with both pathways—and this joint component earns the highest confidence in the retrieval metric because it carries both guarantees.

**A shared limitation, honestly stated.** Both theorem classes deliver guarantees conditional on their assumption sets. Level 1a requires that the perturbation model be bounded in the sup norm—a condition violated by adversarial modifications that exceed the bound or by modeling choices that change the filtration type (cubical vs. Vietoris-Rips, for instance). Level 1b requires A1–A5 of Kong et al. or exponential-family plus $2n + 1$ auxiliary values of iVAE—conditions the principle-based generator is designed to satisfy, but which must be verified per generator and for which A5 provides a documented fallback. Neither guarantee is unconditional; both are stronger than "our empirical tests passed." The framework earns its epistemic confidence not by making unconditional claims but by making *conditional claims whose conditions are themselves verifiable*, then submitting those conditions to severe testing (Level 2) and cross-validation (Levels 4–7).

### 8.3 The Revised Essence Claim

> We claim that a representation captures "essence" when evidence *converges across multiple levels* of this hierarchy. No single level is sufficient. The convergence of mathematical proof (Level 1a stability *and* Level 1b identifiability), survival of severe testing (Level 2), information-theoretic confirmation (Level 3), and empirical validation (Levels 5–7) provides the warranted basis for the essence designation.

This multi-level structure is both more epistemically honest and more powerful than any single empirical test. It acknowledges the structural limitations of empirical invariance testing while building a stronger, multi-layered argument for the essence designation. Two complementary Level 1 streams contribute: the topological pathway supplies Level 1a (stability) from the mathematical structure of persistent homology, and the supervised learned pathway (CG-VAE) supplies Level 1b (identifiability) from the auxiliary-variable theorems of Khemakhem et al. (2020) and Kong et al. (2025). The essence argument rests on the *convergence of two Level 1 guarantees* protecting against different failure modes (§8.2)—not on any single theorem class—plus empirical corroboration at the lower levels. This is a stronger claim than either theorem alone could supply, and it is accessible precisely because the principle-based generator provides the auxiliary-variable supervision that Level 1b requires.

### 8.4 Implications for Descriptor Admissibility and Query Validation

The evidence hierarchy is not merely a philosophical organizing device—it has direct operational consequences for both pipelines of the retrieval architecture. Specifically, the hierarchy governs three critical system-level decisions: which descriptors are admitted into Pipeline A's geologic index, how Pipeline B's query encodings are validated, and what justifies the similarity metric coupling the two pipelines.

**Pipeline A: Descriptor admissibility.** Not every computable feature qualifies as an "essence carrier" for the geologic index. The evidence hierarchy establishes a graded admissibility standard, with Level 1a (stability) and Level 1b (identifiability) admitting different classes of feature at the top tier. Persistent homology features are admitted at Level 1a: they are provably stable under bounded perturbation and thus provably resistant to generator artifacts contaminating the index through input noise. CG-VAE factors that pass the pre-committed MCC threshold (§10.3, §14.6) are admitted at Level 1b: they are provably identifiable against true generative factors, and thus provably resistant to generator artifacts contaminating the index through learned-feature entanglement. DINOv2 residuals—the components of the DINOv2 representation not aligned with CG-VAE's identified factors—are admitted only at Levels 5–7, supported by cross-validation and expert-agreement evidence, and flagged for potential revision as higher-level evidence accumulates. Classical geostatistical descriptors are admitted at Levels 2–6 depending on the specific feature, with variogram parameters at Level 6 (cross-generator validation) and more exotic connectivity measures at lower levels. Descriptors lacking any evidence above Level 7 (expert agreement alone) are excluded from the core index, though they may inform metadata or secondary search facets. This graded admissibility prevents the geologic index from encoding generator identity rather than geological structure—a failure mode that would render Pipeline A's organization scientifically indefensible.

**Pipeline B: Query encoding validation.** The query encoder must map sparse observations into the same descriptor space as Pipeline A. The evidence hierarchy governs validation of this mapping: the query encoder's output, when evaluated on complete analogs where ground truth is available, must reproduce the descriptor values that Pipeline A computes directly. The two Level 1 guarantees contribute asymmetrically. Level 1a (stability) bounds how small input perturbations—the difference between a complete analog and a sparse observation of that analog—translate to perturbations in the topological descriptors, providing a guaranteed error bound for the PH portion of the query-to-index mapping. Level 1b (identifiability) provides no direct bound on perturbation sensitivity; it guarantees correspondence between learned factors and true parameters under auxiliary supervision, but the encoder must additionally be shown empirically to maintain identifiable-factor recovery under the sparse-observation transformation. This is operationalized as MCC on sparse inputs against full-image ground truth, with thresholds pre-committed in §10.3. DINOv2 residuals and classical geostatistical descriptors, lacking Level 1 guarantees, must be validated empirically at Levels 5–7. The asymmetry is deliberate: Level 1a and Level 1b descriptors together provide the mathematically guaranteed substrate onto which empirically validated descriptors are layered.

**Coupling layer: Similarity metric justification.** The similarity metric used to compare Pipeline B queries against Pipeline A index entries must be justified by the same evidence standards. A metric that weights descriptors equally regardless of their evidence level conflates mathematical certainty with empirical conjecture. Instead, the evidence hierarchy suggests a weighted metric in which Level 1 descriptors receive higher weight (or serve as hard constraints) while lower-level descriptors modulate the ranking. Within Level 1, features earning *both* 1a (stability) and 1b (identifiability) guarantees—the "doubly Level 1" joint component that §14.6 isolates via SLIDE decomposition—receive the highest weight, followed by singly-1a or singly-1b features; lower levels follow in descending evidential order. This architecture ensures that retrieval decisions are anchored by the most epistemically secure features and refined by complementary evidence—a design principle that follows directly from the hierarchy's structure and from §8.2's formal complementarity argument.

---

## 9. System Architecture: From Invariants to Analog Retrieval

The preceding sections establish three foundational results: persistent homology provides mathematically guaranteed invariants (Section 3), the three-pathway architecture encodes essence through independent epistemic perspectives (Section 6), and the evidence hierarchy governs which descriptors qualify as essence carriers (Section 8). This section addresses the architectural question that connects these foundations to a working retrieval system: *how do topological invariants, together with complementary descriptors, become a mechanism for finding geological analogs under sparse data constraints?*

The most important conceptual principle governing this architecture is that persistent homology is not simply one of three parallel feature extractors of equal standing. It is the only pathway with a mathematical stability guarantee, and this epistemic asymmetry should govern the entire design. The three pathways produce features of fundamentally different epistemic status: PH features are backed by the stability theorem—a mathematical proof of bounded sensitivity to input perturbation; classical geostatistical features are well-understood but depend on stationarity assumptions that geological data routinely violates, and have no analogous stability theorem; DINOv2 learned features capture rich visual semantics but are opaque, entangled, and dependent on the training distribution. This asymmetry means the three pathways should not be treated symmetrically in fusion. PH features serve as the *epistemic anchor*—the features around which the architecture is organized—and the other pathways are measured against them. Section 14.6 develops this principle into a formal confidence hierarchy with operationalized tiers; here, we show how it shapes the system architecture at every level.

We present the system architecture as a conceptual design with key mathematical formulations. No implementation code is given; the goal is to specify what each component does, why it is needed, and how the components compose into a coherent system. The architecture realizes the two-pipeline structure introduced in Section 1 and is governed at every stage by the evidence hierarchy of Section 8.

### 9.1 Pipeline A: Building the Geologic Index

Pipeline A transforms a heterogeneous repository of geological analog data into a searchable geologic index. The repository may contain full-resolution geological images (binary facies maps, grayscale photomicrographs), three-dimensional reservoir models (discretized volumes with per-cell facies assignments), seismic volumes (amplitude or impedance data on regular grids), core and outcrop photographs, and outputs from process-based simulations (Flumy, BRAHMS, and similar generators). Each analog artifact enters the three-pathway feature extraction architecture described in Section 6.3: the classical pathway computes geostatistical descriptors, the learned pathway extracts DINOv2 visual semantics, and the topological pathway computes persistent homology of the SEDT filtration.

Persistent homology occupies a privileged position within this architecture. The stability theorem (Section 3.6) guarantees that topological descriptors satisfy Level 1 of the evidence hierarchy—the only descriptors in the current framework with a mathematical invariance proof. This means that topological features are provably resistant to the generator-artifact contamination that would render the index scientifically indefensible. Classical and learned features, while providing complementary discriminative power, enter the index at lower evidence levels and are accordingly weighted in the similarity computation.

A critical design decision concerns the *unit of indexing*: what constitutes a single entry in the geologic index? The repository may be indexed at the level of entire analogs (one entry per simulation or outcrop), subvolumes (windowed regions within a larger model), or stratigraphic packages (geologically meaningful intervals such as individual parasequences or depositional units). The choice has consequences for retrieval granularity: indexing entire analogs is computationally efficient but may obscure internal heterogeneity, while subvolume indexing captures multiscale structure at the cost of a larger index. A multiscale indexing strategy—multiple entries per analog at different spatial scales—may ultimately prove necessary, but adds complexity to both the index schema and the similarity computation.

The index schema itself admits several candidate architectures. A metric space with approximate nearest-neighbor (ANN) search via FAISS (Johnson, Douze, & Jégou, 2019) provides fast retrieval in high-dimensional Euclidean or inner-product spaces. A hyperbolic embedding (Section 9.3) encodes the hierarchical taxonomy of depositional environments—fluvial, aeolian, estuarine—with exponentially efficient dimensional scaling. A knowledge graph representation encodes relational geological structure (stratigraphic relationships, lateral transitions, unconformities) that vector spaces cannot naturally represent. A hybrid architecture combining vector search with graph-structured metadata may ultimately be required. The choice among these options is an open design question (Section 9.7), but the evidence hierarchy provides a constraint: whatever schema is selected, topological descriptors must be first-class index entries, not relegated to post-hoc filtering.

### 9.2 Pipeline B: The Neural Process Query Encoder

Pipeline B addresses the fundamental asymmetry of the retrieval problem: Pipeline A operates on complete analog patterns with full spatial coverage, while real geological queries are sparse—a few well logs providing high-resolution but spatially isolated vertical profiles, a partial seismic survey offering broad but low-resolution coverage, scattered outcrop observations constrained to surface exposures. The query encoder must map these sparse, incomplete, multimodal observations into the same descriptor space as Pipeline A's index entries, producing not a point estimate but a calibrated distribution that reflects the inherent uncertainty of inference from limited data.

**Why Neural Processes.** Neural Processes (Garnelo et al., 2018; Kim et al., 2019) solve precisely this problem. A Neural Process takes a *variable number* of context points—the sparse observations—and outputs a *distribution* over possible embeddings, where uncertainty reflects data sparsity rather than model uncertainty alone. This is "amortized Bayesian inference": the Neural Process learns to perform approximate inference in a single forward pass, rather than requiring iterative Markov chain Monte Carlo sampling at query time.

The choice of Neural Processes over alternatives was deliberated as a formal architecture decision (ADR-003). Four alternatives were considered and rejected. A *deterministic encoder* (mapping observations to a point estimate via a set encoder) provides no principled uncertainty quantification and cannot distinguish "confidently wrong" from "appropriately uncertain." *MC Dropout* (Gal & Ghahramani, 2016)—using dropout at inference time to approximate Bayesian uncertainty—captures model uncertainty but not the data-sparsity uncertainty that is central to the retrieval problem: the uncertainty should decrease as the geoscientist provides more observations, not as the model becomes more certain about its own weights. *Deep Ensembles* (Lakshminarayanan et al., 2017) provide better-calibrated uncertainty than MC Dropout but at substantial computational cost (training and maintaining multiple independent models), and the uncertainty remains model-based rather than data-conditioned. *Bayesian Neural Networks* (full posterior inference over network weights) are theoretically appealing but intractable for the architecture sizes required; practical approximations may not calibrate well for the extreme sparsity regimes encountered in geological queries.

A fifth alternative deserves separate discussion. Topological Knowledge Representation (TKR; Chawshin et al., 2021) approaches analog retrieval by explicitly constructing graph representations—segmenting geological images into discrete units, assigning attributes to nodes, encoding spatial relationships as labeled edges, and performing retrieval via graph matching. TKR offers high interpretability (explicit structural relationships) but handles continuous variation poorly (geological patterns vary continuously in sinuosity, bar spacing, and channel geometry, requiring arbitrary discretization), provides limited uncertainty quantification (graph matching produces binary match/no-match rather than calibrated distributions), and has unclear behavior under sparse queries (partial graph matching under missing data is itself a challenging combinatorial problem). The Neural Process approach addresses all four limitations: continuous embeddings naturally capture gradients in geological parameters, the $(\mu, \sigma)$ output provides calibrated uncertainty, and variable-size input is handled natively by the set encoder. TKR and embedding-based retrieval are not mutually exclusive—graph-derived features could serve as a fourth pathway in future work—but the Neural Process architecture is better suited as the primary query encoder.

**Architecture.** Conceptually, the Neural Process query encoder operates as follows. The input is a context set $C = \lbrace (x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n) \rbrace$ where each $x_i$ encodes location and metadata (spatial coordinates, depth, acquisition parameters) and each $y_i$ encodes the observation at that location (well log values, seismic amplitudes, facies interpretations). Because observations are multimodal, modality-specific encoders process each input type: a 1D convolutional neural network processes well log depth sequences, a 2D convolutional neural network processes seismic amplitude patches, and DINOv2 features (pretrained, with optional fine-tuning) process outcrop and core photographs. Each modality-specific encoder produces a fixed-dimensional embedding per observation.

These per-observation embeddings enter a permutation-invariant set encoder—critical because the order in which observations are provided carries no geological information. The set encoder applies a per-element multilayer perceptron, then self-attention layers that capture inter-observation dependencies (e.g., the relationship between two wells constrains the depositional environment more than either well alone), followed by aggregation (mean pooling or learned attention-weighted pooling) to produce a single fixed-dimensional representation of the entire context set.

From this aggregated representation, two parallel networks produce the distribution parameters:

$$\mu(C) = \textrm{MLP}_\mu(\textrm{aggregate}(C))$$

$$\sigma(C) = \textrm{softplus}(\textrm{MLP}_\sigma(\textrm{aggregate}(C)))$$

where the softplus activation ensures positivity of the variance. The output $(\mu, \sigma)$ defines a Gaussian distribution in the embedding space: $\mu$ is the expected position (the system's best estimate of the depositional environment given the sparse observations) and $\sigma$ encodes uncertainty (larger $\sigma$ corresponds to sparser data and less confident inference).

**Training objective.** The Neural Process is trained by the evidence lower bound (ELBO):

$$\mathcal{L}_{\textrm{NP}} = \mathbb{E}_C\left[\textrm{KL}\big(q(z \mid C) \;\lVert\; p(z)\big) + \mathbb{E}_z\left[-\log p(\textrm{targets} \mid z)\right]\right]$$

where $q(z \mid C)$ is the encoder distribution given the context, $p(z)$ is the prior (standard normal or learned), and $p(\textrm{targets} \mid z)$ is the decoder likelihood measuring retrieval accuracy. The KL term regularizes the encoder distribution toward the prior, preventing overfitting to any particular sparsity pattern; the reconstruction term ensures the encoding is informative for retrieval.

**Graceful degradation.** A key property of the Neural Process architecture is that uncertainty scales monotonically with sparsity. With many observations ($n > 10$), the encoder produces low $\sigma$ and confident embeddings. With few observations ($n = 2\text{--}5$), $\sigma$ increases appropriately. With a single observation ($n = 1$), uncertainty is high. With no observations ($n = 0$), the encoder returns the prior—an uninformative distribution reflecting complete ignorance. This graceful degradation is not merely desirable; it is a calibration requirement enforced by the Sākṣī validation layer (Section 10), with a target expected calibration error (ECE) below 0.1. If graceful degradation fails—if $\sigma$ is not monotonically related to sparsity—this is a revision trigger requiring architectural modification (ADR-003).

**Compatibility constraint.** The query encoder must map sparse observations into the *same* descriptor space as Pipeline A. This is the core coupling requirement introduced in Section 1.2. Concretely, when Pipeline B's encoder is given a *complete* analog as input (the limiting case of zero sparsity), its output $\mu$ should closely approximate Pipeline A's descriptor for that analog. This constraint is enforced during training by including complete analogs in the training set and penalizing divergence between the Pipeline A descriptor and the Pipeline B $\mu$ output. Without this compatibility constraint, the two pipelines could organize analogs in incompatible ways, rendering cross-pipeline retrieval meaningless.

### 9.3 The Hyperbolic Embedding Space

Depositional environments exhibit natural hierarchical structure: at the coarsest level, environments are classified as fluvial, aeolian, estuarine, deltaic, and so on; within fluvial, sub-classifications include meandering, braided, and anastomosing; within meandering, further distinctions arise between high-sinuosity and low-sinuosity variants, point-bar-dominated and counter-point-bar-dominated systems, and single-thread versus multi-thread configurations. This hierarchy is not merely a taxonomic convenience—it reflects genuine physical relationships, as environments within the same branch share generative processes and geometric constraints (Leopold & Wolman, 1957).

**Why Euclidean space fails.** Embedding hierarchical (tree-like) data in Euclidean space requires $O(n)$ dimensions to avoid distortion, where $n$ is the number of leaf categories. This is because Euclidean volume grows polynomially with radius, whereas tree structures grow exponentially with depth—there is a fundamental geometric mismatch. Hyperbolic space resolves this mismatch: volume in hyperbolic space grows *exponentially* with radius, naturally accommodating the exponential branching of hierarchical data in $O(\log n)$ dimensions (Nickel & Kiela, 2017).

**The Poincaré ball model.** We adopt the Poincaré ball model $\mathbb{B}^n = \lbrace x \in \mathbb{R}^n : \lVert x \rVert < 1 \rbrace$ equipped with the Riemannian metric:

$$ds^2 = \left(\frac{2}{1 - \lVert x \rVert^2}\right)^2 \lVert dx \rVert^2$$

This metric has two critical properties for our purposes. First, distances grow exponentially toward the boundary: as $\lVert x \rVert \to 1$, the conformal factor $\lambda_x = 2/(1 - \lVert x \rVert^2)$ diverges, so equal Euclidean displacements correspond to increasingly large hyperbolic distances near the boundary. This means the boundary region has "room" for exponentially many distinct points—exactly the capacity needed to represent a fine-grained taxonomy. Second, points near the origin represent general categories (large uncertainty, broad environment type) while points near the boundary represent specific sub-types (high confidence, narrow classification)—a geometric property that aligns naturally with the Neural Process encoder's uncertainty output.

**Key operations.** Three operations are essential for working with the Poincaré ball. The *exponential map* projects Euclidean vectors into hyperbolic space:

$$\textrm{exp}_x(v) = x \oplus \left(\tanh\left(\frac{\lambda_x \lVert v \rVert}{2}\right) \frac{v}{\lVert v \rVert}\right)$$

where $\oplus$ denotes Möbius addition and $\lambda_x = 2/(1 - \lVert x \rVert^2)$ is the conformal factor. The *logarithmic map* performs the inverse projection, mapping hyperbolic points back to the Euclidean tangent space for gradient computation. The *hyperbolic distance* between two points is:

$$d_{\mathbb{B}}(x, y) = 2 \cdot \textrm{arctanh}(\lVert -x \oplus y \rVert)$$

These operations enable standard neural network components (linear layers, attention mechanisms) to operate in hyperbolic space via the "project to tangent space, compute, project back" paradigm.

**Hierarchy-aware training.** The embedding is trained with a hyperbolic proxy-anchor loss that encodes the depositional hierarchy:

$$\mathcal{L} = \frac{1}{\lvert P \rvert} \sum_{p \in P} \log\left(1 + \sum_{a \in A_p} e^{-\alpha(d_{\mathbb{B}}(p, a) - \delta)}\right) + \frac{1}{\lvert N \rvert} \sum_{n \in N} \log\left(1 + \sum_{b \in B_n} e^{\alpha(d_{\mathbb{B}}(n, b) + \delta)}\right)$$

where $P$ and $N$ are positive and negative proxy sets, $\alpha$ is a scaling factor, and $\delta$ is a margin. This loss attracts same-class embeddings and repels different-class embeddings in hyperbolic distance. A hierarchy regularization term supplements the proxy-anchor loss:

$$\mathcal{L}_{\textrm{hier}} = \sum_c \lVert \mu_c - \mu_{\textrm{parent}(c)} \rVert$$

This term forces child-class centroids to remain near their parent-class centroids in the embedding, encoding the physical reality that braided fluvial systems are more similar to meandering fluvial systems than to aeolian dune fields. The expected embedding structure places general environment types (fluvial, aeolian, estuarine) as separated branches near the origin, with progressive specialization (meandering, braided, anastomosing) spreading outward toward the boundary, and fine-grained subtypes (high-sinuosity meandering, low-sinuosity meandering) occupying distinct regions near the boundary of the ball.

### 9.4 Perceiver IO: Handling Variable Modalities

The Neural Process query encoder (Section 9.2) handles variable numbers of observations within a single modality. But real geological queries present a more complex challenge: not only does the *number* of observations vary (3 wells versus 30 wells), but the *modalities present* vary (some queries include seismic, others do not), and the *spatial coverage* varies (clustered wells versus widely distributed wells). The basic cross-attention fusion module described in Section 6.3 assumes all three pathways are always present—an assumption that fails for sparse queries.

Perceiver IO (Jaegle et al., 2021) addresses this variable-input problem through a three-stage architecture. In the first stage, *cross-attention from input to latent*, a fixed-size latent array $L \in \mathbb{R}^{N_{\textrm{latent}} \times D_{\textrm{latent}}}$ attends to the variable-length, variable-modality input. The latent array serves as queries; the encoded inputs serve as keys and values. Because the latent array has fixed size regardless of input length, this stage absorbs arbitrary input complexity into a fixed-dimensional bottleneck. In the second stage, *self-attention*, multiple transformer blocks process the latent array, allowing information from different input elements to interact. In the third stage, *cross-attention from latent to output*, the processed latent array is queried by an output specification to produce the desired output format: a single embedding vector, distribution parameters $(\mu, \sigma)$, and per-modality attention weights.

The benefits for geological retrieval are substantial. *Fixed compute*: the computational cost depends on the latent array size, not the input size, so processing 3 wells costs the same as processing 30 wells. *Modality flexibility*: new data types (e.g., production data, gravity surveys) can be incorporated by adding a modality-specific encoder without modifying the core architecture. *Interpretability*: the cross-attention weights in the input-to-latent stage reveal which observations the system considers most informative for retrieval—a form of built-in explainability. Perceiver IO represents the full-vision architecture; for initial implementation, the simpler cross-attention fusion with the Neural Process encoder achieves most benefits at lower complexity.

### 9.5 Pathway Fusion and the Underdetermination Principle

The three feature-extraction pathways must be combined into a single representation that enters the embedding space. The fusion architecture uses cross-attention: each pathway's output is projected to a shared hidden dimension, the projected representations are stacked and processed by multi-head self-attention (allowing each pathway to attend to the others), and the attended outputs are mean-pooled and projected to the final embedding dimension. This architecture allows the pathways to modulate each other—for instance, if the classical and topological pathways agree on a braided classification but the learned pathway is uncertain, the fusion layer can upweight the agreeing pathways.

Fusion is governed by the convergence regularization loss introduced in Section 6.3:

$$L_{\textrm{conv}} = \sum_{i \lt j} \lVert f_i(x) - f_j(x) \rVert^2$$

This loss encourages pathway agreement while preserving independent signals. It does not force the pathways to produce identical outputs—they operate on different input representations and capture different aspects of geological structure—but it penalizes large disagreements, under the principle that genuine essence should be visible from multiple epistemic perspectives.

The fusion layer must respect a crucial epistemological principle articulated in the QCF's foundational design: the *underdetermination principle*. When sparse observations are genuinely consistent with multiple depositional environments, the epistemically correct behavior is to return a distribution reflecting this ambiguity—not a false point estimate. High uncertainty on ambiguous queries is the system working as intended; confident prediction on ambiguous queries is a calibration failure.

This principle has direct architectural consequences. The fusion layer must not "hallucinate" certainty by averaging over pathway disagreements. When the classical pathway suggests meandering (based on variogram range) but the topological pathway suggests braided (based on $H_1$ loop count), the correct output is a bimodal or high-variance distribution in the embedding space, not a compromise point estimate that corresponds to neither environment. The convergence regularization loss must be balanced against a calibration objective to ensure that genuine ambiguity produces appropriately uncertain outputs. The validation question is reframed: we do not ask "does the system always give the right answer?" but rather "does the system know what it doesn't know?"

### 9.6 Validation: The Sākṣī Layer

The system architecture described in Sections 9.1–9.5 requires a validation framework commensurate with its epistemic ambitions. The QCF employs a comprehensive validation philosophy—the Sākṣī ("witness") framework—in which ten independent tests act as witnesses to the representation's quality. Each witness validates a different aspect of the system, and no single witness is sufficient; confidence accrues through the convergence of independent evidence. The full Sākṣī validation framework, including the complete ten-witness table, the LOGO protocol, all four geology-specific adversarial tests, and the pre-committed Claim Survival Matrix, is developed in Section 10.

### 9.7 Open Design Questions

Several architectural decisions remain unresolved and constitute active research questions for subsequent chapters.

**Similarity under missing invariant dimensions.** When a sparse query lacks sufficient data to infer certain invariant dimensions (e.g., no seismic coverage prevents inference of large-scale connectivity), how should similarity be computed? Candidate approaches include marginalization over missing dimensions, imputation from the prior, constraint relaxation (ignoring missing dimensions), and uncertainty-weighted distance metrics that downweight dimensions with high $\sigma$. The choice has significant implications for retrieval behavior: marginalization treats missing information as maximally uncertain, while constraint relaxation treats it as irrelevant—different epistemic commitments with different retrieval consequences.

**Retrieval format.** What object does Pipeline B return? A single best analog (simplest but loses information about ambiguity), a top-$k$ ranked set (preserves some diversity but the choice of $k$ is arbitrary), an equivalence class (all analogs within a distance threshold, emphasizing structural similarity), or posterior weights over the entire repository (most principled but computationally expensive and difficult to communicate to end users). The underdetermination principle argues against single-analog retrieval for ambiguous queries, but the practical interface for geoscientists may require bounded output sets.

**Uncertainty propagation.** How does uncertainty from query sparsity propagate through the retrieval process to the final output? If the query embedding has high $\sigma$ in certain dimensions, the retrieved analogs should reflect this uncertainty—but the precise mechanism (Monte Carlo sampling from the query distribution, analytical uncertainty propagation, ensemble retrieval) remains to be specified.

**Adaptive metric selection.** Should the similarity metric adapt based on query completeness? A query with seismic coverage might warrant higher weight on connectivity features (inferable from seismic), while a wells-only query might warrant higher weight on vertical facies sequences. Adaptive weighting could improve retrieval relevance but introduces complexity and potential overfitting to query characteristics.

---

## 10. The Sākṣī Validation Framework

The system architecture of Section 9 describes *what* the retrieval system computes; this section describes *how we determine whether it works*. The Qualia Convergence Framework's approach to validation draws on a principle from Vedantic epistemology that addresses the deepest methodological challenge in machine learning evaluation: the circularity of validating a representation using the same features or assumptions used to construct it.

The framework defines ten independent tests—"witnesses"—each probing a different aspect of the representation's quality. It specifies the LOGO protocol for cross-generator invariance testing, a battery of four geology-specific adversarial tests designed for maximum severity, and a Claim Survival Matrix that pre-commits to interpretation criteria before any experiments are conducted. Together, these components operationalize the abstract evidence hierarchy of Section 8 into a concrete, pre-registered validation protocol.

### 10.1 The Witness Principle

The Vedantic tradition offers the concept of **Sākṣī** (साक्षी)—the "witness"—referring to the aspect of consciousness that observes without being entangled in what it observes. We adapt this concept methodologically:

> **The Sākṣī Principle**: A claim about essence must be validated by an observer (test) that is independent of the representation being evaluated.

This principle guards against circular validation—the most common and most insidious failure mode in representation learning evaluation. If we claim a representation captures essence, the test of that claim cannot depend on the same features, the same generators, or the same statistical properties used to construct the representation. Each test must constitute a genuinely independent epistemic perspective on the representation's quality.

The framework operationalizes this principle through ten independent tests, each validating a different aspect of the system. No single witness is sufficient for an essence claim. Confidence accrues through the *convergence* of independent evidence, following the same epistemological logic that justifies the three-pathway architecture itself (Section 6.3): when multiple independent perspectives agree, the shared signal is more likely to reflect genuine structure than artifact.

Critically, the interpretation criteria for all witnesses are fixed *before* any experiments are conducted. This pre-commitment discipline—borrowed from pre-registration practices in experimental psychology and clinical trials—prevents the post-hoc rationalization that vitiates much machine learning evaluation. One cannot adjust the definition of "good performance" after seeing the results.

### 10.2 The Ten Witnesses

Each of the ten witnesses validates a distinct aspect of the representation, drawing its evidentiary power from independence with respect to a specific component of the system:

| # | Witness | Sanskrit Gloss | What It Witnesses | Independence From | Target |
|---|---------|----------------|-------------------|-------------------|--------|
| 1 | Cluster Purity | *Varga-śuddhi* | Basic class separation in embedding space | — | ARI > 0.7 |
| 2 | Retrieval Precision | *Prāpti-sūkṣmatā* | Practical utility for analog retrieval | — | P@10 > 0.8 |
| 3 | LOGO Invariance | *Janaka-nirpekṣatā* | Generator invariance of representation | Training generators | Degradation < 20% |
| 4 | Transfer Prediction | *Saṅkramaṇa* | Generalization to held-out properties | Training features | $R^2$ > 0.5 |
| 5 | Expert Validation | *Vidvat-pratyaya* | Geological meaningfulness | All algorithmic features | Cohen's $\kappa$ > 0.6 |
| 6 | Pathway Convergence | *Mārga-saṅgama* | Agreement across epistemic perspectives | — | Disagreement < 0.2 |
| 7 | Adversarial Robustness | *Pratipakṣa-sthairya* | Resistance to deliberate spoofing | Superficial statistics | Attack success < 30% |
| 8 | Calibration | *Saṅkhyā-samya* | Uncertainty quantification accuracy | — | ECE < 0.1 |
| 9 | Mixture Handling | *Miśra-vicāra* | Appropriate response to ambiguous inputs | — | Correct high entropy on mixtures |
| 10 | Process Correlation | *Prakriyā-sambandha* | Physical interpretability of features | — | $r$ > 0.4 with physical parameters |

The witnesses form a complementary structure in which different tests probe different failure modes. Witnesses 1–2 establish baseline competence: if the representation cannot separate depositional classes in embedding space (Witness 1) or retrieve relevant analogs (Witness 2), no further validation is meaningful. Witness 3 (LOGO) tests the central claim of generator invariance. Witness 4 tests whether the representation generalizes beyond the properties used in its construction—a direct test of whether "essence" has been captured rather than surface statistics memorized. Witness 5 provides the only fully generator-independent assessment, relying on expert geological judgment that is independent of all algorithmic features.

Witnesses 6–8 address internal coherence and epistemic calibration. Pathway convergence (Witness 6) provides indirect evidence for Level 1 of the evidence hierarchy (Section 8): if three independent feature-extraction pathways agree, the shared signal is more likely to reflect genuine invariance than pathway-specific artifacts. Calibration (Witness 8) ensures that the system's stated uncertainty matches its actual accuracy—a prerequisite for the underdetermination principle (Section 9.5) to function as intended: a system that is confident when it should be uncertain is worse than useless. Adversarial robustness (Witness 7) provides direct Level 2 evidence by testing whether the representation survives deliberately constructed attacks designed to exploit superficial statistical regularities. The four adversarial tests are detailed in Section 10.4.

Witnesses 9–10 address edge cases that the other witnesses miss. Mixture handling (Witness 9) tests the system's response to genuinely ambiguous inputs—images that blend characteristics of multiple depositional environments. The correct response is high uncertainty (broad distribution in embedding space), not a confident but arbitrary classification. This witness directly validates the underdetermination principle. Process correlation (Witness 10) tests whether learned features correlate with known physical parameters of the generative process—sinuosity with meander amplitude, net-to-gross ratio with channel density, bar aspect ratio with braid index. A positive correlation provides evidence that the representation is capturing geologically meaningful structure rather than incidental statistical patterns.

### 10.3 The LOGO Protocol

The Leave-One-Generator-Out (LOGO) protocol is the third witness and the direct test of *interventional invariance*—a necessary (though not sufficient) condition for an essence claim grounded in causal representation learning (CRL). Under the Unifying CRL framework (ICLR 2025, arXiv:2409.02772), distinct generators are reinterpreted as *interventions* on a shared data-generating process, and LOGO tests which features remain invariant across that intervention space. The reframing changes what a LOGO pass *means*: it is no longer merely empirical cross-validation, but a test of whether learned features correspond to factors that are provably identifiable under the observed intervention structure, with identifiability strength determined by the *kind* of invariance the pool supports.

**Protocol.** The test requires a pool of generators $\lbrace G_1, G_2, \ldots, G_N \rbrace$ drawn from fundamentally different generative paradigms. For the current research program, the generator pool comprises:

- **$G_1$**: The principle-based generator (§2), producing fluvial, aeolian, and estuarine patterns from empirical formulas
- **$G_2$**: A GAN-based generator (if available), producing patterns via adversarial training on real geological images
- **$G_3$**: An MPS-based generator (SNESIM with varied training images), producing patterns via multiple-point statistical simulation
- **$G_4$**: A process-based generator (Flumy), producing patterns via physical process simulation

In CRL vocabulary, these four generators form the *environment partition*. Each environment corresponds to a particular intervention pattern on the shared data-generating process, and the invariance of candidate features across the partition is what the protocol tests. The use of fundamentally different generator types strengthens the invariance claim precisely because the environment partition is *informative*: the generators differ in mechanism, not merely in random seed.

For each held-out generator $G_h$, the model is trained on all remaining generators $\lbrace G_1, \ldots, G_N \rbrace \setminus \lbrace G_h \rbrace$ and evaluated on $G_h$. Three standard metrics are computed on the held-out generator: cluster purity (adjusted Rand index), retrieval precision (P@$K$), and transfer prediction ($R^2$ on held-out geological properties). A fourth metric applies specifically to the CG-VAE component of the learned pathway (§5.8, §6.5): Mean Correlation Coefficient (MCC) between CG-VAE's learned factors $\hat{z}$ and the held-out generator's ground-truth parameters. The degradation for each metric is:

$$\Delta_m = \frac{M_{\textrm{train}} - M_{\textrm{test}}}{M_{\textrm{train}}}$$

where $M_{\textrm{train}}$ is the metric evaluated on training generators and $M_{\textrm{test}}$ is the metric evaluated on the held-out generator.

**Invariance-to-identifiability taxonomy.** The Unifying CRL framework maps the *kind* of observed invariance to the *strength* of identifiability the observation supports:

| Observed invariance | Identifiability strength | Conditions |
|---|---|---|
| Distribution invariance (marginals match across environments) | Weak: features may be entangled with environment-specific transformations | Held across the pool |
| Mechanism invariance (generating function $f$ identical across environments) | Moderate: block-wise identifiability up to partition-level ambiguity | Mechanism shared; distributional differences via intervention on latents |
| Interventional sufficiency ($2 \lvert z_a \rvert + 1$ informative changes per factor subset $z_a$) | Strong: element-wise identifiability up to invertible transformation | Kong et al. (2025) Theorem 2; A1–A4 satisfied |

LOGO's protocol tests the first column; the identifiability strength it supports depends on which row's conditions the pool satisfies.

**Per-generator assumption audit.** Not every pool of distinct generators is informative in the CRL sense—some are *confounded* (share latent assumptions that induce shared artifacts). The generator pool must be audited:

| Generator | Invariance type contributed | CRL status | Rationale |
|---|---|---|---|
| $G_1$ (principle-based) | Mechanism invariance (empirical-formula mechanism) | Informative | Leopold-Wolman / Parker / Werner mechanisms are explicit and documented |
| $G_2$ (GAN) | Distribution invariance only | Partially confounded | Learned mechanism may encode unknown inductive biases |
| $G_3$ (MPS/SNESIM) | Distribution invariance (via training image) | Informative if training images differ from $G_1$'s implied distribution | Training-image choice determines informativeness |
| $G_4$ (Flumy process-based) | Mechanism invariance (physical process) | Informative, distinct mechanism from $G_1$ | Physical process mechanism, not empirical formulas |

The partition $\lbrace G_1, G_2, G_3, G_4 \rbrace$ is informative overall because $G_1$ and $G_4$ supply mechanism variation while $G_2$ and $G_3$ supply distributional variation. This is sufficient for Kong et al. (2025) Theorem 2 at the subspace-identifiability level, conditional on per-generator A4 (sparse mixing) verification.

**Interpretation thresholds (pre-committed).**

| Metric & threshold | Interpretation | Action |
|---|---|---|
| $\Delta < 0.2$ on all standard metrics for all $G_h$ | Generator-invariant | Witness 3 passed |
| $\Delta < 0.3$ on standard metrics for most $G_h$ | Mostly invariant | Investigate specific generator dependencies |
| $\Delta > 0.3$ on any standard metric for any $G_h$ | Generator-specific | Witness 3 failed; essence claim unsupported |
| MCC$_{\textrm{test}} \geq 0.85$ on held-out $G_h$ | Identifiability preserved under intervention | Level 1b maintained out-of-distribution |
| MCC$_{\textrm{test}} < 0.75$ on held-out $G_h$ | Identifiability fails OOD | Demotes CG-VAE factors for this generator's parameter subspace from Tier 1 |

The MCC thresholds follow the Kong et al. (2025) convention; they may be refined per experimental protocol but must be pre-committed before held-out evaluation.

**Why LOGO is more stringent than standard domain adaptation.** Standard domain adaptation (Ganin & Lempitsky, 2015) assumes partial overlap between source and target domains and employs explicit adaptation techniques (adversarial training, gradient reversal layers) to bridge the gap. LOGO assumes *complete exclusion* of the target generator, with no adaptation mechanism—pure generalization. In CRL terms, standard domain adaptation learns features that *transfer* across environments; LOGO demands features that are *invariant* across the interventional partition. An architecture that passes LOGO without any adaptation mechanism provides stronger evidence for generator-independent essence than one requiring adaptation to bridge generator gaps.

**Epistemic limitations, reframed within CRL's positive theorems.** The caveats that previously qualified LOGO as "necessary but not sufficient" are clarified, rather than undermined, by the Unifying CRL framework. Four structural limitations remain:

1. *Generator-family boundedness.* LOGO tests invariance within the pool, not invariance to geology in general. If all generators share physical assumptions (Leopold-Wolman relationships, process-based sediment transport equations), the pool collapses to a single intervention class and Kong et al.'s Theorem 2 cannot be invoked (Wimsatt, 1981). The audit above separates informative from confounded pools.
2. *Ahuja et al. (2023) impossibility, reinterpreted.* Ahuja et al. proved that invariance alone is insufficient to identify latent causal variables—a defeater for naive LOGO interpretation. Within the Unifying CRL framework, this result is not a defeater but a clarification: invariance recovers identifiability only when the partition is *interventional* (changes mechanism, not just distribution) and the counting condition is met ($2 \lvert z_a \rvert + 1$ informative changes for subspace $z_a$). LOGO supports Level 1b identifiability claims only under these conditions; outside them, it provides empirical Level 6 evidence without Level 1b support. This graded behavior is strictly stronger than the previous "necessary but not sufficient" framing.
3. *Environment diversity.* LOGO's epistemic strength depends on the genuine independence of generators in the pool—the requirement, in CRL vocabulary, that the environment partition admit nontrivial interventions rather than mere relabelings of the same process.
4. *Degrees-of-freedom risk.* With sufficient control over the generator space, LOGO can be made to trivially succeed—not because essence has been captured but because the pool has been (inadvertently) designed to agree on non-essential features. In CRL terms: over-aligning the pool removes the intervention structure LOGO exploits. The audit table is the first line of defense against this pathology.

**Evidence-hierarchy placement.** LOGO provides Level 2–6 evidence depending on which identifiability conditions the generator pool satisfies. When the environment partition is informative and the counting condition holds (taxonomy rows 2–3), LOGO supports Level 1b identifiability claims through the auxiliary-variable theorems (§5.8, §8.1). When only distribution invariance holds (row 1), LOGO provides Level 6 cross-generator validation without Level 1b support. This graded contribution is what §8.4's descriptor admissibility standards operationalize.

### 10.4 Adversarial Tests

The adversarial tests constitute Witness 7 (*Pratipakṣa-sthairya*, "steadiness against opposition") and provide Level 2 evidence in the evidence hierarchy. Following Mayo's (2018) severe testing framework, each test is designed to be *maximally capable of detecting failure* if the representation relies on the specific statistical property being attacked. A claim that survives a severe test—one that was highly likely to reveal the claim's falsity had it been false—carries substantially more evidential weight than a claim that survives only lenient testing. The four tests target different levels of statistical sophistication, ensuring that the representation must capture genuine structural information to survive the full battery.

#### 10.4.1 Variogram-Matched Topology Swap (*Sankhyā-māyā*)

The first adversarial test—"statistical illusion"—attacks the representation's reliance on two-point geostatistics. The test constructs matched pairs of images: one with meandering channel architecture and one with braided channel architecture, modified so that both images share *identical* variogram parameters (range, sill, nugget). By construction, classical geostatistical features cannot distinguish these pairs.

If the system correctly classifies the paired images using topological features alone, the $H_1$ pathway demonstrably captures structural information invisible to two-point statistics. This is the most direct test of the $H_1$ hypothesis (Section 6.6) and is developed into a full experimental protocol in Section 12.2. If the system fails—if variogram-matched pairs defeat the topological pathway—then the representation relies on statistical properties that the classical pathway already captures, and the topological pathway adds no unique discriminative value.

This test was introduced in the adversarial validation subsection (Section 6.9) and is formalized here as a component of the Sākṣī battery.

#### 10.4.2 Style Transfer Attack (*Rūpa-viparyaya*)

The second adversarial test—"form reversal"—attacks the representation's reliance on visual texture and appearance. A meandering channel pattern is subjected to neural style transfer (Gatys, Ecker, & Bethge, 2016) to acquire the visual texture of a braided system: rough, multi-threaded appearance with bar-like texture patterns. The structural connectivity of the channel network is preserved—the single sinuous channel remains topologically unchanged—but the surface appearance mimics a different depositional class.

If the system maintains correct classification despite the style transfer, the representation captures structural connectivity rather than surface texture. This is a direct test of whether the topological pathway's signal survives in the fused representation. Failure indicates that the learned pathway (DINOv2) dominates the classification decision and that the topological pathway's signal is suppressed in fusion—a diagnosis requiring rebalancing of the fusion weights or architectural revision of the cross-attention mechanism (Section 9.5).

#### 10.4.3 Channel Skeleton Permutation (*Nāḍī-krama-pariṇāma*)

The third adversarial test—"conduit rearrangement"—attacks the representation's sensitivity to connectivity structure. The channel skeleton of a geological image is extracted (via morphological thinning), and individual segments are permuted: reconnected in a different configuration while preserving the total channel length, the number of branch points, and the channel-body thickness distribution. The resulting image has identical first-order channel statistics but fundamentally different connectivity topology—the $H_1$ loop structure is disrupted because the permuted connections create different enclosed regions.

If the system detects the difference between the original and permuted images, the representation is genuinely sensitive to topological connectivity rather than aggregate channel statistics such as total channel area or branch density. This is a direct test of whether the $H_1$ persistence features computed in the topological pathway (Section 12.1) are capturing loop structure—as the stability theorem guarantees they should for bounded perturbations—rather than proxy statistics that happen to correlate with topology in the training distribution. Failure indicates that the vectorization step (persistence images or persistence landscapes) loses the connectivity information present in the raw persistence diagram, warranting investigation of alternative vectorization methods.

#### 10.4.4 Histogram Equalization (*Sāmya-karaṇa*)

The fourth adversarial test—"equalization"—attacks the representation's reliance on first-order intensity statistics. Images from different depositional classes are subjected to histogram equalization so that all images share identical first-order statistics (pixel intensity distribution). The spatial structure of each image is preserved, but any information derivable from the marginal distribution of pixel values is eliminated.

If the system still separates depositional classes after histogram equalization, the representation relies on spatial structure (higher-order statistics and topology) rather than intensity distribution. For binary facies images—the primary input to the topological pathway—this test is less discriminating than for continuous-valued data, since binary images already have trivial two-valued histograms. However, the test becomes important when the pipeline processes grayscale SEDT fields or continuous seismic amplitude data, where intensity histograms carry meaningful geological information that could serve as a confounding shortcut for classification.

#### 10.4.5 Factor-Conditioned Counterfactual Severity (*Hetu-vyabhicāra*)

The fifth adversarial test—"cause-specific deviation"—attacks the representation's *factor specificity*: the requirement that a pathway respond to the generative factor it claims to capture and remain largely unresponsive to unrelated factors. Where Tests 10.4.1–10.4.4 attack statistical shortcuts, this test attacks the correspondence claim of the supervised learned pathway. If CG-VAE claims that factor $\hat{z}_k$ identifies true generative parameter $\theta_k$ (per Kong et al. 2025 Theorem 2, §5.8), then counterfactual images produced by varying $\theta_k$ alone should elicit a response concentrated in $\hat{z}_k$ and substantially smaller responses in $\hat{z}_{j \neq k}$. The test is grounded in Chi et al. 2026 flow-matching image synthesis (arXiv:2602.05214)—demoted by the integration plan from standalone feature extractor to controllable counterfactual generator for severe testing of the CG-VAE identifiability claim.

**Protocol.** A flow-matching generative model is trained with $\theta$ as auxiliary supervision (Chi et al. 2026 Path B+ supervised variant), conditioned on the principle-based generator's paired $(I, \theta)$ data. For each factor $\theta_k$, the model synthesizes a counterfactual pair $(I_\theta, I_{\theta + \Delta e_k})$ in which only component $k$ is perturbed by a pre-committed $\Delta$. The response of each pathway is $R_k^{(p)} = \lVert f_p(I_{\theta + \Delta e_k}) - f_p(I_\theta) \rVert$, where $f_p$ is the descriptor map of pathway $p$ and $\lVert \cdot \rVert$ is the pathway-appropriate norm (Wasserstein-2 for PH persistence diagrams; $\ell_2$ for classical, DINOv2, and CG-VAE vectors). The *specificity ratio* is

$$S_k^{(p)} = \frac{R_k^{(p)}}{\max_{j \neq k} R_j^{(p)}}.$$

A high $S_k^{(p)}$ indicates that pathway $p$ responds to factor $k$ far more strongly than to any other factor—the desired behavior for a topologically structured or identified representation. A low ratio is diagnostic of either feature entanglement (DINOv2 residuals) or failed identifiability (CG-VAE factor misalignment).

**Pre-committed thresholds.**

| Pathway | Threshold | Rationale |
|---|---|---|
| PH ($H_1$) | $S_k^{(\textrm{PH})} \geq 3$ for connectivity factors | PH should respond sharply to loop-structure changes, mildly to texture factors |
| Classical variogram | $S_k^{(\textrm{var})} \geq 5$ for scale factors | Variograms isolate correlation scale cleanly |
| CG-VAE (identified) | $S_k^{(\textrm{CG-VAE})} \geq 2$ for factors in $z_a$ per A4 | Matches Kong et al. (2025) Theorem 2 expectations |
| DINOv2 (unsupervised) | *Control; no a priori threshold* | Entanglement expected; provides null baseline for the specificity metric |

The DINOv2 control is the critical comparator. If DINOv2 exhibits specificity comparable to CG-VAE, the identifiability theorem adds nothing beyond what unsupervised pretraining already achieves and the Level 1b claim is empirically weakened. If DINOv2 is entangled (low specificity) while CG-VAE is specific, the theorem's empirical consequences are confirmed.

**Interpretation.** Passing all pathway thresholds provides Level 2 severe evidence that the architecture's factor-level behavior matches its theoretical commitments. Failure on CG-VAE for factors that A4 includes in $z_a$ falsifies the identifiability claim for that subspace at Level 1b and triggers the iVAE fallback (§5.8); failure on PH or classical pathways for expected-specific factors triggers diagnostic investigation of the pathway's feature extractor (vectorization for PH, stationarity for variograms). The VQ-GAN dependency of Chi et al.'s flow-matching architecture (open question 6.2 in the integration plan) is resolved experimentally in §12.6: a raw-pixel diffusion variant serves as a fallback if a geological VQ-GAN is not trained.

**Composite adversarial assessment.** The five tests are designed to be applied as a battery, not individually. Passing all five provides strong evidence that the representation captures genuine structural information at multiple levels of abstraction: beyond two-point statistics (Test 1), beyond surface texture (Test 2), sensitive to connectivity (Test 3), beyond marginal distributions (Test 4), and factor-specific at the per-parameter level (Test 5). Tests 1–4 attack statistical shortcuts; Test 5 attacks the correspondence claim of the supervised learned pathway specifically, failing gracefully into the iVAE fallback (§5.8) when the identifiability claim for specific factor subspaces cannot be sustained. Failure on any single test identifies a specific vulnerability—a statistical shortcut the representation exploits or an identifiability claim that does not hold—and prescribes a targeted diagnostic: which pathway, which feature, which fusion weight, or which factor subspace to investigate.

### 10.5 The Claim Survival Matrix

The Claim Survival Matrix is the pre-committed interpretation framework that translates experimental outcomes into warranted epistemic claims. Its critical property is that all interpretation criteria are fixed *before* any experiments are conducted—a discipline that prevents the post-hoc rationalization that vitiates much of machine learning evaluation.

The matrix is structured around the multi-level evidence hierarchy of Section 8, recognizing that no single test is sufficient for an essence claim:

**Multi-Level Evidence Matrix.**

| Evidence Level | Test | Outcome | Interpretation |
|---|---|---|---|
| L1: Mathematical | Stability theorem applies to topological pathway | Proven | Topological features have formal invariance guarantee |
| L2: Severe Testing | Adversarial tests (§10.4) | Pass | Strong evidence; tests were designed to break claim |
| L2: Severe Testing | Adversarial tests (§10.4) | Fail | Specific vulnerability identified; revise or scope claim |
| L3: Info-Theoretic | $I(f(X); \theta \mid G)$ high | Confirmed | Representation encodes geological information |
| L3: Info-Theoretic | $I(f(X); G \mid \theta)$ high | Contaminated | Representation contains generator artifacts |
| L6: LOGO | $\Delta < 0.2$ all generators | Passed | Generator-invariant within pool (necessary, not sufficient) |
| L6: LOGO | $\Delta > 0.3$ any generator | Failed | Representation depends on generation method |
| L7: Expert | Cohen's $\kappa > 0.6$ | Aligned | Representation matches human geological judgment |

**Composite Claim Interpretations.** The evidentiary configuration determines the strength of the warranted essence claim:

| Configuration | Essence Claim | Epistemic Status |
|---|---|---|
| L1 + L2 pass + L3 confirmed + L6 pass + L7 pass | **Strong** | Multi-level convergence with mathematical, empirical, and human evidence |
| L1 + L2 pass + L6 pass, L7 marginal | **Moderate** | Mathematical and empirical support, but experts do not fully agree |
| L6 pass only (no L1, L2 marginal) | **Weak** | LOGO alone is necessary but not sufficient |
| L6 pass + L5 (real data) pass | **Strong** | Generator-independence confirmed empirically against field data |
| L6 fail, all others pass | **Not supported** | Generator-specific despite other evidence—fundamental problem |
| L1 applies + L2 pass + L6 fail | **Pathway-specific** | Topological pathway has mathematical warrant; other pathways do not |
| Calibration failure (any level) | **Misleading** | Overconfident predictions are worse than no predictions |

Three configurations deserve particular discussion. The "pathway-specific" configuration arises when LOGO fails for the fused representation but the topological pathway individually passes adversarial testing. This indicates that the learned or classical pathways introduce generator-specific artifacts that contaminate the fusion. The response is not to abandon the multi-pathway architecture but to restructure it—using the confidence hierarchy (Section 14.6) to downweight contaminated pathways while preserving the topological pathway's mathematical warrant.

The "misleading" configuration enforces an absolute constraint: a system that is confidently wrong is worse than one that is modestly accurate but well-calibrated. Calibration failure at any evidence level—even if all other witnesses pass—disqualifies the essence claim, because the system's uncertainty estimates cannot be trusted to guide retrieval decisions. This is the architectural consequence of the underdetermination principle (Section 9.5): a system that claims to "know what it doesn't know" must actually know what it doesn't know.

The "weak" configuration is the most epistemically dangerous, because it is the most likely to be misinterpreted. LOGO passing alone, without corroboration from mathematical invariance or severe testing, provides only necessary evidence. As argued in the evidence hierarchy (Section 8), passing LOGO across $N$ generators proves invariance within that generator family—it does not prove geological invariance in general (Wimsatt, 1981; Ahuja et al., 2023). The Claim Survival Matrix makes this limitation explicit and non-negotiable.

### 10.6 Integration with the Evidence Hierarchy

The ten witnesses do not operate in isolation; they provide evidence at specific levels of the evidence hierarchy established in Section 8. The mapping between witnesses and evidence levels reveals the complementary structure of the validation framework:

| Evidence Level | Contributing Witnesses | Evidence Type |
|---|---|---|
| Level 1: Mathematical Invariance | (Not a witness—provided by stability theorem directly) | Mathematical proof |
| Level 2: Severe Testing | Witness 7 (Adversarial Robustness) | Direct severe testing |
| Level 3: Information-Theoretic | (Not directly witnessed—requires mutual information computation) | Quantitative measurement |
| Level 4: Cross-Domain Validation | (Addressed in Section 11, not a numbered witness) | Domain transfer |
| Level 5: Real-Data Validation | Witness 4 (Transfer Prediction), Witness 5 (Expert Validation) | Empirical generalization |
| Level 6: LOGO | Witness 3 (LOGO Invariance) | Cross-generator validation |
| Level 7: Expert Agreement | Witness 5 (Expert Validation) | Human judgment |

Several witnesses contribute to the overall assessment without mapping to a single evidence level. Witnesses 1–2 (cluster purity and retrieval precision) are necessary preconditions—baseline competence that must be established before higher-level evidence is meaningful. Witness 6 (pathway convergence) provides supporting evidence for Level 1: if three independent feature-extraction pathways converge on the same structural characterization, the shared signal is more likely to reflect genuine mathematical invariance than pathway-specific artifacts. Witness 8 (calibration) is a cross-cutting constraint that applies to all evidence levels: evidence from an uncalibrated system is uninterpretable regardless of the level at which it is generated. Witness 5 (expert validation) intentionally appears at two levels: at Level 5, experts assess whether retrieved analogs match real geological data (empirical generalization); at Level 7, experts judge whether the system's similarity rankings agree with their professional intuition (human-AI alignment). These are distinct evaluative acts—one grounds the system in field reality, the other validates its usefulness to practitioners.

Witnesses 9–10 address dimensions of quality not captured by the evidence hierarchy's level structure. Mixture handling (Witness 9) validates the underdetermination principle—a design philosophy rather than an evidence claim. The correct response to a genuinely ambiguous image is not confident classification into one category but a broad distribution reflecting the ambiguity. Process correlation (Witness 10) provides interpretability evidence connecting the learned representation to known physical processes—important for expert adoption and scientific credibility but not reducible to a single evidence level.

The full Sākṣī framework thus provides the operational bridge between the abstract evidence hierarchy of Section 8 and the concrete experimental validation design of Section 12: the evidence hierarchy defines *what kinds of evidence matter and in what order of epistemic strength*, the ten witnesses define *what specific tests provide that evidence*, and the Claim Survival Matrix defines *how to interpret the results once obtained*. Together, they constitute a pre-committed validation protocol that is simultaneously rigorous (no post-hoc rationalization), comprehensive (multiple independent perspectives probing different failure modes), and epistemically honest (explicit about what each test can and cannot establish).

---

## 11. Persistent Homology Across Domains: Music, Neuroscience, and Mathematical Universality

### 11.1 The Argument from Domain Agnosticism

One of the most epistemically significant properties of persistent homology is its domain agnosticism: the same mathematical machinery—filtrations, Betti numbers, persistence diagrams, stability theorems—applies to *any* data that can be represented as a topological space. This property is directly relevant to the evidence hierarchy (Level 4, cross-domain validation) and to the broader philosophical claim about the nature of "essence."

If persistent homology captures meaningful invariant structure only in geology, the skeptic can argue that the invariance is an artifact of the geological domain—perhaps all geological generators share biases that topological methods exploit. But if the same framework captures meaningful invariant structure in music, neural data, and other domains built on entirely different physical processes, then the invariance must be a property of the *mathematics*, not of any particular domain.

### 11.2 TDA Applied to Musical Structure

Recent work has demonstrated that persistent homology captures meaningful structure in musical data:

**Topological Music Analysis (TMA).** Alcala-Alvarez and Padilla-Longoria (2022) developed a framework that converts musical scores to point clouds in Euclidean spaces, computes persistent homology of the resulting simplicial complexes, and uses topological features to compare stylistic properties across composers. They demonstrated that PH can distinguish J.S. Bach's Brandenburg Concertos from compositions by the Mexican composer Armando Luna based on topological fingerprints of their chord sequences—capturing structural differences that spectral analysis alone cannot detect.

**Topological Fingerprints via the Tonnetz.** Bergomi, Barate, and Di Fabio (2016) proposed interpreting the Tonnetz—a classical music-theoretic lattice relating notes, chords, and keys—as a two-dimensional simplicial complex. By applying persistent homology to this complex deformed by consonance values, they extract invariant harmonic features that characterize musical structure from both melodic and harmonic perspectives.

**Homological Persistence for Genre Classification.** Bergomi and Barate (2020) applied persistence to musical time series for genre classification, demonstrating that topological features capture structural patterns invisible to spectral analysis alone. Their approach describes time-varying systems through the evolution of geometric and topological properties, using persistent homology to track how these properties change over time.

### 11.3 TDA in Neuroscience and Consciousness Research

The application of persistent homology to neural data provides another line of cross-domain evidence:

**Brain Network Connectivity.** Giusti, Ghrist, and Bassett (2016) applied algebraic-topological tools, including persistent homology, to understand higher-order structure in neural data. They demonstrated that the topology of brain networks—patterns of connectivity between neural populations—contains information about cognitive function that pairwise correlation analysis misses, paralleling the geological case where variograms miss topological structure.

**Brain Dynamics and Individuality.** Wang, Xian, Chen, and Yan (2025) used persistent homology of fMRI time series from approximately 1,000 Human Connectome Project subjects to reveal individual differences in brain dynamics. Topological features exhibited high test-retest reliability and matched or exceeded the predictive performance of traditional features for higher-order cognitive domains, suggesting that PH captures aspects of brain organization invisible to standard methods.

**Gestalt Pattern Recognition.** Liu et al. (2021) applied persistent homology to EEG data during pattern recognition tasks and showed that the persistence entropy of brain signals evoked by ordered Gestalt images differs significantly from that evoked by random patterns—suggesting that human cognition itself has a topological signature.

### 11.4 The Cross-Domain Argument

The parallel between geological and musical applications of PH is more than analogical. In both domains, the fundamental research question is the same: *what features are invariant across different realizations of the same underlying structure?*

| Domain | PH Application | $H_0$ Captures | $H_1$ Captures |
|---|---|---|---|
| Geology | Channel network structure | Isolated channel bodies | Network loops (braiding) |
| Music | Harmonic structure | Separate tonal regions | Harmonic cycles (chord progressions returning to tonic) |
| Neuroscience | Brain connectivity | Isolated neural populations | Feedback loops in neural circuits |

In each case, $H_1$ captures *cyclic structure*—loops, feedback, recurrence—that is invisible to pairwise statistics. The persistence of these features across different realizations (different generators, different performances, different cognitive states) provides a measure of structural robustness that is domain-general.

If the same mathematical framework captures invariant structure in geology, music, *and* neural dynamics, then "essence" as defined by topological invariance may reflect something genuinely fundamental about pattern structure—not a domain-specific artifact that could be explained away by shared generator biases.

---

## 12. Proposed Experimental Validation

This section describes the experimental design for validating all three pathways of the QCF's feature extraction architecture—topological, classical, and learned—both independently and in combination. It answers the practical question: *given the mathematical framework above, how do we test whether each pathway works, where each fails, and whether the multi-pathway architecture outperforms any single pathway?* Sections 12.1–12.4 detail the topological pathway's validation (the most methodologically novel); Sections 12.5–12.6 develop corresponding experimental designs for the classical and learned pathways; and Section 12.7 addresses cross-pathway fusion and ablation.

### 12.1 The PH Computation Pipeline

The topological pathway follows a six-stage pipeline from raw geological image to fixed-dimensional feature vector:

**Stage 1: Binarization.** Input images are $256 \times 256$-pixel binary facies maps where channel bodies are encoded as 1 and floodplain as 0. These may be generated by process-based simulators (e.g., Flumy for meandering, BRAHMS for braided systems) or derived from real outcrop and seismic interpretations.

**Stage 2: Signed Euclidean Distance Transform.** The binary image is converted to a continuous scalar field via the SEDT: each pixel receives a signed distance to the nearest facies boundary (positive inside channels, negative inside floodplain). This transformation is critical—it provides a geologically meaningful filtration where thick channel cores receive high positive values and thin connections receive values near zero.

**Stage 3: Cubical Complex Construction.** Because the input is a regular pixel grid, we use cubical complexes rather than simplicial complexes (Vietoris–Rips or Čech). Cubical complexes respect the grid structure of image data, avoid the quadratic memory cost of point-cloud methods, and are computed efficiently by algorithms specialized for gridded input (Wagner, Chen, & Vucini, 2012).

**Stage 4: Persistent Homology Computation.** Using Giotto-TDA (Tauzin et al., 2021), we compute persistence in dimensions $H_0$ (connected components) and $H_1$ (loops) as the filtration threshold sweeps from the minimum to maximum SEDT value. The output is a pair of persistence diagrams: one for $H_0$, one for $H_1$.

**Stage 5: Interpretation.** In the $H_1$ diagram, each point $(b, d)$ represents a loop that appears at filtration value $b$ and disappears at value $d$. Long-lived points (far from the diagonal) correspond to robust loops formed by thick, well-connected channel bodies—the topological signature of braided networks. Short-lived points correspond to noise or thin connections.

**Stage 6: Vectorization.** Persistence diagrams are infinite-dimensional objects that cannot be directly input to machine learning models. We convert them to fixed-dimensional vectors via persistence images (Adams et al., 2017), persistence landscapes (Bubenik, 2015), or persistence entropy (Atienza, Gonzalez-Diaz, & Soriano-Trigueros, 2020), producing the 20–50-dimensional topological feature vectors that enter the fusion layer.

### 12.2 The $H_1$ Hypothesis Experiment

The central empirical test is a classification experiment designed to validate or falsify the $H_1$ hypothesis (§6.6).

**Image Generation.** We generate matched pairs of geological images using process-based simulators: one meandering (Flumy or equivalent), one braided (BRAHMS or equivalent). Critically, the generator parameters are adjusted so that both images in each pair share *identical* variogram parameters—range, sill, and nugget. This ensures that two-point geostatistical descriptors cannot distinguish them. The matched-variogram constraint is what makes this a *severe* test: it eliminates the classical pathway's discriminative power by construction.

**Prediction.** For each matched pair, the braided image should exhibit many persistent $H_1$ features—multiple long-lived loops corresponding to the interconnected channel network. The meandering image should exhibit few $H_1$ features—primarily short-lived loops or a single loop at scales corresponding to oxbow-lake geometry.

**Classification Protocol.** Using the vectorized $H_1$ persistence features alone (excluding $H_0$, classical, and learned features), we train a classifier (logistic regression or SVM with pre-committed hyperparameters) to distinguish braided from meandering images. Accuracy is evaluated on held-out matched pairs via 5-fold cross-validation.

**Pre-Committed Decision Thresholds (ADR-S04).** Following the Sākṣī validation philosophy of fixing interpretation criteria before data analysis:

- **> 70% accuracy**: $H_1$ hypothesis supported. TDA becomes a core pathway.
- **< 60% accuracy**: $H_1$ hypothesis not supported. TDA remains an ablation study. Investigate whether the SEDT filtration is suboptimal or multi-parameter persistence is required.
- **60–70% accuracy**: Inconclusive. Expand the test set, refine the filtration, and explore combining $H_0$ + $H_1$ features.

**Per-Pathway Comparison.** The classification is repeated using: (1) classical features only, (2) learned features only, (3) topological features only, and (4) all pathways fused. If the topological pathway outperforms the classical pathway specifically on matched-variogram pairs, this provides direct evidence for PH's unique discriminative contribution.

### 12.3 Validation Through the Evidence Hierarchy

The experimental results feed into the multi-level evidence hierarchy (Section 8):

**Level 1 (Mathematical Invariance).** The stability theorem guarantees $d_B(\textrm{Dgm}(f), \textrm{Dgm}(g)) \leq \lVert f - g \rVert_\infty$. We compute and report the actual perturbation bounds for our matched image pairs: given the SEDT difference between images, how large can the persistence diagram difference be? This provides a theoretical ceiling on expected variability.

**Level 2 (Severe Testing).** After the main classification experiment, we inject adversarial noise at filtration-critical scales—perturbations targeted at the SEDT values where $H_1$ features are born or die. If classification survives adversarial perturbation at these vulnerable scales, the topological features are demonstrably robust, not fragile.

**Level 4 (Cross-Domain Validation).** As a mathematical universality check, the same mathematical machinery (cubical PH computation to vectorization) is applied to appropriately preprocessed musical score data and neural connectivity matrices. If this machinery distinguishes structurally different objects across domains, the argument that PH captures genuine structural invariants—not domain-specific artifacts—is strengthened.

**Levels 5–7 (Empirical Validation).** Real-data validation with field analogs (Level 5), cross-generator protocols with multiple independent simulators (Level 6), and expert geological assessment of retrieval results (Level 7) provide necessary empirical grounding for the mathematical and adversarial evidence above.

### 12.4 What Success and Failure Look Like

**If $H_1$ > 70% on matched-variogram pairs**: PH is validated as a core pathway. Mathematical invariance (the stability theorem) combined with empirical discrimination under statistical degeneracy provides a two-level warrant—the strongest evidence structure within the hierarchy.

**If $H_1$ < 60%**: PH remains an ablation study. Investigation priorities: (1) whether the SEDT filtration is optimal for channel discrimination, (2) whether multi-parameter persistence (incorporating both SEDT and a scale parameter) would capture information that single-parameter PH misses, and (3) whether $H_0$ features contain complementary discriminative power.

**If $H_1$ between 60–70%**: Inconclusive. Expand the test image set, refine the filtration function, and explore combining $H_0$ + $H_1$ features before concluding.

### 12.5 Classical Pathway Experimental Design

The classical pathway requires experimental validation distinct from the topological pathway's. Where PH has a mathematical stability theorem and needs only to demonstrate *relevance*, classical features have established relevance (decades of industry use) but lack formal invariance guarantees. The experiments below test the classical pathway's reliability, quantify its structural boundary, and establish its specific contribution to the multi-pathway architecture.

**Experiment C1: Variogram Parameter Stability Across Generators.** Generate matched geological images from two or more independent generators (Flumy and BRAHMS, or equivalent) with identical target parameters (sinuosity, channel width, net-to-gross ratio). Compute directional variograms for each image and extract the three canonical parameters (nugget, sill, range) from model fits. The test question: *do images representing the same depositional environment but generated by different simulators produce similar variogram parameters?*

Unlike PH's stability theorem, there is no mathematical guarantee that classical features are generator-invariant. The experiment provides empirical bounds. For each variogram parameter $\theta$, compute the coefficient of variation $\textrm{CV}_\theta$ across generators for matched depositional targets. A low $\textrm{CV}$ (< 0.15) indicates that the parameter is generator-robust; a high $\textrm{CV}$ (> 0.30) indicates generator sensitivity, demoting the parameter from Tier 3 to Tier 4 in the confidence hierarchy.

**Experiment C2: Anisotropy Detection Under Rotation and Noise.** Generate a set of geological images with known depositional orientation (channel axis aligned at controlled angles). Compute the estimated anisotropy principal axis from directional variograms. Add progressively stronger noise (random pixel flips at rates 1%, 5%, 10%, 20%) and re-estimate the anisotropy axis. The test question: *how robust is anisotropy estimation to observational noise?*

This experiment provides an empirical analog to PH's stability bound. Report the maximum noise level at which the anisotropy axis estimate remains within 10° of the true value. If this empirical robustness is high, anisotropy features gain support as reliable index entries; if it degrades quickly, the pathway's contribution to Pipeline A must be appropriately uncertainty-weighted.

**Experiment C3: Classical Features as a Negative Control for Variogram-Matched Pairs.** The variogram-matched pairs experiment of §12.2 tests whether PH *can* discriminate where classical features cannot. The converse test is equally important: train a classifier using *only* classical features on the same matched pairs. The expected result is chance-level accuracy ($\approx$50%), confirming that the variogram-matching protocol successfully eliminates classical discriminative power. If classical features achieve significantly above-chance accuracy on matched pairs, the matching protocol is flawed—the variograms are not sufficiently matched—and the PH experiment's evidential value is compromised.

This negative control is essential for the per-pathway comparison of §12.2: PH's discriminative power on matched pairs is meaningful *only if* the classical pathway demonstrably fails on the same pairs. The two experiments must be run jointly.

**Experiment C4: Kriging vs. Neural Process Baseline.** Using the same analog database, generate sparse observation scenarios (3, 5, 10, and 20 randomly placed wells per analog). For each scenario, compare kriging prediction accuracy (using the variogram estimated from sparse data) against the Neural Process query encoder's prediction accuracy. Evaluate using the compatibility constraint: for each analog, how closely does the sparse-data prediction match the complete-image descriptor?

The pre-committed expectation is that kriging should outperform the NP under ideal conditions (stationary fields, sufficient data for variogram estimation) and the NP should outperform kriging under non-ideal conditions (non-stationary fields, very sparse data). If the NP fails to match kriging even under ideal conditions, the query encoder requires architectural revision; if kriging matches the NP under all conditions, the NP adds no value over classical inference.

### 12.6 Learned Pathway Experimental Design

The learned pathway (DINOv2) requires validation that addresses its distinctive epistemic risks: distribution dependence, opacity, and potential generator-artifact encoding. The experiments below test whether DINOv2 features capture geological structure or merely visual patterns, and quantify the pathway's contribution to the multi-pathway architecture.

**Experiment L1: Leave-One-Generator-Out (LOGO) Protocol.** Train a linear classifier on frozen DINOv2 features to predict depositional environment (braided, meandering, anastomosing, etc.), using images from $N - 1$ generators. Evaluate on the held-out generator. Repeat for each generator. The LOGO accuracy is the mean classification accuracy across held-out generators.

This protocol, formalized as Sākṣī Witness 3 (§10.3), directly tests generator invariance. Pre-committed thresholds:

| LOGO Accuracy | Interpretation | Confidence Tier |
|---|---|---|
| > 80% | Features are generator-invariant | Tier 3 (empirically invariant) |
| 60–80% | Features partially generalize | Tier 3–4 (conditional) |
| < 60% | Features are generator-dependent | Tier 4 (uncertain) |

The LOGO protocol is applied independently to each pathway, providing a direct per-pathway comparison of generator invariance. PH features, backed by the stability theorem, are expected to show minimal LOGO degradation. Classical features, if variogram parameters are generator-robust (Experiment C1), should also show moderate LOGO stability. If DINOv2 shows substantially lower LOGO accuracy than PH, this quantifies the epistemic cost of relying on learned features without formal invariance guarantees.

**Experiment L2: Hierarchical Linear Probing.** Train linear probes at three hierarchical levels of geological classification:

1. *Coarse*: Environment type (fluvial vs. aeolian vs. estuarine vs. deltaic)
2. *Medium*: Sub-environment (braided vs. meandering vs. anastomosing within fluvial)
3. *Fine*: Parametric variation (high-sinuosity vs. low-sinuosity meandering)

The scene gist hypothesis (§5.6) predicts that DINOv2 accuracy should decrease monotonically from coarse to fine classification—holistic recognition is strongest for broad categories and weakest for fine parametric distinctions. If accuracy at the fine level is comparable to the coarse level, the representation encodes more detailed geological information than the gist hypothesis predicts—a welcome finding that would elevate the pathway's evidential contribution.

**Experiment L3: Attention Map Analysis.** For a curated set of geological images (5 per environment type, selected to represent clear examples), extract the spatial attention maps from each of DINOv2's 12 attention heads at the final transformer layer. Overlay the attention maps on the original images and compare against expert-annotated regions of geological interest (channel boundaries, bar forms, confluence points, facies transitions).

Quantify alignment using the Intersection-over-Union (IoU) metric between attention-highlighted regions and expert annotations. High IoU (> 0.5) indicates that DINOv2 attends to geologically meaningful image regions; low IoU indicates that the model's feature extraction is driven by visual patterns that do not correspond to geological structure. This experiment does not validate the features themselves but provides interpretability evidence—insight into *why* DINOv2's features may be geologically discriminative.

**Experiment L4: Adversarial Robustness Assessment.** Apply Projected Gradient Descent (PGD; Madry et al., 2018) attacks to test the learned pathway's robustness. For each image, construct adversarial perturbations $\delta$ with $\lVert \delta \rVert_\infty \leq \epsilon$ for $\epsilon \in \lbrace 0.01, 0.05, 0.10 \rbrace$ (as a fraction of the input range) and measure the resulting change in the 768-dimensional DINOv2 representation.

Report two metrics: (1) the maximum representation shift $\max_\delta \lVert f(x + \delta) - f(x) \rVert_2 / \lVert f(x) \rVert_2$ (relative representational instability), and (2) the classification flip rate (fraction of images whose predicted depositional environment changes under perturbation). These metrics provide an empirical upper bound on the learned pathway's sensitivity to input perturbation—the empirical analog of PH's stability theorem. If representational instability is low (< 0.1 relative shift at $\epsilon = 0.05$), DINOv2 features are empirically robust; if high, the pathway's contribution to the confidence hierarchy must be further discounted.

### 12.7 Cross-Pathway Fusion and Ablation Experiments

The multi-pathway architecture's value proposition is that the three pathways contribute complementary information. The experiments below test this claim directly through systematic ablation and convergence analysis.

**Experiment F1: Pathway Ablation.** Train the full retrieval system in seven configurations:

| Configuration | Pathways Included | What It Tests |
|---|---|---|
| PH only | Topological | Topological features alone |
| Classical only | Classical | Variogram-based features alone |
| DINOv2 only | Learned | Learned features alone |
| PH + Classical | Topological, Classical | Structured pathways without learned |
| PH + DINOv2 | Topological, Learned | Theorem-backed + gestalt without classical |
| Classical + DINOv2 | Classical, Learned | What is lost without topological invariants |
| All three | Topological, Classical, Learned | Full architecture |

For each configuration, evaluate retrieval accuracy on three tasks: (1) depositional environment classification (coarse), (2) sub-environment discrimination on standard pairs, and (3) sub-environment discrimination on variogram-matched pairs. The last task is critical: it is the only condition where the classical pathway is expected to contribute nothing, isolating the topological and learned pathways' joint contribution.

Pre-committed expectations: the full three-pathway system should outperform any single pathway on all tasks. PH alone should outperform Classical alone on variogram-matched pairs. DINOv2 alone should outperform PH alone on coarse classification (where gestalt recognition suffices). If any single pathway matches the full system on all tasks, the other two are redundant—a finding that would fundamentally challenge the multi-pathway architecture's rationale.

**Experiment F2: Convergence Analysis.** For each image in the test set, compute the pairwise agreement between pathways using Centered Kernel Alignment (CKA; §14.6). Classify each image into one of four convergence states:

1. *Full convergence*: All three pathways agree (CKA > 0.7 for all pairs)
2. *Partial convergence*: Two pathways agree, third disagrees
3. *Full disagreement*: No pair exceeds CKA > 0.5
4. *Degenerate*: One or more pathways produce uninformative features

Analyze the correlation between convergence state and geological properties. The convergence regularization loss (§6.3) encourages agreement, but perfect agreement is undesirable—it would mean the pathways are redundant. The expected pattern is that structurally unambiguous images (clearly braided, clearly meandering) show full convergence, while transitional or ambiguous images (low-sinuosity systems near the braided-meandering threshold) show partial convergence or disagreement. If full convergence dominates even for ambiguous images, the convergence loss may be over-regularizing; if disagreement dominates even for clear images, the pathways may not be encoding consistent information.

**Experiment F3: Evidence Hierarchy Population.** The multi-level evidence hierarchy (§8) defines seven levels of evidence. The experimental results from §12.1–12.6 and F1–F2 collectively populate these levels:

| Evidence Level | Experiment(s) | What It Establishes |
|---|---|---|
| L1: Mathematical Invariance | Stability theorem (§3.6) | PH features are provably bounded |
| L2: Severe Testing | PH adversarial perturbation (§12.3) | PH survives targeted attacks |
| L3: Information-Theoretic | SLIDE decomposition (§14.6) + mutual information | Cross-pathway information content |
| L4: Cross-Domain | PH across domains (§11) | Mathematical universality |
| L5: Real-Data | Field analog comparison | Ground truth validation |
| L6: Cross-Generator | LOGO per pathway (Exp. L1, Exp. C1, §10.3 for PH) | Generator invariance per pathway |
| L7: Expert Agreement | Expert survey of retrieval results | Human-AI alignment |

This mapping ensures that the experimental program is *complete* with respect to the evidence hierarchy—every level has at least one corresponding experiment—and *traceable*—each experimental result feeds into a specific level of the hierarchy, allowing systematic assessment of which levels are satisfied and which remain open.

---

## 13. Open Questions and the Path Forward

### 13.1 The Central Open Question: Philosophical Robustness of Invariance

The restructured evidence hierarchy (Section 8) does not eliminate the fundamental tension between operational invariance and genuine essence. It acknowledges and addresses the tension more honestly. But several questions remain:

**How do we verify generator independence?** The independence condition (Wimsatt, 1981) is necessary for robust inference, but verifying that generators are genuinely independent—rather than merely superficially different—is itself a non-trivial problem. What constitutes "sufficient diversity" for cross-generator validation to be informative? This question connects to the broader epistemological problem of induction: how can any finite set of tests provide evidence for a universal claim?

**Can causal structure replace empirical invariance?** Instead of testing invariance across generators, one could attempt to identify the *causal structure* that generates geological patterns. If a representation can be shown to capture features that are *causes* of (not merely correlated with) the geological outcome, then invariance follows from the causal graph rather than from empirical testing. This would be the strongest possible evidence—but it requires knowing the causal graph, which is itself a major research challenge.

**What is the relationship between mathematical and geological invariance?** The stability theorem proves that PH features are invariant under bounded perturbations. But does mathematical invariance imply geological invariance? Could there be geological differences that produce unbounded perturbations in the input function, violating the stability theorem's premise? Understanding the relationship between the mathematical bound and the geological reality is essential.

### 13.2 Multi-Parameter Persistence

Standard persistent homology uses a single filtration parameter $\epsilon$. Geological images exhibit structure at multiple scales simultaneously—bar spacing at one scale, channel sinuosity at another, floodplain texture at a third. Multi-parameter persistence (Cerri et al., 2013) would track how topological features at different scales interact—literally the "objects of different dimensions crafting each other" that motivates the research. However, the vectorization problem for multi-parameter persistence remains an active area of research, and computational costs are substantially higher.

### 13.3 Topological Dictionary Learning

An ambitious extension would learn a set of *topological atoms*—canonical persistence diagrams—such that any geological image's persistence diagram decomposes as a sparse combination of these atoms. Each atom would represent a canonical topological primitive ("sinuous channel with one oxbow," "braided network with 3–5 through-going connections"), and the correspondence between generator parameters and these atoms would close the loop between generative processes, topological representations, and the essence claim.

### 13.4 Information-Theoretic Quantification

The information-theoretic measures proposed in the evidence hierarchy (Level 3) have not yet been implemented. Estimating conditional mutual information from finite samples is itself a challenging statistical problem, particularly in high-dimensional representation spaces. The use of variational bounds (MINE; Belghazi et al., 2018) or other neural estimators is a promising but untested direction for this framework.

### 13.5 Cross-Domain Validation as Evidence

The most philosophically compelling line of future work may be systematic cross-domain validation: applying the *identical* PH pipeline used for geological images to musical scores, neural recordings, and other structured data. If the same pipeline that distinguishes braided from meandering channels also distinguishes musical genres or neural states, the argument for mathematical universality becomes very strong. This would provide Level 4 evidence that is not merely "consistent with" but "predicted by" the mathematical theory.

---

## 14. Extensions: Dynamic Essence, Confidence Hierarchy, and Uncertainty

The preceding sections developed persistent homology as the mathematical backbone for *structural* essence—multiscale invariance of spatial pattern independent of generator artifacts. This section extends the framework in three directions that emerged from the research program's natural evolution. First, we generalize essence from static structure to dynamic response, asking whether analogs sharing structural essence also share the same *response* to stimulation (§14.1–14.5). Second, we develop a confidence hierarchy that exploits the epistemic asymmetry between theorem-backed PH features and empirically derived features from other pathways (§14.6). Third, we show how feature residuals—the components of learned representations *not* captured by PH—can be decomposed into meaningful uncertainty estimates that inform retrieval (§14.7). Section 14.8 synthesizes these extensions into concrete implications for the two-pipeline architecture.

### 14.1 From Structural Essence to Response Essence

Section 1.3 defined essence as "multiscale structural invariance independent of generator artifacts" and explicitly deferred response invariance to future work. This deferral was necessary—structural characterization must precede dynamic analysis—but it leaves a critical gap. The ultimate purpose of analog retrieval is not to find analogs that *look like* a target reservoir but to find analogs that *behave like* it: analogs whose response to fluid injection, pressure depletion, or natural loading faithfully predicts the target's response.

We therefore propose extending the essence concept to encompass *response essence*:

> **Response essence** is the equivalence class of geological configurations that produce topologically equivalent dynamic response under a specified class of stimuli.

Two geological configurations share response essence if their trajectories through state space, when subjected to the same forcing, trace out attractors with the same topological structure—even if the trajectories differ in geometric detail. This definition deliberately mirrors the structural essence definition: where structural essence abstracts away generator artifacts, response essence abstracts away transient dynamics to focus on the invariant attractor geometry.

The relationship between structural and response essence is the central question: *does shared structural essence imply shared response essence?* If yes, then Pipeline A's structural index already organizes analogs by dynamic relevance. If no—if structurally equivalent formations can produce topologically distinct responses—then the retrieval system requires additional descriptors capturing dynamic properties. Both outcomes are scientifically valuable; the question is empirical.

### 14.2 Persistent Homology of Dynamical Systems

Applying PH to dynamical systems requires reframing geological response as a trajectory in state space. A reservoir under stimulation evolves according to a state-space model:

$$x_{k+1} = f(x_k, u_k) + w_k$$

where $x_k \in \mathbb{R}^n$ is the reservoir state (pressure, saturation, and stress fields discretized over a grid), $u_k$ represents external forcing (injection rates, boundary conditions), $f$ encodes the physics of multiphase flow through porous media, and $w_k$ captures model uncertainty. Different geological configurations—different permeability fields, facies architectures, fault networks—correspond to different functions $f$, producing different trajectories through the same state space under identical forcing.

This is not merely an analogy. Classical reservoir simulation *is* state-space dynamical systems modeling. He et al. (2023) demonstrated that reservoir dynamics admit Koopman linearization—a transformation into an infinite-dimensional linear system where the nonlinear dynamics become linear operators on observable functions. This linearization enables spectral analysis of reservoir behavior, connecting the geometric complexity of the attractor to eigenvalues of the Koopman operator.

**Takens embedding and topological analysis.** When the full state vector $x_k$ is unobservable—as it invariably is in field settings where only sparse well measurements are available—Takens' embedding theorem (Takens, 1981) guarantees that the attractor topology can be reconstructed from a single time series of sufficient length and embedding dimension. Venkataraman et al. (2016) applied PH to Takens-reconstructed attractors for dynamical system classification, demonstrating that persistence diagrams of the reconstructed attractor reliably distinguish different dynamical regimes. Das et al. (2024) extended this approach to distinguish periodic from chaotic regimes using PH of the reconstructed phase portrait, and Shah et al. (2025) demonstrated that PH can detect bifurcation routes to chaos—transitions between qualitatively different dynamical regimes that are invisible to pointwise statistics. Moon et al. (2019) provided direct evidence for the structural-to-response link: persistent homology features of pore structure predict macroscopic flow properties, demonstrating that topological invariants of static geometry carry information about dynamic behavior.

The pipeline for geological application would be:

1. Generate production time series (e.g., wellhead pressure, water cut) from reservoir simulation under controlled forcing
2. Construct Takens embedding of the time series with appropriate delay and dimension
3. Compute PH of the embedded point cloud, yielding persistence diagrams that characterize the attractor topology
4. Compare attractor topologies across geological configurations to test whether structural essence predicts response essence

**Double persistent homology.** Kramar et al. (2016) introduced a particularly relevant technique: computing PH not of the raw attractor but of *snapshots* of a spatiotemporal field, then tracking how the persistence diagrams themselves evolve over time. Applied to Rayleigh-Benard convection, this "double PH" approach captured transitions between flow regimes that single-snapshot PH missed. For geological systems, double PH could track how the topological structure of a pressure or saturation field evolves during production—providing a topological fingerprint of the dynamic response that goes beyond single-time-step analysis.

### 14.3 Defining Response Essence via Basin-of-Attraction Topology

The attractor perspective suggests a precise mathematical definition of response essence. A dynamical system's long-term behavior is organized by its *attractors*—stable equilibria, limit cycles, strange attractors—and the *basins of attraction* that partition state space into regions flowing toward each attractor. Two dynamical systems have the same qualitative behavior if and only if their basin-of-attraction structures are topologically equivalent.

**Morse-Smale decomposition.** For gradient-like dynamical systems (which include many dissipative physical systems), the Morse-Smale decomposition (Conley, 1978) provides a rigorous partition of state space into cells, each associated with a critical point (equilibrium) and its stable/unstable manifolds. The combinatorial structure of this decomposition—which critical points exist, how their basins connect—is a topological invariant of the dynamical system.

We propose:

> **Response essence (formal)**: Two geological configurations $G_1$ and $G_2$ share response essence with respect to stimulus class $\mathcal{U}$ if the Morse-Smale decompositions of their respective dynamical systems $f_{G_1}$ and $f_{G_2}$ under stimuli $u \in \mathcal{U}$ are combinatorially equivalent.

This definition has several attractive properties. It is mathematically precise, admitting formal comparison. It abstracts away metric details (how fast trajectories approach attractors) while preserving qualitative behavior (which attractors exist and how state space is organized around them). And it connects directly to PH: Lipinski et al. (2023) developed persistent Conley-Morse graphs that track how the Morse decomposition changes under parameter variation, providing a persistence-theoretic tool for comparing basin structures.

**Practical computation.** Computing full Morse-Smale decompositions for high-dimensional reservoir systems is currently intractable. However, Dey et al. (2020) developed computational methods for approximating Morse decompositions from sampled trajectories, and dimension reduction via the Koopman operator (He et al., 2023) may make the problem tractable in a reduced state space. This remains a research challenge, but the mathematical framework is well-defined.

### 14.4 Formation Dynamics as Attractor Systems

The dynamical systems perspective extends beyond reservoir response to the *formation* of geological structures themselves. The geological record is not merely a static pattern—it is a frozen signature of dynamical processes operating over geological time. This observation suggests that structural essence and response essence may be connected at a deeper level than the retrieval problem requires.

**Meandering rivers as self-organized criticality.** Stolum (1996) demonstrated that river meandering exhibits self-organized criticality: the channel evolves toward a critical state where meander cutoffs maintain a characteristic sinuosity. Frascati and Lanzoni (2009) formalized this further, showing that meandering dynamics can be modeled as attractor systems in which channel geometry converges to characteristic planform distributions. The attractor of this system is not a fixed channel geometry but a *statistical steady state*—a distribution over channel configurations. Phillips (1992, 2003, 2006, 2011) developed this perspective systematically for geomorphological systems, showing that landscape evolution frequently exhibits nonlinear dynamics including bifurcations, chaos, and self-organization.

**Channel pattern bifurcation.** Leopold and Wolman (1957) identified the now-classical threshold between braided and meandering channel patterns as a function of slope and discharge. Kleinhans and van den Berg (2011) extended this to include sediment transport, revealing a richer bifurcation structure. In dynamical systems terms, this threshold is a *bifurcation boundary*: the same governing equations produce qualitatively different attractors (braided vs. meandering) depending on parameter values. The PH computation of §12.1—distinguishing braided from meandering via $H_1$ features—is therefore detecting *which side of a dynamical bifurcation* the formation process occupied.

**Delta lobe switching as limit cycles.** Fluvial delta systems exhibit quasi-periodic lobe switching, where the active depositional lobe shifts position over millennial timescales. This behavior is naturally modeled as a limit cycle in the dynamical system governing sediment routing and channel avulsion. The topological signature of a limit cycle—a persistent $H_1$ feature in the attractor's phase portrait—connects directly to the PH machinery developed in §14.2.

**Equifinality and the limits of structural inference.** A complicating factor is *equifinality*—the well-documented phenomenon in geomorphology whereby fundamentally different processes can produce landforms with similar structural signatures (Phillips, 2006). Two depositional environments governed by different dynamical systems could, in principle, converge on similar topological structures through different attractor mechanisms. Equifinality implies that the mapping from formation dynamics to structural PH may be many-to-one: identical $H_1$ signatures could arise from different formation processes. This does not invalidate the structural-to-response link, but it constrains the inference direction—shared structural PH is *necessary* but may not be *sufficient* for shared response essence.

These observations suggest a provocative hypothesis: *structural PH of the geological record encodes information about the attractor of the formation process*. If true, structural essence and response essence are not independent properties but reflections of the same underlying dynamical organization—one frozen in the rock, the other activated by stimulation. Testing this hypothesis requires comparing structural PH features of geological images with response PH features of simulated dynamics on those same images, a direction for future experimental work.

### 14.5 State Space Models: Classical and Modern

The state-space formulation of §14.2 connects to two distinct but converging research traditions that are relevant to the retrieval architecture.

**Classical state space models.** Reservoir simulation has always been a state-space problem: discretize the governing PDEs (Darcy's law, mass conservation, constitutive relations) on a grid, advance the state vector through time. Jansen et al. (2009) made this connection explicit, framing reservoir management as optimal control of a state-space system. The Koopman linearization of He et al. (2023) does not change the physics but provides a new mathematical lens—one that enables spectral decomposition of reservoir dynamics and direct connection to the attractor topology discussed in §14.3.

**Modern ML state space models.** A parallel development in machine learning has produced architectures—S4, Mamba, and their variants—that process sequential data through learned state-space representations. These models learn compact state representations that capture long-range dependencies in time series. Early geoscience applications (2024–2025) have applied these architectures to pore pressure prediction, well log interpretation, and seismic processing, demonstrating that learned state spaces can capture geological dynamics.

**Convergence opportunity.** The two traditions meet at a natural interface: classical SSMs provide the physical state space whose attractor topology defines response essence; modern ML SSMs provide efficient learned approximations that could make attractor topology computation tractable for high-dimensional systems. A hybrid approach—using physics-informed ML state-space models to approximate the Koopman operator, then computing PH of the resulting attractor—could bridge the computational gap between the mathematical framework of §14.3 and practical implementation.

### 14.6 The Confidence Hierarchy: PH and CG-VAE as Epistemic Anchors

The multi-pathway architecture of the Qualia Convergence Framework (§6) extracts features through three independent pathways: topological (PH), classical (geostatistical), and learned (DINOv2 + CG-VAE). These pathways produce features of fundamentally *different epistemic status*—a distinction that the framework exploits through a tiered confidence hierarchy. Following the §8 evidence-hierarchy extension, the confidence hierarchy anchors on *two* theorem-backed classes: PH features (Level 1a, stability) and CG-VAE factors that pass the pre-committed MCC threshold (Level 1b, identifiability).

**The asymmetric trust structure, now two-anchored.** PH features enjoy a mathematical guarantee via the stability theorem (§3.6): persistence diagrams are Lipschitz-continuous functions of the input. CG-VAE factors passing the §10.3 MCC threshold enjoy a different mathematical guarantee via Kong et al. (2025) Theorem 2: learned factors are identifiable up to element-wise invertible transformation against true generative factors. Both are formal proofs, and each protects against a distinct failure mode (§8.2). No analogous theorem exists for DINOv2 residuals (which depend on training-data distribution and model architecture) or for classical geostatistical descriptors (which depend on stationarity assumptions that geological data routinely violate). This creates a refined asymmetric trust structure:

| Tier | Source | Epistemic Basis | Invariance Guarantee |
|------|--------|----------------|---------------------|
| 1a — Proven (stability) | PH features | Stability theorem (§3.6) | $d_B(\textrm{Dgm}(f), \textrm{Dgm}(g)) \leq \lVert f - g \rVert_\infty$ |
| 1b — Proven (identifiability) | CG-VAE factors passing MCC $\geq 0.85$ | Kong et al. (2025) Theorem 2 | $\hat{z}$ identifies true $z$ up to element-wise invertible transformation |
| 1-joint — Doubly Proven | PH $\cap$ CG-VAE joint component (via SLIDE) | Both theorem classes apply | Robust against perturbation *and* correctly identified |
| 2 — Corroborated | Joint components across three or more pathways | Cross-pathway convergence | Strong empirical + partial theoretical |
| 3 — Empirically invariant | Features passing LOGO but low CKA with PH or CG-VAE | Empirical testing | LOGO-validated, no theoretical backing |
| 4 — Uncertain | Unique to one pathway | Single-source | No cross-validation |

This hierarchy is not merely taxonomic—it has operational consequences for how features are weighted in retrieval (§8.4).

**Two complementary guarantees.** The distinction between Tier 1a and Tier 1b is substantive: each protects against a different failure mode. Tier 1a bounds *sensitivity to perturbation*—the persistence diagram of $f + \delta f$ is close to the diagram of $f$ when $\delta f$ is bounded. It does not bound *correspondence*: the features could be maximally stable yet encode generator-specific artifacts. Tier 1b bounds *correspondence*—the learned factor $\hat{z}_k$ is in known relationship with the true generative parameter $z_k$ under auxiliary supervision. It does not bound *perturbation sensitivity*: the factor could be correctly identified yet arbitrarily sensitive to small image noise. A feature at Tier 1-joint enjoys both guarantees simultaneously, and is the highest-confidence class in the system. §8.2 develops the formal complementarity argument; this section operationalizes it at the feature-fusion level.

**Measuring cross-pathway alignment.** To populate this hierarchy, quantitative measures of agreement between feature spaces are required. Williams et al. (2024) proved that Centered Kernel Alignment (CKA; Kornblith et al., 2019), Representational Similarity Analysis (RSA; Kriegeskorte et al., 2008), and Canonical Correlation Analysis (CCA; Raghu et al., 2017) are mathematically equivalent under appropriate normalization—they measure the same underlying alignment from different perspectives. We adopt CKA as the primary alignment metric due to its robustness to representation dimensionality mismatch (PH produces 20–50 features; classical $\sim 50$; DINOv2 768; CG-VAE $\sim 15$–$30$ identified factors plus residuals).

**SLIDE decomposition.** Global alignment metrics like CKA reveal *how much* two feature spaces agree but not *which* features agree. The SLIDE framework (Structured Integration of Linked Data from Experiments; Gaynanova and Li, 2019) decomposes multi-view data into three components:

$$X = X_{\text{joint}} + X_{\text{partial}} + X_{\text{individual}}$$

where $X_{\text{joint}}$ captures variation shared across all views, $X_{\text{partial}}$ captures variation shared between some but not all views, and $X_{\text{individual}}$ captures view-specific variation. Applied to the four feature extractors (PH, classical, DINOv2, CG-VAE):

- **PH $\cap$ CG-VAE joint component (the doubly-Level-1 class).** Features simultaneously aligned with PH and CG-VAE occupy Tier 1-joint of the hierarchy. This is the system's highest-confidence set: stability (PH) and identifiability (CG-VAE) both apply to the same feature, and cross-pathway corroboration between the two theorem-backed anchors provides evidence beyond what either anchor alone could supply.
- **Four-way joint component** (PH $\cap$ classical $\cap$ DINOv2 $\cap$ CG-VAE): Features all four pathways agree on — the highest cross-pathway corroboration class at Tier 2, with a subset already at Tier 1-joint via the PH $\cap$ CG-VAE intersection.
- **Partial components.** Pairwise and three-way overlaps indicate real structure that some but not all pathways detect. Epistemic weight depends on which pathways participate: PH $\cap$ classical lacks CG-VAE's identifiability guarantee; DINOv2 $\cap$ classical is the weakest partial because it involves no Level 1 source.
- **Individual components.** Features unique to one pathway — genuine unique information, pathway-specific artifacts, or DINOv2 residuals (Tier 3–4 per §8.4).

The SLIDE implementation requires a per-dimension assignment of CG-VAE features, distinguishing *identified* factors ($z_a$ passing MCC threshold) from *residual* factors (not in $z_a$ or failing threshold). Only identified factors contribute to Tier 1b; residuals are handled analogously to DINOv2 residuals at lower tiers.

**Directed probing: DINOv2 $\to$ PH.** The learned pathway (DINOv2) operates in a 768-dimensional space that is far richer than PH's 20–50 dimensions. A natural question is: *which DINOv2 features encode topological information?* Linear probing (Alain and Bengio, 2016) and Testing with Concept Activation Vectors (T-CAV; Kim et al., 2018) provide complementary answers. Linear probes test whether PH features are *linearly decodable* from DINOv2 representations—a strong test given that Oquab et al. (2023) showed DINOv2 features are generally linearly separable. T-CAV identifies *directions* in DINOv2 space that correspond to topological concepts (e.g., "high $H_1$ persistence"), providing interpretable decomposition of the learned representation into topologically meaningful and topologically opaque components.

**Directed probing: Classical $\leftrightarrow$ PH and Classical $\leftrightarrow$ DINOv2.** The directed probing framework extends naturally to the classical pathway, revealing a different pattern of cross-pathway alignment. Classical features (~50 dimensions) overlap with PH in a specific, interpretable way: variogram range encodes spatial scale information that PH does not directly capture, but connectivity functions partially encode the same structural information as $H_0$ persistence features. A linear probe testing whether PH features (specifically $H_0$ lifetimes) are decodable from connectivity function values quantifies this overlap. High decodability confirms that the classical pathway's connectivity features are partially redundant with PH—information that the SLIDE decomposition would assign to the partial component (PH $\cap$ geostat) rather than the joint or individual components.

The classical-DINOv2 probe is equally informative. DINOv2's 768 dimensions likely encode variogram-like spatial correlation information implicitly—the self-attention mechanism can detect spatial periodicity, directional patterns, and scale structure. A linear probe testing whether variogram parameters are decodable from DINOv2 representations quantifies what classical information the learned pathway captures on its own. High decodability would mean that DINOv2 partially subsumes the classical pathway, reducing the marginal value of including classical features in the fusion layer. Low decodability would confirm that classical features provide genuinely independent information—spatial statistics that the neural network does not learn to extract from raw pixels.

**Directed probing: CG-VAE $\leftrightarrow$ PH and CG-VAE $\leftrightarrow$ DINOv2.** Two additional probes are specific to the CG-VAE integration. First, CG-VAE $\to$ PH: which identified factors $\hat{z}_k$ encode topological information present in PH features? High decodability indicates convergence between Level 1a and Level 1b on the same underlying structural information—the ideal case for the doubly-Level-1 joint component. Second, CG-VAE $\to$ DINOv2 residuals: which DINOv2 residuals (after subtracting the CG-VAE-aligned portion) still encode identifiable-factor information missed by CG-VAE training? Strong residual signal suggests that the auxiliary encoding should be refined (§6.5: categorical vs continuous vs hierarchical) or that some geological information lies genuinely outside $\theta$'s span.

**Evidence combination via Dempster-Shafer Theory.** The confidence hierarchy requires a formal framework for combining evidence of asymmetric reliability. Classical Bayesian fusion treats all sources symmetrically—each contributes a likelihood. But when multiple sources have different levels of theoretical backing (Level 1a, Level 1b, Levels 3–7), symmetric treatment is epistemically inappropriate. Dempster-Shafer Theory (DST) provides an alternative: each source contributes a *belief function* (lower bound on probability) and a *plausibility function* (upper bound), with the gap between them encoding *ignorance*. For Tier 1-joint features (doubly Level 1), the belief-plausibility gap is narrowest. For Tier 1a-only or Tier 1b-only features, the gap widens to reflect one-sided protection. For Tier 2 features (cross-pathway joint without Level 1 backing), the gap is wider still. For Tier 4 features (single-pathway unique), the gap is widest. Dempster's rule of combination then fuses these asymmetric assessments into a combined belief structure that appropriately weights theorem-backed evidence over empirically derived evidence, with doubly-Level-1 features at the top of the fused hierarchy.

The proposed pipeline for confidence-tiered feature fusion is:

1. **Compute features**: PH (20–50d), classical geostatistical (~50d), DINOv2 (768d), CG-VAE (identified factors plus residuals)
2. **Verify Level 1b**: MCC evaluation of CG-VAE factors against held-out $\theta$ (§10.3 thresholds); retain only identified factors $\hat{z}_a$ passing $\textrm{MCC} \geq 0.85$
3. **Global alignment**: CKA pairwise between all four pathway-feature sets
4. **Decomposition**: SLIDE into joint / partial / individual components, marking the PH $\cap$ CG-VAE joint component as doubly-Level-1
5. **Directed probing**: Linear probes and T-CAV across all pathway pairs, including the CG-VAE probes above
6. **Confidence assignment**: Map each feature dimension to Tiers 1a / 1b / 1-joint / 2 / 3 / 4 based on decomposition results and theorem applicability
7. **Evidence combination**: DST with tier-dependent reliability weights for retrieval scoring, weighting Tier 1-joint highest per §8.4's descriptor admissibility

### 14.7 From Feature Residuals to Uncertainty Quantification

The SLIDE decomposition of §14.6 partitions DINOv2's 768-dimensional representation into PH-aligned and PH-residual components. A natural but premature conclusion would be to discard the residual as noise. However, DeCUR (Decoupling Common and Unique Representations; Wang et al., 2024) demonstrated that the unique (non-shared) components of self-supervised representations carry *meaningful* information—they encode view-specific structure that is genuinely present in the data but not captured by shared features. Applied to our setting, DINOv2's PH-residual features may encode geological information that is real but not topological: texture gradients, facies boundary sharpness, spatial frequency content, or other properties that PH's topological abstraction deliberately ignores.

**Aleatoric vs. epistemic decomposition.** The critical question is whether these residual features represent *aleatoric* uncertainty (genuine intra-class variability—different braided systems have different textures) or *epistemic* uncertainty (model ignorance—the feature extractor is uncertain about what it sees). Kendall and Gal (2017) established the foundational framework for this decomposition. Kotelevskii et al. (2025) extended it to feature space, showing that uncertainty can be decomposed *per feature dimension* without requiring model ensembles—using density estimation in the representation space to distinguish regions of high data density (low epistemic uncertainty) from regions of low density (high epistemic uncertainty).

**The propagation chain.** These methods compose into a coherent pipeline linking PH's mathematical guarantees to calibrated uncertainty in retrieval:

1. **PH features** provide bounded invariants via the stability theorem
2. **DeCUR decomposition** separates DINOv2 into PH-aligned and PH-residual components, confirming that residual components carry meaningful (not random) information
3. **Kotelevskii density model** decomposes residual uncertainty into aleatoric (intra-class variability) and epistemic (data sparsity) components, *per feature dimension*
4. **Heteroscedastic embedding**: Rather than representing each analog as a point in feature space, represent it as a distribution $\mathcal{N}(\mu, \Sigma)$ where $\Sigma$ encodes per-feature uncertainty (following Oh et al., 2019, on hedged instance embeddings)
5. **Uncertainty-weighted similarity**: Retrieval uses a similarity metric that downweights feature dimensions with high uncertainty, following Uncertainty-Aware Embedding Comparison (UEC) principles
6. **Neural Process integration**: The Neural Process query encoder (§9.2) naturally produces uncertainty-calibrated outputs $(\mu, \sigma)$; the structured uncertainty from steps 3–5 provides a principled initialization of the encoder's uncertainty prior

**Classical pathway residuals and three-pathway decomposition.** The residual analysis above focuses on DINOv2's PH-residual—what the learned pathway captures beyond topology. But the classical pathway also produces residuals worth analyzing. The *classical PH-residual*—geostatistical features not predictable from PH—encodes scale, anisotropy, and stationarity information that PH deliberately abstracts away. Unlike DINOv2's opaque residual, the classical residual is fully interpretable: it consists of variogram range (depositional scale), anisotropy ratio (directional fabric), and fractal dimension (multiscale roughness), each with direct physical meaning. This interpretability makes the classical residual particularly valuable for uncertainty quantification: when the classical and topological pathways disagree, the classical residual identifies *which specific geostatistical property* is responsible for the disagreement, enabling targeted investigation rather than opaque "pathway disagreement" diagnostics.

The full three-pathway residual decomposition is therefore:

- **PH features**: Tier 1 anchor — bounded invariants via the stability theorem
- **Classical PH-residual**: Scale, anisotropy, and roughness not captured by topology — interpretable, Tier 3
- **DINOv2 PH-residual**: Gestalt and texture information not captured by topology — opaque, Tier 3–4
- **DINOv2 classical-residual**: Visual information captured by neither geostatistics nor topology — the most uncertain features, requiring the strongest uncertainty discounting

This hierarchy of residuals maps directly to the tiered descriptor structure of Pipeline A (§14.8): core index features come from PH, extended index features come from the interpretable classical residual, and the uncertainty envelope incorporates the opaque learned residuals with appropriate discounting.

**Connection to subsurface uncertainty quantification.** This pipeline connects to established practice in geostatistical uncertainty quantification. Scheidt, Li, and Caers (2018) developed distance-based methods for subsurface uncertainty assessment that use feature-space distances to define scenario probabilities—precisely the framework that uncertainty-weighted retrieval implements. Arnold et al. (2018) extended this to geological scenario probability estimation. The contribution here is to ground the distance computation in features with *known* epistemic status: PH features anchor the distance with mathematical guarantees, while residual features contribute with appropriate uncertainty discounting.

### 14.8 Implications for the Two-Pipeline Architecture

The three extensions of this section have concrete implications for both pipelines and their coupling.

**Pipeline A (Cataloguing).** The confidence hierarchy (§14.6) changes what gets indexed and how. Rather than a flat feature vector, each analog's index entry becomes a *tiered descriptor*:

- **Core index** (Tiers 1–2): PH features and cross-pathway corroborated features. These are the primary keys for retrieval—the features with strongest invariance guarantees.
- **Extended index** (Tier 3): Empirically invariant features. Used for refinement within equivalence classes defined by the core index.
- **Uncertainty envelope** (Tier 4 + aleatoric): Single-pathway features and intra-class variability estimates. Not used for primary retrieval but inform uncertainty quantification in the returned results.

This tiered structure means Pipeline A does not merely store analogs—it stores analogs *with calibrated confidence about what is known and unknown* about each one.

**Pipeline B (Retrieval).** Sparse field observations will typically constrain some feature dimensions well and leave others poorly constrained. The confidence hierarchy provides a principled way to handle this asymmetry: features that are both well-constrained by observations *and* high-tier in the confidence hierarchy receive maximal weight in retrieval. Features that are poorly constrained or low-tier contribute uncertainty rather than false precision.

The Neural Process query encoder (§9.2) is naturally suited to this framework. Given sparse observations, it produces a posterior distribution in feature space. The structured uncertainty from §14.7 provides an informative prior: dimensions corresponding to Tier 1 features have tight priors (PH constrains them strongly), while dimensions corresponding to Tier 4 features have diffuse priors (little a priori constraint). This is a concrete realization of the Bayesian retrieval framework discussed abstractly in §9.

**Response essence and Pipeline validation.** The dynamic extensions (§14.1–14.5) suggest a validation criterion for the entire retrieval system: analogs retrieved by Pipeline B (based on structural similarity) should exhibit similar dynamic response when subjected to identical simulation protocols. If structural retrieval predicts response similarity, the system is validated at the deepest level. If not, the gap between structural and response essence identifies which additional descriptors Pipeline A must incorporate.

**The coupling layer.** The coupling between pipelines—the similarity metric that compares a sparse query to dense catalog entries—benefits from all three extensions. The confidence hierarchy ensures the metric is grounded in features with known invariance properties. The uncertainty decomposition ensures the metric is uncertainty-aware, returning not just a ranked list but a *posterior distribution* over candidate analogs with calibrated confidence intervals. And the response essence framework provides the ultimate validation criterion: retrieved analogs should not only look similar but behave similarly.

---

## 15. Conclusion

The Qualia Convergence Framework addresses the essence problem through three pillars: a principle-based generator providing controlled experimental data, a three-pathway architecture for essence determination, and a retrieval system mapping sparse observations to catalogued analogs with calibrated uncertainty.

The framework's central epistemological contribution is the recognition that the three pathways provide evidence of fundamentally *different* epistemic status—and that this asymmetry should govern the entire architecture. Persistent homology, backed by the stability theorem, provides the only mathematical invariance guarantee among the three pathways, making it the natural epistemic anchor. Classical geostatistical descriptors provide well-understood spatial characterization grounded in decades of established theory. Self-supervised visual representations (DINOv2) capture the holistic pattern recognition that experienced geoscientists perform intuitively. The framework's power comes not from any single pathway but from their *convergence*: when topology, statistics, and learned semantics agree on a structural characterization, the evidence for essence is strongest.

The confidence hierarchy of Section 14.6 operationalizes this principle: PH features anchor the architecture as Tier 1 descriptors, cross-pathway agreement provides Tier 2 corroboration, and the epistemic asymmetry between theorem-backed and empirically derived features—previously unexploited in multi-modal fusion research—structures how evidence from different pathways is weighted, combined, and trusted.

The colleague's challenge—"patterns based on statistical coherence will never solve the essence problem"—remains the animating question. Our response is now more nuanced: patterns based on statistical coherence indeed cannot capture topological structure, but no single pathway captures the full picture. The convergence of topological, statistical, and learned representations—validated by mathematical invariance theorems, severe testing, and the pre-committed Sākṣī protocol—can approach something worthy of the designation "essence," with epistemic humility about the gap between operational definitions and deeper truths.

The principle-based generator (Section 2) provides the experimental apparatus, and the proposed validation design (Section 12) provides the concrete testing protocol. Together, these components form a research program that is mathematically grounded, architecturally specified, experimentally equipped, epistemologically honest about its limitations, and empirically testable.

*[Note: The following areas require expansion to bring the full dissertation to comparable rigor across all components: (1) mathematical foundations for classical geostatistics and learned representations have been drafted (§4, §5) but need comparable depth to the persistent homology treatment; (2) detailed generator mechanism verification against current literature.]*

---

## References

Adams, H., Emerson, T., Kirby, M., Neville, R., Peterson, C., Shipman, P., ... & Ziegelmeier, L. (2017). Persistence images: A stable vector representation of persistent homology. *Journal of Machine Learning Research*, 18(8), 1–35.

Ahuja, K., Hartford, J., & Bengio, Y. (2023). Invariance & causal representation learning: Prospects and limitations. *arXiv:2312.03580*.

Alain, G., & Bengio, Y. (2016). Understanding intermediate layers using linear classifier probes. *arXiv:1610.01644*.

Alcala-Alvarez, A., & Padilla-Longoria, P. (2022). A framework for topological music analysis (TMA). *arXiv:2204.09744*.

Arjovsky, M., Bottou, L., Gulrajani, I., & Lopez-Paz, D. (2019). Invariant risk minimization. *arXiv:1907.02893*.

Arnold, D., Demyanov, V., Tatum, D., Christie, M., Roesner, K., & Champlong, P. (2018). Hierarchical benchmark case study for history matching, uncertainty quantification and reservoir characterisation. *Mathematical Geosciences*, 50(7), 793–826.

Atienza, N., Gonzalez-Diaz, R., & Soriano-Trigueros, M. (2020). On the stability of persistent entropy and new summary functions for topological data analysis. *Pattern Recognition*, 107, 107509.

Bengio, Y., Courville, A., & Vincent, P. (2013). Representation learning: A review and new perspectives. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 35(8), 1798–1828.

Bhojanapalli, S., Chakrabarti, A., Glasner, D., Li, D., Unterthiner, T., & Veit, A. (2021). Understanding robustness of transformers for image classification. *ICCV 2021*. *arXiv:2108.02972*.

Belghazi, M. I., Barber, A., Balin, O., Dresdner, R., et al. (2018). Mutual information neural estimation. *ICML*.

Bergomi, M. G., Barate, A., & Di Fabio, B. (2016). Towards a topological fingerprint of music. In *Computational Topology in Image Context*, LNCS 9667, 88–100. Springer.

Bergomi, M. G., & Barate, A. (2020). Homological persistence in time series: An application to music classification. *Journal of Mathematics and Music*, 14(2), 204–221.

Bubenik, P. (2015). Statistical topological data analysis using persistence landscapes. *Journal of Machine Learning Research*, 16(3), 77–102.

Caron, M., Touvron, H., Misra, I., Jégou, H., Mairal, J., Bojanowski, P., & Synnaeve, G. (2021). Emerging properties in self-supervised vision transformers. *ICCV 2021*. *arXiv:2104.14294*.

Carlsson, G. (2009). Topology and data. *Bulletin of the American Mathematical Society*, 46(2), 255–308.

Cerri, A., Di Fabio, B., Ferri, M., Frosini, P., & Landi, C. (2013). Betti numbers in multidimensional persistent homology are stable functions. *Mathematical Methods in the Applied Sciences*, 36(12), 1543–1557.

Chami, I., Ying, Z., Ré, C., & Leskovec, J. (2019). Hyperbolic graph convolutional neural networks. *Advances in Neural Information Processing Systems* 32.

Chawshin, K., et al. (2021). U.S. Patent 11,386,143.

Chilès, J.-P., & Delfiner, P. (2012). *Geostatistics: Modeling Spatial Uncertainty* (2nd ed.). Wiley.

Chazal, F., de Silva, V., Glisse, M., & Oudot, S. (2016). *The Structure and Stability of Persistence Modules*. SpringerBriefs in Mathematics.

Cohen-Steiner, D., Edelsbrunner, H., & Harer, J. (2007). Stability of persistence diagrams. *Discrete & Computational Geometry*, 37(1), 103–120.

Conley, C. (1978). *Isolated Invariant Sets and the Morse Index*. CBMS Regional Conference Series in Mathematics, Vol. 38. American Mathematical Society.

Das, S., Bhattacharya, S., & Bhowmick, S. (2024). Topological analysis of dynamical systems: Distinguishing periodic and chaotic regimes using persistent homology. *arXiv:2408.15834*.

Dalal, N., & Triggs, B. (2005). Histograms of oriented gradients for human detection. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, 886–893.

Dey, T. K., Hou, T., & Mandal, S. (2020). Computing Morse decomposition of vector fields. *Journal of Computational Geometry*, 11(1), 305–333.

Dosovitskiy, A., Beyer, L., Kolesnikov, A., Weissenborn, D., Zhai, X., Unterthiner, T., ... & Houlsby, N. (2020). An image is worth 16x16 words: Transformers for image recognition at scale. *ICLR 2021*. *arXiv:2010.11929*.

Edelsbrunner, H., & Harer, J. (2010). *Computational Topology: An Introduction*. American Mathematical Society.

Edelsbrunner, H., Letscher, D., & Zomorodian, A. (2002). Topological persistence and simplification. *Discrete & Computational Geometry*, 28(4), 511–533.

Frascati, A., & Lanzoni, S. (2009). Morphodynamic regime and long-term evolution of meandering rivers. *Journal of Geophysical Research: Earth Surface*, 114(F2), F02002.

Fredsøe, J. (1978). Meandering and braiding of rivers. *Journal of Fluid Mechanics*, 84(4), 609–624.

Gal, Y., & Ghahramani, Z. (2016). Dropout as a Bayesian approximation: Representing model uncertainty in deep learning. *Proceedings of the 33rd International Conference on Machine Learning (ICML)*, 1050–1059.

Ganin, Y., & Lempitsky, V. (2015). Unsupervised domain adaptation by backpropagation. *Proceedings of the 32nd International Conference on Machine Learning (ICML)*, 1180–1189.

Garnelo, M., Schwarz, J., Rosenbaum, D., Viola, F., Rezende, D. J., Eslami, S. M. A., & Teh, Y. W. (2018). Neural processes. *arXiv:1807.01622*.

Gatys, L. A., Ecker, A. S., & Bethge, M. (2016). Image style transfer using convolutional neural networks. *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, 2414–2423.

Gaynanova, I., & Li, G. (2019). Structural learning and integrative decomposition of multi-view data. *Biometrics*, 75(4), 1121–1132.

Guardiano, F. B., & Srivastava, R. M. (1993). Multivariate geostatistics: Beyond bivariate moments. In *Geostatistics Tróia '92*, Quantitative Geology and Geostatistics (Vol. 5, pp. 133–144). Springer.

Giusti, C., Ghrist, R., & Bassett, D. S. (2016). Two's company, three (or more) is a simplex: Algebraic-topological tools for understanding higher-order structure in neural data. *Journal of Computational Neuroscience*, 41(1), 1–14.

He, Q., Zhong, Z., Alabert, F., & Datta-Gupta, A. (2023). Koopman operator-based model reduction for reservoir simulation and optimization. *SPE Journal*, 28(4), 2024–2040.

Hu, E. J., Shen, Y., Wallis, P., Allen-Zhu, Z., Li, Y., Wang, S., ... & Chen, W. (2022). LoRA: Low-rank adaptation of large language models. *ICLR 2022*. *arXiv:2106.09685*.

Hoydic, C. J. (2026). On the nature of geological essence: A critical analysis of the ellipse degradation thought experiment. Unpublished manuscript.

Hundey, E. J., & Ashmore, P. E. (2009). Length scale of braided river morphology. *Water Resources Research*, 45(8), W08409.

Jaegle, A., Gimeno, F., Brock, A., Zisserman, A., Vinyals, O., & Carreira, J. (2021). Perceiver IO: A general architecture for structured inputs & outputs. *arXiv:2107.14795*.

Jansen, J. D., Brouwer, R., Naevdal, G., & van Kruijsdijk, C. P. J. W. (2009). Closed-loop reservoir management. *SPE Reservoir Evaluation & Engineering*, 12(1), 145–154.

Journel, A. G., & Huijbregts, C. J. (1978). *Mining Geostatistics*. Academic Press.

Jiwei, L., Zhenyu, C., Chunmei, D., Xixin, W., & Junhui, W. (2025). Characteristics and distribution of interlayers in tidal-dominated estuarine reservoir: Insights from the Dongying Depression, China. *Scientific Reports*, 15, 3591.

Johnson, J., Douze, M., & Jegou, H. (2019). Billion-scale similarity search with GPUs. *IEEE Transactions on Big Data*, 7(3), 535–547.

Kaczynski, T., Mischaikow, K., & Mrozek, M. (2004). *Computational Homology*. Applied Mathematical Sciences, Vol. 157. Springer.

Kendall, A., & Gal, Y. (2017). What uncertainties do we need in Bayesian deep learning for computer vision? *Advances in Neural Information Processing Systems* 30.

Kemmea, A. J., & Agyingi, C. A. (2025). Persistent homology: A pedagogical introduction with biological applications. *arXiv:2505.06583*.

Kim, B., Wattenberg, M., Gilmer, J., Cai, C., Wexler, J., Viegas, F., & Sayres, R. (2018). Interpretability beyond feature attribution: Quantitative testing with concept activation vectors (TCAV). *ICML 2018*.

Kim, H., Mnih, A., Schwarz, J., Garnelo, M., Eslami, A., Rosenbaum, D., ... & Teh, Y. W. (2019). Attentive Neural Processes. *ICLR 2019*.

Kleinhans, M. G., & van den Berg, J. H. (2011). River channel and bar patterns explained and predicted by an empirical and a physics-based method. *Earth Surface Processes and Landforms*, 36(6), 721–738.

Kornblith, S., Norouzi, M., Lee, H., & Hinton, G. (2019). Similarity of neural network representations revisited. *ICML 2019*. *arXiv:1905.00414*.

Kotelevskii, N., Panov, M., Zaytsev, A., & Spokoiny, V. (2025). Uncertainty decomposition in feature space without ensembles. *arXiv:2511.12389*.

LeCun, Y., Bottou, L., Bengio, Y., & Haffner, P. (1998). Gradient-based learning applied to document recognition. *Proceedings of the IEEE*, 86(11), 2278–2324.

Lakshminarayanan, B., Pritzel, A., & Blundell, C. (2017). Simple and scalable predictive uncertainty estimation using deep ensembles. *Advances in Neural Information Processing Systems* 30.

Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). ImageNet classification with deep convolutional neural networks. *Advances in Neural Information Processing Systems* 25.

Kramar, M., Levanger, R., Tithof, J., Suri, B., Xu, M., Paul, M., ... & Mischaikow, K. (2016). Analysis of Kolmogorov flow and Rayleigh-Benard convection using persistent homology. *Physica D*, 334, 82–98.

Kriegeskorte, N., Mur, M., & Bandettini, P. (2008). Representational similarity analysis — connecting the branches of systems neuroscience. *Frontiers in Systems Neuroscience*, 2, Article 4.

Leopold, L. B., & Wolman, M. G. (1957). River channel patterns: Braided, meandering, and straight. *U.S. Geological Survey Professional Paper* 282-B.

Leopold, L. B., & Wolman, M. G. (1960). River meanders. *Geological Society of America Bulletin*, 71(6), 769–793.

Leopold, L. B., Wolman, M. G., & Miller, J. P. (1964). *Fluvial Processes in Geomorphology*. W. H. Freeman.

Lipinski, M., Mrozek, M., & Batko, B. (2023). Persistent Conley-Morse graphs: Attractor structure under perturbation. *arXiv:2107.02115*.

Lowe, D. G. (2004). Distinctive image features from scale-invariant keypoints. *International Journal of Computer Vision*, 60(2), 91–110.

Liu, J., Wang, J., Liu, B., & Ma, Z. (2021). Persistent homology-based topological analysis on the Gestalt patterns during human brain cognition process. *Journal of Healthcare Engineering*, 2021, 2334332.

Madry, A., Makelov, A., Schmidt, L., Tsipras, D., & Vladu, A. (2018). Towards deep learning models resistant to adversarial attacks. *Proceedings of the 6th International Conference on Learning Representations (ICLR 2018)*.

Mandelbrot, B. B. (1982). *The Fractal Geometry of Nature*. W. H. Freeman.

Matheron, G. (1963). Principles of geostatistics. *Economic Geology*, 58(8), 1246–1266.

Mayo, D. G. (2018). *Statistical Inference as Severe Testing: How to Get Beyond the Statistics Wars*. Cambridge University Press.

Moon, C., Mitchell, S. A., Heath, J. E., & Andrew, M. (2019). Statistical inference over persistent homology predicts fluid flow in porous media. *Water Resources Research*, 55(11), 9592–9603.

Nanson, G. C., & Knighton, A. D. (1996). Anabranching rivers: Their cause, character and classification. *Earth Surface Processes and Landforms*, 21(3), 217–239.

Nickel, M., & Kiela, D. (2017). Poincaré embeddings for learning hierarchical representations. *Advances in Neural Information Processing Systems* 30.

Nickel, M., & Kiela, D. (2018). Learning continuous hierarchies in the Lorentz model of hyperbolic geometry. *ICML 2018*.

Ojala, T., Pietikäinen, M., & Mäenpää, T. (2002). Multiresolution gray-scale and rotation invariant texture classification with local binary patterns. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 24(7), 971–987.

Oh, S., Song, H., Yun, S., Kim, S., & Yoon, S. (2019). Hedged instance embedding. *ICLR 2019*. *arXiv:1810.00319*.

Oliva, A., & Torralba, A. (2006). Building the gist of a scene: The role of global image features in recognition. *Progress in Brain Research*, 155, 23–36.

Oquab, M., Darcet, T., Moutakanni, T., Vo, H., Szafraniec, M., Khalidov, V., ... & Bojanowski, P. (2023). DINOv2: Learning robust visual features without supervision. *arXiv:2304.07193*.

Orzack, S. H., & Sober, E. (1993). A critical assessment of Levins's "The strategy of model building in population biology." *Quarterly Review of Biology*, 68(4), 533–546.

Otter, N., Porter, M. A., Tillmann, U., Grindrod, P., & Harrington, H. A. (2017). A roadmap for the computation of persistent homology. *EPJ Data Science*, 6, Article 17.

Oudot, S. Y. (2015). *Persistence Theory: From Quiver Representations to Data Analysis*. Mathematical Surveys and Monographs, Vol. 209. American Mathematical Society.

Parker, G. (1976). On the cause and characteristic scales of meandering and braiding in rivers. *Journal of Fluid Mechanics*, 76(3), 457–480.

Peng, W., Varanka, T., Tirnauca, A., Xiao, B., Jensen, H. J., & Zhao, G. (2022). Hyperbolic deep neural networks: A survey. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 44(12), 10023–10044.

Phillips, J. D. (1992). Nonlinear dynamical systems in geomorphology: Revolution or evolution? *Geomorphology*, 5(3–5), 219–229.

Phillips, J. D. (2003). Sources of nonlinearity and complexity in geomorphic systems. *Progress in Physical Geography*, 27(1), 1–23.

Phillips, J. D. (2006). Deterministic chaos and historical geomorphology: A review and look forward. *Geomorphology*, 76(1–2), 109–121.

Plotnick, R. E., Gardner, R. H., Hargrove, W. W., Prestegaard, K., & Perlmutter, M. (1996). Lacunarity analysis: A general technique for the analysis of spatial patterns. *Physical Review E*, 53(5), 5461–5468.

Phillips, J. D. (2011). Emergence and pseudo-equilibrium in geomorphology. *Geomorphology*, 132(3–4), 319–326.

Raghu, M., Gilmer, J., Yosinski, J., & Sohl-Dickstein, J. (2017). SVCCA: Singular vector canonical correlation analysis for deep learning dynamics and interpretability. *arXiv:1706.05806*.

Robins, V., Saadatfar, M., Delgado-Friedrichs, O., & Sheppard, A. P. (2016). Percolating length scales from topological persistence analysis of micro-CT images of porous materials. *Water Resources Research*, 52(1), 315–329.

Rosenfeld, E., Ravikumar, P., & Risteski, A. (2021). The risks of invariant risk minimization. *ICLR*.

Scheidt, C., Li, L., & Caers, J. (2018). *Quantifying Uncertainty in Subsurface Systems*. Geophysical Monograph Series, Vol. 236. Wiley/AGU.

Shah, P., Mukherjee, S., & Sousbie, T. (2025). Persistent homology detects bifurcation routes to chaos. *arXiv preprint*.

Stauffer, D., & Aharony, A. (1994). *Introduction to Percolation Theory* (2nd ed.). Taylor & Francis.

Strebelle, S. (2002). Conditional simulation of complex geological structures using multiple-point statistics. *Mathematical Geology*, 34(1), 1–21.

Stolum, H.-H. (1996). River meandering as a self-organization process. *Science*, 271(5256), 1710–1713.

Takens, F. (1981). Detecting strange attractors in turbulence. In *Dynamical Systems and Turbulence*, Lecture Notes in Mathematics, Vol. 898, 366–381. Springer.

Tauzin, G., Lupo, U., Tunstall, L., et al. (2021). giotto-tda: A topological data analysis toolkit for machine learning and data exploration. *Journal of Machine Learning Research*, 22(39), 1–6.

Thompson, A. B., Mayall, M., & Sherborne, A. (2023). Persistent homology tracks dynamic topological changes in dissolving porous media. *Water Resources Research*, 59(5), e2022WR033750.

Turcotte, D. L. (1997). *Fractals and Chaos in Geology and Geophysics* (2nd ed.). Cambridge University Press.

Tye, M. (2021). Qualia. *Stanford Encyclopedia of Philosophy*. https://plato.stanford.edu/entries/qualia/

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., ... & Polosukhin, I. (2017). Attention is all you need. *Advances in Neural Information Processing Systems* 30.

Vaughan, A., Tebbutt, W., Hosking, J. S., & Turner, R. E. (2022). Convolutional conditional neural processes for local climate downscaling. *Geoscientific Model Development*, 15(1), 251–268.

Venkataraman, V., Ramamurthy, K. N., & Turaga, P. (2016). Persistent homology of attractors for action recognition. *IEEE International Conference on Image Processing (ICIP)*, 4150–4154.

Wagner, H., Chen, C., & Vucini, E. (2012). Efficient computation of persistent homology for cubical data. In *Topological Methods in Data Analysis and Visualization II*. Springer.

Wang, Z., Zhao, Q., Zuo, Z., Li, S., & Li, B. (2024). Decoupling common and unique representations for multiview self-supervised learning. *ECCV 2024*. *arXiv:2309.05300*.

Wang, Y., Xian, Y., Chen, X., & Yan, C. (2025). Topological signatures of brain dynamics: Persistent homology reveals individuality and brain-behaviour links. *Frontiers in Human Neuroscience*, 19, 1607941.

Werner, B. T. (1995). Eolian dunes: Computer simulations and attractor interpretation. *Geology*, 23(12), 1107–1110.

Williams, A. H., Kunz, E., Kornblith, S., & Linderman, S. W. (2024). Generalized shape metrics on neural representations. *Nature Machine Intelligence*, 6, 100–113.

Williams, G. P. (1986). River meanders and channel size. *Journal of Hydrology*, 88(1–2), 147–164.

Weisberg, M. (2006). Robustness analysis. *Philosophy of Science*, 73(5), 730–742.

Wimsatt, W. C. (1981). Robustness, reliability, and overdetermination. In *Scientific Inquiry and the Social Sciences*, ed. Brewer & Collins.

Zomorodian, A., & Carlsson, G. (2005). Computing persistent homology. *Discrete & Computational Geometry*, 33(2), 249–274.
