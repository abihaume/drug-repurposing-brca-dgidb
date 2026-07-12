# Drug Repurposing for Breast Cancer Using DGIdb

## Project Overview

This project explores drug repurposing opportunities for Breast Invasive Carcinoma (BRCA) by integrating differential gene expression analysis with the Drug Gene Interaction Database (DGIdb).

Starting from significantly differentially expressed genes identified from TCGA BRCA RNA-seq data, the project identifies existing drugs that target these genes, providing potential candidates for drug repurposing.

---

## Objectives

- Identify significantly differentially expressed genes.
- Apply false discovery rate (FDR) correction.
- Select the most significant genes.
- Retrieve known drug–gene interactions from DGIdb.
- Clean and integrate interaction data.
- Analyze potential drug repurposing candidates.
- Visualize gene–drug interaction patterns.

---

## Workflow

1. Load differential gene expression results.
2. Apply Benjamini–Hochberg FDR correction.
3. Filter significant genes.
4. Select the top 100 differentially expressed genes.
5. Query DGIdb using its GraphQL API.
6. Clean and merge drug interaction data.
7. Perform drug repurposing analysis.
8. Generate publication-quality visualizations.

---

## Repository Structure

```
drug-repurposing-brca-dgidb/
│
├── notebook/
│   └── Drug_Repurposing_BRCA_DGIdb.ipynb
│
├── figures/
│   ├── top15_genes_drug_interactions.png
│   ├── top20_drugs.png
│   ├── interaction_types.png
│   └── gene_drug_network.png
│
├── results/
│   ├── dge_results.csv
│   ├── filtered_deg_genes.csv
│   ├── top100_dge_genes.csv
│   ├── drug_gene_interactions.csv
│   ├── cleaned_drug_gene_interactions.csv
│   └── drug_target_summary.csv
│
└── README.md
```

---

## Technologies

- Python
- Databricks
- Pandas
- NumPy
- Matplotlib
- NetworkX
- Requests
- DGIdb GraphQL API

---

## Key Findings

- 277 significantly differentially expressed genes were retained after filtering.
- The top 100 genes were queried against DGIdb.
- 33 genes had known drug interactions.
- A total of 520 drug–gene interactions were identified.
- After cleaning, 460 unique drugs remained.
- Several drugs targeted multiple dysregulated genes, highlighting potential drug repurposing candidates.

---

## Author

**Ume Abiha**
