# DSCI 552 Homework 5

This repository contains the Homework 5 submission for DSCI 552. The assignment covers multi-class and multi-label classification with support vector machines, k-means clustering on the Anuran Calls data set, and hierarchical clustering from ISLR 12.6.2.

## Contents

- `Homework5.pdf` - original assignment prompt.
- `notebook/hw5.ipynb` - completed analysis notebook.
- `data/Anuran Calls (MFCCs)/Frogs_MFCCs.csv` - Anuran Calls MFCC data set used in the notebook.
- `requirements.txt` - Python dependencies needed to run the notebook.

## Setup

Create and activate a Python environment, then install the required packages:

```bash
pip install -r requirements.txt
```

Launch Jupyter and open the notebook:

```bash
jupyter notebook notebook/hw5.ipynb
```

The data set is already included under `data/`, so the notebook can be run without downloading the UCI archive again.

## Assignment Summary

### 1. Multi-Class and Multi-Label Classification

The notebook uses the Anuran Calls (MFCCs) data set, with `Family`, `Genus`, and `Species` as the three labels. A random 70/30 train-test split is used for supervised learning.

Models evaluated:

- Gaussian-kernel SVMs with one-vs-all classifiers on raw attributes.
- Gaussian-kernel SVMs with standardized attributes.
- L1-penalized linear SVMs with standardized attributes.
- L1-penalized linear SVMs with SMOTE for class imbalance.
- Extra practice: classifier chains for the same multi-label problem.

The notebook evaluates models using exact match ratio, Hamming score, and Hamming loss.

Best reported supervised result:

| Model | Exact Match Ratio | Hamming Score | Hamming Loss |
| --- | ---: | ---: | ---: |
| Gaussian SVM, raw attributes | 0.987957 | 0.991817 | 0.008183 |
| Gaussian SVM, standardized | 0.983789 | 0.988266 | 0.011734 |
| L1 Linear SVM, standardized | 0.912459 | 0.943029 | 0.056971 |
| SMOTE + L1 Linear SVM | 0.855952 | 0.924348 | 0.075652 |

The strongest result in this run came from the Gaussian-kernel SVM on the original normalized attributes.

### 2. K-Means Clustering

The notebook performs k-means clustering on the full Anuran Calls data set without a train-test split. For each Monte Carlo run, it selects `k` from 1 through 50, assigns each cluster a majority `Family`, `Genus`, and `Species` label, and computes Hamming metrics against the true labels.

Monte Carlo summary over 50 runs:

| Metric | Value |
| --- | ---: |
| Average Hamming Distance | 0.718669 |
| Average Hamming Score | 0.760444 |
| Average Hamming Loss | 0.239556 |
| Standard Deviation of Hamming Distance | 0.130910 |

The selected `k` values across the runs were `{2, 3, 4, 5, 6}`.

### 3. ISLR 12.6.2

The notebook answers the hierarchical clustering questions from ISLR 12.6.2, including complete-linkage and single-linkage dendrograms and the two-cluster cuts for each dendrogram.

Reported cluster cuts:

- Complete linkage: `(0, 1)` and `(2, 3)`.
- Single linkage: `(3)` and `(2, 0, 1)`.
