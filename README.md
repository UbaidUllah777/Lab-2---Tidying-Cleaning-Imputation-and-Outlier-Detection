# Lab 2 – Tidying, Cleaning, Imputation, and Outlier Detection

## Student Information

**Student:** Ubaid Ullah  
**Student ID:** 9110715  

---

## Project Overview

This project completes **Lab 2 – Tidying, Cleaning, Imputation, and Outlier Detection**. The lab focuses on practical data-preprocessing skills used before machine-learning analysis, including data tidying, reshaping, cleaning, missing-value handling, imputation, visualization, and outlier detection.

All four required sections are completed in a single Jupyter notebook, `week5Lab.ipynb`. The project is organized for reproducibility by using local data files, relative paths, a Python virtual environment, a `requirements.txt` file, and Git version control.

## Learning Objectives

The project demonstrates how to:

- inspect dataset structure, columns, data types, and data quality;
- distinguish between wide and long/tidy data;
- reshape data using `pd.melt()` / `DataFrame.melt()`;
- clean text using Pandas string operations;
- identify and quantify missing values;
- compare row/column dropping and mean, median, and mode imputation;
- use Scikit-Learn's `SimpleImputer`;
- identify possible outliers using box plots and scatter plots;
- detect outliers statistically using Z-Scores and the Interquartile Range (IQR);
- compare outlier-detection methods and evaluate the effect of treatment;
- document a reproducible notebook workflow using Markdown and Git.

---

## Project Structure

```text
project/
├── week5Lab.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── data/
    ├── pew-raw.csv
    ├── billboard.csv
    ├── auto-mpg.data
    └── diabetes.csv
```

All datasets are loaded using **relative paths** from the `data/` directory so that the notebook can run on another machine without changing local file paths.

---

## Datasets

### 1. PEW Research Dataset

File:

```text
data/pew-raw.csv
```

The PEW dataset contains religion categories and income ranges. It is used to demonstrate conversion from a wide structure to tidy/long format using `melt()`.

Key work completed:

- inspected shape, columns, and observations;
- cleaned whitespace from column names;
- identified `religion` as the identifier variable;
- reshaped six income columns into `income` and `count`;
- transformed the dataset from **10 rows × 7 columns** to **60 rows × 3 columns**;
- created and interpreted an income-category visualization.

### 2. Billboard Dataset

File:

```text
data/billboard.csv
```

The Billboard dataset contains song information and weekly ranking columns from `1st week` through `65th week`.

Key work completed:

- inspected **317 rows × 77 columns**;
- identified 12 song-level identifier columns and 65 weekly ranking columns;
- reshaped the dataset to **20,605 rows × 14 columns**;
- cleaned week labels with Pandas string operations including:
  - `.str.strip()`
  - `.str.lower()`
  - `.str.replace()`
  - `.str.extract()`
- converted week numbers and chart rankings to numeric values;
- identified **15,298 missing ranking observations**;
- removed missing ranking rows rather than inventing artificial chart positions;
- retained **5,307 valid weekly ranking observations**;
- calculated weekly chart dates using the entry date and `Timedelta`;
- verified the date calculation to avoid an off-by-one-week error;
- visualized and interpreted a song's Billboard ranking trend.

### 3. Cars / Auto MPG Dataset

File:

```text
data/auto-mpg.data
```

The Auto MPG dataset is used for data cleaning and missing-value handling.

Key work completed:

- inspected **398 rows × 9 columns**;
- verified that no metadata or irrelevant rows were present;
- found **6 missing `Horsepower` values**;
- confirmed that all expected numeric variables were stored with numeric data types;
- found no duplicate rows;
- compared:
  - dropping rows with missing values;
  - dropping columns with missing values;
  - mean imputation;
  - median imputation;
  - mode imputation for a discrete variable;
- analyzed the `Horsepower` distribution;
- observed right skew with a skewness of approximately **1.087**;
- selected median imputation because the median is more robust to skewed data;
- used `SimpleImputer(strategy="median")`;
- imputed missing `Horsepower` values with **93.5**;
- preserved all **398 observations**;
- validated that the cleaned dataset contained no missing values.

### 4. Diabetes Dataset

File:

```text
data/diabetes.csv
```

The Diabetes dataset is used to compare visual and statistical outlier-detection approaches.

Key work completed:

- inspected **768 rows × 9 columns**;
- identified eight numeric predictor features for outlier analysis;
- documented potentially invalid zero values in physiological measurements without automatically deleting them;
- created box plots for numeric features;
- created a `Glucose` vs `Insulin` scatter plot;
- applied the Z-Score method to `Insulin` using the required threshold:

```text
|z| > 3
```

- identified **18 potential Z-Score outliers**;
- applied the IQR rule to `Insulin`;
- calculated:
  - `Q1 = 0.0`
  - `Q3 = 127.25`
  - `IQR = 127.25`
  - lower bound = `-190.875`
  - upper bound = `318.125`
- identified **34 potential IQR outliers**;
- compared Z-Score and IQR detection results;
- demonstrated an IQR-based treatment on a copy of the dataset;
- preserved the original dataframe for comparison;
- compared row count, mean, median, standard deviation, and visualization before and after treatment.

---

## Software Requirements

The notebook uses the following main Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- Jupyter / IPython environment

The exact package versions used for the final submission are stored in:

```text
requirements.txt
```

Do not add `!pip install ...` commands inside the notebook. The Python environment should be created from `requirements.txt`.

---

## Environment Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd <repository-folder>
```

### 2. Create a Virtual Environment

Windows:

```powershell
python -m venv .env
```

macOS/Linux:

```bash
python3 -m venv .env
```

### 3. Activate the Virtual Environment

Windows PowerShell:

```powershell
.\.env\Scripts\Activate.ps1
```

Windows Command Prompt:

```cmd
.env\Scripts\activate
```

macOS/Linux:

```bash
source .env/bin/activate
```

### 4. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 5. Confirm Required Data Files

Before running the notebook, confirm that the following files exist:

```text
data/pew-raw.csv
data/billboard.csv
data/auto-mpg.data
data/diabetes.csv
```

## Replicability Check

To verify that the project is reproducible on systems other than the development machine, the GitHub repository was shared with two classmates, **Vid** and **Koushik**, for independent testing.

Both testers cloned the repository onto their own machines and created separate Python environments. They installed the required dependencies using:

```bash
pip install -r requirements.txt
```

---

## Author

**Ubaid Ullah**  
**Student ID:** 9110715

---

## Academic Note

This repository is prepared as coursework for **Lab 2 – Tidying, Cleaning, Imputation, and Outlier Detection**. The notebook contains the completed analysis, supporting explanations, visualizations, reflections, and reproducibility workflow required for the assignment.

---
