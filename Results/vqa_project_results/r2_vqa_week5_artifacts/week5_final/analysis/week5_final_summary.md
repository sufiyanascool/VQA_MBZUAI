# Week 5 Final Summary - Invisible Gorilla medical VQA study

- Cases: 500 | prediction rows: 1925 | matched design: inside/outside x similar/dissimilar (strength fixed)
- Overall flip rate: 0.031 | clean accuracy: 0.746

## H5: inside-ROI artifacts affect the model more than matched outside-ROI artifacts
H5 SUPPORTED: inside-ROI artifacts move the model more than matched outside-ROI artifacts on flipped, js, p_shift.

### Main comparison (pooled)
| comparison              |   n_pairs | metric    |   mean_inside |   mean_outside |   mean_diff |   ci95_low |   ci95_high |   p_one_sided |   mean_lesion-similar |   mean_lesion-dissimilar | significant_bonferroni   |
|:------------------------|----------:|:----------|--------------:|---------------:|------------:|-----------:|------------:|--------------:|----------------------:|-------------------------:|:-------------------------|
| inside_vs_outside | all |       925 | flipped   |        0.0389 |         0.0173 |      0.0216 |     0.0097 |      0.0357 |        0.0008 |                   nan |                      nan | True                     |
| inside_vs_outside | all |       925 | js        |        0.0425 |         0.0252 |      0.0174 |     0.0141 |      0.0205 |        0      |                   nan |                      nan | True                     |
| inside_vs_outside | all |       925 | conf_drop |        0.006  |         0.0046 |      0.0014 |    -0.0021 |      0.0051 |        0.0826 |                   nan |                      nan | False                    |
| inside_vs_outside | all |       925 | p_shift   |        0.0407 |         0.024  |      0.0167 |     0.0133 |      0.0204 |        0      |                   nan |                      nan | True                     |

## All comparisons
| comparison                            |   n_pairs | metric    |   mean_inside |   mean_outside |   mean_diff |   ci95_low |   ci95_high |   p_one_sided |   mean_lesion-similar |   mean_lesion-dissimilar | significant_bonferroni   |
|:--------------------------------------|----------:|:----------|--------------:|---------------:|------------:|-----------:|------------:|--------------:|----------------------:|-------------------------:|:-------------------------|
| inside_vs_outside | all               |       925 | flipped   |        0.0389 |         0.0173 |      0.0216 |     0.0097 |      0.0357 |        0.0008 |              nan      |                 nan      | True                     |
| inside_vs_outside | all               |       925 | js        |        0.0425 |         0.0252 |      0.0174 |     0.0141 |      0.0205 |        0      |              nan      |                 nan      | True                     |
| inside_vs_outside | all               |       925 | conf_drop |        0.006  |         0.0046 |      0.0014 |    -0.0021 |      0.0051 |        0.0826 |              nan      |                 nan      | False                    |
| inside_vs_outside | all               |       925 | p_shift   |        0.0407 |         0.024  |      0.0167 |     0.0133 |      0.0204 |        0      |              nan      |                 nan      | True                     |
| inside_vs_outside | lesion-similar    |       464 | flipped   |        0.0194 |         0.0151 |      0.0043 |    -0.0129 |      0.0216 |        0.3953 |              nan      |                 nan      | False                    |
| inside_vs_outside | lesion-similar    |       464 | js        |        0.0313 |         0.0203 |      0.011  |     0.0076 |      0.0148 |        0      |              nan      |                 nan      | True                     |
| inside_vs_outside | lesion-similar    |       464 | conf_drop |        0.0026 |        -0.0001 |      0.0027 |    -0.0015 |      0.0068 |        0.0363 |              nan      |                 nan      | False                    |
| inside_vs_outside | lesion-similar    |       464 | p_shift   |        0.0292 |         0.0193 |      0.0099 |     0.0066 |      0.0139 |        0      |              nan      |                 nan      | True                     |
| inside_vs_outside | lesion-dissimilar |       461 | flipped   |        0.0586 |         0.0195 |      0.039  |     0.0195 |      0.0607 |        0.0001 |              nan      |                 nan      | True                     |
| inside_vs_outside | lesion-dissimilar |       461 | js        |        0.0538 |         0.0301 |      0.0237 |     0.0182 |      0.029  |        0      |              nan      |                 nan      | True                     |
| inside_vs_outside | lesion-dissimilar |       461 | conf_drop |        0.0094 |         0.0092 |      0.0001 |    -0.006  |      0.0061 |        0.3994 |              nan      |                 nan      | False                    |
| inside_vs_outside | lesion-dissimilar |       461 | p_shift   |        0.0523 |         0.0286 |      0.0237 |     0.0181 |      0.0296 |        0      |              nan      |                 nan      | True                     |
| similar_vs_dissimilar | inside        |       495 | flipped   |      nan      |       nan      |     -0.0444 |    -0.0667 |     -0.0242 |        1      |                0.0222 |                   0.0667 | False                    |
| similar_vs_dissimilar | inside        |       495 | js        |      nan      |       nan      |     -0.0242 |    -0.0296 |     -0.0194 |        1      |                0.0315 |                   0.0557 | False                    |
| similar_vs_dissimilar | inside        |       495 | conf_drop |      nan      |       nan      |     -0.0067 |    -0.0124 |     -0.001  |        0.9961 |                0.003  |                   0.0096 | False                    |
| similar_vs_dissimilar | inside        |       495 | p_shift   |      nan      |       nan      |     -0.0248 |    -0.0306 |     -0.0194 |        1      |                0.0293 |                   0.0541 | False                    |
| similar_vs_dissimilar | outside       |       461 | flipped   |      nan      |       nan      |     -0.0065 |    -0.0195 |      0.0066 |        0.8867 |                0.013  |                   0.0195 | False                    |
| similar_vs_dissimilar | outside       |       461 | js        |      nan      |       nan      |     -0.0096 |    -0.0128 |     -0.0068 |        1      |                0.0204 |                   0.03   | False                    |
| similar_vs_dissimilar | outside       |       461 | conf_drop |      nan      |       nan      |     -0.0091 |    -0.0128 |     -0.0054 |        1      |                0.0001 |                   0.0092 | False                    |
| similar_vs_dissimilar | outside       |       461 | p_shift   |      nan      |       nan      |     -0.0092 |    -0.0122 |     -0.0063 |        1      |                0.0194 |                   0.0286 | False                    |

Notes: one-sided tests; flip = exact McNemar on discordant pairs, other metrics = Wilcoxon signed-rank;
CI = bootstrap 95% on mean paired difference. The pooled test uses 2 pairs per case (correlated), so the
per-similarity rows are the cleaner evidence.
