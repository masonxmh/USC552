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
