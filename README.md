# GSE338571-RNAseq-Interaction-Analysis
Reproducible computational analysis of GSE338571 RNA-seq data examining cell-context-dependent epithelial responses to macrophage-associated IL-1β exposure.
# GSE338571 RNA-seq Interaction Analysis

Reproducible computational repository for the GSE338571 epithelial/macrophage RNA-seq interaction analysis.

## Overview

This repository contains the reproducible computational workflow used to analyze cell-context-dependent epithelial transcriptional responses associated with macrophage IL-1β exposure in GSE338571.

The analysis compares two epithelial cell contexts:

- FHC
- NCM460

under two macrophage-associated IL-1β conditions:

- Low IL-1β
- High IL-1β

The primary question is whether the transcriptional response to increased IL-1β differs between FHC and NCM460 cells.

## Primary interaction contrast

The primary interaction was defined as:

`(NCM460 high - low) - (FHC high - low)`

Interpretation:

- Negative interaction values indicate a relatively stronger response in FHC.
- Positive interaction values indicate a relatively stronger response in NCM460.

This interaction term tests whether the high-versus-low IL-1β response differs between the two epithelial cell contexts.

## Dataset

The analysis uses the publicly available NCBI Gene Expression Omnibus dataset:

**GSE338571**

The original GEO dataset should be obtained directly from the public GEO record.

NCBI GEO:

https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE338571

The original GEO source data are not redistributed in this repository.

## Sample design

The study contains 12 samples with three biological replicates per experimental group.

### FHC-low

- GSM9877619
- GSM9877620
- GSM9877621

### FHC-high

- GSM9877622
- GSM9877623
- GSM9877624

### NCM460-low

- GSM9877625
- GSM9877626
- GSM9877627

### NCM460-high

- GSM9877628
- GSM9877629
- GSM9877630

## Computational workflow

The primary interaction analysis consists of the following steps:

1. Read the 12-sample expression matrix.
2. Normalize each sample to counts per million (CPM) using its library total.
3. Retain genes with CPM >= 1 in at least 3 samples.
4. Transform retained expression values using:

   `log2(CPM + 0.5)`

5. Fit a two-factor ordinary least-squares model:

   `expression ~ context + condition + context:condition`

6. Extract the context-by-condition interaction coefficient.
7. Calculate the nominal P value for the interaction term.
8. Apply Benjamini-Hochberg false discovery rate (FDR) correction across all retained genes.

The implementation uses Python and ordinary least squares rather than DESeq2.

## Primary audited results

The supplied expression matrix contained:

- **60,664 genes represented**
- **15,313 genes retained after filtering**
- **0 individual interaction genes with FDR < 0.05**
- **Minimum interaction FDR = approximately 0.559615**

The top nominal interaction candidate was:

`ENSG00000260526`

with an interaction effect of approximately:

`+1.20347`

and nominal:

`P ≈ 4.812 × 10^-5`

Because no individual interaction gene passed FDR < 0.05, the gene-level interaction analysis does not support a genome-wide FDR-significant individual-gene interaction set.

## Ordered KEGG pathway analysis

Genome-wide ordered pathway analysis identified two pathway-level signals:

### Cell cycle

- KEGG:04110
- Adjusted P = 0.0177243
- 10 pathway-hit genes

### Homologous recombination

- KEGG:03440
- Adjusted P = 0.0321138
- 9 pathway-hit genes

Across the 19 pathway-hit genes:

- 18 showed an FHC-direction interaction
- 1 showed an NCM460-direction interaction

These are pathway-level findings and should be interpreted as hypothesis-generating evidence rather than as evidence that individual genes are genome-wide FDR-significant.

## Coexpression network

Network #5 was constructed from 15 nominal interaction candidates.

The network uses:

- Pearson correlation
- 12 samples
- absolute correlation threshold |r| >= 0.75
- 50 coexpression edges

Fourteen unique genes are represented among the edges, with one of the 15 candidate genes isolated.

This is a **coexpression network**, not a protein-protein interaction (PPI) network.

The network does not establish molecular causality.

## Independent biological context

GSE62208 was examined as an independent biological context.

The analysis used untreated H4 controls versus IL-1β-only samples and identified transcript-level differential signals.

This dataset is considered independent biological support/context rather than an exact quantitative replication of the GSE338571 interaction analysis.

The available audit does not establish homologous-recombination replication in GSE62208.

## Reproducibility

The primary analysis was independently reconstructed from the supplied expression matrix.

The reconstructed workflow reproduces the previously validated interaction results to floating-point precision, including:

- interaction effect estimates
- nominal P values
- FDR values
- nominal-P ranking

The primary computational workflow is provided in:

```text
code/01_reproduce_interaction.py
