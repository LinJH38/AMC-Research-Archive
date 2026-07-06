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

| Paper | Citekey | Tags |
|-------|---------|------|
| FEA-T | `chenAbandonLocalityFrameWise2023` | AMC, Transformer, FEM, DB-GLU |
| AWN | `zhangAutomaticModulationClassification2023` | AMC, Wavelet, LiftingScheme |
| CV-TRN | `liComplexValuedTransformerAutomatic2024` | AMC, Transformer, ComplexValued |
| ULCNN | `guoUltralightConvolutionalNeural2024` | AMC, CNN, Lightweight |
| RepCCNet | `tangReparameterizationCausalConvolutional2024` | AMC, CNN, Causal |
| CPPCNet | `xinCPPCNetHighPerformanceLowComplexity2025` | AMC, ComplexValued, Lightweight |
| IDHNet | `liIDHNetCNNTransformerHybrid2026` | AMC, HybridArchitecture |

## Adding a New Paper

1. Import from Zotero via Desktop Connector
2. Fill `## AMC 연구 적용 포인트`
3. Add a row to the manual table above
4. Update [README](../README.md) Literature table
5. `git commit -m "literature: add {citekey}"`
