---
type: template
---

---
type: experiment
model: <% tp.file.title %>
dataset:
date: <% tp.date.now("YYYY-MM-DD") %>
tags: [AMC, experiment]
---

# Experiment: <% tp.date.now("YYYY-MM-DD") %>

## Setup

| Item | Value |
|------|-------|
| Model | |
| Dataset | |
| SNR range | |
| Epochs | |
| Optimizer | |
| Learning rate | |

## Results

| SNR (dB) | Accuracy |
|----------|----------|
| | |

## Figures

*(Link figures from `figures/` folder)*

## Conclusions

*(What worked, what didn't, next steps)*

## Links

- Model card: [[My_Research/Models/]]
- Config: `configs/`
