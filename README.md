README
Single-Cell RNA-seq Analysis of Immune Cells (COVID-19 PBMC Dataset)

This repository contains a single-cell RNA-seq analysis using the dataset bone_marrow.h5ad and the notebook Single_Cell_Pipeline.ipynb.
Although the filename suggests bone marrow, metadata and cellular composition confirm the dataset contains PBMCs from COVID-19 patients.

Project Structure
- Single_Cell_Pipeline.ipynb
- bone_marrow.h5ad
- README.md

Dataset Overview
- File: bone_marrow.h5ad
- Number of cells: ~14,783
- Data type: Single-cell RNA sequencing (UMI-based)
- disease = "COVID-19"
- COVID-19 Condition = ["severe", "remission"]
- tissue = "blood"
- tissue_original = "PBMC"
- Cell.class_reannotated = curated fine-grained cell types
- Lineage = broad lineage labels


These fields confirm the dataset is PBMC, not bone marrow.

Pipeline Summary
- Load dataset
- Perform quality control (low gene count, high mitochondrial %, doublet removal)
- Normalize and log-transform counts
- Identify highly variable genes
- Perform PCA
- Build neighbor graph
- Generate UMAP embedding
- Run Leiden clustering
- Identify marker genes
- Annotate cell types
- Summarize lineage-level distributions

Biological Interpretation
1. Identified Cell Types
B lineage
- B naive
- B intermediate
- B memory
- Plasmablast

T and NK lineage
- CD4+ T naive
- CD4+ T central memory
- CD8+ T naive
- CD8+ T effector memory
- T/NK proliferative
- NK cells

Myeloid lineage
- Classical monocytes
- Non-classical monocytes
- Conventional dendritic cells (cDC)
- Plasmacytoid dendritic cells (pDC)

Granulocyte / progenitor / megakaryocyte lineage
- Neutrophils
- Immature neutrophils
- Hematopoietic stem/progenitor cells (HSPC)
- Platelets / megakaryocyte fragments

2. Biological Roles of Each Cell Type
B lineage
- B naive: Antigen-inexperienced B cells.
- B intermediate: Transitional or activated B cells.
- B memory: Antigen-experienced long-lived B cells.
- Plasmablasts: Antibody-producing cells during active infection.

T and NK lineage
- CD4+ T naive: Helper T precursors.
- CD4+ T central memory: Memory helper cells.
- CD8+ T naive: Cytotoxic T-cell precursors.
- CD8+ T effector memory: Rapid-response cytotoxic cells.
- T/NK proliferative: Actively dividing T or NK cells.
- NK cells: Innate cytotoxic lymphocytes.

Myeloid lineage
- Classical monocytes: Inflammatory monocytes.
- Non-classical monocytes: Patrolling vascular monocytes.
- cDC: Professional antigen-presenting cells.
- pDC: Type I interferon–producing viral sentinels.

Granulocytic and progenitor lineage
- Neutrophils: Phagocytic first responders.
- Immature neutrophils: Granulocyte precursors.
- HSPC: Multipotent stem/progenitor cells.
- Platelets: Clotting and inflammatory mediators.

3. Is the Tissue Source Bone Marrow?
- Metadata indicates PBMC ("blood", "PBMC")
- Bone marrow normally contains many progenitors and erythroid cells
- These populations are almost absent
- Dataset dominated by mature lymphocytes and monocytes
- Neutrophils essentially absent due to Ficoll PBMC isolation
- Conclusion: The dataset is PBMC, not bone marrow

4. Is the Patient Healthy or Infected?
- Plasmablasts strongly expanded (~5.5%), typical of infection
- Large CD8 effector memory population (~22%)
- Presence of proliferating T/NK cells indicates clonal expansion
- Classical monocytes expanded, especially in severe samples
- Non-classical monocytes reduced
- Naive T cells depleted in severe condition
- Platelet/megakaryocyte fragments elevated
- Metadata labels all samples as COVID-19
- Conclusion: The immune profile shows infection (COVID-19), not healthy baseline
