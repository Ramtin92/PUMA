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

# Methods

## Illustrative Example

<img src="Figures/Figure 1.png" alt="drawing" width="600px"/> 
<p>Illustrative example of uncertainty when mapping measurements to metabolites and pathways. Pathways (ovals) are associated with metabolites (circles), which in turn are associated with measurements (square). White circles represent non-measured metabolite with membership in one or more pathways. Blue circles represent measured metabolites that have multiple-pathway memberships (multiple-pathway membership is assumed but not shown for j3 and j4). The red circle represents a metabolite that has membership in only one pathway. Measurement w5 uniquely maps to j13, which uniquely maps to Pathway 2, while all other measurements map to multiple metabolites, as shown by solid or dotted lines.</p>


## Workflow

<img src="Figures/Figure 2.png" alt="drawing" width="600px"/> 
<p>Comparison of a workflow to collect and interpret observations (A), and a generative model that captures a biological process (B).</p>


## The Generative Model

<img src="Figures/Figure 3.png" alt="drawing" width="600px"/> 
<p>Graphical representation of the generative model. To avoid representing all I pathways, J metabolites, and K masses in the graph we use the ‘plate’ notation and draw one representative node per variable and enclosing these variables in a plate (rectangular box). The number of instances of each enclosed variable is indicated by the fixed constant in the lower right corner of the box. Random variables of the model (a, z, m, w) are shown in white circles. The variable m has a deterministic relationship with Z. The shaded circle, labelled w, represents an observed random variable. μ, λ, γ are parameters to the model.</p>

# Results

## Model Validation

<img src="Figures/Figure 4.png" alt="drawing" width="600px"/> 
<p>AUC for ROC curves for the synthetic datasets under different assumptions regarding pathway activity and metabolite generation. (A,C,E) PUMA. (B,D,F) Enrichment ratio.</p>

## Case Study: Chinese Hamster Ovary (CHO) Cell

### Probabilities of Pathway Activities

<img src="Figures/Figure 5.png" alt="drawing" width="600px"/> 
<p>Probability of pathway activities as computed by PUMA vs. enrichment ratios for CHO cell. Each data point is marked as either statistically enriched (red) or non-statistically enriched (blue) based on a Fisher’s Exact Test p-values of 0.05.</p>

### Probabilities of Metabolite Annotations

<img src="Figures/Figure 6.png" alt="drawing" width="600px"/> 
<p>Metabolite annotations attained with PUMA against those identified by: (A) searching spectral databases, HMDB and METLIN, and (B) BioCAn. The blue slice in each pie represents “agreement”. The orange and gray slices represent “semi-agreement” and “disagreement” respectively. Finally, the yellow slice represents the number of mass measurements that could only be annotated by PUMA.</p>


### Evaluation of PUMA in Overcoming Uncertainty in Annotation

#### Experiments on synthetic datasets

<img src="Figures/Figure S1.png" alt="drawing" width="600px"/> 
<p> PUMA performance in overcoming uncertainty of multiple assignments. Average recall, precision and accuracy for different experiments in synthetic dataset assuming 0.3 of pathways are active. The x-axis corresponds to the fraction of active metabolites, and y-axis shows correctly identified pathways with multiple candidates. (A) original 𝜏 matrix, mapping metabolites to the corresponding mass bin, (B) 𝜏 matrix is modified based on ground truth, and (C) 𝜏 matrix is modified based on random selection of metabolites.</p>

<img src="Figures/Figure S2.png" alt="drawing" width="600px"/> 
<p>PUMA performance in overcoming uncertainty of multiple assignments. Average recall, precision and accuracy for different experiments in synthetic dataset assuming 0.5 of pathways are active. The x-axis corresponds to the fraction of active metabolites, and y-axis shows correctly identified pathways with multiple candidates. (A) original 𝜏 matrix, (B) 𝜏 matrix is modified based on ground truth, and (C) 𝜏 matrix is modified based on random selection of metabolites.</p>

<img src="Figures/Figure S3.png" alt="drawing" width="600px"/> 
<p>PUMA performance in overcoming uncertainty of multiple assignments. Average recall, precision and accuracy for different experiments in synthetic dataset assuming 0.7 of pathways are active. The x-axis corresponds to the fraction of active metabolites, and y-axis shows correctly identified pathways with multiple candidates. (A) original 𝜏 matrix, (B) 𝜏 matrix is modified based on ground truth, and (C) 𝜏 matrix is modified based on random selection of metabolites.</p>

## Case Study: Human Urinary Sample

### Probabilities of Pathway Activities

<img src="Figures/Figure 7.png" alt="drawing" width="600px"/> 
<p>Probability of pathway activities as computed by PUMA vs. enrichment ratios for the human urine sample. Each data point is marked as either statistically enriched (red) or non-statistically enriched (blue) based on a Fisher’s Exact Test p-values of 0.05.</p>

### Probabilities of Metabolite Annotations

<img src="Figures/Figure 8.png" alt="drawing" width="600px"/> 
<p>Metabolite annotations attained with PUMA against those identified by Roux et al. The blue slice represents “agreement”. The orange slice represents “clarification”. The gray slice represents “disagreement” and the yellow slice represents “model incompleteness issue”.</p>
