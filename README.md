# Duchenne-Muscular-Dystrophy-long-read-transcriptomics

This repository contains the computational pipelines and bioinformatic workflows developed for my **Final Degree Project (TFG) in Biomedical Sciences** at the **Instituto Químico de Sarria (IQS)**, Barcelona. The project focuses on performing a transcriptomic analysis of Duchenne Muscular Dystrophy mouse models using long-read Nanopore sequencing to identify candidate biomarkers for personalised genetic therapies.

## EXPERIMENTAL OVERVIEW
* **Animal model:** Three-month-old male mice (Wild-Type C57BL/6 vs. D2-Mdx dystrophic models).
* **Target tissue:** Cardiac muscle (whole heart RNA extraction).
* **Sequencing platform:** Oxford Nanopore Technologies (ONT) MinION.
* **Chemistry and library preparation:** R10.4.1 flow cells (FLO-MIN114) and cDNA-PCR Sequencing Kit with Barcoding (SQK-PCB114.24).

### BIOINFORMATIC FRAMEWORK

The definitive computational strategy implements two complementary, highly reproducible pipelines using standard Bioconductor and open-source command-line tools:

### Pipeline 1: Index-Based Transcript Quantification
Direct, ultra-fast alignment-free quantification at the individual transcript variant level.
* **Basecalling and demultiplexing:** Dorado v1.1.1
* **File formatting:** Samtools v1.22.1
* **Transcript indexing and quasi-mapping:** Salmon v2.0.1
* **Downstream statistical analysis:** DESeq2 (with `tximport` integration and `apeglm` log2 fold change shrinkage).

### Pipeline 2: Genome Alignment for Gene-Level Quantification
Alignment-based workflow designed to capture total gene-level expression.
* **Genome mapping:** Minimap2 v2.30-r1287 (against NCBI reference genome).
* **Feature counting:** Subread package (`featureCounts` function mapping reads to reference annotation exons).
* **Differential expression:** DESeq2

### REPOSITORY STRUCTURE AND USAGE

1. Ensure your conda environments are set up with the required packages and libraries.
2. Adapt the  storage directory paths (`<path>`) before executing script sequences.
3. For downstream data visualization (Volcano plots, interactive sample PCA, and hierarchical clustering heatmaps), scripts should be executed natively within RStudio environment using `Bioconductor v3.23` repositories.

### LICENCE

This project is open-source and available under the **MIT License**.
