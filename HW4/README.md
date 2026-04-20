# homework-4-masonxmh

## Windows setup procedure (HW4)

Python requirement: use Python 3.10 for this homework.

### 1. Create and activate conda environment

```powershell
conda create -n py310 python=3.10 -y
conda activate py310
```

### 2. Configure Java for WEKA notebooks (current shell)

Use JDK 17:

```powershell
$env:JAVA_HOME="C:\Program Files\Java\jdk-17"
$env:Path="$env:JAVA_HOME\bin;$env:Path"
```

Optional: persist `JAVA_HOME` for future shells:

```powershell
[Environment]::SetEnvironmentVariable("JAVA_HOME","C:\Program Files\Java\jdk-17","User")
```

### 3. Install Python dependencies

Install from `requirements.txt`:

```powershell
python -m pip install -r requirements.txt
```

### 4. Verify key imports

```powershell
python -c "import numpy,pandas,sklearn,scipy,matplotlib,seaborn,xgboost,impyute,weka; print('imports OK')"
```

### 5. Run notebooks

```powershell
jupyter notebook
```

### 6. Java environment by notebook

- `HW4_part1.ipynb`: no Java required.
- `HW4_part2.ipynb`: no Java required.
- `HW4_part3.ipynb`: requires WEKA/JVM. Use `JAVA_HOME=C:\Program Files\Java\jdk-17` before running.
- `HW4_part4.ipynb`: requires WEKA/JVM. Use `JAVA_HOME=C:\Program Files\Java\jdk-17` before running.

## Notes

- `python-weka-wrapper3` works in this setup via `jpype1`.
- Direct `javabridge` installation failed on this Windows machine due to missing MSVC build tools.
- If a notebook has `import javabridge`, remove that import and keep `import weka.core.jvm as jvm`.

## Assignment Scope (from `Homework4.pdf`)

1. LASSO and Boosting for Regression
- Dataset: Communities and Crime.
- Tasks: imputation, correlation/CV analysis, feature visualization, linear/ridge/LASSO/PCR, XGBoost.

2. Tree-Based Methods
- Dataset: APS Failure at Scania Trucks.
- Tasks: imputation + analysis, random forest (with and without imbalance compensation), model trees (Logistic Model Trees in WEKA), SMOTE workflow.

3. ISLR 6.6.3
4. ISLR 6.6.5
5. ISLR 8.4.5
6. ISLR 9.7.3

Extra practice (optional in PDF): ISLR 5.4.2, 6.8.4, 8.4.4, 9.7.2.

## Notebook-to-Question Mapping

- `notebook/HW4_part1.ipynb`: PDF Section 1(a) to 1(j).
- `notebook/HW4_part2.ipynb`: PDF Section 2(a) to 2(d), plus prep for 2(e)/(2f).
- `notebook/HW4_part3.ipynb`: PDF Section 2(e) and 2(f) (WEKA + SMOTE).
- `notebook/HW4_part4.ipynb`: PDF Sections 3, 4, 5, 6 (ISLR questions).

## Data Files Used

- `data/communities.data`
- `data/communities.names`
- `data/aps_failure_training_set.csv`
- `data/aps_failure_test_set.csv`
- `data/aps_failure_description.txt`
- `data/weka_train.csv`
- `data/weka_test.csv`

## Recommended Run Order

1. `HW4_part1.ipynb`
2. `HW4_part2.ipynb`
3. `HW4_part3.ipynb`
4. `HW4_part4.ipynb`

For Section 2(f), apply SMOTE to the training workflow correctly during cross-validation (as noted in the PDF).
