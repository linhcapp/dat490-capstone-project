# 🏈 College Football: Detecting Overrated (Fraud) Teams

## 📘 Overview

This project develops a **data-driven framework** to identify *“fraud”* teams in college football — teams whose rankings and public perception exceed their on-field performance.

The study was conducted as part of the **DAT 490 Capstone Project** at **Arizona State University** (Fall 2025).

---

## 🧠 Methodology

### 1\. **Data Collection**

We combined data from two major public sources:

* [College Football Data API](https://collegefootballdata.com)
* [Sports-Reference.com](https://sports-reference.com/cfb)

The merged dataset spans **2014–2024**, covering over **1000 team-seasons** with key metrics such as:

* Strength of Schedule (SOS)
* Margin of Victory (MOV)
* Simple Rating System (SRS)
* Elo Ratings
* AP Poll Rankings

### 2\. **Methods Summary**

* EDA: Explore correlations between AP ranks, win percentage, and efficiency metrics.
* Clustering (KMeans + PCA): Identify groups such as elite, contender, and overvalued teams.
* Fraud Score Construction: Combine standardized perception and performance metrics.
* Regression Models: Validate the Fraud Score and assess prediction accuracy.
