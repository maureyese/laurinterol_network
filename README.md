# laurinterol_network
Network Pharmacology Analysis of Laurinterol for Target Identification in Breast Cancer **Under development (As of August 2024)**

Laurinterol, a brominated sesquiterpene derived from marine red algae, has shown promise as a bioactive compound with potential anticancer properties. However, the exact molecular mechanisms and potential targets of laurinterol in breast cancer remain largely unexplored. Identifying these targets is crucial for understanding its therapeutic potential and guiding its development as a cancer treatment.

## Objectives:

1. Utilize computational tools to predict potential targets of laurinterol within the context of breast cancer.
2. Develop a protein interaction network using identified targets, and screen for hub genes that play central roles in breast cancer pathogenesis.
3. Conduct functional annotation and pathway enrichment analysis on the hub genes to elucidate the biological processes and signaling pathways influenced by laurinterol in breast cancer.
4. Perform molecular docking analysis to validate the interaction between laurinterol and the identified hub genes, confirming their potential as therapeutic targets in breast cancer.
5. Assess the prognostic significance of the identified hub genes through survival analysis, particularly in estrogen receptor-positive (ER-positive), estrogen receptor-negative (ER-negative), and PAM50 molecular subtypes.

## 1. Pharmacological evaluation of laurinterol

- PubChem: https://pubchem.ncbi.nlm.nih.gov/
- SwissADME: http://www.swissadme.ch/
- ADMETlab: https://admetmesh.scbdd.com/
- Tox-Prediction-II: https://tox.charite.de/protox3/?site=compound_input
- Molinspiration: https://molinspiration.com/

## 2. Databases to identify potential laurinterol targets in human

- SwissTargetPrediction: http://swisstargetprediction.ch/
- SuperPred: https://prediction.charite.de/
- TargetNet: http://targetnet.scbdd.com/
- PharmMapper: https://www.lilab-ecust.cn/pharmmapper/

## Approach 1 - 3. Databases to identify breast cancer-associated genes

- GeneCards: https://www.genecards.org/
- DisGeNET: https://disgenet.com/
- OMIM: https://omim.org/

## Approach 2 - 3. WGCNA to identify module-trait relationships

Dataset: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE25066 (Discovery and validation cohort)
or
Dataset: TCGA-BRCA

```R
library(WGCNA)
```

Follow instructions from: https://link.springer.com/article/10.1186/s13020-021-00534-y

## 3.1 Normalize IDs across databases

- DAVID: https://david.ncifcrf.gov/list.jsp (Retrieve gene SYMBOL)

## 4. Construction of protein interaction network and screening of hub target

- Venn Diagram (R library)
- STRING (Follow instructions from https://www.biorxiv.org/content/10.1101/2024.04.30.580419v1.full.pdf): https://cn.string-db.org/
- Cytoscape
- CytoHubba

## 5. Gene Set Enrichment Analysis

```R
library(clusterProfiler) # GO and KEGG
```

## Approach 1 - 6. Multivariate Cox Proportional-Hazards Model

**Justification:** Construct Cox Proportional-Hazards models to assess the impact of hub gene expression on survival while controlling for other clinical variables such as age, tumor size, or lymph node status.

```R
library(survival)
library(survminer)
```

Time to distant relapse using https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE25066
or
Overall survival using TCGA-BRCA

## Approach 2 - 6. Survival analysis using Kaplan-Meier

Analyze how the identified targets and pathways affect different subgroups of breast cancer patients (e.g., based on subtype or treatment response).

- Stratify patients into high and low expression groups using median or quartile cut-offs.
- Perform Kaplan-Meier survival analysis for each hub gene within these subtypes to compare the survival rates between the high and low expression groups.
- Use the log-rank test to determine if the differences in survival are statistically significant.

## 7. Molecular Docking

- Autodock Vina (Python)
- PyMOL visualization

## Future perspectives:

- Cell lines and cell proliferation assays
- Reverse transcription quantitative polymerase chain reaction (RT-qPCR) analysis
- Enzyme-linked immunosorbent assay (ELISA)
- Western blot assay
