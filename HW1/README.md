# Homework 1

DSCI 552 - Classification Using KNN

## Files

- `notebook/KNN_Classification.ipynb`: Main solution notebook
- `data/vertebral_column_data/`: Vertebral Column dataset files
- `Homework1.pdf`: Assignment prompt
- `requirements.txt`: Python dependencies used by the notebook

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the notebook from `HW1/notebook` so relative paths to `../data/...` resolve correctly.

## Assignment Mapping (Notebook + Homework1.pdf)

### (a) Download Vertebral Column dataset
- Implemented in notebook with download/extract utilities.
- Local dataset is used from `data/vertebral_column_data`.

### (b) Pre-processing and EDA
- Implemented:
- Pairwise scatter plots by class (`NO` vs `AB`)
- Boxplots for the six features by class
- Train/test split rule from PDF:
  first 70 rows of class 0 and first 140 rows of class 1 for training;
  remaining rows for test

### (c) KNN classification

#### (c.i) Euclidean KNN implementation
- Implemented custom helper logic and scikit-learn `KNeighborsClassifier` workflow.

#### (c.ii) Model selection over `k` and classification report
- Searched `k` in reverse with step 3 (starting from 208 down to 1).
- Best `k*`: `4`
- Minimum test error rate: `0.06`
- Minimum train error rate: `0.00`
- Metrics at `k = 4`:
- True Positive Rate: `0.9857142857142858`
- True Negative Rate: `0.8333333333333334`
- Precision: `0.9324324324324325`
- F1 score: `0.9583333333333333`

#### (c.iii) Learning curve (`N` from 10 to 210)
- Best test error by training size is computed using the PDF rule and `k` grid with step 5.
- Best overall point on this curve:
- `N* = 210`
- `k* = 6`
- Minimum test error rate: `0.08`

| N | k* | Minimum test error rate |
| --- | --- | --- |
| 10 | 1 | 0.25 |
| 20 | 6 | 0.20 |
| 30 | 1 | 0.22 |
| 40 | 11 | 0.25 |
| 50 | 26 | 0.30 |
| 60 | 21 | 0.29 |
| 70 | 26 | 0.29 |
| 80 | 31 | 0.29 |
| 90 | 41 | 0.29 |
| 100 | 6 | 0.25 |
| 110 | 6 | 0.22 |
| 120 | 16 | 0.17 |
| 130 | 16 | 0.16 |
| 140 | 16 | 0.15 |
| 150 | 16 | 0.13 |
| 160 | 6 | 0.13 |
| 170 | 6 | 0.13 |
| 180 | 6 | 0.10 |
| 190 | 6 | 0.09 |
| 200 | 6 | 0.09 |
| 210 | 6 | 0.08 |

### (d) Distance metric variants

Test-error summary at each metric's best `k`:

| Distance | k* | Minimum test error rate |
| --- | --- | --- |
| Manhattan (Minkowski p=1) | 6 | 0.11 |
| Minkowski with `log10(p)=0.6` | 6 | 0.06 |
| Chebyshev | 16 | 0.08 |
| Mahalanobis | 1 | 0.17 |

### (e) Weighted KNN voting

Best test errors with weighted voting:

| Distance | k* | Minimum test error rate |
| --- | --- | --- |
| Euclidean | 6 | 0.10 |
| Manhattan | 26 | 0.10 |
| Chebyshev | 16 | 0.11 |

### (f) Lowest training error achieved

| Problem | Minimum training error rate |
| --- | --- |
| cii | 0.000000 |
| ciii | 0.000000 |
| diA | 0.000000 |
| diB | 0.133333 |
| diC | 0.000000 |
| dii | 0.000000 |
| e_Euclidean | 0.000000 |
| e_Manhattan | 0.000000 |
| e_Chebyshev | 0.000000 |

## Notes

- The notebook includes compatibility fixes for recent scikit-learn versions:
  `ConfusionMatrixDisplay.from_estimator(...)` is used in place of deprecated `plot_confusion_matrix`.
