# Qualia Convergence Framework
## Implementation Specification

### Practical Research Guide with Decision Points and Phased Complexity

---

**Document Purpose**: This document provides the **practical implementation roadmap** for the Qualia Convergence Framework. It specifies phased development, decision trees for architectural choices, simplifying assumptions appropriate at each phase, validation checkpoints, and contingency plans.

**Document Type**: Implementation Specification (2 of 3)
- **Complete Vision**: What we are building (see companion document)
- **This document**: How we build it (phased approach with decision points)
- **Architecture Decision Record**: Why we made these choices

**Version**: 6.3 — January 2026 (Updated with Query 17-20 findings)

---

# Part I: Implementation Philosophy

## 1.1 Core Principles

### Build Incrementally, Validate Continuously

Each phase must produce:
1. A **working system** (even if simplified)
2. **Validation evidence** (metrics against targets)
3. **Decision data** (to inform next phase)

### Simplify Strategically, Not Permanently

Simplifications are **temporary constraints**, not permanent limitations. Each simplification should have:
- Clear rationale
- Defined upgrade path
- Trigger conditions for when to upgrade

### Validate Before Extending

Never add complexity until current complexity is validated. The pattern is:
```
Implement → Validate → Decision Point → Extend or Pivot
```

---

## 1.2 Phase Overview

| Phase | Focus | Key Deliverable | Validation Target |
|-------|-------|-----------------|-------------------|
| **Phase 1** | Generator + Basic Embeddings | Working retrieval system | Cluster purity > 0.6 |
| **Phase 2** | Full Three-Pathway Architecture | Multi-pathway fusion | P@10 > 0.7 |
| **Phase 3** | Hyperbolic + Neural Process | Hierarchy + uncertainty | LOGO degradation < 25% |
| **Phase 4** | Complete Sākṣī Validation | All 10 tests | Survival matrix applied |
| **Phase 5** | Integration + Refinement | Publication-ready system | All targets met |

---

# Part II: Phase 1 — Foundation

## 2.1 Objectives

1. ✅ Implement principle-based generator (all three environments)
2. ✅ Implement basic learned pathway (DINOv2)
3. ✅ Implement basic retrieval system
4. ✅ Establish validation infrastructure

## 2.2 Generator Implementation

**Why Build a Generator?** (Validated by Queries 17-20)

Literature validation confirms four critical findings:
1. **Query 17**: Rule-based generators are "indispensable for scenarios where interpretability and strict adherence to expert geological rules are paramount"
2. **Query 18**: "The absence of widely accepted benchmark datasets for geological image classification is a major limitation"
3. **Query 19**: Aeolian/estuarine simulators dominated by expensive process-based (Delft3D) or emergent CA (Werner); principle-based approach fills distinct niche for ML training
4. **Query 20**: Deep generative models (GANs/VAEs/diffusion) focus on surrogate simulation (replacing numerical solvers), not training data generation with known ground truth

Our principle-based generator addresses all four: interpretable parameters, standardized multi-environment training data with known ground truth, computational efficiency for ML-scale dataset generation, AND distinct purpose from deep generative approaches.

### 2.2.1 Fluvial Generator

**Simplification (Phase 1)**: Start with meandering only, add braided and anastomosing after validation.

```python
# Phase 1 fluvial generator structure
class FluvialGenerator:
    def __init__(self, style='meandering'):
        self.style = style
        self.params = DEFAULT_PARAMS[style]
    
    def generate(self, params=None):
        if params is None:
            params = self.sample_params()
        
        canvas = self.initialize_canvas()
        centerline = self.generate_centerline(params)
        channel = self.generate_channel(centerline, params)
        features = self.add_features(channel, params)  # levees, bars, etc.
        
        if not self.validate(features, params):
            return self.generate(params)  # Rejection sampling
        
        return features, params
```

**Decision Point 1.1**: After implementing meandering:
- If acceptance rate > 80% → proceed to braided
- If acceptance rate < 50% → debug/refine before proceeding

### 2.2.2 Aeolian Generator

**Simplification (Phase 1)**: Implement transverse dunes first (simplest morphology).

**Decision Point 1.2**: After transverse validation:
- Add barchan (moderate complexity)
- Add linear (highest complexity, bidirectional wind)

### 2.2.3 Estuarine Generator

**Simplification (Phase 1)**: Start with tide-dominated only.

**Rationale**: Clearest morphological signatures, best-documented in Jiwei et al.

### 2.2.4 Generator Validation Checklist

| Environment | Style | Status | Acceptance Rate | Metric Compliance |
|-------------|-------|--------|-----------------|-------------------|
| Fluvial | Meandering | [ ] | ___% | β: [ ] Aniso: [ ] |
| Fluvial | Braided | [ ] | ___% | β: [ ] Aniso: [ ] |
| Fluvial | Anastomosing | [ ] | ___% | β: [ ] Aniso: [ ] |
| Aeolian | Transverse | [ ] | ___% | Crest: [ ] Cont: [ ] |
| Aeolian | Barchan | [ ] | ___% | Crest: [ ] Horn: [ ] |
| Aeolian | Linear | [ ] | ___% | Crest: [ ] Cont: [ ] |
| Estuarine | Tide-dominated | [ ] | ___% | Ebb/flood: [ ] Aspect: [ ] |
| Estuarine | Wave-dominated | [ ] | ___% | Ebb/flood: [ ] Aspect: [ ] |
| Estuarine | Mixed | [ ] | ___% | Ebb/flood: [ ] Aspect: [ ] |

---

## 2.3 Basic Learned Pathway (DINOv2)

### 2.3.1 Implementation

**Simplification (Phase 1)**: Use frozen DINOv2 features, no fine-tuning initially.

```python
class BasicLearnedPathway:
    def __init__(self, model_name='dinov2_vitb14'):
        self.backbone = torch.hub.load('facebookresearch/dinov2', model_name)
        self.backbone.eval()  # Frozen in Phase 1
        
    def extract(self, images):
        with torch.no_grad():
            features = self.backbone(images)
        return features  # [B, 768]
```

**Rationale**: Query 7 shows DINOv2 achieves "near-perfect accuracy" even without fine-tuning. Validate this claim first.

**Decision Point 1.3**: After basic DINOv2 evaluation:
- If cluster purity > 0.6 with frozen features → consider delaying fine-tuning
- If cluster purity < 0.5 → implement LoRA fine-tuning immediately

### 2.3.2 Fine-Tuning (If Needed)

```python
from peft import LoraConfig, get_peft_model

class FineTunedLearnedPathway:
    def __init__(self, model_name='dinov2_vitb14', lora_rank=8):
        self.backbone = torch.hub.load('facebookresearch/dinov2', model_name)
        
        lora_config = LoraConfig(
            r=lora_rank,
            lora_alpha=16,
            target_modules=['qkv'],  # Attention layers
            lora_dropout=0.1
        )
        self.backbone = get_peft_model(self.backbone, lora_config)
```

---

## 2.4 Basic Retrieval System

### 2.4.1 Implementation

**Simplification (Phase 1)**: k-NN retrieval in Euclidean space.

```python
class BasicRetrievalSystem:
    def __init__(self, embedding_dim=768):
        self.index = faiss.IndexFlatL2(embedding_dim)
        self.metadata = []  # Store (class_label, params) for each embedded pattern
        
    def index_patterns(self, patterns, labels, params):
        embeddings = self.encoder.extract(patterns)
        self.index.add(embeddings.numpy())
        self.metadata.extend(zip(labels, params))
        
    def retrieve(self, query, k=10):
        query_emb = self.encoder.extract(query)
        distances, indices = self.index.search(query_emb.numpy(), k)
        
        results = []
        for idx, dist in zip(indices[0], distances[0]):
            label, params = self.metadata[idx]
            results.append({
                'index': idx,
                'distance': dist,
                'label': label,
                'params': params
            })
        return results
```

### 2.4.2 Phase 1 Validation Targets

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Cluster Purity (ARI)** | > 0.6 | sklearn.metrics.adjusted_rand_score |
| **P@1** | > 0.7 | Top-1 retrieval accuracy |
| **P@10** | > 0.5 | Top-10 contains correct class |

**Decision Point 1.4**: Phase 1 completion criteria:
- All generators producing valid outputs ✓
- Cluster purity > 0.6 ✓
- P@1 > 0.7 ✓
- → Proceed to Phase 2

---

# Part III: Phase 2 — Three-Pathway Architecture

## 3.1 Objectives

1. ✅ Implement classical pathway (variogram, fractal, connectivity)
2. ✅ Implement topological pathway (persistent homology)
3. ✅ Implement pathway fusion
4. ✅ Validate multi-pathway improvement

## 3.2 Classical Pathway

### 3.2.1 Implementation

```python
class ClassicalPathway:
    def __init__(self):
        self.variogram = VariogramAnalyzer()
        self.fractal = FractalAnalyzer()
        self.connectivity = ConnectivityAnalyzer()
        
    def extract(self, images):
        features = []
        for img in images:
            vario_feats = self.variogram.compute(img)      # ~20 dim
            fractal_feats = self.fractal.compute(img)      # ~10 dim
            conn_feats = self.connectivity.compute(img)    # ~20 dim
            features.append(np.concatenate([vario_feats, fractal_feats, conn_feats]))
        return np.array(features)  # [B, ~50]
```

### 3.2.2 Variogram Computation

```python
class VariogramAnalyzer:
    def __init__(self, directions=[0, 45, 90, 135], max_lag=50):
        self.directions = directions
        self.max_lag = max_lag
        
    def compute(self, image):
        features = []
        
        # Omnidirectional variogram
        omni_vario = compute_variogram(image, direction=None, max_lag=self.max_lag)
        sill, range_, nugget = fit_variogram_model(omni_vario)
        features.extend([sill, range_, nugget])
        
        # Directional variograms
        for direction in self.directions:
            dir_vario = compute_variogram(image, direction=direction, max_lag=self.max_lag)
            sill_d, range_d, nugget_d = fit_variogram_model(dir_vario)
            features.extend([sill_d, range_d, nugget_d])
        
        # Anisotropy ratio
        anisotropy = compute_anisotropy(image)
        features.append(anisotropy)
        
        return np.array(features)
```

---

## 3.3 Topological Pathway

### 3.3.1 Implementation

**Simplification (Phase 2)**: H₀ and H₁ only (skip H₂ for 2D images).

```python
from gtda.homology import VietorisRipsPersistence
from gtda.diagrams import PersistenceEntropy, Amplitude

class TopologicalPathway:
    def __init__(self, homology_dims=[0, 1]):
        self.homology_dims = homology_dims
        self.vr = VietorisRipsPersistence(homology_dimensions=homology_dims)
        self.entropy = PersistenceEntropy()
        self.amplitude = Amplitude()
        
    def extract(self, images):
        features = []
        for img in images:
            # Convert to point cloud (skeleton)
            skeleton = self.skeletonize(img)
            points = np.array(np.where(skeleton)).T
            
            # Compute persistent homology
            diagrams = self.vr.fit_transform([points])
            
            # Vectorize
            entropy_feats = self.entropy.fit_transform(diagrams)
            amplitude_feats = self.amplitude.fit_transform(diagrams)
            
            features.append(np.concatenate([entropy_feats.flatten(), 
                                            amplitude_feats.flatten()]))
        return np.array(features)  # [B, ~20-50]
```

### 3.3.2 TDA Hypothesis Test

**Hypothesis**: H₁ (loops/cycles) discriminates braided from meandering channels even when variograms are matched.

**Test Protocol**:
```
1. Generate matched-variogram pairs:
   - Meandering pattern A with variogram V
   - Braided pattern B with variogram ≈ V (within 5%)
   
2. Compute H₁ features for both

3. Test: Can classifier separate A from B using only H₁?
   - If accuracy > 70%: Hypothesis supported
   - If accuracy < 60%: Hypothesis not supported
```

**Decision Point 2.1**: TDA hypothesis outcome:
- If supported → TDA becomes core pathway
- If not supported → TDA remains as ablation study component

---

## 3.4 Pathway Fusion

### 3.4.1 Implementation Options

**Option A: Simple Concatenation + MLP** (Start here)

```python
class SimpleFusion(nn.Module):
    def __init__(self, classical_dim=50, learned_dim=768, topo_dim=30, output_dim=256):
        super().__init__()
        self.projection = nn.Sequential(
            nn.Linear(classical_dim + learned_dim + topo_dim, 512),
            nn.ReLU(),
            nn.Linear(512, output_dim)
        )
        
    def forward(self, classical, learned, topo):
        concat = torch.cat([classical, learned, topo], dim=-1)
        return self.projection(concat)
```

**Option B: Cross-Attention Fusion** (Upgrade if needed)

```python
class CrossAttentionFusion(nn.Module):
    def __init__(self, input_dims, hidden_dim=256, num_heads=8, output_dim=256):
        super().__init__()
        self.projections = nn.ModuleList([
            nn.Linear(dim, hidden_dim) for dim in input_dims
        ])
        self.attention = nn.MultiheadAttention(hidden_dim, num_heads, batch_first=True)
        self.output = nn.Linear(hidden_dim, output_dim)
        
    def forward(self, *pathways):
        projected = [proj(p) for proj, p in zip(self.projections, pathways)]
        stacked = torch.stack(projected, dim=1)  # [B, num_pathways, hidden_dim]
        attended, _ = self.attention(stacked, stacked, stacked)
        pooled = attended.mean(dim=1)
        return self.output(pooled)
```

**Decision Point 2.2**: Fusion architecture:
- Start with Option A (simple concatenation)
- If P@10 improves < 5% over single pathway → keep simple
- If P@10 improves > 10% → upgrade to Option B

### 3.4.2 Phase 2 Validation Targets

| Metric | Target | Phase 1 Baseline | Phase 2 Target |
|--------|--------|------------------|----------------|
| **ARI** | Improvement | 0.6 | > 0.7 |
| **P@10** | Improvement | 0.5 | > 0.7 |
| **Pathway agreement** | New | N/A | Disagreement < 0.3 |

**Decision Point 2.3**: Phase 2 completion criteria:
- Three pathways implemented and fused ✓
- P@10 > 0.7 ✓
- Multi-pathway improves over single pathway ✓
- → Proceed to Phase 3

---

# Part IV: Phase 3 — Hyperbolic Embeddings + Neural Process

## 4.1 Objectives

1. ✅ Implement hyperbolic projection layer
2. ✅ Implement Neural Process query encoder
3. ✅ Run LOGO validation
4. ✅ Calibrate uncertainty

## 4.2 Hyperbolic Projection

### 4.2.1 Implementation

```python
import geoopt

class HyperbolicProjection(nn.Module):
    def __init__(self, input_dim=256, output_dim=128, curvature=1.0):
        super().__init__()
        self.ball = geoopt.PoincareBall(c=curvature)
        self.fc = nn.Linear(input_dim, output_dim)
        
    def forward(self, euclidean_features):
        # Project to tangent space at origin
        tangent = self.fc(euclidean_features)
        
        # Exponential map: tangent space → Poincaré ball
        hyperbolic = self.ball.expmap0(tangent)
        
        return hyperbolic
```

### 4.2.2 Hyperbolic Distance and Loss

```python
def hyperbolic_distance(x, y, ball):
    """Compute distance in Poincaré ball."""
    return ball.dist(x, y)

class HyperbolicProxyAnchorLoss(nn.Module):
    def __init__(self, num_classes, embedding_dim, curvature=1.0, margin=0.1, alpha=32):
        super().__init__()
        self.ball = geoopt.PoincareBall(c=curvature)
        self.proxies = geoopt.ManifoldParameter(
            self.ball.random(num_classes, embedding_dim),
            manifold=self.ball
        )
        self.margin = margin
        self.alpha = alpha
        
    def forward(self, embeddings, labels):
        # Compute distances to all proxies
        dist_matrix = torch.cdist(
            self.ball.logmap0(embeddings),
            self.ball.logmap0(self.proxies)
        )
        # ... rest of proxy-anchor loss computation
```

### 4.2.3 Decision Point 3.1: Hyperbolic vs Euclidean

**Ablation Study**:
```
1. Train identical system with:
   - Euclidean projection + Euclidean loss
   - Hyperbolic projection + Hyperbolic loss
   
2. Compare on:
   - P@10 overall
   - P@10 within-hierarchy (e.g., meandering vs braided)
   - P@10 cross-hierarchy (e.g., fluvial vs aeolian)
   
3. Decision:
   - If hyperbolic improves within-hierarchy P@10 by > 5%: Use hyperbolic
   - If no improvement: Document as negative result, use Euclidean
```

---

## 4.3 Neural Process Query Encoder

### 4.3.1 Implementation

```python
class NeuralProcessEncoder(nn.Module):
    def __init__(self, observation_dim, hidden_dim=256, latent_dim=128):
        super().__init__()
        
        # Per-observation encoder
        self.obs_encoder = nn.Sequential(
            nn.Linear(observation_dim, hidden_dim),
            nn.ReLU(),
            nn.Linear(hidden_dim, hidden_dim)
        )
        
        # Self-attention for set aggregation
        self.attention = nn.MultiheadAttention(hidden_dim, num_heads=4, batch_first=True)
        
        # Latent distribution parameters
        self.mu_net = nn.Linear(hidden_dim, latent_dim)
        self.sigma_net = nn.Linear(hidden_dim, latent_dim)
        
    def forward(self, observations, mask=None):
        """
        observations: [B, N, obs_dim] where N is variable
        mask: [B, N] boolean, True for valid observations
        """
        # Encode each observation
        h = self.obs_encoder(observations)  # [B, N, hidden_dim]
        
        # Self-attention (masked)
        if mask is not None:
            attn_mask = ~mask
        else:
            attn_mask = None
        h, _ = self.attention(h, h, h, key_padding_mask=attn_mask)
        
        # Aggregate (mean over valid observations)
        if mask is not None:
            h = (h * mask.unsqueeze(-1)).sum(dim=1) / mask.sum(dim=1, keepdim=True).clamp(min=1)
        else:
            h = h.mean(dim=1)
        
        # Latent distribution
        mu = self.mu_net(h)
        sigma = F.softplus(self.sigma_net(h)) + 1e-6  # Ensure positive
        
        return mu, sigma
```

### 4.3.2 Training with Variable Sparsity

```python
def train_np_step(complete_patterns, encoder, optimizer):
    """Train NP with synthetic sparse observations."""
    
    # Sample number of observations (simulate sparsity)
    n_obs = torch.randint(1, 20, (1,)).item()
    
    # Sample observation locations
    obs_locs = sample_locations(complete_patterns, n_obs)
    
    # Extract observations at those locations
    observations = extract_observations(complete_patterns, obs_locs)
    
    # Encode sparse observations
    mu, sigma = encoder(observations)
    
    # Target: embedding of complete pattern
    target_emb = embed_complete(complete_patterns)
    
    # Loss: reconstruction + KL
    recon_loss = F.mse_loss(mu, target_emb)
    kl_loss = 0.5 * (mu**2 + sigma**2 - torch.log(sigma**2) - 1).sum(dim=-1).mean()
    
    loss = recon_loss + 0.1 * kl_loss
    
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
    
    return loss.item()
```

### 4.3.3 Decision Point 3.2: NP Complexity

**Options**:
- **Simple NP**: Single aggregation, diagonal covariance
- **Attentive NP**: Cross-attention, full covariance
- **Transformer NP**: Multiple attention layers

**Start with Simple NP**. Upgrade if:
- Calibration (ECE) > 0.15 with simple
- Graceful degradation test fails (see below)

### 4.3.4 Graceful Degradation Test

```python
def test_graceful_degradation(encoder, test_patterns):
    """Verify uncertainty increases appropriately with sparser observations."""
    
    results = []
    for n_obs in [1, 3, 5, 10, 20]:
        # Extract n observations
        observations = sample_observations(test_patterns, n_obs)
        
        # Encode
        mu, sigma = encoder(observations)
        
        # Record mean uncertainty
        mean_sigma = sigma.mean().item()
        
        # Record retrieval accuracy
        accuracy = compute_retrieval_accuracy(mu, test_patterns)
        
        results.append({
            'n_obs': n_obs,
            'mean_uncertainty': mean_sigma,
            'accuracy': accuracy
        })
    
    # Check: uncertainty should decrease as n_obs increases
    # Check: accuracy should increase as n_obs increases
    
    return results
```

**Expected Behavior**:

| n_obs | Expected σ | Expected Accuracy |
|-------|------------|-------------------|
| 1 | High (> 0.5) | Low (< 0.4) |
| 5 | Medium (0.2-0.4) | Medium (0.5-0.7) |
| 20 | Low (< 0.2) | High (> 0.8) |

---

## 4.4 LOGO Validation

### 4.4.1 Generator Pool

| Generator ID | Type | Description |
|--------------|------|-------------|
| G1 | Principle-based | Our generator (fluvial + aeolian + estuarine) |
| G2 | GAN-based | Info-WGAN or similar (if available) |
| G3 | MPS-based | SNESIM with varied training images |
| G4 | Process-based | Flumy (held-out for primary test) |

**Simplification (Phase 3)**: If G2 and G3 unavailable, use:
- G1: Our generator (meandering + braided + anastomosing)
- G1': Our generator (aeolian styles)
- G1'': Our generator (estuarine styles)
- G4: Flumy (held-out)

### 4.4.2 LOGO Protocol Implementation

```python
def logo_validation(generators, embedding_model):
    """Leave-One-Generator-Out validation."""
    
    results = {}
    
    for held_out_name, held_out_gen in generators.items():
        # Training generators
        train_gens = {k: v for k, v in generators.items() if k != held_out_name}
        
        # Generate training data
        train_data = []
        for gen in train_gens.values():
            train_data.extend(gen.generate_batch(n=1000))
        
        # Train embedding model
        model = embedding_model.clone()
        train(model, train_data)
        
        # Evaluate on held-out generator
        test_data = held_out_gen.generate_batch(n=500)
        
        metrics = {
            'cluster_purity': compute_ari(model, test_data),
            'p_at_10': compute_p_at_k(model, test_data, k=10),
            'transfer_r2': compute_transfer_r2(model, test_data)
        }
        
        results[held_out_name] = metrics
    
    return results
```

### 4.4.3 Phase 3 Validation Targets

| Metric | Target |
|--------|--------|
| **LOGO degradation** | < 25% (each held-out generator) |
| **LOGO degradation** | < 20% (average across generators) |
| **Calibration (ECE)** | < 0.15 |
| **Graceful degradation** | Monotonic σ decrease with n_obs |

**Decision Point 3.3** (Revised February 2026): Phase 3 outcome:
- If LOGO < 20%: Necessary condition met — proceed to corroborating evidence (see 4.5)
- If LOGO 20-30%: Moderate evidence — corroborating evidence critical
- If LOGO > 30%: Need more generators / pivot strategy

**Important**: LOGO alone is necessary but not sufficient for a strong essence claim (see ADR-008 revision, February 2026). Phase 3 now includes corroborating validation steps (Section 4.5).

## 4.5 Corroborating Validation (Evidence Hierarchy)

*Added February 2026 — see Complete Vision Section 4.7 and ADR-008 limitations for rationale.*

The evidence hierarchy requires corroboration beyond LOGO. The following steps are performed in Phase 3 alongside LOGO:

### 4.5.1 Mathematical Invariance Check (Topological Pathway Only)

For the topological pathway, verify that the stability theorem's bounds are meaningful for the data at hand:

```python
def stability_bound_check(images_gen1, images_gen2, ph_pipeline):
    """Verify stability theorem bounds are empirically tight."""

    # Compute PH for both generator outputs
    dgms1 = [ph_pipeline(img) for img in images_gen1]
    dgms2 = [ph_pipeline(img) for img in images_gen2]

    # Compute bottleneck distances between matched pairs
    bottleneck_dists = [bottleneck(d1, d2) for d1, d2 in zip(dgms1, dgms2)]

    # Compute input function distances (sup norm)
    input_dists = [np.max(np.abs(i1 - i2)) for i1, i2 in zip(images_gen1, images_gen2)]

    # Verify: bottleneck ≤ sup norm (stability theorem)
    # Report: how tight is the bound?
    ratios = [b / i for b, i in zip(bottleneck_dists, input_dists) if i > 0]

    return {
        'stability_holds': all(b <= i for b, i in zip(bottleneck_dists, input_dists)),
        'mean_tightness': np.mean(ratios),  # closer to 1 = tighter bound
        'max_tightness': np.max(ratios)
    }
```

**Interpretation**: If the stability bound is empirically tight (ratio > 0.5), topological features are strongly constrained by the mathematics. If loose (ratio < 0.1), the theorem holds but may not be the driving factor in practice.

### 4.5.2 Severe Adversarial Testing

Run the adversarial tests from Chapter 23 of the Complete Vision, assessed for severity:

| Test | Severity Target | Pass Criterion |
|---|---|---|
| Variogram-matched topology swap | High | System distinguishes classes with > 80% accuracy |
| Style transfer attack | High | Classification maintains > 70% accuracy |
| Channel skeleton permutation | Maximum | System detects connectivity change in > 90% of cases |
| Adversarial generator (NEW) | Maximum | H₁ features distinguish images designed to fool them |

### 4.5.3 Information-Theoretic Assessment (Phase 3+)

If MINE or similar estimators are available:

```python
def info_theoretic_assessment(representations, params, generator_ids):
    """Estimate mutual information quantities for essence assessment."""

    # I(f(X); θ | G) — geological info, conditioned on generator
    mi_geology = conditional_mi(representations, params, generator_ids)

    # I(f(X); G | θ) — generator artifacts, conditioned on geology
    mi_artifacts = conditional_mi(representations, generator_ids, params)

    return {
        'geological_info': mi_geology,    # Want: HIGH
        'artifact_contamination': mi_artifacts,  # Want: LOW
        'info_ratio': mi_geology / (mi_geology + mi_artifacts)  # Want: > 0.8
    }
```

**Status**: Proposed for Phase 3+. May require dedicated implementation effort.

### 4.5.4 Revised Phase 3 Completion Criteria

| Evidence Level | Metric | Target | Required? |
|---|---|---|---|
| **Mathematical (L1)** | Stability bounds verified | Theorem holds empirically | Yes (topological pathway) |
| **Severe Testing (L2)** | Adversarial test pass rate | > 70% of severe tests pass | Yes |
| **LOGO (L6)** | LOGO degradation | < 20% average | Yes (necessary condition) |
| **Info-Theoretic (L3)** | Info ratio | > 0.7 | If available |
| **Expert (L7)** | Cohen's κ | > 0.6 | If available |

**Decision Point 3.3** (Revised): Phase 3 outcome now requires multi-level evidence:
- **Strong claim**: L1 + L2 + L6 pass → "topological features have mathematical + empirical invariance evidence"
- **Moderate claim**: L6 passes but L2 marginal → "generator-invariant within pool; severity evidence needed"
- **Weak claim**: L6 passes alone → "necessary condition met; insufficient for essence claim"
- **No claim**: L6 fails → "representation is generator-specific"

---

# Part V: Phase 4 — Complete Sākṣī Validation

## 5.1 Objectives

1. ✅ Implement all 10 Sākṣī tests
2. ✅ Run complete validation suite
3. ✅ Apply claim survival matrix
4. ✅ Document results with pre-committed interpretations

## 5.2 Test Implementation Checklist

| # | Test | Implementation Status | Target | Result |
|---|------|----------------------|--------|--------|
| 1 | Cluster Purity | [ ] | ARI > 0.7 | ___ |
| 2 | Retrieval Precision | [ ] | P@10 > 0.8 | ___ |
| 3 | LOGO | [ ] | Δ < 20% | ___ |
| 4 | Transfer Prediction | [ ] | R² > 0.5 | ___ |
| 5 | Expert Validation | [ ] | κ > 0.6 | ___ |
| 6 | Pathway Convergence | [ ] | Disagreement < 0.2 | ___ |
| 7 | Adversarial Robustness | [ ] | Attack success < 30% | ___ |
| 8 | Calibration | [ ] | ECE < 0.1 | ___ |
| 9 | Mixture Handling | [ ] | Correct high entropy | ___ |
| 10 | Process Correlation | [ ] | r > 0.4 | ___ |

## 5.3 Expert Validation Protocol

### 5.3.1 Survey Design

```
EXPERT VALIDATION SURVEY

For each query-result pair:

1. "Is this retrieved pattern a reasonable analog for the query?"
   [ ] Strongly agree
   [ ] Agree
   [ ] Neutral
   [ ] Disagree
   [ ] Strongly disagree

2. "Would you use this analog for reservoir modeling?"
   [ ] Yes, without modification
   [ ] Yes, with minor adjustments
   [ ] Maybe, needs review
   [ ] No

3. "Rate the similarity (1-5):"
   [ ] 1 (Not similar)
   [ ] 2
   [ ] 3
   [ ] 4
   [ ] 5 (Very similar)

4. "What features make these similar/different?"
   [Free text]
```

### 5.3.2 Expert Recruitment

**Target**: 3-5 sedimentologists with reservoir modeling experience

**Compensation**: Acknowledge in paper, possible co-authorship for substantial contribution

## 5.4 Adversarial Test Implementation

### 5.4.1 Variogram-Matched Topology Swap

```python
def variogram_matched_swap_test(model, class_a_patterns, class_b_patterns):
    """Test robustness to variogram-matched different-topology patterns."""
    
    results = []
    
    for a, b in zip(class_a_patterns, class_b_patterns):
        # Match variograms
        b_matched = match_variogram(b, target_variogram=compute_variogram(a))
        
        # Verify variogram match
        vario_diff = variogram_distance(a, b_matched)
        assert vario_diff < 0.05, "Variogram matching failed"
        
        # Test classification
        pred_a = model.classify(a)
        pred_b_matched = model.classify(b_matched)
        
        # Record if model correctly distinguishes
        correct = (pred_a != pred_b_matched)
        results.append(correct)
    
    attack_success_rate = 1 - np.mean(results)
    return attack_success_rate
```

---

# Part VI: Phase 5 — Integration and Refinement

## 6.1 Objectives

1. ✅ Integrate all components into unified system
2. ✅ Optimize hyperparameters
3. ✅ Prepare publication-ready results
4. ✅ Document failure modes and limitations

## 6.2 Final System Configuration

### 6.2.1 Recommended Configuration (Post-Validation)

```yaml
# config.yaml - Final system configuration

generator:
  environments: [fluvial, aeolian, estuarine]
  samples_per_class: 5000
  
pathways:
  classical:
    variogram_lags: 50
    fractal_boxes: [2, 4, 8, 16, 32, 64]
    output_dim: 50
    
  learned:
    backbone: dinov2_vitb14
    finetune: true
    lora_rank: 8
    output_dim: 768
    
  topological:
    homology_dims: [0, 1]
    vectorization: [entropy, amplitude, landscape]
    output_dim: 30
    
fusion:
  type: cross_attention  # or perceiver_io for full vision
  hidden_dim: 256
  num_heads: 8
  output_dim: 256
  
embedding:
  geometry: hyperbolic  # or euclidean for baseline
  curvature: 1.0
  output_dim: 128
  
query_encoder:
  type: neural_process
  latent_dim: 128
  
training:
  loss: hyperbolic_proxy_anchor
  margin: 0.1
  alpha: 32
  convergence_weight: 0.1
  
validation:
  logo_generators: [ours, flumy, gan, mps]
  calibration_bins: 15
```

## 6.3 Known Limitations Document

```markdown
# Known Limitations

## Scope Limitations

1. **2D Only**: Current implementation handles 2D patterns only.
   - 3D extension requires volumetric generators and TDA
   
2. **Synthetic Focus**: Validation primarily on synthetic data.
   - Real data validation planned but not complete
   
3. **Discrete Hierarchy**: Assumes tree-like class structure.
   - Mixture-of-Archetypes extension needed for continuum

## Technical Limitations

1. **Generator Fidelity**: Principle-based generator has lower physical fidelity than Flumy.
   - Mitigated by LOGO validation across generator types
   
2. **Sparse Observation Types**: NP encoder currently handles spatial sparsity, not modality sparsity.
   - Extension needed for "have seismic but no wells" scenarios
   
3. **Calibration Bounds**: ECE < 0.1 target may not hold for extreme out-of-distribution queries.

4. **Synthetic Data Overfitting Risk** (Query 18 finding): *"Because synthetic data tends to be 'clean' and adheres strictly to the simulation rules, ML models trained on such data may overfit to these idealized features."*
   - Mitigated by: LOGO test with Flumy, acceptance metrics enforcing variability, eventual real-data validation

## Interpretability Limitations

1. **Process Correlation**: r > 0.4 achieved but not r > 0.7.
   - Representations are not fully interpretable in physical terms
   
2. **Adversarial Boundaries**: Some adversarial examples succeed.
   - Attack success rate ~25% indicates partial vulnerability
```

---

# Part VII: Contingency Plans

## 7.1 If LOGO Fails

**Symptom**: LOGO degradation > 30% for all held-out generators

**Diagnosis**:
- Model learning generator artifacts, not geology
- Insufficient generator diversity

**Contingency**:
1. Add more generator diversity (different parameter ranges, noise models)
2. Implement domain adaptation techniques
3. Pivot to "generator fingerprinting" research question

## 7.2 If Hyperbolic Doesn't Help

**Symptom**: No improvement over Euclidean baseline

**Diagnosis**:
- Hierarchy may not be relevant for this task
- Curvature may need tuning

**Contingency**:
1. Tune curvature parameter
2. Try mixed-curvature model
3. Document as negative result, use Euclidean

## 7.3 If TDA Hypothesis Fails

**Symptom**: H₁ doesn't discriminate matched-variogram patterns

**Diagnosis**:
- Topology may not be the distinguishing feature
- Or: preprocessing (skeletonization) loses information

**Contingency**:
1. Try alternative TDA preprocessing
2. Try different vectorization
3. Remove TDA from core claims, report as ablation

## 7.4 If Expert Agreement Low

**Symptom**: κ < 0.4 between experts

**Diagnosis**:
- Task may be inherently ambiguous
- Survey design may be flawed

**Contingency**:
1. Refine survey with expert feedback
2. Report inter-expert agreement as context for model agreement
3. Focus on cases where experts agree

## 7.5 Hybrid Training Strategy (Query 18 Recommendation)

**Literature Recommendation**: *"Utilize synthetic data to generate initial training datasets but always validate and finetune models on field data wherever possible."*

**Implementation Path**:
1. Train initial model on synthetic (principle-based) data
2. Validate transfer via LOGO with Flumy (process-based)
3. When real data becomes available:
   - Fine-tune on real data subset
   - Evaluate sim-to-real transfer gap
   - Recalibrate uncertainty estimates
4. Periodically update as more real data accumulates

---

# Part VIII: Decision Tree Summary

```
START
│
├── Phase 1: Generator + Basic DINOv2
│   │
│   ├── Generator acceptance > 80%?
│   │   ├── YES → Continue
│   │   └── NO → Debug generator
│   │
│   └── Cluster purity > 0.6?
│       ├── YES → Phase 2
│       └── NO → Fine-tune DINOv2
│
├── Phase 2: Three Pathways
│   │
│   ├── TDA hypothesis supported?
│   │   ├── YES → TDA = core pathway
│   │   └── NO → TDA = ablation only
│   │
│   └── Multi-pathway improves P@10?
│       ├── YES → Phase 3
│       └── NO → Simplify fusion, debug
│
├── Phase 3: Hyperbolic + NP
│   │
│   ├── Hyperbolic improves within-hierarchy?
│   │   ├── YES → Use hyperbolic
│   │   └── NO → Use Euclidean, report negative
│   │
│   ├── NP calibration < 0.15?
│   │   ├── YES → Simple NP sufficient
│   │   └── NO → Upgrade to Attentive NP
│   │
│   └── LOGO < 20%?
│       ├── YES → Strong invariance claim
│       ├── 20-30% → Moderate claim
│       └── > 30% → Contingency plan
│
├── Phase 4: Sākṣī Validation
│   │
│   └── Apply claim survival matrix
│       ├── Pass all → Strong essence claim
│       ├── Pass most → Supported claims
│       └── Fail critical → Weaken claims
│
└── Phase 5: Integration
    │
    └── Publication-ready system
```

---

# Appendix A: Quick Reference Tables

## A.1 Validation Targets by Phase

| Phase | Metric | Target | Gate to Next Phase |
|-------|--------|--------|-------------------|
| 1 | Generator acceptance | > 80% | YES |
| 1 | Cluster purity (ARI) | > 0.6 | YES |
| 1 | P@1 | > 0.7 | YES |
| 2 | P@10 | > 0.7 | YES |
| 2 | Multi-pathway improvement | > 5% | YES |
| 3 | LOGO degradation | < 25% | YES |
| 3 | Calibration (ECE) | < 0.15 | YES |
| 4 | All Sākṣī tests | Per matrix | N/A |

## A.2 Component Dependencies

```
Generator → (All other components depend on this)
    │
    ├── Classical Pathway (no dependencies)
    ├── Learned Pathway (requires generator data)
    └── Topological Pathway (no dependencies)
           │
           └── Fusion (requires all three pathways)
                  │
                  ├── Hyperbolic Projection (requires fusion)
                  └── Neural Process (requires fusion)
                         │
                         └── Sākṣī Validation (requires complete system)
```

## A.3 Simplification Levels

| Component | Level 1 (Simplest) | Level 2 | Level 3 (Full Vision) |
|-----------|-------------------|---------|----------------------|
| **Fusion** | Concatenation + MLP | Cross-Attention | Perceiver IO |
| **Geometry** | Euclidean | Hyperbolic | Product Manifold |
| **Query Encoder** | Deterministic | Simple NP | Attentive NP |
| **TDA** | Ablation only | Core pathway | Multi-scale TDA |
| **Retrieval** | k-NN | k-NN + calibration | Bayesian posterior |

---

*Implementation Specification — Version 6.0*
*January 2026*

**Document Purpose**: Practical guide with decision points and phased complexity.
**Companion Documents**: Complete Vision (what to build), Architecture Decision Record (why these choices)
