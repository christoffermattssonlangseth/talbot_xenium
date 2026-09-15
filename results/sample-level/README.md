# Wound-skin sample-level data (per biological replicate)

These files provide the **per-sample** (per-replicate) values underlying the
group-level pseudobulk comparisons, so that data can be plotted as **mean ± SEM**
across biological replicates.

## Files
| File | Description |
|------|-------------|
| `logcpm_mat.csv` | genes × samples matrix. edgeR-style **log2(CPM + 1)** (`prior_count=1`, `scale=1e6`). Genes prefiltered to total pseudobulk counts ≥ 10 (4,956 genes × 17 samples). |
| `pseudobulk_counts_mat.csv` | genes × samples matrix of **raw summed counts** (before CPM/log), if you prefer your own normalization. |
| `sample_meta.csv` | one row per sample: `sample_id, mouse_id, mouse_id_status, condition, genotype, timepoint, replicate, n_cells, total_pseudobulk_counts`. |

## Method
Reproduces exactly the pseudobulk recipe in
`notebooks/level-2/2_skin_comparision.ipynb`: raw counts from
`talbot_xenium.h5ad` (tissue == skin), QC filter `min_counts=30` /
`min_genes=10`, counts summed per `sample_id`, then log2-CPM.
**Validated:** averaging these per-sample values reproduces the `mean_logCPM_*`
columns in `results/differential-gene-expression/skin_grafts/` to 6 decimal places.

## ⚠️ IMPORTANT — mouse IDs are PROVISIONAL
The dataset contains **no recorded animal IDs**. The 17 "samples" are the
**spatial sections** produced by the KMeans sample-separation step (2–3 per
condition), which the existing DGE pipeline already treated as biological
replicates. Every row is flagged
`mouse_id_status = PROVISIONAL_from_kmeans_section__replace_with_real_animal_ID`.

**Before using for mean ± SEM statistics, confirm with the wet-lab that each
section corresponds to one distinct mouse.** If the sections are fragments of the
same animal, treating them as independent replicates is pseudoreplication.

Notes on the current data:
- `wt_24h` has only **2** sections (not 3).
- `litt_72h_m1` is small (**506 cells / 34,917 counts**) vs ~4–8k cells in other
  samples — may be a tissue fragment rather than a full replicate.

Once real animal IDs / the section→mouse mapping are available, update the
`mouse_id` column in `sample_meta.csv`.
