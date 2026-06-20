# Hamming PUF Response Prediction using Linear Machine Learning Models

## Overview

This project investigates the vulnerability of XOR-based Hamming Physical Unclonable Functions (PUFs) to linear machine learning attacks. The objective is to predict PUF responses from Challenge-Response Pairs (CRPs) by transforming the challenge space into a higher-dimensional feature representation that enables effective linear classification.

## Problem Statement

Physical Unclonable Functions (PUFs) are widely used for hardware authentication and security. This project explores whether an XOR-based Hamming PUF can be accurately modeled using linear machine learning techniques given a sufficient number of challenge-response pairs.

## Methodology

### Feature Mapping

The original 32-bit challenge vector is transformed into a 288-dimensional feature space:

* 256 pairwise interaction features between even and odd indexed challenge bits
* 16 transformed even-indexed challenge bits
* 16 transformed odd-indexed challenge bits

The binary challenge values `{0,1}` are first mapped to `{-1,+1}` before feature construction.

### Machine Learning Model

* Model: Linear Support Vector Classifier (LinearSVC)
* Loss Function: Squared Hinge Loss
* Regularization Parameter (C): 0.5
* Tolerance: 0.01
* Maximum Iterations: 5000

### Hyperparameter Exploration

The project includes experiments involving:

* Different regularization strengths (C)
* Hinge vs Squared-Hinge loss functions
* L1 vs L2 penalties
* Comparison between LinearSVC and Logistic Regression
* Training-set size analysis

## Results

### Key Findings

* Achieved **99.88% test accuracy** on unseen Challenge-Response Pairs.
* Demonstrated that approximately **3500 CRPs** are sufficient to achieve **99% prediction accuracy**.
* LinearSVC provided an excellent trade-off between accuracy and training time.
* The proposed feature mapping effectively transforms the PUF prediction problem into a nearly linearly separable classification task.

## Repository Structure

```text
.
├── PUFs.ipynb          # Complete Colab notebook
├── Final.py           # Final implementation
├── Report.pdf         # Detailed project report
├── requirements.txt
└── README.md
```

## Requirements

```bash
pip install numpy scikit-learn pandas matplotlib seaborn
```

## Running the Project

1. Obtain the dataset and place it in the appropriate directory.
2. Open `PUFs.ipynb` or execute the Python implementation.
3. Train the model and evaluate performance on the test set.


## Technologies Used

* Python
* NumPy
* Scikit-Learn
* Google Colab

