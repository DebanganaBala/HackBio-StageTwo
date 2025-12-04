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
1. What cell types did you identify?

The dataset contains the typical immune populations found in peripheral blood mononuclear cells (PBMCs). These include naive, memory, and intermediate B cells; plasmablasts; naive and central-memory CD4 T cells; naive and effector-memory CD8 T cells; natural killer (NK) cells; proliferating T/NK cells; classical CD14 monocytes; non-classical CD16 monocytes; conventional dendritic cells; plasmacytoid dendritic cells; rare mature neutrophils; rare immature neutrophils; platelets; and a small number of hematopoietic stem or progenitor–like cells. These identities are supported by the annotated metadata (Cell.group and Cell.class_reannotated) and confirmed by expected marker gene expression patterns visualized in UMAPs and heatmaps.

2. Biological role of each cell type

Naive B cells are antigen-inexperienced lymphocytes that differentiate into antibody-producing cells after encountering a pathogen. Memory B cells are long-lived cells that respond rapidly during reinfection. Plasmablasts are highly secretory antibody-producing cells that expand dramatically during active viral infection. Naive CD4 T cells are helper T-cell precursors that differentiate after antigen presentation, while CD4 central-memory T cells provide long-term helper function. Naive CD8 T cells give rise to cytotoxic effector cells, and CD8 effector-memory T cells directly kill infected cells and produce antiviral cytokines. NK cells are innate cytotoxic lymphocytes that respond rapidly to infected or stressed cells without prior antigen exposure. Classical CD14 monocytes are inflammatory phagocytes that produce cytokines and contribute to pathogen recognition, whereas non-classical CD16 monocytes patrol the vasculature and respond to tissue damage. Conventional dendritic cells present antigens to T cells and initiate adaptive immunity, while plasmacytoid dendritic cells produce type I interferons during viral infection. Neutrophils are short-lived phagocytes that respond rapidly to inflammation. Platelets contribute to coagulation and also interact with innate immune pathways. The rare HSPC-like cells represent circulating progenitor cells occasionally found in blood.

3. Is the tissue source really bone marrow? Justify your answer.

The tissue is not bone marrow; it is PBMC. This is supported by both metadata and biological composition. The metadata fields tissue and tissue_original explicitly identify the sample as PBMC. The cellular composition confirms this: the dataset is dominated by mature T cells, B cells, NK cells, and monocytes, which is characteristic of PBMC. Bone marrow would instead contain abundant erythroid precursors, megakaryocyte progenitors, and a continuous granulocytic maturation hierarchy from myeloblasts through segmented neutrophils. These expected bone marrow lineages are absent. Neutrophils appear only as a tiny fraction, which is expected in PBMC because density-based isolation removes granulocytes. The dataset also contains only very rare hematopoietic progenitors, whereas bone marrow contains many such cells. Every line of evidence therefore supports that the tissue source is PBMC rather than bone marrow.

4. Based on the relative abundance of cell types, is the patient healthy or infected? Defend your conclusion.

The patient is infected and shows clear signs of systemic inflammation. Severe cases in the dataset display an expansion of classical monocytes, which is a hallmark of inflammatory responses and cytokine-driven innate activation. Plasmablasts are also substantially increased, reflecting strong antibody-secreting activity characteristic of acute viral infection. Effector-memory CD8 T cells are elevated, indicating an active cytotoxic antiviral response. NK cell levels remain high, consistent with innate activation in viral disease. In contrast, naive CD4 T cells are sharply decreased in severe samples, a well-documented form of lymphopenia in COVID-19. Together, these shifts support that the immune system is responding to an ongoing infection rather than representing a healthy baseline.
