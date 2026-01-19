# 🧬 Talbot Lab Xenium Analysis

This repository documents the work by **Spatialist** on the **Talbot Lab Xenium** project, focusing on **skin graft** and **melanoma** samples.  
The analysis is structured into three progressive levels, each building on the previous one.

---

## 🗺️ Project Map

**Notebooks (analysis workflow)**
- `notebooks/level-1/0_QC.ipynb`: QC metrics and segmentation overview across all samples.
- `notebooks/level-2/0_kmeans_sample_separation.ipynb`: Sample-level clustering/separation setup.
- `notebooks/level-2/1_tumor_comparision.ipynb`: Tumor group comparisons and DE.
- `notebooks/level-2/2_skin_comparision.ipynb`: Skin graft comparisons and DE.
- `notebooks/level-2/3_exploring_mouse_color.ipynb`: Exploratory pigmentation classification.
- `notebooks/level-2/4_binning_expression.ipynb`: Binning-based expression summaries.
- `notebooks/level-3/00_tumor_clustering.ipynb`: Tumor cell clustering and embedding.
- `notebooks/level-3/01_cytetype_tumor.ipynb`: Tumor cluster annotation to cell types.
- `notebooks/level-3/02_skin_clustering.ipynb`: Skin graft clustering and embedding.
- `notebooks/level-3/03_cytetype_skin.ipynb`: Skin cluster annotation to cell types.

**Outputs (results and artifacts)**
- `results/differential-gene-expression/`: CSVs with DE comparisons (tumor and skin).
- `results/cell-driven-analysis/`: Cell-type annotation exports.
- `notebooks/level-3/query.json`: Cluster metadata export used by Level 3.

**High-level flow**
- Level 1 establishes QC baseline.
- Level 2 produces sample-level differential comparisons.
- Level 3 performs clustering and assigns cell types.

---

## 🔹 Level 1 — Quality Control & Segmentation Overview
This stage provides an overview of transcript content and segmentation metrics across all samples.

- Summarizes segmentation strategies and their effects on cell size, transcript density, and total cell counts  
- Presents key QC metrics such as total transcripts and detected genes per cell  
- Flags low-quality cells and outlier samples  
- Compares QC performance across samples and experimental conditions  
- Establishes a transparent and reproducible baseline for all downstream analyses  

---

## 🔹 Level 2 — Sample-Level Comparisons
This level separates samples and performs targeted differential analyses between defined experimental groups.  
Comparisons are based on condition mappings specified by the customer, enabling focused interpretation of biological contrasts.

---

## 🔹 Level 3 — Cell-Focused Analyses
This final level zooms into fine-grained, **cell-level (or tissue bins in the case of the skin grafts)** patterns to uncover spatial and molecular heterogeneity across conditions and cell types.

---

## 🔍 How to Read This Repo

Start with Level 1 for QC context, then Level 2 for sample comparisons, and finish with Level 3 for clustering and cell-type calls. The outputs under `results/` are the materialized artifacts from those notebooks.

---

_This structured framework ensures transparency, reproducibility, and scalability across all stages of the Talbot Lab Xenium analysis pipeline._
