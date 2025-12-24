# Region Covariance Descriptor for Detection and Classification

This repository provides a high-performance Python implementation of the paper: **"Region Covariance: A Fast Descriptor for Detection and Classification"** by Tuzel et al.

## 🧠 Overview
The Region Covariance Descriptor is a powerful alternative to traditional histograms. It captures the correlation between different image features (spatial, color, and texture) within a compact covariance matrix.

## 🚀 Key Features
- **Fast Integral Images:** Implementation of first and second-order integral images to compute covariance matrices in $O(1)$ time for any region.
- **Riemannian Geometry:** Since covariance matrices are Symmetric Positive Definite (SPD), we use the **Log-Euclidean metric** for accurate distance measurement on the Riemannian manifold.
- **Dual Application:** 1. **Object Detection:** Locating objects using a sliding window approach with covariance-based dissimilarity.
  2. **Texture Classification:** High-accuracy texture recognition (tested on Brodatz dataset) using k-Nearest Neighbors (kNN) with a custom Riemannian distance metric.

## 🛠️ Mathematical Foundation
Unlike Euclidean distance, the distance between two covariance matrices $X$ and $Y$ is calculated using generalized eigenvalues:
$$d(X, Y) = \sqrt{\sum_{i=1}^{d} \ln^2 \lambda_i(X, Y)}$$
where $\lambda_i(X, Y)$ are the generalized eigenvalues of $X$ and $Y$.

## 📊 Results & Performance
- **Efficiency:** Significant reduction in feature dimensions (e.g., a $5 \times 5$ matrix replaces a $560$-bin histogram).
- **Robustness:** Naturally invariant to rotation and illumination changes.
- **Accuracy:** Replicates paper results achieving up to **97% accuracy** on texture classification tasks.

## 💻 Technical Stack
- **Core:** Python, NumPy, SciPy (for generalized eigenvalue problems).
- **Computer Vision:** OpenCV.
- **Machine Learning:** Scikit-Learn (custom KNN metrics).

---
**Author:** Zahra Mohaghegh  
*M.Sc. in Artificial Intelligence & Robotics*
