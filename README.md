# R²-VQA: Region-of-Interest Reasoning for Reliable Visual Question Answering on Medical Images

A multi-week research project exploring **Visual Question Answering (VQA)** on medical radiology images using the [VQA-RAD](https://huggingface.co/datasets/flaviagiammarino/vqa-rad) dataset. The project develops **R²-VQA** — a pipeline that combines a Vision-Language Model (VLM) with grounded region-of-interest (ROI) proposals and causal consistency checks to improve both accuracy and reliability of medical VQA.

> **Institution:** Mohamed Bin Zayed University of Artificial Intelligence (MBZUAI)

---

## Overview

Standard VLMs can answer medical questions from radiology images, but they often lack spatial grounding and provide unreliable confidence estimates. R²-VQA addresses this by:

1. **ROI Proposal** — Using Grounding DINO to localize the anatomical region relevant to each question
2. **Multi-View Reasoning** — Querying the VLM from multiple perspectives (direct, cropped ROI, jittered, masked, random crop) and checking consistency
3. **Causal Faithfulness Checks** — Verifying that the model's answer changes appropriately when evidence is removed (necessity) or isolated (sufficiency)
4. **Selective Abstention** — A logistic regression signal combining confidence and consistency features to abstain on unreliable predictions, boosting accuracy on answered questions

### Key Results (Test Set, n=451)

| Metric | Value |
|--------|-------|
| **Model** | Qwen2.5-VL-7B-Instruct (4-bit) |
| **Direct VQA Accuracy** | 55.4% |
| **R²-VQA Accuracy (@ 80% coverage)** | 62.9% |
| **R²-VQA AUROC** | 0.732 vs 0.666 (confidence alone) |
| **Gain vs Direct** | +7.0 pp (CI: +4.6 to +9.5) |

---

## Repository Structure

```
VQA_MBZUAI/
├── VQA_MBZUAI.ipynb              # Main Colab notebook (all weeks)
├── README.md
├── .gitignore
└── Results/
    └── vqa_project_results/
        ├── comparison_images/         # Side-by-side VLM vs ground truth
        ├── contact_sheets/            # Visual overview grids
        ├── proposals/                 # ROI proposal visualizations
        ├── r2_vqa_week2/              # Week 2: VLM proposals & baselines
        ├── r2_vqa_week3_interventions/# Week 3: Causal interventions
        ├── r2_vqa_week4_abstention/   # Week 4: Abstention & risk-coverage
        ├── r2_vqa_week5_artifacts/    # Week 5: Full pipeline artifacts
        ├── r2_vqa_week6_experiments/  # Week 6: 7 baseline comparisons
        ├── r2_vqa_week7_annotations/  # Week 7: Manual annotations & report
        ├── r2_vqa_week8_final/        # Week 8: Frozen test & paper draft
        │   ├── frozen_config.json     # Frozen pipeline configuration
        │   ├── results/               # Final scored results
        │   ├── figures/               # Paper figures (PDF + PNG)
        │   ├── paper/                 # LaTeX paper draft
        │   ├── analysis/              # Dev set analysis
        │   ├── dev/                   # Dev cache
        │   ├── metadata/              # Dev/test set definitions
        │   └── test/                  # Test run cache
        ├── plausibility_summary.json
        ├── proposal_summary.json
        ├── vqa_results.csv
        └── *.csv / *.png             # Top-level result files
```

---

## Weekly Progress

| Week | Focus | Key Deliverables |
|------|-------|-----------------|
| **2** | VLM Proposals & Initial Evaluation | ROI proposal generation, contact sheets, manual review |
| **3** | Causal Interventions | Sufficiency, necessity, and stability checks |
| **4** | Selective Abstention | Risk-coverage curves, abstention thresholds |
| **5** | Full Pipeline Build | End-to-end R²-VQA with all views |
| **6** | Baseline Comparisons | 7 baselines (direct, crop, grounder, etc.) scored |
| **7** | Manual Annotations & Report | 300+ annotated cases, failure categorization, LaTeX report |
| **8** | Final Evaluation & Paper | Frozen config, test set evaluation, paper draft |

---

## Setup & Usage

The entire project runs in a **Google Colab** notebook with a T4 GPU.

### Requirements

```
transformers
accelerate
bitsandbytes
qwen-vl-utils
datasets
```

### Quick Start

1. Open `VQA_MBZUAI.ipynb` in Google Colab
2. Select a **T4 GPU** runtime
3. Run cells sequentially — each week's cells are clearly labeled (e.g., `WEEK 8 - CELL 1`)
4. Results are saved to Google Drive under `vqa_project_results/`

---

## Model

- **VLM:** [Qwen2.5-VL-7B-Instruct](https://huggingface.co/Qwen/Qwen2.5-VL-7B-Instruct) (4-bit quantized via BitsAndBytes)
- **Grounder:** [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) for ROI detection
- **Dataset:** [VQA-RAD](https://huggingface.co/datasets/flaviagiammarino/vqa-rad) (451 test questions on radiology images)

---

## License

This project is for academic/research purposes at MBZUAI.
