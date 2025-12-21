# i-MAAR: Interpretable Multi-window and AutoML-based Adaptable Regression

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Research-Reproducible](https://img.shields.io/badge/status-research--reproducible-brightgreen.svg)]()

## 📌 Abstract
The **i-MAAR Algorithm** (Interpretable Multi-window and AutoML-based Adaptable Regression) is a novel framework designed for high-velocity streaming data environments. Unlike traditional batch-learning models, i-MAAR operates under strict real-time constraints, utilizing a **single-pass** execution model and a **dynamic multi-windowing** strategy. 

The core of this research focuses on the "Explainability-Performance" trade-off. By integrating an AutoML backbone for autonomous model selection and an interpretability layer (SHAP/LIME), i-MAAR ensures that every prediction is not only accurate but also human-verifiable in non-stationary environments.

---

## 🚀 Key Research Contributions

*   **Single-Pass Streaming Logic:** Optimized for environments where data cannot be stored in its entirety. The algorithm processes each data point exactly once.
*   **Multi-Window Adaptation:** Implements sliding windows (default 1,440 rows/day) to capture temporal dependencies without the computational overhead of "whole-data" processing.
*   **AutoML-based Adaptability:** The system monitors performance metrics in real-time. If performance degrades due to concept drift, it autonomously re-triggers the AutoML engine to adapt to the new data distribution.
*   **Core Interpretability & Explainability:** Provides local and global explanations for regression outputs, ensuring stakeholders understand the *why* behind the *what*.
*   **Verified Ablation Study:** Includes a rigorous evaluation of individual components (Windowing vs. No-Windowing, AutoML vs. Static) to prove the algorithm's robustness.

---

## 📂 Repository Structure

i-MAAR_Research/
├── data/                            # Dataset Management
│   ├── processed_30_days.csv        # Pre-processed 30-day training stream
│   └── raw_data/                    # Original raw sensor streams
│
├── src/                             # Core Logic
│   ├── imaar_engine.py              # Main algorithm and Windowing logic
│   ├── automl_handler.py            # PyCaret-based model selection
│   └── config.py                    # Hyperparameters (window size, thresholds)
│
├── explainability/                  # XAI Module
│   ├── shap_explainer.py            # Local feature importance
│   └── visualizer.py                # Real-time explainability dashboards
│
├── experiments/                     # Research Validation
│   ├── ablation_study.py            # Component-wise impact analysis
│   └── benchmark_tests.py           # Comparison vs. Static Regressors
│
├── results/                         # Evaluation Outputs
│   ├── plots/                       # Performance & Explainability graphs
│   └── metrics/                     # CSV logs of R², RMSE, and Latency
│
├── requirements.txt                 # Project dependencies
└── main.py                          # Execution entry point

## 🛠 Installation & Setup

1. Clone the Repository

git clone https://github.com/your-username/i-MAAR-Algorithm.git
cd i-MAAR-Algorithm

2. Create a Virtual Environment (Recommended)

Given the complexity of PyCaret dependencies on Windows, a clean environment is highly recommended.

python -m venv venv
# Activate on Windows:
venv\Scripts\activate
# Activate on Linux/Mac:
source venv/bin/activate

3. Install Dependencies

To avoid "subprocess-exited-with-error" issues on Windows, install core binaries first:
python -m pip install --upgrade pip
pip install --only-binary :all: numpy pandas
pip install pycaret shap matplotlib seaborn

📊 Experimental Results
1. Model Performance vs. Adaptability

Under conditions of simulated concept drift, i-MAAR maintains a stable R² score while traditional models degrade.
Model	Avg. R² (Stable)	Avg. R² (After Drift)	Adaptation Latency
Static Regressor	0.88	0.42	N/A
i-MAAR (Proposed)	0.89	0.84	< 1.2s
2. Ablation Study

We evaluated the impact of removing key modules:

    w/o Multi-window: Performance drops by 15% during seasonal shifts.

    w/o AutoML: Reduced accuracy in high-dimensional feature spaces.

Interpretability in Action

One of the core strengths of i-MAAR is the real-time generation of explainability plots. During the streaming process, the model outputs:

    Global Feature Importance: Which variables are driving the trend in the current window.

    Local SHAP Values: Precise explanation for individual outlier predictions.

Usage
Running the Full Pipeline

To process the 30-day pre-processed stream and generate the i-MAAR performance report:
code Bash

    
python main.py --input data/processed/30_days_data.csv --windows 1440 --xai True

  

Reproducing Ablation Studies
code Bash

    
python experiments/ablation_study.py

  

🎓 Citation

If you use this algorithm or code in your research, please cite:

    Author Name, "Interpretable Multi-window and AutoML-based Adaptable Regression (i-MAAR Algorithm)", Research Article, 2024.

Contact
For inquiries regarding the architecture or experimental data, please refer to the corresponding author details in the associated manuscript.

This repository is part of ongoing research into Explainable AI (XAI) for Streaming Data.
