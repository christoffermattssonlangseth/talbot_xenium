# 🧬 Talbot Lab Xenium Analysis

This repository documents the work by **Spatialist** on the **Talbot Lab Xenium** project, focusing on **skin graft** and **melanoma** samples.  
The analysis is structured into three progressive levels, each building on the previous one.

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

## 🧰 TODO / Next Steps

1. **Remove the following samples:**  ✅ [Status: DONE]
   - `output-XETG00045__0059973__Oprl1_wt__20250725__091031`  
   - `output-XETG00045__0059973__Pdl1_cre__20250725__091031_0`  

2. **Update Oprl1_cre comparisons:**  ✅ [Status: DONE]
   - Substitute `Oprl1_wt` with `C57_wt` as the control group.  

3. **Mouse pigmentation classification:**  🟡 [Status: ONGOING]
   - Implement a method to distinguish **white vs black mice**.  

4. **Export DE results:**  ✅ [Status: DONE]
   - Generate `.csv` files containing **log2FC values for all genes** per comparison.  

5. **Initiate Level 3 analysis:**  🟡 [Status: ONGOING]
   - Begin detailed single-cell exploration and visualization.  

---

_This structured framework ensures transparency, reproducibility, and scalability across all stages of the Talbot Lab Xenium analysis pipeline._