# Talbot Lab Xenium

This repository collects the work by **Spatialist** on the Talbot Lab Xenium analysis of **skin grafts** and **melanoma** samples.  
The analysis is organized into three levels:

- **Level 1**  
  Provides an overall breakdown of transcript content per sample.  
  - Summarizes segmentation strategies and evaluates their impact on cell size, transcript density, and overall cell counts  
  - Presents transcript-level QC metrics, including total counts and detected genes per cell  
  - Identifies potential low-quality cells or outlier samples  
  - Compares QC metrics across samples and experimental conditions to highlight technical variation or biases  
  - Establishes a transparent baseline for downstream analyses, ensuring that filtering decisions and biological conclusions are built on well-documented QC checks  

- **Level 2**  
  Separates the samples from one another and performs targeted comparisons between selected sample groups, as specified by the customer.  

- **Level 3**  
  Cell-focused analysis, drilling down to fine-grained patterns at the single-cell level.  

TODO: 
1. remove following samples: "output-XETG00045__0059973__Oprl1_wt__20250725__091031", "output-XETG00045__0059973__Pdl1_cre__20250725__091031_0", 
2. for opr1 cre comparisions substitute oprl1_wt with c57. 
3. find a way to separate white from black mice. 
4. give csv files with log2fc for all genes. 
5. start level 3. 
