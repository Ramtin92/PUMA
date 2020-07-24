# Pathway-Activity Likelihood Analysis and Metabolite Annotation for Untargeted Metabolomics Using Probabilistic Modeling

> **Motivation:** Untargeted metabolomics comprehensively characterizes small molecules and elucidates activities of biochemical pathways within a biological sample. Despite computational advances, interpreting collected measurements and determining their biological role remains a challenge. 
**Results:** To interpret measurements, we present an inference-based approach, termed Probabilistic modeling for Untargeted Metabolomics Analysis (PUMA). Our approach captures metabolomics measurements and the biological network for the biological sample under study in a generative model and uses stochastic sampling to compute posterior probability distributions. PUMA predicts the likelihood of pathways being active, and then derives probabilistic annotations, which assign chemical identities to measurements. Unlike prior pathway analysis tools that analyze differentially active pathways, PUMA defines a pathway as active if the likelihood that the path generated the observed measurements is above a particular (user-defined) threshold. Due to the lack of “ground truth” metabolomics datasets, where all measurements are annotated and pathway activities are known, PUMA is validated on synthetic datasets that are designed to mimic cellular processes. PUMA, on average, outperforms pathway enrichment analysis by 8%. PUMA is applied to two case studies. PUMA suggests many biological meaningful pathways as active. Annotation results were in agreement to those obtained using other tools that utilize additional information in the form of spectral signatures. Importantly, PUMA annotates many measurements, suggesting 23 chemical identities for metabolites that were previously only identified as isomers, and a significant number of additional putative annotations over spectral database lookups. For an experimentally validated 50-compound dataset, annotations using PUMA yielded 0.833 precision and 0.676 recall.

Keywords: machine learning; inference; untargeted metabolomics; biological network; metabolic model

Ramtin Hosseini, Neda Hassanpour, Liping Liu, and Soha Hassoun (Ramtin.Hosseini@tufts.edu) "Pathway-Activity Likelihood Analysis and Metabolite Annotation for Untargeted Metabolomics using Probabilistic Modeling", Metabolites 2020, 10, 183.

Link: https://www.mdpi.com/2218-1989/10/5/183

# Getting Started
`Python 3.5.6` is used for development. We recommend installing packages using Anaconda as follows:<br>
`conda create --name PUMA --file enviroment.yml`<br>
`conda activate PUMA`<br>

# Dataset
Two examples are provided: <br>
[CHO_cell:](data/CHO_cell) Chinese Hampster Ovary Cell example provided in the paper <br>
[human_urine:](data/human_urine) A human urine example, see reference in the paper <br>

# How to run the code?
 Start executing the code by `python run_puma.py`


