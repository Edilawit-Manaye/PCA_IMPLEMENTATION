 # Comparative Analysis of Dimensionality Reduction via  Principal Component Analysis (PCA)

# Prepared by : Edilawit Manaye Endeshaw
Project Objective: To analyze the impact of PCA on computational efficiency and
model reliability using the high-dimensional MNIST dataset.

# 1. Executive Summary
This work demonstrates the power of Principal Component Analysis (PCA) as a tool for feature extraction and noise reduction. By implementing PCA manually through Eigen-decomposition, we reduced the feature space of the MNIST dataset by 96.2% (from 784 to 30 dimensions). The results prove that this massive compression leads to a 7x increase in training speed while maintaining 100% of the baseline accuracy (89.95%).

# 2. Dataset & Preprocessing
   - Dataset: MNIST Digits (784 pixel-features per image).
  - EDA Insight: Exploratory Data Analysis confirmed a balanced class
    distribution (0-9) and showed that the "Spatial Signal" is concentrated in
    the center of the frame, justifying the removal of low-variance edge pixels.
  - Standardization: Applied Z-score normalization to ensure the covariance matrix calculation   was not biased by pixel intensity scales.
    <img width="859" height="393" alt="image" src="https://github.com/user-attachments/assets/552f60ad-6b40-4d20-9c29-4509072905f7" />
    <img width="328" height="371" alt="image" src="https://github.com/user-attachments/assets/339dfb5a-7fc4-46e1-813d-8f4ace2c0170" />


    
  


# 3. Mathematical Methodology (Manual Implementation)

To prove the "math behind the machine," I avoided high-level libraries and
implemented PCA using the following linear algebra workflow:

1.  Covariance Matrix (\Sigma): Calculated the 784 \times 784 matrix to find
    relationships between pixels.
2.  Eigen-Decomposition: Solved for Eigenvalues (\lambda) and Eigenvectors (v).
      - Eigenvalues: Represented the "Information Magnitude" of each direction.
      - Eigenvectors: Provided the new orthonormal axes (Principal Components).
3.  Projection: Transformed the raw data into a 30-dimensional space using the
    top 30 eigenvectors.

# 4. Visual Analysis & Justification

A. The Scree Plot (Information Decay)

The Scree Plot justifies the choice of 30 components. The "Elbow" occurs very
early, proving that the first few components capture the majority of the
cumulative variance.
<img width="846" height="470" alt="image" src="https://github.com/user-attachments/assets/01f456b0-4bcf-4681-bf36-fc395d9a64f8" />




B. 3D Manifold Visualization

Projecting the 784-dimensional data into a 3D space revealed distinct "clusters"
for different digits. This confirms that PCA preserves the global structure and
class boundaries necessary for classification.
<img width="642" height="658" alt="image" src="https://github.com/user-attachments/assets/6d246bda-eac2-4954-90d3-b5505eb8b793" />




C. Signal Reconstruction (MSE Analysis)

By reconstructing the images from 30 components, we observed a "denoising"
effect. The low Mean Squared Error (0.2085) proves that the 30-dimensional space
is a high-fidelity representation of the original 784-dimensional space.
<img width="955" height="506" alt="image" src="https://github.com/user-attachments/assets/eb30a0c2-bdc8-4591-b126-92e7da1dee53" />




# 5. Comparative Results & Performance Metrics

Metric   
Baseline (Raw)
PCA Optimized
Improvement
Feature Count
784
30 
96.2% Compression
Training Time
5.79s
0.89s
7x Speed Increase
Accuracy
89.95%
89.95%
0% Accuracy Los





# 6.Evaluation results
Beyond simple accuracy, the Precision, Recall, and F1-Scores across all 10 classes (0-9) remained stable. The side-by-side Confusion Matrices show identical error patterns, proving that PCA did not introduce any new classification bias.
<img width="1323" height="590" alt="image" src="https://github.com/user-attachments/assets/61dc3a13-4504-406e-86b0-44b7c879ffd6" />




# 7. Final Conclusion

The evidence from this competition-grade implementation confirms that PCA is not
merely a compression tool, but a strategic optimization.

1.  Computationally: It solves the "Curse of Dimensionality," allowing for
    near-instant training.
2.  Mathematically: It successfully identifies the "Eigen-digits" that contain
    the most information.
3.  Operationally: In real-world AI workflows, PCA provides a path to high-speed
    inference without sacrificing the quality of results.


