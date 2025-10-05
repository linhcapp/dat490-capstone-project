# 🏈 College Football Fraud Score: Detecting Overrated Teams with Machine Learning

## 📘 Overview
This project develops a **data-driven framework** to identify *“fraud”* teams in college football — teams whose rankings and public perception exceed their on-field performance.  

The study was conducted as part of the **DAT 490 Capstone Project** at **Arizona State University** (Fall 2025).

---

## 🧠 Methodology

### 1. **Data Collection**
We combined data from two major public sources:
- [College Football Data API](https://collegefootballdata.com)  
- [Sports-Reference.com](https://sports-reference.com/cfb)

The merged dataset spans **2014–2024**, covering over **1000 team-seasons** with key metrics such as:
- Strength of Schedule (SOS)  
- Margin of Victory (MOV)  
- Simple Rating System (SRS)  
- Elo Ratings  
- AP Poll Rankings  

### 2. **Feature Engineering & Standardization**
- Standardized all numeric variables using **z-scores** within each season.  
- Created composite indices for:
  - **Perception** → based on AP rankings and excitement metrics  
  - **Performance** → based on efficiency and dominance metrics  
- Defined the **Fraud Score** as:  

  \[
  \text{Fraud Score} = \text{Perception} - \text{Performance}
  \]

  Positive values indicate *overrated (fraudulent)* teams; negative values indicate *underrated* teams.

### 3. **Unsupervised Learning (Clustering)**
- Applied **KMeans Clustering** (season by season) to group teams into performance tiers:
  - **Cluster 0:** Elite Contenders  
  - **Cluster 1:** Solid Performers  
  - **Cluster 2:** Underperformers / Frauds  
- Evaluated clustering quality using **Silhouette Scores** and **Inertia (Elbow) plots**.  
- Used **Principal Component Analysis (PCA)** for 2D visualization of clusters.

### 4. **Fraud Labeling & Classification**
- Constructed **empirical performance thresholds** based on the average of historical top-10 teams in each season.  
- Assigned teams as **“Elite”**, **“Borderline”**, or **“Fraud”** based on threshold comparisons and AP Rank deviation.  
- Trained a **Random Forest Classifier** using independent performance metrics (WinPct, SRS, MOV, SOS, Elo) to evaluate whether the fraud labeling aligns with actual outcomes.

---

## 🧩 Repository Structure

```
📁 CollegeFootball-FraudScore/
│
├── data/
│   ├── raw/                      # Original CSVs from Sports Reference & CFBD API
│   ├── processed/                # Cleaned & merged datasets (final_merged.csv)
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_clustering_pca.ipynb
│   ├── 04_random_forest.ipynb
│
├── src/
│   ├── utils.py                  # Helper functions for cleaning & feature creation
│   ├── clustering.py             # KMeans + PCA visualization
│   ├── modeling.py               # Random Forest classifier and metrics
│
├── results/
│   ├── figures/                  # Plots: threshold charts, PCA, elbow curves
│   ├── tables/                   # Cluster summaries and fraud score tables
│
├── README.md                     # Project documentation
├── requirements.txt              # Dependencies list
└── LICENSE
```

---

## 📊 Example Outputs

- **Elbow & Silhouette Plots:** Helped determine the optimal number of clusters (k ≈ 3).  
- **PCA Visualization:** Showed clear separation between elite contenders, average teams, and underperformers.  
- **Random Forest Feature Importance:** Highlighted WinPct, MOV, and SRS as the strongest predictors of fraud labels.

---

## 🧾 Key Findings

- Fraud Scores successfully distinguished between **overvalued teams (e.g., Texas A&M 2019, Clemson 2022)** and **legitimate contenders (e.g., Ohio State 2014, LSU 2019)**.  
- Statistical validation showed strong alignment between **model predictions** and **expert consensus**.  
- The model generalizes across seasons, providing a foundation for automated ranking fairness audits.

---

## 🧩 Future Work
- Incorporate advanced efficiency metrics (e.g., **SP+**, **EPA/play**, **Massey Ratings**) for deeper contextual modeling.  
- Extend framework to real-time fraud detection during the ongoing season.  
- Compare machine-driven “Fraud Scores” to human poll updates weekly to detect media overreactions.

---

## 👥 Contributors
- **Hai Ta Tuan** – Data Engineering, Modeling, Report Writing  
- **Linh Luong**, **Khanh Nguyen**, **Nam Tran** – EDA, Feature Engineering, Visualization

---

## 📚 References
- [College Football Data API](https://collegefootballdata.com/about)  
- [Sports Reference](https://www.sports-reference.com/cfb/)  
- Coleman et al. (2010), *Journal of Sports Economics*, “Voter Bias in the Associated Press College Football Poll”  
- Stone & Rod (2016), *Marquette Sports Law Review*, “Bias in the College Football Playoff Selection Process”
