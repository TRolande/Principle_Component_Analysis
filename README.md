# Principle_Component_Analysis
# Mathematics for Machine Learning — Formative 2
## Principal Component Analysis (PCA)
### Cohort 3 | Team 49

---

## 👥 Team Members

| Name | Role | Email |
|------|------|-------|
| Robert Cyubahiro | Member | r.cyubahiro@alustudent.com |
| Rolande Tumugane | Member | r.tumugane@alustudent.com |

---

##  Overview

This project implements **Principal Component Analysis (PCA) from scratch** using NumPy only on an African Life Expectancy dataset. The goal is to reduce a 19-feature matrix to a lower-dimensional space while retaining as much variance as possible, and to interpret what is gained and lost in that reduction.

---

## Dataset

- **Source:** African Life Expectancy records across multiple countries and years
- **Shape:** 864 rows × 22 columns (19 numeric features used)
- **Non-numeric columns:** Country, Year, Status (columns 0–2) — dropped before PCA
- **Missing values:** 888 NaN entries in the raw numeric matrix, imputed with column means
- **Features used (19):** Life Expectancy, Adult Mortality, Infant Deaths, Alcohol, Percentage Expenditure, Hepatitis B, Measles, BMI, Under-Five Deaths, Polio, Total Expenditure, Diphtheria, HIV/AIDS, GDP, Population, Thinness 1-19 Years, Thinness 5-9 Years, Income Composition of Resources, Schooling

---

## 📁 Repository Structure

```
Principle_Component_Analysis/
│
├── PCA_Formative_2_Team49.ipynb     # Main notebook (all outputs visible)
├── Africa_Life_Expectancy_Data.csv  # Dataset
├── task_sheet.pdf                   # Task sheet
└── README.md                        # This file
```

---

##  Implementation Steps

| Step | Description |
|------|-------------|
| 1 | Load CSV, isolate 19 numeric columns, report missing values |
| 2 | Impute NaNs with column means (NumPy `nanmean`) |
| 3 | Standardize: `z = (x − μ) / σ` (population std, ddof=0) |
| 4 | Compute covariance matrix: `Cᵀ · C / (n − 1)` |
| 5 | Eigendecomposition via `np.linalg.eigh` |
| 6 | Sort eigenvalues descending; compute explained variance ratios |
| 7 | Select components dynamically at 90% cumulative variance threshold |
| 8 | Project standardized data onto top principal eigenvectors |
| 9 | Visualize before PCA (Life Expectancy vs GDP) and after PCA (PC1 vs PC2), coloured by Status |

---

## Results

| PC | Variance Explained | Cumulative |
|----|-------------------|------------|
| 1  | TBD % | TBD % |
| 2  | TBD % | TBD % |
| 3  | TBD % | TBD % |
| 4  | TBD % | TBD % |
| 5  | TBD % | TBD % |

>  Fill in the variance table after running the notebook.

---

## 🔍 Key Findings

**Why N components?**
The selected number of PCs is the smallest count whose cumulative explained variance reaches the **90% threshold**. The trade-off is compactness vs. completeness: we accept losing ~10% of variance (mainly minor country-specific variation) in exchange for a simpler, lower-dimensional representation that is faster to compute on and easier to visualise.

**What is lost?**
PC1 likely acts as a **health development/wealth** axis (combining Life Expectancy, GDP, Schooling, and mortality indicators). The top PCs preserve large-scale cross-country structure well. What is discarded are finer distinctions: a country with an atypical HIV/AIDS burden or unusual thinness patterns relative to its income level may appear identical to neighbours in the reduced space — nuances that matter for health policy analysis.

---

##  Libraries Used

| Library | Purpose |
|---------|---------|
| `numpy` | All numerical computation (standardization, covariance, eigendecomposition, projection) |
| `matplotlib` | Visualizations only |

> No `sklearn` or other ML libraries were used anywhere in this project.

---

##  How to Run

1. Open `PCA_Formative_2_Team49.ipynb` in Google Colab
2. Upload `Africa_Life_Expectancy_Data.csv` to `/content/` (or mount Drive)
3. Run all cells top to bottom — all outputs are pre-saved in the notebook

-
