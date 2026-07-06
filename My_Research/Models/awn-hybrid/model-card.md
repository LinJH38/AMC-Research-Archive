---
type: model_card
model_name: awn-hybrid
status: draft
tags: [AMC, model, Wavelet, HybridArchitecture]
created: 2026-07-06
---

# AWN-Hybrid

## Motivation

Combine the adaptive wavelet decomposition strengths of [[@zhangAutomaticModulationClassification2023]] (AWN) with lightweight O(N) attention and CNN-Transformer hybrid ideas from [[@liIDHNetCNNTransformerHybrid2026]] and [[@chenAbandonLocalityFrameWise2023]].

Target: **≤15K parameters** with robust low-SNR AMC on RadioML datasets.

## Related Literature

- [[@zhangAutomaticModulationClassification2023]] — Lifting scheme, multi-band features, channel attention
- [[@chenAbandonLocalityFrameWise2023]] — DB-GLU, frame embedding trade-offs
- [[@liComplexValuedTransformerAutomatic2024]] — Complex-valued embedding, RPO augmentation
- [[@liIDHNetCNNTransformerHybrid2026]] — I/Q/IQ-fusion triple-path stem
- [[@xinCPPCNetHighPerformanceLowComplexity2025]] — Complex-valued lightweight convolutions

## Architecture (Draft)

```
Input I/Q [B, 2, N]
  → Learnable Lifting Scheme (P/U as CNN blocks)
  → Multi-band feature maps (L, H at each level)
  → Temporal alignment (interpolation across bands)
  → SNR-aware / Multi-band Cross-Attention (O(N))
  → Classification head
```

## Key Design Decisions

| Decision | Rationale |
|----------|-----------|
| Learnable P/U operators | AWN paper: fixed lifting limits adaptability |
| No GAP before attention | Preserve temporal correlation across bands |
| O(N) attention | FEA-T/CV-TRN: full MHSA too slow for deployment |
| CNN front-end | FEA-T: Transformer-only fails at low SNR |
| RPO augmentation | CV-TRN: phase-invariant training |

## Target Metrics

| Metric | Target |
|--------|--------|
| Parameters | ≤ 15K |
| Dataset | RadioML2016.10a |
| Avg accuracy | TBD (beat AWN baseline) |
| Inference time | < 1 ms/sample (edge target) |

## Open Questions

- Continuous frequency representation vs discrete T+1 bands (from AWN notes)
- Analog modulation silent-period handling (WBFM, AM-DSB)
- High-order QAM discrimination at low SNR

## Implementation

- Code: `src/` (to be created)
- Config: `Experiments/awn-hybrid/configs/`

## Experiment Log

- [[Experiments/awn-hybrid/results/summary]]
