Prognica Labs – Computational Hit Discovery & QSAR Prototype

Tasks 5 & 6: Hit Identification and AI-Based Hit Scoring

Overview

This repository contains an end-to-end computational drug discovery workflow developed as part of Prognica Labs Tasks 5 and 6. The project focuses on:

Mining bioactive compounds against DNA gyrase from ChEMBL

Curating and filtering compounds using classical drug-likeness rules

Shortlisting viable hits with physicochemical rationale

Building an explainable QSAR prototype for AI-based hit prioritization

The pipeline integrates RDKit-based cheminformatics with machine learning (Random Forest), chemical space visualization (UMAP), model interpretability (SHAP), and scaffold-aware validation to provide a realistic early-stage hit discovery framework.

Repository Structure
.
├── Task5/
│   ├── Task_5_.ipynb                # Hit identification and compound mining
│   ├── shortlisted_hits.csv        # Final shortlisted compounds
│   └── Task5_summary.pdf           # Written Task 5 summary
│
├── Task6/
│   ├── Task6.ipynb                 # QSAR modeling and AI-based hit scoring
│   └── Task6_summary.pdf           # Written Task 6 summary
│
├── data/
│   └── (supporting CSV files)
│
├── figures/
│   └── (UMAP, SHAP, ROC images if exported)
│
├── README.md
└── requirements.txt

Task 5 – Hit Identification & Compound Mining
Objectives

Retrieve compounds targeting DNA gyrase from ChEMBL

Curate and standardize activity data

Generate molecular descriptors using RDKit

Apply Lipinski and Veber drug-likeness filters

Explore chemical space and shortlist viable hits

Key Steps

Compound Retrieval

DNA gyrase queried in ChEMBL

IC50 activity data and canonical SMILES extracted

Dataset Curation

Removal of missing/invalid SMILES

Deduplication by canonical SMILES

Conversion of IC50 values to pIC50

Descriptor Generation (RDKit)

Molecular Weight (MW)

LogP

Hydrogen Bond Donors (HBD)

Hydrogen Bond Acceptors (HBA)

Topological Polar Surface Area (TPSA)

Rotatable Bonds

Drug-Likeness Filtering

Lipinski’s Rule of Five

Veber criteria

Exploratory Analysis

Descriptor distributions

Pairwise relationships

PCA/UMAP chemical space visualization

Hit Shortlisting

Ranking by pIC50

Automated rationale per compound

Structural novelty assessment using Tanimoto similarity

Outputs

Curated compound dataset

Drug-like filtered subset

Ranked shortlist of hits with physicochemical rationale

CSV export of shortlisted compounds

Task 6 – AI-Based Hit Scoring / QSAR Prototype
Objectives

Train ML models to predict compound bioactivity

Evaluate performance using regression and classification metrics

Apply explainable AI and chemical space analysis

Generate ML-based hit rankings

Modeling Workflow

Feature Matrix

RDKit descriptors: MW, LogP, TPSA, HBD, HBA, RotBonds

Targets

Regression: pIC50

Classification: Active / Inactive (pIC50 threshold)

Modeling

Random Forest Regressor (pIC50 prediction)

Random Forest Classifier (activity classification)

Validation

RMSE and R² for regression

ROC curve for classification

Scaffold-based train/test split using Murcko scaffolds

Explainability

SHAP analysis to identify key descriptor contributions

Chemical Space

UMAP visualization (static and interactive) colored by pIC50

AI-Based Hit Scoring

Prediction of pIC50 for all compounds

ML-driven re-ranking of hits

Outputs

Trained QSAR models

RMSE, R², ROC metrics

SHAP feature importance plots

UMAP chemical space visualization

ML-ranked hit list

Model Reliability and Limitations

Dataset size is limited and derived from heterogeneous ChEMBL assays

Experimental noise and chemical series bias may affect performance

Only physicochemical descriptors were used (no fingerprints)

Therefore, the QSAR model is intended for hit prioritization rather than precise activity prediction. Despite these limitations, the workflow demonstrates a robust, explainable AI-based screening prototype suitable for early-stage discovery.

Requirements

Recommended environment:

Python ≥ 3.9

Key packages:

pandas
numpy
scikit-learn
rdkit
matplotlib
seaborn
plotly
shap
umap-learn


Install dependencies:

pip install -r requirements.txt

How to Run

Clone the repository:

git clone <your-repo-url>
cd prognica-hit-discovery


Install requirements.

Launch Jupyter:

jupyter notebook


Run notebooks in order:

Task5/Task_5_.ipynb

Task6/Task6.ipynb