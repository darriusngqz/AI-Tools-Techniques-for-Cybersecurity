# AI-Tools-Techniques-for-Cybersecurity

## Overview
This repository documents an end-to-end Data Science project focused on detecting cybersecurity threats in Internet of Things (IoT) environments. Using the CIC-BCCC-NRC TabularIoTAttack-2024 dataset, this project applies the full data science lifecycle—from data mining to predictive modeling—to distinguish between benign IoT traffic and various cyberattack vectors.

The core objective was to move beyond static, signature-based detection and leverage machine learning to identify behavioral patterns in network traffic, such as packet flow statistics and timing irregularities.

## Problem Statement
"How might we leverage IoT network traffic data to accurately distinguish between benign traffic and multiple IoT-specific cyberattack categories in a data-driven manner?"

Traditional Security Information and Event Management (SIEM) systems often struggle with the evolving nature of IoT attacks. This project explores a SMART (Specific, Measurable, Actionable, Relevant, Timebound) approach to building a robust detection system using supervised machine learning.

## Dataset: CIC-BCCC-NRC TabularIoTAttack-2024
The dataset contains 722,144 records with 85 features, simulating a real-world IoT environment.

### Traffic Categories Analyzed:
* Benign: Normal IoT device communication.
* DoS (Denial of Service): DNS Flood, ICMP Flood, SYN Flood, UDP Flood.
* Reconnaissance: Host Discovery, OS Scan, Ping Sweep, Port Scan, Vulnerability Scan.
* Brute Force: Dictionary-based credential attacks.
* MITM (Man-in-the-Middle): ARP Spoofing.

## Data Science Lifecycle

### 1. Data Mining & Cleaning
* Consolidation: Merged 12 separate CSV files into a unified dataset for analysis.
* Validation: Performed schema checks and data type validation across all sources.
* Sanitization: Removed duplicate records and verified data integrity to ensure a zero-missing-value baseline.

### 2. Exploratory Data Analysis (EDA)
* Traffic Profiling: Identified that flooding traffic exhibits high median flow durations, while reconnaissance traffic shows higher Inter-Arrival Times (IAT).
* Statistical Analysis: Conducted multicollinearity checks to remove redundant features and used boxplots to identify extreme outliers.

### 3. Feature Engineering: IoC Scoring
A unique contribution of this project was the development of Indicator of Compromise (IoC) scores.
* We transformed raw network metrics into behavioral scores (e.g., unusual packet rates, irregular timing).
* These scores allow the model to focus on the intent of the traffic rather than just raw numbers, enhancing interpretability.

### 4. Predictive Modeling & Evaluation
We developed several iterations of the model to optimize performance:
* Model 1 (Binary): Classified traffic as "Benign" vs "Attack" using Logistic Regression and Random Forest. Achieved ~0.89 accuracy using engineered IoC scores.
* Model 2.1 (Enhanced Multiclass): Implemented a multi-class classifier using raw flow features and Robust-Scaler. This version successfully segregated different attack types with an accuracy of 0.82 and a macro average precision of 0.83.

## Key Learning Outcomes
* Behavioral Analysis: Timing features (IAT) and packet-level statistics are superior to static protocol flags for identifying modern IoT threats.
* Feature Scaling: Learned the importance of using RobustScaler when dealing with network data, which is inherently prone to extreme outliers during DDoS events.
* Lifecycle Management: Gained hands-on experience in managing the end-to-end pipeline from raw data mining to a deployable predictive model.

## Tools Used
* Language: Python
* Libraries: Pandas, NumPy, Scikit-Learn (Logistic Regression, Random Forest, Robust-Scaler), Matplotlib, Seaborn
* Environment: Jupyter Notebook

## Contributors
* Jay Tan Chee Leong
* Joel Tan
* Ng QianZheng Darrius

## Disclaimer
This project was completed for academic purposes as part of the AI Tools & Techniques for Cybersecurity module at Ngee Ann Polytechnic. The findings and models are intended for educational and portfolio demonstration only.
