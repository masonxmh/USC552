# DSCI 552 Homework 6

This repository contains the Homework 6 submission for DSCI 552.

The assignment covers:

1. Supervised, semi-supervised, and unsupervised learning on the Breast Cancer Wisconsin (Diagnostic) dataset.
2. Active vs passive learning with SVMs on the Banknote Authentication dataset.

## Contents

- `Homework6.pdf` - assignment prompt.
- `notebook/hw6.ipynb` - completed notebook with experiments, metrics, plots, and conclusions.
- `data/wdbc.data`, `data/wdbc.names` - Breast Cancer Wisconsin dataset files.
- `data/data_banknote_authentication.txt` - Banknote Authentication dataset file.
- `requirements.txt` - Python dependencies used by the notebook.

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook notebook/hw6.ipynb
```

## Part 1: Breast Cancer Wisconsin

Monte Carlo setup in notebook:

- `M = 30` runs
- stratified-style split by class with 20% per class used as test data
- metrics: accuracy, precision, recall, F1-score, AUC

### 1(b)i Supervised Learning (L1 Linear SVM, 5-fold CV)

Average metrics over 30 runs:

| Split | Accuracy | Precision | Recall | F1 | AUC |
| --- | ---: | ---: | ---: | ---: | ---: |
| Train | 0.985316 | 0.989349 | 0.971006 | 0.980069 | 0.997448 |
| Test | 0.972174 | 0.980392 | 0.944961 | 0.961767 | 0.991559 |

Example run ROC AUCs shown in notebook:

- Train: `0.996823`
- Test: `0.997416`

### 1(b)ii Semi-Supervised Self-Training (L1 Linear SVM, 5-fold CV)

Procedure:

- use 50% of each class in training set as labeled pool
- iteratively label farthest unlabeled sample from decision boundary
- retrain until unlabeled pool is exhausted

Average metrics over 30 runs:

| Split | Accuracy | Precision | Recall | F1 | AUC |
| --- | ---: | ---: | ---: | ---: | ---: |
| Train | 0.975771 | 0.983674 | 0.950888 | 0.966825 | 0.994398 |
| Test | 0.962609 | 0.971217 | 0.927907 | 0.948391 | 0.987715 |

Example run ROC AUCs shown in notebook:

- Train: `0.990366`
- Test: `0.991925`

### 1(b)iii Unsupervised Learning (KMeans as Classifier, `k=2`)

Average metrics over 30 runs:

| Split | Accuracy | Precision | Recall | F1 | AUC |
| --- | ---: | ---: | ---: | ---: | ---: |
| Train | 0.925771 | 0.948442 | 0.846943 | 0.894641 | 0.979405 |
| Test | 0.924928 | 0.946520 | 0.847287 | 0.893527 | 0.982052 |

Example run ROC AUCs shown in notebook:

- Train: `0.982726`
- Test: `0.968023`

### 1(b)iv Spectral Clustering (RBF kernel)

Average metrics over 30 runs:

| Split | Accuracy | Precision | Recall | F1 | AUC |
| --- | ---: | ---: | ---: | ---: | ---: |
| Train | 0.915859 | 0.979259 | 0.790927 | 0.874571 | 0.890434 |
| Test | 0.917391 | 0.988442 | 0.788372 | 0.876162 | 0.891408 |

Example run ROC AUCs shown in notebook:

- Train: `0.894695`
- Test: `0.876776`

### 1(b)v Comparison Summary

Based on notebook results:

- Supervised learning performs best overall.
- Semi-supervised learning is close to supervised, but slightly lower on all major metrics.
- KMeans and Spectral clustering underperform relative to supervised methods.
- Spectral clustering shows high precision but lower recall and lower AUC.

## Part 2: Banknote Authentication (Active vs Passive Learning)

Experiment setup in notebook:

- 50 Monte Carlo runs
- 472 test points, 900 training points
- linear SVM with L1 penalty and 5-fold CV
- 90 incremental models per run (10, 20, ..., 900 training samples)

### 2(b)i Passive Learning

- Adds 10 randomly selected training points per step.
- Stores test error for each incremental model.

### 2(b)ii Active Learning

- Starts with random pool of 10 points.
- Adds 10 points closest to current SVM hyperplane each step.
- Stores test error for each incremental model.

### 2(c) Learning Curve (Monte Carlo Average)

Notebook plots average test error vs number of training samples for active and passive learning.

Notebook conclusion:

- Active learning performs better than passive learning when training pool is relatively small.
- As pool size becomes large, active and passive learning converge to similar test error.

## Notes

- The notebook includes confusion matrices and ROC plots for representative runs.
- Paths and pandas/scipy/sklearn compatibility fixes were applied in notebook cells to support current package versions in `requirements.txt`.
