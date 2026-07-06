---
type: hub
tags: [MOC, literature]
---

# Literature Index

## Auto-generated (Dataview)

> Enable the **Dataview** community plugin in Obsidian to populate the table below.

```dataview
TABLE tags, file.ctime as "Added"
FROM "AMC_Papers"
WHERE type = "literature_note"
SORT file.name ASC
```

## Manual Index

| Paper | Citekey | My Review | HTML Report | Tags |
|-------|---------|-----------|-------------|------|
| FEA-T | `chenAbandonLocalityFrameWise2023` | [[@chenAbandonLocalityFrameWise2023|Read Review]] | [[AMC_Papers/reports/FEA-T.html|View HTML]] | AMC, Transformer, FEM, DB-GLU |
| AWN | `zhangAutomaticModulationClassification2023` | [[@zhangAutomaticModulationClassification2023|Read Review]] | [[AMC_Papers/reports/AWN.html|View HTML]] | AMC, Wavelet, LiftingScheme |
| CV-TRN | `liComplexValuedTransformerAutomatic2024` | [[@liComplexValuedTransformerAutomatic2024|Read Review]] | [[AMC_Papers/reports/CV-TRN.html|View HTML]] | AMC, Transformer, ComplexValued |
| ULCNN | `guoUltralightConvolutionalNeural2024` | [[@guoUltralightConvolutionalNeural2024|Read Review]] | [[AMC_Papers/reports/ULCNN.html|View HTML]] | AMC, CNN, Lightweight |
| RepCCNet | `tangReparameterizationCausalConvolutional2024` | [[@tangReparameterizationCausalConvolutional2024|Read Review]] | [[AMC_Papers/reports/RepCCNet.html|View HTML]] | AMC, CNN, Causal |
| CPPCNet | `xinCPPCNetHighPerformanceLowComplexity2025` | [[@xinCPPCNetHighPerformanceLowComplexity2025|Read Review]] | [[AMC_Papers/reports/CPPCNet.html|View HTML]] | AMC, ComplexValued, Lightweight |
| IDHNet | `liIDHNetCNNTransformerHybrid2026` | [[@liIDHNetCNNTransformerHybrid2026|Read Review]] | [[AMC_Papers/reports/IDHNet.html|View HTML]] | AMC, HybridArchitecture |

## Adding a New Paper

1. Import from Zotero via Desktop Connector
2. Export Zotero HTML report → `AMC_Papers/reports/{short-name}.html`
3. Fill `## AMC 연구 적용 포인트`
4. Add a row to the manual table above
5. Update [README](../README.md) Literature table
6. `git commit -m "literature: add {citekey}"`
