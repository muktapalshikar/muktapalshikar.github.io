---
layout: archive
title: "Some of Mukta's projects"
permalink: /projects/
author_profile: true
---

## Spatial analysis of human colorectal tumors reveals organized immune hubs at the stromal/epithelial interface

GitHub repository: [https://github.com/muktapalshikar/crcmanuscript2025](https://github.com/muktapalshikar/crcmanuscript2025)

- Manuscript under review - coming soon!

## scBONITA: single-cell Boolean Omics Network Invariant Time Analysis

GitHub repository: [https://github.com/muktapalshikar/scBONITA](https://github.com/muktapalshikar/scBONITA)

- uses scRNA-seq data to infer Boolean regulatory rules for topologically characterized networks
- prioritizes genes based on their impact on signaling
- performs pathway analysis, and
- maps sequenced cells to characteristic signaling states of these networks

### Executable models of immune signaling pathways in HIV-associated atherosclerosis

#### Citation: 

**Palshikar, M. G.**, Palli, R., Tyrell, A., Maggirwar, S., Schifitto, G., Singh, M. V., & Thakar, J. (2022). _Executable models of immune signaling pathways in HIV-associated atherosclerosis_. npj Systems Biology and Applications, 8(1), 35. [PMID36131068](https://pubmed.ncbi.nlm.nih.gov/36131068/)

[Download paper here](https://doi.org/10.1038/s41540-022-00246-5)

#### Abstract:
Atherosclerosis (AS)-associated cardiovascular disease is an important cause of mortality in an aging population of people living with HIV (PLWH). This elevated risk has been attributed to viral infection, anti-retroviral therapy, chronic inflammation, and lifestyle factors. However, rates at which PLWH develop AS vary even after controlling for length of infection, treatment duration, and for lifestyle factors. To investigate the molecular signaling underlying this variation, we sequenced 9368 peripheral blood mononuclear cells (PBMCs) from eight PLWH, four of whom have atherosclerosis (AS+). Additionally, a publicly available dataset of PBMCs from persons before and after HIV infection was used to investigate the effect of acute HIV infection. To characterize dysregulation of pathways rather than just measuring enrichment, we developed the single-cell Boolean Omics Network Invariant Time Analysis (scBONITA) algorithm. scBONITA infers executable dynamic pathway models and performs perturbation analysis to identify high impact genes. These dynamic models are used for pathway analysis and to map sequenced cells to characteristic signaling states (attractor analysis). scBONITA revealed that lipid signaling regulates cell migration into the vascular endothelium in AS+ PLWH. Pathways implicated included AGE-RAGE and PI3K-AKT signaling in CD8+ T cells, and glucagon and cAMP signaling pathways in monocytes. Attractor analysis with scBONITA facilitated pathway-based characterization of cellular states in CD8+ T cells and monocytes. In this manner, we identify critical cell-type specific molecular mechanisms underlying HIV-associated atherosclerosis using a novel computational method.

## WikiNetworks: Process pathways from the WikiPathways database into machine-readable network representations

GitHub repository: [https://github.com/muktapalshikar/WikiNetworks](https://github.com/muktapalshikar/WikiNetworks)

#### Citation:

***Palshikar, M. G.***, S. P. Hilchey, M. S. Zand and J. Thakar (2022). "WikiNetworks: translating manually created biological pathways for topological analysis." Bioinformatics 38(3): 869-871.

[Download paper here](https://doi.org/10.1093/bioinformatics/btab699)

#### Abstract:
WikiPathways is a database of 2979 biological pathways across 31 species created using the drawing software PathVisio. Many of these pathways are not directly usable for network-based topological analyses due to differences in curation styles and drawings. We developed the WikiNetworks package to standardize and construct directed networks by combining geometric information and manual annotations from WikiPathways. WikiNetworks performs significantly better than existing tools. This enables the use of high-quality WikiPathways resource for network-based topological analysis of high-throughput data.

## BONITA: Boolean rules and pathway analysis on bulk omics data

GitHub repositories: [BONITA - Python3](https://github.com/Thakar-Lab/BONITA-Python3), [BONITA - Python2](https://github.com/Thakar-Lab/BONITA)

#### Citation:

Palli, R., ***M. G. Palshikar*** and J. Thakar (2019). "Executable pathway analysis using ensemble discrete-state modeling for large-scale data." PLoS computational biology 15(9): e1007317.

[Download paper here](https://doi.org/10.1093/bioinformatics/btab699)

#### Abstract:
Pathway analysis is widely used to gain mechanistic insights from high-throughput omics data. However, most existing methods do not consider signal integration represented by pathway topology, resulting in enrichment of convergent pathways when downstream genes are modulated. Incorporation of signal flow and integration in pathway analysis could rank the pathways based on modulation in key regulatory genes. This implementation can be facilitated for large-scale data by discrete state network modeling due to simplicity in parameterization. Here, we model cellular heterogeneity using discrete state dynamics and measure pathway activities in cross-sectional data. We introduce a new algorithm, Boolean Omics Network Invariant-Time Analysis (BONITA), for signal propagation, signal integration, and pathway analysis. Our signal propagation approach models heterogeneity in transcriptomic data as arising from intercellular heterogeneity rather than intracellular stochasticity, and propagates binary signals repeatedly across networks. Logic rules defining signal integration are inferred by genetic algorithm and are refined by local search. The rules determine the impact of each node in a pathway, which is used to score the probability of the pathway’s modulation by chance. We have comprehensively tested BONITA for application to transcriptomics data from translational studies. Comparison with state-of-the-art pathway analysis methods shows that BONITA has higher sensitivity at lower levels of source node modulation and similar sensitivity at higher levels of source node modulation. Application of BONITA pathway analysis to previously validated RNA-sequencing studies identifies additional relevant pathways in in-vitro human cell line experiments and in-vivo infant studies. Additionally, BONITA successfully detected modulation of disease specific pathways when comparing relevant RNA-sequencing data with healthy controls. Most interestingly, the two highest impact score nodes identified by BONITA included known drug targets. Thus, BONITA is a powerful approach to prioritize not only pathways but also specific mechanistic role of genes compared to existing methods.
