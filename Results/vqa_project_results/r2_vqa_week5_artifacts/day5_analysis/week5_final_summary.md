
# Week 5 Final Summary: Paired Statistical Analysis of Artifact Study

## Pairing Diagnostics
Match level used for this analysis: **relaxed** (7 matched pairs).
See `week5_pairing_diagnostics.csv` for the full per-sample breakdown of why pairs did or did not match.

## Core Hypothesis (H5) Evaluation
**H5: The model is more sensitive to artifacts placed INSIDE the ROI than to matched artifacts placed OUTSIDE it.**

### Flip Rate (McNemar's Test)
- Flip Rate (Inside ROI): 0.000
- Flip Rate (Outside ROI): 0.143
- McNemar Statistic: 0.000, p-value: 1.000

### JS Divergence (Wilcoxon Signed-Rank Test)
- Mean JS Divergence (Inside ROI): 0.000
- Mean JS Divergence (Outside ROI): 0.000
- Wilcoxon Statistic: 0.000, p-value: 1.000

### Confidence Drop (Wilcoxon Signed-Rank Test)
- Mean Confidence Drop (Inside ROI): 0.000
- Mean Confidence Drop (Outside ROI): 0.000
- Wilcoxon Statistic: 0.000, p-value: 1.000

---

## Conclusion on H5 Support


The results indicate that 

---

## Breakdowns by Artifact Conditions
| dimension                     | value             |   num_pairs |   num_js_valid_pairs | match_level_used   |   flip_rate_inside |   flip_rate_outside |   mean_js_divergence_inside |   mean_js_divergence_outside |   mean_confidence_drop_inside |   mean_confidence_drop_outside |
|:------------------------------|:------------------|------------:|---------------------:|:-------------------|-------------------:|--------------------:|----------------------------:|-----------------------------:|------------------------------:|-------------------------------:|
| artifact_similarity_requested | lesion-similar    |           7 |                    4 | relaxed            |                  0 |            0.142857 |                           0 |                            0 |                             0 |                              0 |
| artifact_similarity_requested | lesion-dissimilar |           0 |                    0 | strict             |                nan |          nan        |                         nan |                          nan |                           nan |                            nan |
| artifact_strength_requested   | medium            |           0 |                    0 | strict             |                nan |          nan        |                         nan |                          nan |                           nan |                            nan |
| artifact_strength_requested   | low               |           0 |                    0 | strict             |                nan |          nan        |                         nan |                          nan |                           nan |                            nan |
| artifact_strength_requested   | high              |           0 |                    0 | strict             |                nan |          nan        |                         nan |                          nan |                           nan |                            nan |
| category                      | long-tail         |           1 |                    1 | relaxed            |                  0 |            0        |                           0 |                            0 |                             0 |                              0 |
| category                      | small-object      |           4 |                    2 | relaxed            |                  0 |            0.25     |                           0 |                            0 |                             0 |                              0 |
| category                      | general           |           2 |                    1 | relaxed            |                  0 |            0        |                           0 |                            0 |                             0 |                              0 |
| category                      | temporal          |           0 |                    0 | strict             |                nan |          nan        |                         nan |                          nan |                           nan |                            nan |

