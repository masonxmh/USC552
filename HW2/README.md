# Homework 2

DSCI 552 - Linear Regression


## Files

- `notebook/LNN.ipynb`: Main solution notebook
- `data/CCPP/`: Combined Cycle Power Plant dataset files
- `Homework2.pdf`: Assignment prompt
- `requirements.txt`: Python dependencies used in the notebook

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Run notebook from `HW2/notebook` so relative paths to `../data/...` resolve correctly.

## Assignment Mapping (Homework2.pdf + LNN.ipynb)

### 1(a) Download CCPP dataset
- Implemented in notebook (download/unzip utilities and local file loading).
- Main analysis uses `../data/CCPP/Folds5x2_pp.xlsx` (Sheet1).

### 1(b) Explore the data
- Implemented:
- Dataset loaded with `9568` rows and `5` columns (`AT`, `V`, `AP`, `RH`, `PE`).
- Pairwise scatterplots created for variables.
- Summary statistics table created (mean, median, quartiles, ranges, IQR).

### 1(c) Simple linear regression (one predictor at a time)
- Implemented for all four predictors (`AT`, `V`, `AP`, `RH`).
- All models show statistically significant association (`p < 0.05` for slope).
- R-squared values from notebook output:
- `PE ~ AT`: `0.899`
- `PE ~ V`: `0.757`
- `PE ~ AP`: `0.269`
- `PE ~ RH`: `0.152`
- Diagnostic/outlier visualization is included in plots.

### 1(d) Multiple linear regression with all predictors
- Implemented with `PE ~ AT + V + AP + RH`.
- All predictor coefficients are statistically significant in notebook output.
- Reported model fit:
- `R-squared: 0.929`

### 1(e) Compare coefficients from (c) vs (d)
- Implemented with coefficient comparison plot:
- x-axis: univariate coefficients from simple regressions
- y-axis: coefficients from multiple regression

### 1(f) Nonlinear association check
- Implemented by fitting cubic polynomial form per predictor:
- `Y = β0 + β1X + β2X^2 + β3X^3 + ε`
- Polynomial summaries and plots are included for each predictor.

### 1(g) Pairwise interaction model
- Implemented full model with all pairwise interaction terms.
- Significant and non-significant interaction terms are visible via `p`-values in OLS summary.
- Full interaction model reported `R-squared: 0.936`.

### 1(h) Model improvement with interactions/nonlinearities
- Implemented 70/30 train-test split models:
- Baseline model with original predictors
- Expanded model with pairwise interactions + quadratic terms
- Reduced model after removing non-significant terms
- Reported result dictionaries include train/test MSE values.

### 1(i) KNN regression
- Implemented for both normalized and raw features.
- Evaluated `k` in `{1, 2, ..., 100}` and plotted errors vs `1/k`.
- Best normalized KNN:
- `k = 4`, test MSE `14.348653474399166`
- Best raw-feature KNN:
- `k = 5`, test MSE `15.726819842563568`

### 1(j) Compare KNN with best linear-regression model
- Implemented summary table in notebook output:

| Model | Test error | Train error |
| --- | ---: | ---: |
| LinearRegression | 18.694346 | 17.917813 |
| normKNN | 14.348653 | 0.000000 |
| rawKNN | 15.726820 | 0.000000 |

- Based on this run, normalized KNN gives the smallest test error.

## Additional Questions

### 2) ISLR 2.4.1
- Section headings for parts (a)-(d) are present in the notebook.
- Detailed written answers are not fully populated in saved markdown cells.

### 3) ISLR 2.4.7
- Section headings for parts (a)-(d) are present.
- Written answer is present for part (d):
  best `K` expected to be small when decision boundary is highly nonlinear.

## Notes

- The Excel load step uses `openpyxl` through `pandas.read_excel`.
- Ensure `openpyxl` is installed (included in `requirements.txt`).
