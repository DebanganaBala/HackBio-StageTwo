# HackBio-StageTwo
🧬 Single-Cell RNA-seq Analysis of Immune Cells (COVID-19 PBMC Dataset)

This repository contains a full single-cell RNA-seq analysis pipeline applied to the dataset bone_marrow.h5ad using the notebook Single_Cell_Pipeline (2).ipynb.
Despite the filename, metadata and cell composition show that the dataset is not bone marrow — it consists of PBMCs from COVID-19 patients (severe and remission states).

The pipeline performs preprocessing, QC, dimensionality reduction, clustering, marker identification, and cell-type annotation to produce biologically interpretable results.

🔧 Project Structure
.
├── Single_Cell_Pipeline (2).ipynb     # Main analysis notebook
├── bone_marrow.h5ad                  # Input single-cell dataset (PBMC)
└── README.md                         # Project documentation

🧪 Dataset Overview

File: bone_marrow.h5ad
Cells: ~14,783
Modality: scRNA-seq (UMI counts)
Metadata fields include:

disease = "COVID-19"

COVID-19 Condition = ["severe", "remission"]

tissue = "blood"

tissue_original = "PBMC"

Cell.class_reannotated — curated fine-grained cell types

Lineage — broad lineage categories

Thus the dataset is PBMCs from COVID-19 patients, not bone marrow.

📘 Pipeline Summary

The notebook executes:

Load & inspect metadata

Quality control

Remove low-gene cells, high-mito cells, doublets (Scrublet)

Normalization & log transform

Highly variable gene selection

PCA → neighbors graph → UMAP

Leiden clustering

Differential expression

Cell-type annotation

Lineage-level summaries & marker visualization

Outputs include QC plots, UMAPs, DE tables, dotplots, and annotated cluster assignments.

🧫 Biological Interpretation

Below are the required answers from the assignment (cell types, roles, tissue source, health state).

1️⃣ What cell types were identified?

Using Cell.class_reannotated, the following 18 cell types were identified:

B lineage

B naive

B intermediate

B memory

Plasmablast

T & NK lineage

CD4+ T naive

CD4+ T central memory

CD8+ T naive

CD8+ T effector memory

T/NK proliferative

NK cells

Myeloid lineage

Classical monocytes

Non-classical monocytes

cDCs (conventional dendritic cells)

pDCs (plasmacytoid dendritic cells)

Granulocytic / progenitor / megakaryocytic

Neutrophils

Immature neutrophils

HSPC (hematopoietic stem/progenitor cells)

Platelets / megakaryocytic fragments

2️⃣ Biological role of each cell type (concise definitions)

B-lineage cells

B naive: antigen-inexperienced B cells, ready to respond to new pathogens.

B intermediate: activated/transitional B cells on the path to memory/plasma fate.

B memory: long-lived antigen-experienced B cells enabling rapid secondary responses.

Plasmablasts: short-lived antibody-producing B-cell descendants during active infection.

T & NK cells

CD4+ T naive: helper T-cell precursors awaiting antigen encounter.

CD4+ Tcm: memory helper cells that coordinate secondary immune responses.

CD8+ T naive: cytotoxic precursors that differentiate upon viral recognition.

CD8+ Tem: circulating cytotoxic memory T cells capable of rapid effector functions.

T/NK proliferative: cycling T/NK cells undergoing clonal expansion during infection.

NK cells: innate cytotoxic cells that kill virally infected or stressed cells.

Myeloid

Classical monocytes: inflammatory monocytes that enter tissues and become macrophages/DCs.

Non-classical monocytes: patrolling cells that survey vasculature and clear debris.

cDCs: professional antigen-presenting cells that activate naive T cells.

pDCs: major producers of type I interferons in viral infection.

Granulocytic / progenitor

Neutrophils: short-lived phagocytes and first responders to infection.

Immature neutrophils: early granulocytic precursors, often seen in severe inflammation.

HSPC: multipotent blood progenitors, typically residing in bone marrow.

Platelets: megakaryocyte-derived fragments essential for clotting and inflammation.

3️⃣ Is the tissue source really bone marrow?
Conclusion: No — this is PBMC, not bone marrow.
Biological evidence:
⭐ Expected in bone marrow but missing here

High abundance of HSC/MPP/CMP/GMP/MEP progenitors → not present

Rich granulocytic maturation series (myelocytes, metamyelocytes) → almost entirely absent

Large erythroid precursor compartment → completely absent

⭐ Observed cell composition matches PBMC

Dominance of mature lymphocytes (T, B, NK)

Classical + non-classical monocytes present in typical PBMC proportions

Neutrophils nearly absent (as expected with Ficoll prep)

Only trace HSPCs and immature neutrophils

⭐ Metadata says so directly

tissue = "blood"

tissue_original = "PBMC"

The dataset layout, cell-type composition, and metadata all confirm this is peripheral blood mononuclear cells, not bone marrow.

4️⃣ Based on cell-type abundances, is the patient healthy or infected?
Conclusion: The patients are infected — consistent with COVID-19.
Supporting evidence:
🔹 Strong plasmablast expansion (~5.5%)

Healthy PBMC typically show <1% plasmablasts.
This is a hallmark of acute viral infection.

🔹 Effector/memory T-cell dominance

CD8+ Tem extremely high (~22%)

Proliferating T/NK cluster present (~3.5%)

Naive T cells depleted in severe condition

This reflects antigen-driven activation and clonal expansion.

🔹 Monocyte inflammation signature

Classical monocytes nearly double in “severe” vs “remission”

Non-classical monocytes reduced (common in inflammation)

This is typical of systemic immune activation.

🔹 Condition metadata

Dataset includes two categories:

"severe" COVID-19

"remission" COVID-19

The immunological pattern matches the expected COVID-19 response:
plasmablast surge, inflammatory monocytes, activated cytotoxic lymphocytes, and platelet elevation.

✔ Final Interpretation

The dataset contains PBMCs, not bone marrow.

The immune landscape clearly indicates infection, not a healthy baseline.

Metadata confirms the disease is COVID-19, which is consistent with the observed immune signatures.

📎 Citation / Attribution

If you reuse this analysis, please cite this repository and the original dataset source if known.
