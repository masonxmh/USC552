# Homework 0

Name  
USCID: 

## Files

- `notebook/INF-552 Lab0.ipynb`: Main solution notebook
- `data/Salaries.csv`: Dataset used for Pandas and Seaborn sections
- `Homework 0.pdf`: Original assignment instructions
- `requirements.txt`: Python dependencies

## Environment

Install dependencies:

```bash
pip install -r requirements.txt
```

## Progress Summary (Based on Notebook + Homework 0.pdf)

### 1) IDE Setup (Anaconda)
- Status: Not documented in notebook

### 2) Google Colab Familiarization
- Status: Not documented in notebook

### 3) Pandas (Salaries.csv)
- Status: Completed
- Implemented tasks:
- Read `Salaries.csv` into a DataFrame
- Used `playerID` as index and skipped row 2
- Filtered ATL/HOU players with salary > 1,000,000
- Computed ATL salary statistics (`describe`, quartiles/median)
- Built dictionary representation with `iterrows` (and `to_dict` comparison)
- Reconstructed DataFrame and renamed headers to alphabetical labels

### 4) NumPy
- Status: Completed
- Implemented tasks:
- Converted 2D Python list to NumPy array
- Checked `ndim`, `shape`, `size`, `dtype`, `itemsize`, `data`
- Practiced `reshape` and `flatten`
- Practiced slicing/indexing on arrays
- Exercised core operations:
  `argmin`, `argmax`, `min`, `max`, `mean`, `sum`, `std`, `dot`, `square`, `sqrt`, `abs`, `exp`, `sign`, `mod`
- Exercised array constructors/utilities:
  `arange`, `ones`, `zeros`, `eye`, `linspace`, `concatenate`

### 5) Scikit-Learn / Scipy Familiarization
- Status: Not implemented in this notebook

### 6) Git and GitHub Practice
- Status: Not documented in notebook

### 7) Matplotlib
- Status: Completed
- Implemented tasks:
- Basic line plots with title/labels/grid
- Multiple lines/styles and legends
- Text/annotation and equation-style labels
- Subplots and figure sizing
- Axis control and logarithmic scaling

### 8) Seaborn
- Status: Partially completed
- Implemented tasks:
- Loaded and visualized salary data with Seaborn
- Created axis-level visualizations (`boxplot`)
- Created structure visualization (`pairplot`)
- Not clearly present: `lmplot`, `catplot`, `relplot`, `jointplot`

## Notes

- A pandas compatibility bug in the ATL quartile step was fixed by computing quantiles on `salary` only (numeric series).
