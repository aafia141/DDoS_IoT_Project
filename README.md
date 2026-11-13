# Evaluating Supervised Ensemble Learning for DDoS Detection in IoT Networks under Unseen Attack Conditions

## Overview

This project investigates supervised machine learning and ensemble-based approaches for detecting Distributed Denial-of-Service (DDoS) attacks in IoT-oriented network traffic.

The study evaluates the performance of individual classifiers and voting-based ensemble mechanisms under unseen attack-category conditions. It also investigates threshold calibration, feature importance stability, feature ablation and cross-dataset generalisation.

## Research Objectives

- Evaluate supervised machine learning models for DDoS detection.
- Compare Random Forest, Extra Trees and XGBoost classifiers.
- Investigate hard voting and soft voting ensemble mechanisms.
- Evaluate generalisation under Leave-One-Category-Out (LOCO) conditions.
- Apply validation-based threshold calibration subject to a false-positive-rate constraint.
- Analyse feature importance and ranking stability across random seeds.
- Investigate the impact of removing the `Inbound` feature.
- Examine cross-dataset transfer from CIC-DDoS2019 to ToN-IoT.
- Evaluate Isolation Forest as a separate unsupervised anomaly-detection baseline.

## Datasets

The experiments use the following publicly available datasets:

**1. CIC-DDoS2019**

Source: https://cicresearch.ca/CICDataset/CICDDoS2019/

Used for the primary DDoS detection experiments, including attack-category holdout evaluation.

**2. ToN-IoT**

Source: https://research.unsw.edu.au/projects/toniot-datasets

Used for supplementary cross-dataset evaluation.

The datasets are not included in this repository. Users must obtain them from their respective official sources and prepare the required processed files.

## Machine Learning Models

The following supervised classifiers and ensemble mechanisms are evaluated:

- Random Forest
- Extra Trees
- XGBoost
- Hard Voting
- Soft Voting

An independently trained Isolation Forest is also evaluated as an unsupervised anomaly-detection baseline.

## Experimental Methodology

The experimental evaluation includes:

1. Data preprocessing and feature preparation.
2. Training and validation using stratified data splits.
3. Leave-One-Category-Out evaluation across selected DDoS attack categories.
4. Validation-based threshold calibration with a false-positive-rate constraint.
5. Feature importance analysis across five random seeds.
6. Feature ablation to investigate dependence on the `Inbound` feature.
7. Supplementary cross-dataset evaluation using five mapped traffic features.

## Key Findings

- Calibrated Extra Trees achieved 100% aggregate attack recall in the LOCO evaluation, with an aggregate false-positive rate of approximately 0.833%.
- Calibrated soft voting achieved 100% aggregate attack recall, with an aggregate false-positive rate of approximately 0.900%.
- Hard voting produced a lower aggregate false-positive rate but missed additional attack observations.
- Feature-ranking stability analysis produced a mean pairwise Spearman correlation of 0.816 across five random seeds.
- Removing the `Inbound` feature increased aggregate false negatives from zero to seven.
- Cross-dataset evaluation showed performance degradation when transferring the CIC-DDoS2019-trained model to ToN-IoT.

These findings are specific to the datasets, preprocessing procedures and experimental configurations used in this study.

## Repository Structure

```text
ddos-detection-iot/
│
├── DDoS_IoT_Majority_Voting_Zero_Day.ipynb
│
├── results/
│   ├── Experiment result CSV files
│   ├── Evaluation summaries
│   └── Generated figures
│
├── .gitignore
├── README.md
└── requirements.txt
```

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- PyArrow

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/ddos-detection-iot.git
cd ddos-detection-iot
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `DDoS_IoT_Majority_Voting_Zero_Day.ipynb` to explore the implementation and experiments.

**Note:** Dataset preparation and local file paths must be configured before executing the notebook.

## Limitations

- The primary evaluation uses selected processed CIC-DDoS2019 attack categories.
- Category holdout is a controlled proxy for unseen attack conditions and does not establish detection of arbitrary future exploits.
- Feature stability results are based on five random seeds within the same dataset.
- Cross-dataset evaluation uses a limited five-feature mapping.
- The experiments do not establish deployment readiness in real-world IoT environments.

## Author

Aafia Amina  
B.Tech Computer Science and Engineering  
National Institute of Technology Puducherry

## Disclaimer

This repository accompanies an academic research project. Experimental results should be interpreted in the context of the datasets, preprocessing procedures and evaluation settings described in the research study.