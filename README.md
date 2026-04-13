# 🧬 Talbot Lab Xenium Analysis

This repository documents the work by **Spatialist** on the **Talbot Lab Xenium** project, focusing on **skin graft** and **melanoma tumor** samples profiled with spatially resolved transcriptomics (10x Xenium).

The analysis is structured into three progressive levels, each building on the previous one.

---

## 🗺️ Project Map

**Notebooks (analysis workflow)**

| Notebook | Description |
|----------|-------------|
| `notebooks/level-1/0_QC.ipynb` | QC metrics, segmentation overview, and outlier flagging across all samples |
| `notebooks/level-2/0_kmeans_sample_separation.ipynb` | Spatial KMeans to assign cells to their correct sample when multiple sections share a capture area |
| `notebooks/level-2/1_tumor_comparision.ipynb` | Pseudobulk DGE and per-cell-type volcano plots for tumor comparisons |
| `notebooks/level-2/2_skin_comparision.ipynb` | Pseudobulk DGE for skin graft comparisons at 24 h and 72 h |
| `notebooks/level-2/3_exploring_mouse_color.ipynb` | Melanocyte marker and melanin synthesis gene expression across skin samples |
| `notebooks/level-2/4_binning_expression.ipynb` | Annotation-free 30 µm spatial grid binning and bin-level DGE |
| `notebooks/level-3/00_tumor_clustering.ipynb` | Normalization, PCA, UMAP, and multi-resolution Leiden clustering of tumor cells |
| `notebooks/level-3/01_cytetype_tumor.ipynb` | CyteType cell type annotation for tumor clusters; immune compartment survey; genotype-group UMAPs |
| `notebooks/level-3/02_skin_clustering.ipynb` | Normalization, PCA, UMAP, and Leiden clustering of skin graft cells |
| `notebooks/level-3/03_cytetype_skin.ipynb` | CyteType cell type annotation for skin clusters; cell-type proportion heatmap |
| `notebooks/level-3/04_cellcharter.ipynb` | scVI-based batch correction followed by CellCharter spatial niche detection |

**Outputs (results and artifacts)**

| Path | Contents |
|------|----------|
| `results/differential-gene-expression/tumor/` | DGE results for tumor pairwise comparisons |
| `results/differential-gene-expression/skin_grafts/` | DGE results for skin graft comparisons |
| `results/differential-gene-expression/tumor_non_pseudobulk_comparision.csv` | Non-pseudobulk tumor DGE |
| `results/cell-driven-analysis/` | CyteType annotation exports (per-cluster cell type labels and scores) |

---

## 🔹 Level 1 — Quality Control & Segmentation Overview

Establishes a QC baseline across all samples before any downstream analysis.

- Summarizes segmentation strategies and their effects on cell size, transcript density, and total cell counts
- Presents key QC metrics: total transcripts and detected genes per cell
- Flags low-quality cells and outlier samples
- Compares QC performance across samples and experimental conditions

---

## 🔹 Level 2 — Sample-Level Comparisons

Separates samples and performs targeted differential analyses between defined experimental groups.

- **`0_kmeans_sample_separation`**: Multiple tissue sections placed on the same Xenium capture area are deconvolved using KMeans on spatial coordinates, producing a reliable `sample_id` used throughout all downstream notebooks.
- **`1_tumor_comparision`**: Pseudobulk differential gene expression between tumor genotype groups, with volcano plots generated per cell type.
- **`2_skin_comparision`**: Six pairwise DGE comparisons for skin grafts, split by timepoint (24 h and 72 h).
- **`3_exploring_mouse_color`**: Exploratory analysis of melanocyte identity and melanin synthesis genes across skin samples.
- **`4_binning_expression`**: Transcript-level spatial binning as an annotation-free complement to cell-level DGE, capturing spatially coherent expression differences without relying on segmentation.

---

## 🔹 Level 3 — Cell-Focused Analyses

Fine-grained, cell-level analyses to uncover spatial and molecular heterogeneity across conditions and cell types.

- **`00_tumor_clustering`** / **`02_skin_clustering`**: Standard preprocessing (normalization → PCA → UMAP) and Leiden clustering at resolutions 0.5–4. Resolution 4 is used for downstream annotation. The 67 clusters produced at resolution 4 intentionally exceed the final number of annotated cell types (36), as multiple transcriptionally similar clusters are merged under a single biological label by CyteType.
- **`01_cytetype_tumor`** / **`03_cytetype_skin`**: LLM-assisted cluster annotation using [CyteType](https://cytetype.ai). Each Leiden cluster is assigned a cell type label and confidence score (0–1). The tumor notebook additionally surveys the full immune compartment (T cells, B cells, NK cells, macrophages, dendritic cells, mast cells, Schwann cells, neutrophils) and provides genotype-group-separated UMAP visualizations.
- **`04_cellcharter`**: Spatial niche detection using [CellCharter](https://github.com/CSOgroup/cellcharter). Raw counts are used to train an scVI model to obtain a low-dimensional latent representation of each cell, which is then combined with spatial neighborhood context to cluster cells into recurrent tissue niches. This reveals which microenvironmental configurations differ between genotypes, beyond individual cell type composition.

---

## 🔍 How to Read This Repo

Start with **Level 1** for QC context → **Level 2** for sample-level differential comparisons → **Level 3** for clustering, cell type annotation, and spatial niche analysis. The outputs under `results/` are the materialized artifacts from those notebooks.

---

_This structured framework ensures transparency, reproducibility, and scalability across all stages of the Talbot Lab Xenium analysis pipeline._
