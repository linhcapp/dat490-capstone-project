# \# 🏈 College Football Fraud Score: Detecting Overrated Teams with Machine Learning

# 

# \## 📘 Overview

# This project develops a data-driven framework to identify “fraud” teams in college football — teams whose rankings and public perception exceed their on-field performance.  

# 

# This research was completed as part of the \*\*DAT 490 Capstone Project\*\* at \*\*Arizona State University\*\*, Fall 2025.

# 

# ---

# 

# \## 🧠 Methodology

# 

# \### 1. \*\*Data Collection\*\*

# We combined data from multiple sources:

# \- \[College Football Data API](https://collegefootballdata.com)

# \- \[Sports-Reference.com](https://sports-reference.com/cfb)

# 

# The merged dataset spans \*\*2014–2024\*\*, covering over \*\*1000 teams\*\* and metrics for \*\*strength of schedule (SOS)\*\*, \*\*margin of victory (MOV)\*\*, \*\*Simple Rating System (SRS)\*\*, \*\*Elo ratings\*\*, and \*\*AP Poll ranks\*\*.

# 

# \### 2. \*\*Feature Engineering \& Standardization\*\*

# \- Standardized all numeric variables (z-scores) by season.

# \- Computed separate \*\*Perception\*\* and \*\*Performance\*\* composites.

# \- Defined \*\*Fraud Score = Perception – Performance\*\* (positive → overrated, negative → underrated).

# 

# \### 3. \*\*Unsupervised Learning (Clustering)\*\*

# \- Applied \*\*KMeans\*\* clustering by season to group teams into tiers:

# &nbsp; - \*\*Cluster 0:\*\* Elite Contenders  

# &nbsp; - \*\*Cluster 1:\*\* Solid Performers  

# &nbsp; - \*\*Cluster 2:\*\* Underperformers / Frauds

# \- Evaluated cluster validity using \*\*silhouette scores\*\* and \*\*inertia plots\*\*.

# \- Visualized results via \*\*PCA\*\* for dimensionality reduction.

# 

# \### 4. \*\*Fraud Labeling \& Classification\*\*

# \- Constructed empirical performance thresholds based on historical top-10 teams.

# \- Labeled teams as \*\*“Fraud”\*\* based on constructed thresholds and AP Rank.

# \- Trained a \*\*Random Forest Classifier\*\* using independent features different from features used to construct fraud labels to evaluate the effectiveness of fraud labels.

# 

# ---

# 

# \## 🧩 Repository Structure



