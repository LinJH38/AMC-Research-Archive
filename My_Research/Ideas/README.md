# Ideas

Unstructured research ideas derived from literature, before they are assigned to a specific model.

## From [[@zhangAutomaticModulationClassification2023]]

- SNR-aware attention: inject estimated SNR as extra input to attention network
- Multi-band cross-attention: Query from L (low-freq trend), Key/Value from H (high-freq detail)
- Interpolate band sequences to equal length before concatenation + PWConv1D

## From [[@chenAbandonLocalityFrameWise2023]]

- DB-GLU in FFN with O(N) attention replacement for MHSA
- Optimal frame length L via F = (N-L)/R + 1 trade-off

## From [[@liIDHNetCNNTransformerHybrid2026]]

- Triple-path stem: I, Q, and IQ-fusion with `Result = I*Sigmoid(IQ) + Q*Sigmoid(IQ)`
