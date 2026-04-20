# Homework 3

DSCI 552 - Time Series Classification

USCID: 

## Files

- `notebook/hw3.ipynb`: Main solution notebook
- `Homework3.pdf`: Assignment prompt
- `data/AReM/`: AReM dataset files
- `requirements.txt`: Libraries used by the notebook

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the notebook from `HW3/notebook` so relative paths to `../data/...` resolve correctly.

## Assignment Mapping (Homework3.pdf + hw3.ipynb)

### 1(a) Dataset
- AReM dataset loading and file handling are implemented.

### 1(b) Train/Test Split
- Split rule from the PDF is implemented in notebook code:
  `bending1/bending2` dataset 1-2 and other folders dataset 1-3 are held for test, remaining files for train.

### 1(c) Feature Extraction
- Time-domain features are extracted for all 6 time series in each instance:
  min, max, mean, median, std, first quartile, third quartile.
- Raw, normalized, and standardized variants are prepared.
- Bootstrap confidence interval analysis is implemented for feature standard deviations.
- Three key features are selected and used in later visualizations/models.

### 1(d) Binary Logistic Regression (bending vs other)
- Scatter plots for selected features are included.
- Time-series segmentation experiments for `l = 1..20` are implemented.
- Recursive feature elimination with stratified CV is implemented.
- Example best row from the saved output table:
  `l=1, p=6, mean_cv_score=1.0, train_accuracy=1.0, test_accuracy=1.0`.
- Confusion matrices, ROC, AUC, and classification reports are generated for train/test.
- Saved binary results show perfect scores in the displayed run:
  test accuracy `1.00`, AUC `1.0`.
- Case-control sampling experiment is also implemented and evaluated.

### 1(e) L1-Penalized Logistic Regression
- Implemented across `l = 1..20` with CV over regularization.
- Comparison between p-value/RFE style selection and L1-penalized models is included in summary tables.
- Saved output best row (raw-feature L1 section):
  `l=1, c=0.359381, mean_cv_score=1.0, train_accuracy=1.0, test_accuracy=1.0`.

### 1(f) Multi-class Classification
- Multinomial L1 logistic regression is implemented for all activities.
- Gaussian Naive Bayes and Multinomial Naive Bayes are also implemented and compared.
- Multi-class confusion matrices, ROC plots, and classification reports are produced.
- Reported test accuracies from saved outputs include:
- L1 multinomial (raw): `0.894737`
- GaussianNB: `0.947368`
- MultinomialNB: `0.842105`
- Final comparison table in notebook indicates GaussianNB as the best test performer in that run.

### 2) ISLR 3.7.4
- Section present in notebook.

### 3) ISLR 4.8.3
- Section present in notebook.

### 4) ISLR 4.8.7
- Section present in notebook.

## Notes

- The notebook has compatibility updates for newer package versions (scikit-learn/pandas) so it can run in modern environments.
