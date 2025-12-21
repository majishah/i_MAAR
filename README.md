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

```text
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
