---
type: hub
tags: [roadmap, AMC]
---

# Research Roadmap

## Research Direction

Develop a **lightweight CNN + Transformer hybrid** for AMC that:

- Preserves complex I/Q correlation (unlike simple I/Q concatenation)
- Uses wavelet or multi-band feature extraction for frequency-domain priors
- Applies O(N) attention instead of full MHSA for inference efficiency
- Targets **≤15K parameters** with robust low-SNR performance

## Progress

| Phase | Status | Notes |
|-------|--------|-------|
| Literature survey | In progress | 7 papers archived |
| Model design (AWN-Hybrid) | Draft | [[My_Research/Models/awn-hybrid/model-card]] |
| Implementation | Not started | — |
| Experiments (RadioML) | Not started | [[Experiments/datasets]] |

## Key Ideas from Literature

Derived from [[@zhangAutomaticModulationClassification2023]] (AWN):

- Replace fixed Lifting Scheme P/U operators with learnable CNN blocks
- SNR-aware attention across frequency bands
- Multi-band cross-attention (L as Query, H as Key/Value) for noise suppression
- Avoid GAP before temporal correlation learning

Derived from [[@chenAbandonLocalityFrameWise2023]] (FEA-T):

- DB-GLU for FFN parameter reduction (adapt with O(N) attention)
- Frame-wise embedding trade-off (L vs F complexity)
- CNN front-end needed for low-SNR robustness

Derived from [[@liIDHNetCNNTransformerHybrid2026]] (IDHNet):

- I/Q/IQ-fusion triple-path convolution stem
- Lightweight attention backend (EAA-style)

## Next Steps

- [ ] Finalize AWN-Hybrid architecture diagram
- [ ] Implement baseline on RadioML2016.10a
- [ ] Compare against AWN, FEA-T, IDHNet baselines
- [ ] Document first experiment in `Experiments/awn-hybrid/results/summary.md`
