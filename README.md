# Enhancing Model Adaptability and Transparency:i-MAAR Algorithm for Non-Stationary Streaming Data Analysis

We propose a novel algorithm, termed i-MAAR (Interpretable Multi-Window and AutoML-based Adaptable Regression). The primary objective of i-MAAR is to enable adaptive and transparent learning in non-stationary streaming data environments.

# Abstract

The interpretable Multi-window and AutoML-based Adaptable Regression (i-MAAR) algorithm presents a state-of-the-art solution for analyzing fast-moving, non-stationary streaming data. It effectively addresses key challenges such as reliability, low-latency response, computational efficiency, storage constraints, and concept drift. By maintaining multiple data windows, i-MAAR enables efficient training, retraining, and accurate detection of concept drift, ensuring consistent and reliable model performance. To dynamically adapt to evolving data patterns, i-MAAR uses concept drift as a trigger to check for performance degradation and invokes an AutoML-based strategy to maintain robustness. The integration of SHAP values enhances transparency and trust by providing clear explanations for performance issues and guiding optimal feature selection. Operating asynchronously, the algorithm supports continuous forecasting and retraining while optimizing resource utilization. An ablation study highlights the contribution of each component to the system’s overall accuracy and stability. Experimental results show that i-MAAR consistently outperforms existing methods in predictive accuracy and adaptability, making it a powerful and efficient choice for real-time streaming data analysis.

# Features 

- Robust performance for streaming data analysis (SDA)  
- Adaptive model updating based on evolving feature importance  
- Built-in interpretability using SHAP for transparency and trust  
- Ablation study demonstrating the role of each component  

# Experimental results (Reproducibility)
    
    The Colab notebook linked here presents the experimental results obtained using the Tétouan dataset.
    
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](
https://colab.research.google.com/drive/1rOZxySMbhsSuUCuqBA3RcMGxoP_NV7AM)




