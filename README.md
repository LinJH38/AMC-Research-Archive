# AMC Research Archive

Personal research archive for **Automatic Modulation Classification (AMC)** and model compression studies.

This repository is an [Obsidian](https://obsidian.md/) vault synced with GitHub. Literature notes are imported from Zotero; research models and experiment summaries are maintained here for portfolio sharing and long-term organization.

## Literature Notes

| Paper | Key Idea | My Review Link | HTML Report |
|-------|----------|----------------|-------------|
| FEA-T (Chen 2023) | Frame-wise Embedding Transformer | [Read Review](AMC_Papers/@chenAbandonLocalityFrameWise2023.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/FEA-T.htm) |
| AWN (Zhang 2023) | Adaptive Wavelet Network | [Read Review](AMC_Papers/@zhangAutomaticModulationClassification2023.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/AWN.htm) |
| CV-TRN (Li 2024) | Complex-Valued Transformer | [Read Review](AMC_Papers/@liComplexValuedTransformerAutomatic2024.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/CV-TRN.htm) |
| ULCNN (Guo 2024) | Ultralight CNN for UAV | [Read Review](AMC_Papers/@guoUltralightConvolutionalNeural2024.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/ULCNN.htm) |
| RepCCNet (Tang 2024) | Reparameterization Causal CNN | [Read Review](AMC_Papers/@tangReparameterizationCausalConvolutional2024.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/RepCCNet.htm) |
| CPPCNet (Xin 2025) | Complex Partial Pointwise CNN | [Read Review](AMC_Papers/@xinCPPCNetHighPerformanceLowComplexity2025.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/CPPCNet.htm) |
| IDHNet (Li 2026) | CNN-Transformer Hybrid | [Read Review](AMC_Papers/@liIDHNetCNNTransformerHybrid2026.md) | [View HTML](https://raw.githubusercontent.com/LinJH38/AMC-Research-Archive/main/AMC_Papers/reports/IDHNet.htm) |

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
3. Export Zotero HTML report → `AMC_Papers/reports/{short-name}.htm`
4. Fill in `## AMC 연구 적용 포인트` for research ideas
5. Document models in `My_Research/Models/` and results in `Experiments/`
6. Commit with prefixes: `literature:`, `model:`, `experiment:`, `hub:`

## Obsidian Setup

Open this folder as an Obsidian vault. Recommended community plugins:

- Zotero Desktop Connector (configured)
- Templater
- Dataview (enable in Settings → Community plugins, then reload Literature Index)
