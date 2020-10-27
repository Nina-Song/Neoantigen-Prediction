# Neoantigen Prediction Pipeline

  * Author: Nina Song

## Overview of the Project

  * Acccumulating abberrations in tumor cells lead to present tumor-specific mutabt peptides (neoantigens) on MHC molecules on their surface, which can distinguish tumor cells from normal cells to the immune system and are thus targets for cancer immunotherapy. Technology Platfroms and algorithms enable indentification of tumor neoantigens, such as the use of next-generation Sequencing to screen the exome and transcriptome of a tumor. The process of neoantigen identification entails indentification of tumor-specific protein sequnces and prioritization of candidate neoantigens according to their abundance, presence on patient HLA molecules and ability to elicit a T-cell response. [<sup>1</sup>](#refer-anchor-1)
  * In this project, a computational pipeline, pVACseq, is used to predict the neoantigens present in melanoma with a focus on high-throughput sequencing data. Personalized Variant Antigens by Cancer Sequencing (pVAC-Seq) is a flexible, streamlined computational workflow for identification of neoantigens that integrates tumor mutation and expression data (DNA- and RNA-seq).[<sup>2</sup>](#refer-anchor-2) pVAC-seq is available at https://github.com/griffithlab/pVAC-Seq.

## Data Demonstration

 * Metastatic melanoma cell line (COLO829) is required in this project.
 * FASTQs for tumor and germline exomes of COLO829 is available in trgn.usc.edu. To view the data by

 ```
 cd /data/colo829 
 ```

## Proposed Analysis and Tools &Software

### Prepared Input Data

#### Alignment and variant calling

| Tool                                 | Function                                       |
| ------------------------------------ | ---------------------------------------------- |
| Genome Modeling System (GMS)         | Somatic variant analysis of exome seq datasets |
| BWA (version 0.5.9)                  | Used for alignment with default parameters     |
| Picard MarkDuplicates (version 1.46) | Deduplicates the resulting alignments          |
| HLAminer (version 1)                 | Generate HLA class I haplotype of the patient  |

#### Somatic Mutation Detection and List Variants

| Tool                                     | Function                                     |
| ---------------------------------------- | -------------------------------------------- |
| Strelka (version 1.0.10)                 | Mutation Detection                           |
| Variant Effect Predictor (VEP) or Snpeff | Properly format a list of annotated variants |

### Perform Epitope Prediction

#### Generate FASTA file of peptide sequences

 * Generate a FASTA file of 17-21 mers

#### Run epitope prediction software

| Tool        | Function                                                     |
| ----------- | ------------------------------------------------------------ |
| NetMHC v3.4 | Predict high affinity peptides that bind to the HLA class I molecule |

#### Parse and filter the ouput

 * Filter: Binding-based

#### Filter neoepitope candidates

* Sequencing-based filter: Depth-based Filters and Gene Expression

### Results: Prioritized list of neoantigen vaccine candidates

## Proposed Timeline

### Milestone 1 (Due 11/03)

* Finish the data preparation (alignment and variant calling as well as somatic mutation detection)
* Check-point: Variant List

### Milestone 2 (Due 11/12)

* Complete the final list of variants, check if RNA-seq is required for further analysis. (If necessary, complete the steps of alignment and expression estimation)
* Perform epitope prediction by running epitope prediction sofeare
* Check-point: Epitope prediction results file

### Final Project Presentation (11/17)

 * Parse and filter the output to get the final results: prioritized list of neoantigen vaccine candidates
 * *Note: things could be changed depend on the feasibility



## Deliverable

 * Notebook (TBD)



## Reference

<div id="refer-anchor-1"></div>

- [1] [Bioinformatic methods for cancer neoantigen prediction](https://www.sciencedirect.com/science/article/pii/S1877117319301061)

<div id="refer-anchor-2"></div>

- [2] [pVAC-Seq: A genome-guided in silico approach to identifying tumor neoantigens](https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-016-0264-5)

