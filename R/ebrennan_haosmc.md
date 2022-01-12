---
title: "ebrennan_haosmc Analysis"
author: "BM"
date: "12/28/2021"
mainfont: "Helvetica Light"
output: 
  pdf_document:
    keep_md: yes
always_allow_html: yes
urlcolor: blue
---

# **Analysis**

## **Overview**

Salmon merged gene counts were created using Nextflow nf-core_rnaseq ([commit: 8094c42add](https://github.com/nf-core/rnaseq/commit/8094c42add6dcdf69ce54dfdec957789c37ae903)) using hg38 Homo_sapiens.GRCh38.dna_sm.primary_assembly.fa.gz and Homo_sapiens.GRCh38.96.gtf.gz. These data are used here in RDS format to run DESeq2 @Love2014.

Data comprise of mRNA from Human aortic smooth muscle cells (haosmc) in `group` 'scrambled miRNA mimic' (`Scramble`) or 'let-7d miRNA mimic' (`Let7d`), and treated (`drug`) with no drug (`None`), TNF alpha alone (`TNFa`; 10ng/ml, 24hr), or in combination with one of the statins Atorvastatin or Lovastation (`Ator`, `Lova`; 1uM, 24hr). This leads to10 contrasts (i.e. comparisons) of interest: between `group` with `None` and with `TNFa` (2), and within `group` comparing `TNFa` with `None` (2), `Ator` (2), and `Lova` (2), and `Ator` with `Lova` (2). 

Data is saved as XLSX and RDS for ongoing analysis in the `output` directory. Plots are displayed herein and saved to `output` as PDF.



## **Differential Expression Analysis**

The DESeq2 package (@love2014) was used to determine 'differentially expressed' genes (DEG) between each group and treatment. The full analysis code is available from www.github.com/brucemoran/ebrennan_haosmc. Table 1a outlines the number of DEG between each 'contrast', i.e. group/treatment being compared, at three levels of false discovery rate (FDR) adjusted p-values. Thousands of DEG are evident between each contrast. Table 1b shows overlap of DEG found between treatments between groups (e.g. `Ator` vs. `Lova` in `Scramble` and `Let7d`) are shown to indicate <level of similarity?>  

### **Table 1b: Total DE Genes Found per Contrast**


|                               | p < 0.001| p < 0.01| p < 0.05|
|:------------------------------|---------:|--------:|--------:|
|Scramble_None_vs_Scramble_TNFa |      3070|     3902|     4947|
|Let7d_None_vs_Let7d_TNFa       |      2281|     3028|     4114|
|Let7d_None_vs_Scramble_None    |      5580|     6891|     8283|
|Let7d_TNFa_vs_Scramble_TNFa    |      5694|     6901|     8270|
|Scramble_Ator_vs_Scramble_TNFa |      6397|     7586|     8895|
|Scramble_Lova_vs_Scramble_TNFa |      6154|     7374|     8740|
|Let7d_Ator_vs_Let7d_TNFa       |      5133|     6355|     7763|
|Let7d_Lova_vs_Let7d_TNFa       |      5181|     6386|     7718|
|Let7d_Ator_vs_Scramble_Ator    |      5175|     6397|     7840|
|Let7d_Lova_vs_Scramble_Lova    |      5193|     6373|     7782|
|Let7d_Ator_vs_Let7d_Lova       |         0|        0|        1|
|Scramble_Ator_vs_Scramble_Lova |         1|        2|        2|

### **Table 1b: Overlap of DE Genes Found per Contrast Between Groups (padj < 0.01)**


|             | Unique| Overlap| Overlap %|
|:------------|------:|-------:|---------:|
|None_vs_TNFa |   1343|    1727|     47.65|
|Ator_vs_TNFa |   2109|    4288|     59.21|
|Lova_vs_TNFa |   1876|    4278|     60.62|

## **QC Plots**



### **Heatmap**

![](ebrennan_haosmc_files/figure-latex/ebrennan_haosmc.Heatmap-1.pdf)<!-- --> 

### **PCA Plots**

### *PCA 1 vs 2*

PC 1 accounts for 41% of variance (quite a lot), and very clearly serparates based on drug treatment. Evident on the x-axis between -40, -20 are `Ator`, `Lova` treated cells, between 0 - 20 are `TNFa` treated cells, and after 40 are cells treated with no drug (`None`).

PC2 accounts for 24% variance, still quite high, and is based on `Scramble`/`Let7d`.

![](ebrennan_haosmc_files/figure-latex/ebrennan_haosmc.PCA_1_2-1.pdf)<!-- --> 

### *PCA 1 vs 3*

PC3 (y-axis) accounts for 10% variance, so we have attributed 3/4 total variance. This is also a biologically based PC, given that `TNFa` treated cells are clearly separated. There is also some separation of `Ator`/`Lova` treated cells from untreated `None` cells. 

![](ebrennan_haosmc_files/figure-latex/ebrennan_haosmc.PCA_1_3-1.pdf)<!-- --> 

## **Pathway Analysis**

Pathways are taken from [MsigDB](https://www.gsea-msigdb.org/gsea/msigdb/)(@subramanian2011) 'Hallmark' gene sets (@liberzon2015) and analysis conducted with the `fGSEA` package (<ref>)


```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Running: fgsea_plot()"
## [1] "Found rank_col: stat"
```

```
## [1] "Working on: Scramble_None_vs_Scramble_TNFa"
## Estimating ssGSEA scores for 20 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_None_vs_Let7d_TNFa"
## Estimating ssGSEA scores for 19 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_None_vs_Scramble_None"
## Estimating ssGSEA scores for 18 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_TNFa_vs_Scramble_TNFa"
## Estimating ssGSEA scores for 21 gene sets.
## 
## 
```

```
## [1] "Working on: Scramble_Ator_vs_Scramble_TNFa"
## Estimating ssGSEA scores for 33 gene sets.
## 
## 
```

```
## [1] "Working on: Scramble_Lova_vs_Scramble_TNFa"
## Estimating ssGSEA scores for 35 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_Ator_vs_Let7d_TNFa"
## Estimating ssGSEA scores for 36 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_Lova_vs_Let7d_TNFa"
## Estimating ssGSEA scores for 34 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_Ator_vs_Scramble_Ator"
## Estimating ssGSEA scores for 17 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_Lova_vs_Scramble_Lova"
## Estimating ssGSEA scores for 13 gene sets.
## 
## 
```

```
## [1] "Working on: Let7d_Ator_vs_Let7d_Lova"
## [1] "No genesets in pathways, skipping..."
## [1] "Working on: Scramble_Ator_vs_Scramble_Lova"
## [1] "No genesets in pathways, skipping..."
```