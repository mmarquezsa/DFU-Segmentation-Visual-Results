# DFU Segmentation Visual Results — Supplementary Material

This repository provides **252 visual result triplets** from the segmentation stage of the framework described in:

> **A Framework for Diabetic Foot Ulcer Assessment Integrating Segmentation, Interpretable PWAT Scoring, and Exploratory Phototype-Stratified Analysis**
>
> Marcelo Márquez-Sandoval, Benjamín Morales Carvajal, Julio Sotelo Parraguez, and Ana Aguilera
>
> *Submitted to IEEE Access*

## Contents

Each image in `triplets/` shows three panels side by side:

| Panel | Description |
|-------|-------------|
| **Left** | Original DFU photograph |
| **Center** | Original ground-truth binary mask (expert annotation) |
| **Right** | Consensus-corrected mask after model-assisted annotation refinement |

### Naming Convention

Files follow the pattern `NNN_source_XXXX.png`, where:

- `NNN` — sequential index (001–252)
- `source` — origin dataset: `fusc` (FUSeg2021), `wsnet` (WoundSeg/WSNet DFU subset), or `medetec` (Medetec Wound Database)
- `XXXX` — original image identifier within the source dataset

## Dataset Context

The images belong to the curated 2,245-image DFU corpus assembled from three public repositories:

| Source | Retained Images |
|--------|----------------:|
| FUSeg2021 | 1,180 |
| WoundSeg/WSNet DFU subset | 886 |
| Medetec Wound Database | 179 |
| **Total** | **2,245** |

The 252 triplets shown here correspond to cases where the multi-model consensus correction pipeline detected annotation discrepancies between the original expert masks and the agreement of eight independently trained segmentation architectures (ConvNeXt-Base, SegFormer-B5, MaxViT, U-Net EfficientNet-B7, U-Net++ ResNet-50, DeepLabV3+ ResNet-50, WoundNetB7-CA, and SegFormer-CA). Corrections were applied only when high-confidence model agreement indicated likely missed or over-annotated wound regions, following a semi-automatic refinement protocol designed to reduce inter-annotator variability.

## Purpose

These visual results are provided as **supplementary material** for transparency and reproducibility. They allow readers to:

1. Inspect the quality of original expert annotations alongside corrected masks.
2. Assess the magnitude and location of consensus-driven corrections.
3. Evaluate the clinical plausibility of the refinement process on a per-image basis.

## Related Repository

The main manuscript source (LaTeX, figures, and bibliography) is maintained in a separate repository linked from the publication.

## License

This supplementary material is provided for **academic and research purposes only**. The original images are derived from publicly available datasets (Medetec, FUSeg2021, WoundSeg) and are subject to their respective licenses and terms of use.

## Citation

If you use this material, please cite the accompanying article:

```bibtex
@article{marquez2026dfu_framework,
  title   = {A Framework for Diabetic Foot Ulcer Assessment Integrating
             Segmentation, Interpretable {PWAT} Scoring, and Exploratory
             Phototype-Stratified Analysis},
  author  = {M{\'a}rquez-Sandoval, Marcelo and Morales Carvajal, Benjam{\'i}n
             and Sotelo Parraguez, Julio and Aguilera, Ana},
  journal = {IEEE Access},
  year    = {2026},
  note    = {Submitted}
}
```
