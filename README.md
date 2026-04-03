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
| **Right** | Consensus-corrected mask after expert-reviewed, model-assisted annotation refinement. Pixels shown in **green** represent regions added or confirmed by expert consensus |

### Naming Convention

Files follow the pattern `NNN_source_XXXX.png`, where:

- `NNN` — sequential index (001–252)
- `source` — origin dataset: `fusc` (FUSeg2021), `wsnet` (WoundSeg/WSNet DFU subset), or `medetec` (Medetec Wound Database)
- `XXXX` — original image identifier within the source dataset

## Dataset Context

The images belong to a curated DFU corpus derived from three public wound-image repositories. The original pool of **2,845 images** was filtered through a diagnostic screening process in which wound-care experts reviewed each photograph and retained only those depicting diabetic foot ulcers (DFU-compatible). Non-DFU cases (pressure ulcers, surgical wounds, burns, etc.) were excluded. A subsequent quality-control step removed images with severe artifacts, inadequate resolution, or unusable masks, yielding a final corpus of **2,245 image–mask pairs**.

| Source repository | Original | DFU-compatible | Excluded (non-DFU) | Retained after QC |
|-------------------|:--------:|:--------------:|:-------------------:|:-----------------:|
| Medetec Wound Database | 374 | 212 | 162 | 179 |
| FUSeg2021 challenge dataset | 1,295 | 1,295 | 0 | 1,180 |
| WoundSeg/WSNet-derived DFU subset | 1,176 | 893 | 283 | 886 |
| **Total** | **2,845** | **2,400** | **445** | **2,245** |

The 252 triplets shown here correspond to cases where an initial multi-model consensus pipeline flagged potential annotation discrepancies. Eight independently trained segmentation architectures (ConvNeXt-Base, SegFormer-B5, MaxViT, U-Net EfficientNet-B7, U-Net++ ResNet-50, DeepLabV3+ ResNet-50, WoundNetB7-CA, and SegFormer-CA) were used to identify candidate regions where the original expert masks and high-confidence model agreement diverged — indicating likely missed or over-annotated wound areas.

Critically, the model-proposed corrections were **not applied automatically**. Each flagged case was subsequently reviewed by **three wound-care experts**, who independently evaluated the candidate regions and reached a final consensus on which corrections were clinically justified. Only expert-validated corrections were retained in the final masks. In the right panel, regions shown in **green** represent pixels added through this expert consensus process, distinguishing them from the original annotation (white) in the center panel.

This two-stage protocol — computational screening followed by expert adjudication — was designed to reduce inter-annotator variability while ensuring that all corrections reflect clinical judgment rather than purely algorithmic agreement.

## Purpose

These visual results are provided as **supplementary material** for transparency and reproducibility. They allow readers to:

1. Inspect the original expert annotations alongside the expert-reviewed corrected masks.
2. Assess the magnitude and location of corrections validated by the three-expert consensus.
3. Identify the green-highlighted regions that were added through expert adjudication.
4. Evaluate the clinical plausibility of the refinement process on a per-image basis.

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
