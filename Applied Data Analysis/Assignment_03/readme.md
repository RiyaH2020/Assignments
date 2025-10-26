# Network Flow Classification and Attack Detection

 

---

## Overview
Multi-class network flow classification for **attack detection**. Distinguishes benign vs malicious flows and classifies attack types using ML. Includes **preprocessing, feature analysis, class imbalance handling, and model evaluation**.

---

## Dataset
- **Size:** 1.6M+ flows  
- **Features:** Source/dest IP & port, protocol, bytes/packets, flow duration, TCP flags  
- **Labels:** Benign (0) / Malicious (1), plus attack type (Exploits, DoS, Recon, Fuzzers, etc.)  
- **Preprocessing:** Deduplication, aggregation, SMOTE for imbalance

---

## Modeling
- **Binary Classification:** Random Forest (Accuracy ~99%)  
- **Multi-Class Classification:** Random Forest, XGBoost, LightGBM  
- SMOTE improves minority detection; duplicates reduce performance  
- Tree-based models outperform linear models for attack detection

---

## Tools & Libraries
Python | Pandas | NumPy | Scikit-learn | XGBoost | LightGBM | SMOTE

---



