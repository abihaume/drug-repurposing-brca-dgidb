# Drug Repurposing for Breast Cancer Using DGIdb

## Project Overview

This project explores drug repurposing opportunities for Breast Invasive Carcinoma (BRCA) by integrating differential gene expression results with the Drug Gene Interaction Database (DGIdb).

Starting from genes that are differentially expressed between tumor and normal tissue in TCGA-BRCA RNA-seq data, the project finds existing drugs that target these genes, then keeps only the drugs whose mechanism would push each gene back towards its normal level.

The differential expression input comes from my [TCGA-BRCA gene expression analysis](https://github.com/abihaume/tcga-brca-gene-expression-analysis).

---

## Objectives

- Identify significantly differentially expressed genes.
- Apply Benjamini–Hochberg false discovery rate (FDR) correction.
- Select the most strongly up- and downregulated genes.
- Retrieve known drug–gene interactions from DGIdb.
- Clean and integrate interaction data.
- Identify direction-aware repurposing candidates.
- Visualize gene–drug interaction patterns.

---

## Workflow

1. Load differential gene expression results (20,530 genes, 1,097 tumor vs 114 normal samples).
2. Apply Benjamini–Hochberg FDR correction.
3. Filter significant genes (FDR < 0.05 and |log2FC| > 1): **4,225 genes**, 1,412 up and 2,813 down.
4. Select the 50 most upregulated and 50 most downregulated genes.
5. Query DGIdb for all 100 genes in one GraphQL request, keeping every interaction type and source.
6. Clean and merge drug interaction data with the expression statistics.
7. Keep direction-aware candidates: inhibitors of upregulated genes, activators of downregulated genes.
8. Generate visualizations.

---

## Key Findings

<!-- Fill in after re-running the notebook with the corrected inputs -->

---

## How to Run

1. Open `notebook/Drug_Repurposing_BRCA_DGIdb.ipynb` in Databricks or Jupyter.
2. The input `results/dge_results.csv` is included. To regenerate it, run the [TCGA-BRCA analysis](https://github.com/abihaume/tcga-brca-gene-expression-analysis) and copy its `results/dge_results.csv` here.
3. For a local run, install the dependencies:

```bash
pip install -r requirements.txt
```

4. Run all cells. The notebook needs internet access to query the DGIdb API (`https://dgidb.org/api/graphql`). Tables are written to `results/` and figures to `figures/`.

---

## Repository Structure

```
drug-repurposing-brca-dgidb/
├── README.md
├── LICENSE
├── requirements.txt
├── notebook/
│   └── Drug_Repurposing_BRCA_DGIdb.ipynb
├── figures/
│   ├── top15_genes_drug_interactions.png
│   ├── top20_drugs.png
│   ├── interaction_types.png
│   └── gene_drug_network.png
└── results/
    ├── dge_results.csv                     # input: all genes with log2FC, p-value, FDR
    ├── filtered_dge_genes.csv              # FDR < 0.05 and |log2FC| > 1
    ├── top100_dge_genes.csv                # 50 most up- and 50 most downregulated
    ├── drug_gene_interactions.csv          # raw DGIdb results
    ├── cleaned_drug_gene_interactions.csv  # cleaned and merged with expression data
    ├── drugs_per_gene.csv
    ├── drug_target_summary.csv
    └── reversal_candidates.csv             # direction-aware repurposing candidates
```

---

## Technologies

- Python
- Databricks
- pandas
- NumPy
- SciPy
- Matplotlib
- NetworkX
- Requests
- DGIdb GraphQL API

---

## Limitations

- DGIdb lists known drug–gene interactions, not proven anti-cancer effects.
- Many interactions have no defined mechanism, and some entries are broad drug classes rather than single compounds.
- Many downregulated genes are adipocyte genes, which partly reflects the fat-rich composition of normal breast tissue rather than changes in tumor cells.
- Candidates are hypotheses that need literature review and experimental validation.

---

## Author

**Ume Abiha**
