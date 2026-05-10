# Fuzzy Expert System for Emergency Triage Classification

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Library-Skfuzzy](https://img.shields.io/badge/Library-scikit--fuzzy-orange.svg)](https://pythonhosted.org/scikit-fuzzy/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains a clinical decision support pipeline for the automated classification of patient acuity using the **Emergency Severity Index (ESI 1–5)**. The system implements a **Mamdani Fuzzy Inference System (FIS)** designed to provide interpretable triage priority in high-stakes environments.This project was developed as part of the Master’s program in Biomedical Engineering at **Universitas Gadjah Mada (UGM)**.

---

## Project Overview
The system replicates clinical reasoning by mapping physiological variables to urgency levels through expert-defined IF-THEN rules. Unlike black-box models, this system offers full transparency, allowing clinicians to audit the logic behind every triage assignment.

## Technical Specifications
* **Methodology**: Mamdani-type Fuzzy Inference System (FIS).
* **Dataset**: [Triagegeist](https://kaggle.com/competitions/triagegeist) (80,000 synthetic ED encounters).
* **Input Variables**: 7 physiological features (Pain Score, NEWS2, SpO2, Systolic BP, GCS, Respiratory Rate, and Temperature).
* **Rule Base**: 46 IF-THEN rules grounded in established clinical guidelines: NEWS2 (RCP 2017), WHO hypoxia definitions, Surviving Sepsis Campaign 2021, and GCS (Teasdale-Jennett 1974).
* **Data Handling**: ESI-level stratified median imputation to address Missing Not At Random (MNAR) patterns identified during exploratory data analysis.

---

## Key Results
* **Ordinal Agreement**: Quadratic Weighted Kappa (**QWK**) of **0.819**, indicating "almost perfect" agreement with clinical labels.
* **Safety Profile**: 99.9% of all misclassifications occur between adjacent ESI levels.
* **Zero-Tolerance**: No ESI 1 (immediate life threat) patients were misclassified as low-acuity (ESI 4–5).
* **Key Finding**: Handling MNAR missingness via stratified imputation yielded the largest single performance boost (+0.017 F1).

---

## Installation & Usage
The implementation requires the `scikit-fuzzy` library. To replicate the analysis:

```bash
pip install numpy pandas scikit-fuzzy scikit-learn matplotlib seaborn
