# NYC Air Quality: Clustering & Classification Pipeline

End-to-end data mining pipeline on the NYC Community Air Survey dataset — profiling, cleaning, unsupervised clustering, and supervised classification of air pollution across New York City community districts.

## 🤝 Contributing Partners

We are a team of Computer Science students dedicated to building efficient, scalable solutions.

MahnourAslam [GitHub](https://github.com/MahnourAslam)
Fatemeh Najafi ([GitHub](https://github.com/Fatemeh-Najafi1))

> **Note:** This project was developed as a collaborative effort. Each contributor played a vital role in the design, implementation, and debugging phases.

---

## Overview

New York City publishes annual air quality measurements across 59 community districts, tracking pollutants like NO₂, PM2.5, and O₃. This project applies a full data mining workflow to that dataset — cleaning and standardizing ~18,800 rows, then using unsupervised learning to discover natural pollution regimes and supervised learning to classify districts into those regimes.

The goal was to answer: **can we automatically identify distinct air quality profiles across NYC, and predict which profile a district belongs to?**

---


## Pipeline 
Raw CSV → Profiling → Cleaning → Feature Engineering → Clustering → Classification → Evaluation

1. **Data Profiling** — inspected distributions, missing values, and data types across all features
2. **Missing Value Handling** — dropped or imputed based on missingness rate per column
3. **Outlier Detection** — applied Isolation Forest to flag and remove anomalous readings
4. **Filtering** — restricted to summer months to control for seasonal confounding
5. **Standardization** — Z-score normalization across pollutant features
6. **Encoding** — one-hot encoding of categorical district metadata
7. **Clustering (K-Means)** — selected K=3 via the elbow method; validated with silhouette and Calinski-Harabasz scores
8. **Classification (Random Forest)** — trained on cluster labels; evaluated with cross-validation

---

## Key Results

| Metric | Value |
|---|---|
| Dataset size | ~18,800 rows |
| Pollutants | NO₂, PM2.5, O₃ |
| Clusters (K) | 3 |
| Silhouette Score | 0.34 |
| Calinski-Harabasz Score | 687 |

**Identified pollution regimes:**
- 🟢 **Clean** — 109 community districts
- 🟡 **Moderate** — 356 community districts
- 🔴 **High-traffic** — 420 community districts

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Data manipulation | Pandas, NumPy |
| ML & clustering | scikit-learn |
| Environment | Google Colab, Jupyter Notebook |

---

## How to Run

1. Open `Copy_of_Final_Version.ipynb` in [Google Colab](https://colab.research.google.com/) or Jupyter
2. Install dependencies if running locally:
```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
```
3. Run all cells in order — each section is labelled with its pipeline stage

---
## Requirements

- Python 3.8+
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

Install all dependencies with:
pip install -r requirements.txt

---

## Dataset

**NYC Community Air Survey (NYCCAS)** — publicly available from the [NYC Open Data portal](https://data.cityofnewyork.us/Environment/Air-Quality/c3uy-2p5r). Measurements cover annual pollutant concentrations by community district.
