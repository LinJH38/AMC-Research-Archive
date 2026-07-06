---
type: template
---

---
type: model_card
model_name: <% tp.file.title %>
status: draft
tags: [AMC, model]
created: <% tp.date.now("YYYY-MM-DD") %>
---

# <% tp.file.title %>

## Motivation

*(Why this model? What gap does it address?)*

## Related Literature

- [[@citekey]]

## Architecture

*(Describe blocks, data flow, input/output shapes)*

```
Input [B, 2, N] → ... → Output [B, num_classes]
```

## Key Design Decisions

| Decision | Rationale |
|----------|-----------|
| | |

## Target Metrics

| Metric | Target |
|--------|--------|
| Parameters | ≤ 15K |
| Dataset | RadioML2016.10a |
| Avg accuracy | TBD |

## Implementation

- Code: `src/`
- Config: `Experiments/<model>/configs/`

## Experiment Log

- [[Experiments/<model>/results/summary]]
