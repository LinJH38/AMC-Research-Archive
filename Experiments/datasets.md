---
type: reference
tags: [AMC, dataset]
---

# Datasets

Reference for AMC benchmark datasets used in literature and planned experiments.

## RadioML2016.10a

- **Classes:** 11 modulation types
- **SNR range:** -20 to 18 dB (2 dB steps)
- **Input:** I/Q, 128 samples per example
- **Used in:** AWN, ULCNN, RepCCNet, IDHNet, CPPCNet

## RadioML2016.10b

- **Classes:** 10 modulation types (no AM-SSB)
- **Used in:** IDHNet, CPPCNet

## RadioML2018.01A

- **Classes:** 24 modulation types
- **Used in:** FEA-T, RepCCNet

## RML22

- **Used in:** IDHNet

## HisarMod2019.1

- **Note:** More realistic channel impairments
- **Used in:** CPPCNet

## Planned Usage

Primary benchmark for AWN-Hybrid: **RadioML2016.10a** (consistent with most surveyed papers).
