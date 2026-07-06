# AMC Research Archive

Personal research archive for **Automatic Modulation Classification (AMC)** and model compression studies.

This repository is an [Obsidian](https://obsidian.md/) vault synced with GitHub. Literature notes are imported from Zotero; research models and experiment summaries are maintained here for portfolio sharing and long-term organization.

## Literature Notes

| Paper | Key Idea | My Review Link | HTML Report |
|-------|----------|----------------|-------------|
| FEA-T (Chen 2023) | Frame-wise Embedding Transformer | [Read Review](AMC_Papers/@chenAbandonLocalityFrameWise2023.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/FEA-T.html) |
| AWN (Zhang 2023) | Adaptive Wavelet Network | [Read Review](AMC_Papers/@zhangAutomaticModulationClassification2023.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/AWN.html) |
| CV-TRN (Li 2024) | Complex-Valued Transformer | [Read Review](AMC_Papers/@liComplexValuedTransformerAutomatic2024.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/CV-TRN.html) |
| ULCNN (Guo 2024) | Ultralight CNN for UAV | [Read Review](AMC_Papers/@guoUltralightConvolutionalNeural2024.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/ULCNN.html) |
| RepCCNet (Tang 2024) | Reparameterization Causal CNN | [Read Review](AMC_Papers/@tangReparameterizationCausalConvolutional2024.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/RepCCNet.html) |
| CPPCNet (Xin 2025) | Complex Partial Pointwise CNN | [Read Review](AMC_Papers/@xinCPPCNetHighPerformanceLowComplexity2025.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/CPPCNet.html) |
| IDHNet (Li 2026) | CNN-Transformer Hybrid | [Read Review](AMC_Papers/@liIDHNetCNNTransformerHybrid2026.md) | [View HTML](https://linjh38.github.io/AMC-Research-Archive/IDHNet.html) |

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
3. Export Zotero HTML report → `AMC_Papers/reports/{short-name}.html`
4. Fill in `## AMC 연구 적용 포인트` for research ideas
5. Document models in `My_Research/Models/` and results in `Experiments/`
6. Commit with prefixes: `literature:`, `model:`, `experiment:`, `hub:`

## Obsidian Setup

Open this folder as an Obsidian vault. Recommended community plugins:

- Zotero Desktop Connector (configured)
- Templater
- Dataview (enable in Settings → Community plugins, then reload Literature Index)

## HTML Reports (GitHub Pages)

Zotero HTML reports are published via **GitHub Pages** (`text/html`로 렌더링).  
`raw.githubusercontent.com` 링크는 HTML을 소스 코드로 보여주므로 사용하지 않습니다.

### 최초 1회 설정 (필수)

1. [Repository → Settings → Pages](https://github.com/LinJH38/AMC-Research-Archive/settings/pages) 열기
2. **Build and deployment → Source**: `Deploy from a branch` 선택
3. **Branch**: `gh-pages` / `/ (root)` 선택 → **Save**
4. 1~2분 후 [CV-TRN 리포트](https://linjh38.github.io/AMC-Research-Archive/CV-TRN.html)가 정상 렌더링되는지 확인

`main`에 push하면 `Deploy HTML reports to GitHub Pages` 워크플로가 `gh-pages` 브랜치를 자동 갱신합니다.

Base URL: `https://linjh38.github.io/AMC-Research-Archive/`
