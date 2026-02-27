# Essence Under Constraint

## Structural Invariance as the Foundation of Analog Cataloguing and Sparse Retrieval

Author: Corey James Hoydic\
Status: Context Document for Full-Project Alignment\
Date: 2026

------------------------------------------------------------------------

# 1. The Original Dissertation Research Question (Primary Frame)

The foundational research problem of this dissertation is:

    How can we predict the response of subsurface geological formations
    to natural and anthropogenic stimuli when available observations
    are sparse and incomplete?

Accurate prediction requires spatial models that faithfully represent
multiscale geological variability.

However:

1.  Available field data are sparse and multimodal.
2.  Vast repositories of analog information exist.
3.  Selecting appropriate analogs is currently subjective and
    expertise-driven.

Therefore, the operational research question becomes:

    How can large cyber-repositories of geological analog data
    be systematically organized, indexed, and retrieved
    to support defensible subsurface modeling under sparse data constraints?

This document ensures that "geological essence" is framed inside this
objective.

------------------------------------------------------------------------

# 2. The Two-Pipeline Architecture (Central Project Structure)

To address the operational research question, the project is explicitly
organized as **two coupled pipelines**.

## Pipeline A --- Repository / Cataloguing Pipeline

    Analog data → encode essence → index analogs → geologic index (database)

This pipeline answers:

-   How do we transform heterogeneous analog artifacts into a searchable
    structural representation?
-   What constitutes an "index entry" for an analog?
-   How do we organize the repository such that retrieval is fast and
    defensible?

## Pipeline B --- Query / Retrieval Pipeline

    Sparse observations → encode essence → compare to geologic index → retrieve analog(s)

This pipeline answers:

-   How do sparse, incomplete observations become a query in the same
    "essence space" as the database?
-   How is similarity computed when some invariant dimensions are
    missing or unobservable?
-   What retrieval object is returned (single analog, ranked set,
    posterior over analogs)?

The core coupling requirement is:

    The essence representation used in Pipeline A must be compatible with the essence representation inferred from sparse data in Pipeline B.

This document exists to define the context and questions that govern
both pipelines.

------------------------------------------------------------------------

# 3. Purpose of This Document

This document does NOT prescribe implementation details.

It ensures that any indexing/retrieval architecture is explicitly
governed by a rigorously defined notion of structural invariance, and it
frames the necessary questions that must be answered in order for the
two pipelines to function coherently.

------------------------------------------------------------------------

# 4. Core Structural Commitment

For this phase of the research, ESSENCE is defined as:

    Multiscale structural invariance independent of generator artifacts.

Response invariance is deferred to future work.

The purpose of determining essence is therefore:

    To identify invariant structural descriptors that can organize analog repositories (Pipeline A)
    and be inferable, at least partially, from sparse observations (Pipeline B).

------------------------------------------------------------------------

# 5. Why Essence Matters for Both Pipelines

If structural invariants can be formally identified and validated, then:

-   Pipeline A can organize the repository around scientifically
    justified equivalence classes.
-   Pipeline B can query the repository using structurally meaningful
    constraints rather than subjective matching.

Without a rigorous essence definition:

-   Pipeline A collapses into heuristic clustering.
-   Pipeline B collapses into ad hoc similarity judgments.

Essence determination is the bridge that makes both pipelines
principled.

------------------------------------------------------------------------

# 6. Multimodal Nature of Inputs (Analog + Query)

Both pipelines must handle multimodality.

## Analog side (Pipeline A) may include:

-   Full-resolution geological images
-   3D reservoir models
-   Seismic volumes
-   Core / outcrop photographs
-   Experimental measurements
-   Incomplete but rich simulation models

## Query side (Pipeline B) may include:

-   Well logs (1D sparse vertical profiles)
-   Sparse facies labels or interpreted intervals
-   Partial seismic sections / patches
-   Indirect measurements (plume extent proxies, pressure data, etc.)

The architecture must therefore answer:

    How can the essence representation be defined so that it supports consistent comparison between dense analogs and sparse queries across modalities?

------------------------------------------------------------------------

# 7. Questions Governing Pipeline A: Building the Geologic Index

## 7.1 Index Unit and Granularity

-   What is the unit of indexing: entire analog, subvolume, window,
    object graph, stratigraphic package?
-   Is the index static (one entry per analog) or multiscale (multiple
    entries per analog)?

## 7.2 Descriptor Admissibility

-   Which descriptors qualify as "essence carriers" for index
    construction?
-   What evidence must a descriptor satisfy (stability, severe tests, MI
    constraints)?
-   How do we prevent the index from encoding generator identity?

## 7.3 Organization / Schema

-   Is the index best represented as:
    -   metric space + ANN search?
    -   hierarchical embedding (e.g., hyperbolic) for depositional
        taxonomy?
    -   knowledge graph for relational geological structure?
    -   hybrid (graph + vectors + metadata)?

------------------------------------------------------------------------

# 8. Questions Governing Pipeline B: Encoding Sparse Queries

## 8.1 Inference of Essence from Sparse Data

-   What portion of essence is inferable from wells alone?
-   What invariants require 2D/3D coverage?
-   How do we represent "unknown" or "uninferable" invariants in the
    query encoding?

## 8.2 Compatibility Constraint

-   Does the query encoder map sparse observations into the same
    descriptor space as analog encodings?
-   If not, is there a learned alignment layer, and how is it validated
    to avoid artifact leakage?

## 8.3 Uncertainty Representation

-   Does Pipeline B output a point estimate, a distribution, or a
    constraint set in descriptor space?
-   How is uncertainty calibrated as a function of sparsity?

------------------------------------------------------------------------

# 9. Questions About Similarity and Retrieval Coupling

Once both pipelines produce comparable representations, the system must
decide:

-   What similarity metric is used and why is it justified?
-   How is similarity computed under missing invariant dimensions?
-   Is retrieval nearest-neighbor, constrained optimization, or
    probabilistic ranking?
-   Should retrieval return:
    -   single best analog,
    -   top-k analog set,
    -   equivalence class / cluster,
    -   posterior weights over candidate analogs?

------------------------------------------------------------------------

# 10. Evidence Hierarchy Governing Essence Claims

Evidence levels (strongest → weakest):

1.  Mathematical invariance theorems (e.g., PH stability)
2.  Severe adversarial testing
3.  Information-theoretic validation
4.  Cross-domain structural validation
5.  Real-data validation
6.  Generator invariance (LOGO) --- necessary but insufficient
7.  Expert agreement

The evidence hierarchy governs:

-   Descriptor admissibility (Pipeline A)
-   Query encoding validation (Pipeline B)
-   Similarity metric justification (coupling layer)

------------------------------------------------------------------------

# 11. Essence as Enabler, Not Endpoint

Determining structural essence does not complete the project.

It enables:

-   A principled schema for organizing geological repositories (Pipeline
    A)
-   Multimodal structural alignment
-   Sparse-data-conditioned retrieval (Pipeline B)
-   Bayesian uncertainty interpretation
-   Transparent justification of analog selection

------------------------------------------------------------------------

# 12. Summary

This document restores and centers:

-   The original dissertation research question,
-   The explicit two-pipeline architecture,
-   The multimodal nature of both analog and query data,
-   The question-driven requirements for indexing and sparse retrieval,
-   The role of essence as the enabling structural abstraction.

End of Document.
