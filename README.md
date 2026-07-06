# AMC Research Archive

Personal research archive for **Automatic Modulation Classification (AMC)** and model compression studies.

This repository is an [Obsidian](https://obsidian.md/) vault synced with GitHub. Literature notes are imported from Zotero; research models and experiment summaries are maintained here for portfolio sharing and long-term organization.

## Literature Notes

| Paper | Key Idea | Note |
|-------|----------|------|
| FEA-T (Chen 2023) | Frame-wise Embedding Transformer | [Read](AMC_Papers/@chenAbandonLocalityFrameWise2023.md) |
| AWN (Zhang 2023) | Adaptive Wavelet Network | [Read](AMC_Papers/@zhangAutomaticModulationClassification2023.md) |
| CV-TRN (Li 2024) | Complex-Valued Transformer | [Read](AMC_Papers/@liComplexValuedTransformerAutomatic2024.md) |
| ULCNN (Guo 2024) | Ultralight CNN for UAV | [Read](AMC_Papers/@guoUltralightConvolutionalNeural2024.md) |
| RepCCNet (Tang 2024) | Reparameterization Causal CNN | [Read](AMC_Papers/@tangReparameterizationCausalConvolutional2024.md) |
| CPPCNet (Xin 2025) | Complex Partial Pointwise CNN | [Read](AMC_Papers/@xinCPPCNetHighPerformanceLowComplexity2025.md) |
| IDHNet (Li 2026) | CNN-Transformer Hybrid | [Read](AMC_Papers/@liIDHNetCNNTransformerHybrid2026.md) |

## My Research

- [Research Roadmap](00_Hub/Research%20Roadmap.md)
- [AMC Research Hub (Obsidian MOC)](00_Hub/AMC%20Research%20Hub.md)
- [Literature Index](00_Hub/Literature%20Index.md)
- [Models](My_Research/Models/)

## Experiments

- [Datasets](Experiments/datasets.md)
- (Results will be added under `Experiments/{model-name}/results/`)

## Workflow

1. Annotate papers in **Zotero**
2. Import via **Obsidian Zotero Desktop Connector** → `AMC_Papers/@{citekey}.md`
3. Fill in `## AMC 연구 적용 포인트` for research ideas
4. Document models in `My_Research/Models/` and results in `Experiments/`
5. Commit with prefixes: `literature:`, `model:`, `experiment:`, `hub:`

## Obsidian Setup

Open this folder as an Obsidian vault. Recommended community plugins:

- Zotero Desktop Connector (configured)
- Templater
- Dataview (enable in Settings → Community plugins, then reload Literature Index)
