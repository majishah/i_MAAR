# interpretable Multi-window and AutoML-based Adaptable Regression (i-MAAR Algorithm)
We propose a novel algorithm, termed i-MAAR (interpretable Multi-window and AutoML-based Adaptable Regression). The primary objective of i-MAAR  is to enable adaptive and transparent learning in non-stationary streaming data environments.

# Abstract

The i-MAAR (interpretable Multi-window and AutoML-based Adaptable Regression) algorithm presents a state-of-the-art solution for analyzing fast-moving, non-stationary streaming data. It effectively addresses key challenges such as reliability, low-latency response, computational efficiency, storage constraints, and concept drift. By maintaining multiple data windows, it enables efficient training, retraining, and accurate detection of concept drift, ensuring consistent and reliable model performance. To dynamically adapt to evolving data patterns, i-MAAR uses concept drift as a trigger to check for performance degradation and invokes an AutoML-based strategy to maintain robustness. The integration of SHAP values enhances transparency and trust by providing clear explanations for performance issues and guiding optimal feature selection. Operating asynchronously, the algorithm supports continuous forecasting and retraining while optimizing resource utilization. An ablation study highlights the contribution of each component to the system’s overall accuracy and stability. Experimental results show that i-MAAR consistently outperforms existing methods in predictive accuracy and adaptability, making it a powerful and efficient choice for real-time streaming data analysis.

# Features 

- Robust performance for streaming data analysis (SDA)  
- Adaptive model updating based on evolving feature importance  
- Built-in interpretability using SHAP for transparency and trust  
- Ablation study demonstrating the role of each component  

# Experimental results (Reproducibility)
    
    The Colab notebook linked here presents the experimental results obtained using the Tetouan dataset.
    
Experiment with Tetouan Dataset:  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](
https://colab.research.google.com/drive/1rOZxySMbhsSuUCuqBA3RcMGxoP_NV7AM)

Baseline Model Comparisons:  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1NL3Vlu27wgHRZ_IJ5SDnGLffFB29eFlO?authuser=3#scrollTo=tSv8SGovKQrx)


# Contact & Acknowledgment  

This work is part of the ongoing Ph.D. research at Indian Institute of Information Technology Kottayam, carried out under the guidance of Dr.Ebin Deni Raj, Assistant Professor.  

For questions, collaborations, or further information, please contact:  

Shahad P  
PhD Scholar  
Indian Institute of Information Technology, Kottayam  
shahadphd2019@iiitkottayam.ac.in 





