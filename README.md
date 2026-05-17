NYC Air Quality: Clustering & Classification Pipeline
End-to-end data mining pipeline on the NYC Community Air Survey dataset — profiling, cleaning, unsupervised clustering, and supervised classification of air pollution across New York City community districts.
Team:
MahnourAslam [GitHub](https://github.com/MahnourAslam)
Fatemeh Najafi ([GitHub](https://github.com/Sascha295)

> **Note:** This project was developed as a collaborative effort. Each contributor played a vital role in the design, implementation, and debugging phases.

Overview
New York City publishes annual air quality measurements across 59 community districts, tracking pollutants like NO₂, PM2.5, and O₃. This project applies a full data mining workflow to that dataset — cleaning and standardizing ~18,800 rows, then using unsupervised learning to discover natural pollution regimes and supervised learning to classify districts into those regimes.
The goal was to answer: can we automatically identify distinct air quality profiles across NYC, and predict which profile a district belongs to?
> Pipeline
Raw CSV → Profiling → Cleaning → Feature Engineering → Clustering → Classification → Evaluation

Data Profiling — inspected distributions, missing values, and data types across all features
Missing Value Handling — dropped or imputed based on missingness rate per column
Outlier Detection — applied Isolation Forest to flag and remove anomalous readings
Filtering — restricted to summer months to control for seasonal confounding
Standardization — Z-score normalization across pollutant features
Encoding — one-hot encoding of categorical district metadata
Clustering (K-Means) — selected K=3 via the elbow method; validated with silhouette and Calinski-Harabasz scores
Classification (Random Forest) — trained on cluster labels; evaluated with cross-validation


Key Results
MetricValueDataset size~18,800 rowsPollutantsNO₂, PM2.5, O₃Clusters (K)3Silhouette Score0.34Calinski-Harabasz Score687
Identified pollution regimes:

🟢 Clean — 109 community districts
🟡 Moderate — 356 community districts
🔴 High-traffic — 420 community districts
CategoryToolsLanguagePythonData manipulationPandas, NumPyML & clusteringscikit-learnEnvironmentGoogle Colab, Jupyter Notebook
How to Run

Open Copy_of_Final_Version.ipynb in Google Colab or Jupyter
Install dependencies if running locally:

bash   pip install pandas numpy scikit-learn matplotlib seaborn

Run all cells in order — each section is labelled with its pipeline stage
Dataset
NYC Community Air Survey (NYCCAS) — publicly available from the NYC Open Data portal. Measurements cover annual pollutant concentrations by community district.
