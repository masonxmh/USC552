# homework-4-masonxmh

## Windows setup procedure (HW4)

Python requirement: use Python 3.10 for this homework.

### 1. Create and activate conda environment

```powershell
conda create -n py310 python=3.10 -y
conda activate py310
```

### 2. Configure Java for WEKA (current shell)

Use JDK 9.0.4 (available on this machine at `C:\Program Files\Java\jdk-9.0.4`):

```powershell
$env:JAVA_HOME="C:\Program Files\Java\jdk-9.0.4"
$env:Path="$env:JAVA_HOME\bin;$env:Path"
```

Optional: persist `JAVA_HOME` for future shells:

```powershell
[Environment]::SetEnvironmentVariable("JAVA_HOME","C:\Program Files\Java\jdk-9.0.4","User")
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

## Notes

- `python-weka-wrapper3` works in this setup via `jpype1`.
- Direct `javabridge` installation failed on this Windows machine due to missing MSVC build tools.
- If a notebook has `import javabridge`, remove that import and keep `import weka.core.jvm as jvm`.
