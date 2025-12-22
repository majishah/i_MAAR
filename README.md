# i-MAAR: Interpretable Multi-window and AutoML-based Adaptable Regression

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Research-Reproducible](https://img.shields.io/badge/status-research--reproducible-brightgreen.svg)]()
[![XAI: SHAP/LIME](https://img.shields.io/badge/XAI-SHAP%20%7C%20LIME-orange)]()


## 📌 Abstract
The **i-MAAR Algorithm** (Interpretable Multi-window and AutoML-based Adaptable Regression) is a novel framework designed for high-velocity streaming data environments. Unlike traditional batch-learning models, i-MAAR operates under strict real-time constraints, utilizing a **single-pass** execution model and a **dynamic multi-windowing** strategy. 

The core of this research focuses on the "Explainability-Performance" trade-off. By integrating an AutoML backbone for autonomous model selection and an interpretability layer (SHAP/LIME), i-MAAR ensures that every prediction is not only accurate but also human-verifiable in non-stationary environments.

---


```markdown

## 📌 Overview
This repository contains the official implementation of the **i-MAAR Algorithm** (Interpretable Multi-window and AutoML-based Adaptable Regression). 

In modern streaming environments, data arrives in a continuous flow, often exhibiting stochastic drift. Traditional regression models struggle to balance real-time adaptation with human-understandable logic. **i-MAAR** addresses this by combining a dynamic multi-windowing strategy with an AutoML-driven regression backbone, ensuring high predictive performance without sacrificing explainability.

### Core Research Constraints:
*   **Single Pass Execution:** The algorithm processes data in a single pass, making it suitable for high-velocity streaming.
*   **Multi-Window Processing:** Instead of looking at the entire historical horizon, i-MAAR utilizes sliding windows to maintain temporal relevance.
*   **Adaptability:** The model automatically re-tunes or switches its regression architecture based on performance degradation detected in the stream.
*   **Explainability (XAI):** Integrated interpretability layers (SHAP/LIME) provide local and global explanations for every decision made by the AutoML engine.

---

## 🚀 Key Technical Contributions

1.  **Dynamic Multi-Window Strategy:** Implements a sliding window protocol that isolates recent trends from historical noise, allowing the model to focus on relevant data segments.
2.  **AutoML-Driven Adaptability:** Leverages an automated pipeline to select the optimal regression model (e.g., LightGBM, CatBoost, or Ridge) for the current data window.
3.  **Granular Interpretability:** Unlike "black-box" stream learners, i-MAAR generates feature importance and contribution plots for every window shift, ensuring the "Why" behind a prediction is always visible.
4.  **Ablation Validated:** Comprehensive study comparing i-MAAR against static models and non-interpretable variants to prove the value of each component.

---

## 📂 Repository Structure

```text
i-MAAR_Research/
├── data/                            # Data Engineering
│   ├── raw/                         # Raw streaming sensor/log data
│   ├── processed/                   # Pre-processed 30-day windowed data (.csv)
│   └── data_loader.py               # Stream simulation utilities
│
├── src/                             # Core Algorithm Logic
│   ├── imaar_engine.py              # Main i-MAAR Class (Windowing + AutoML)
│   ├── model_pool.py                # Automated model selection logic
│   └── config.py                    # Hyperparameters and window sizes
│
├── interpretability/                # XAI Layer
│   ├── explainer.py                 # SHAP/LIME integration
│   └── visualizer.py                # Plotting feature contributions over time
│
├── experiments/                     # Research Validation
│   ├── ablation_study.py            # Component-wise performance tests
│   ├── drift_analysis.py            # Testing adaptability against concept drift
│   └── benchmark_comparison.py      # i-MAAR vs. Standard Regressors
│
├── results/                         # Output generation
│   ├── plots/                       # Performance and XAI visualizations
│   └── metrics/                     # CSVs of R2, RMSE, and Latency stats
│
├── requirements.txt                 # Reproducibility dependencies
└── main.py                          # Execution entry point
```

---

## 🛠 Installation & Setup

### Prerequisites
- Windows 10/11 or Linux
- Python 3.10+ (Python 3.10.x is recommended for PyCaret stability)

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/i-MAAR-Algorithm.git
cd i-MAAR-Algorithm
```

### 2. Environment Setup
Create a clean virtual environment to avoid dependency conflicts.
```bash
python -m venv venv
# Activate on Windows:
venv\Scripts\activate
# Activate on Linux/Mac:
source venv/bin/activate
```

### 3. Install Dependencies
To prevent common installation errors with Pandas/PyCaret on Windows, use the following sequence:
```bash
python -m pip install --upgrade pip setuptools wheel
pip install --only-binary :all: numpy pandas
pip install pycaret shap matplotlib seaborn
```

---

## 📊 Experimental Results & Ablation Study

### 1. Comparative Streaming Performance and Efficiency

To rigorously evaluate the model's capability under high-velocity data streams, we compared i-MAAR against five state-of-the-art streaming algorithms across three consecutive sliding windows. As detailed in the table below, the evaluation considers both predictive accuracy (MAE, RMSE, MAPE) and computational efficiency (Time).

While distance-based methods like KNN achieve low error margins, they suffer from prohibitive computational costs (averaging >330ms per update). In contrast, i-MAAR demonstrates superior real-time adaptability, processing updates in single-digit milliseconds (Avg<9.8ms)—an improvement of orders of magnitude over ensemble methods like ARF (up to 1987 ms) and LBR. Consequently, i-MAAR secures the Rank 1 position overall by delivering competitive accuracy without compromising the low-latency requirements of real-time systems.
Model	W1 MAE	W1 RMSE	W1 MAPE	W1 Time	W2 MAE	W2 RMSE	W2 MAPE	W2 Time	W3 MAE	W3 RMSE	W3 MAPE	W3 Time	Rank
i-MAAR	3437.6	4213.9	12.2	9.8	3172.0	4273.4	11.4	9.3	3750.4	4895.0	13.5	6.2	1
HTR	4591.1	6334.3	17.0	75.8	3849.7	5665.6	14.1	72.6	3466.7	5136.6	12.1	92.4	4
ARF	3080.4	5235.1	11.0	130.0	2367.8	4284.6	8.3	636.4	2176.4	3856.0	7.5	1987.8	3
OBR	19533.7	23377.4	70.2	92.7	19637.1	23474.9	70.2	69.0	19965.0	23762.8	70.3	68.4	6
LBR	4841.6	6402.2	18.0	161.1	4039.2	5764.3	14.5	211.9	3420.7	5199.4	11.4	174.2	5
KNN	1283.9	4309.3	5.3	339.4	1522.7	4059.0	5.0	348.5	1425.5	3832.6	4.6	331.6	2

Table 1: Performance comparison over the first 3 streaming windows (W1, W2, W3) using MAE, RMSE, MAPE (%) and Time (ms). Bold indicates the best value per column. The overall best average rank is also bolded. HTR – Hoeffding Tree Regressor, ARF – Adaptive Random Forest Regressor, OBR – Online Bayesian Regressor, LBR – Leveraging Bagging Regressor.

The results further validate that i-MAAR maintains robust error rates (MAPE: 11.4–13.5%, RMSE:<4900) while acting as the most computationally efficient solution among all compared baselines.

### 2. Ablation Study Summary
We evaluated the impact of removing key modules to justify our architecture:
*   **w/o Multi-window:** Performance drops by ~15% during seasonal shifts due to historical noise.
*   **w/o AutoML:** Reduced accuracy (~8% lower) in high-dimensional feature spaces where fixed models fail to generalize.
*   **w/o Adaptability:** Model fails to recover after sudden concept drifts in the stream.

---

## 🔍 Interpretability in Action
One of the core strengths of i-MAAR is the real-time generation of explainability plots. During the streaming process, the model outputs:
*   **Global Feature Importance:** Identifies which variables are driving the trend in the current window.
*   **Local SHAP Values:** Provides a precise explanation for individual outlier predictions.

*(Tip: Place a screenshot of your SHAP/LIME plots in `results/plots/` and link them here!)*

---

## 📖 Usage

### Running the Full Pipeline
To process the 30-day pre-processed stream and generate the i-MAAR performance report:
```bash
python main.py --input data/processed/preprocessed_30_days.csv --windows 1440 --xai True
```

### Reproducing Experiments
To replicate the benchmarks and ablation study presented in the manuscript:
```bash
python experiments/ablation_study.py
python experiments/drift_analysis.py
```

---


🎓 Contact
For inquiries regarding the architecture or experimental data, please refer to the corresponding author details in the associated manuscript.

This repository is part of ongoing research into Explainable AI (XAI) for Streaming Data.
