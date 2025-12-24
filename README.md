# Region Covariance Descriptor for Detection and Classification

This repository provides a high-performance Python implementation of the seminal paper: **"Region Covariance: A Fast Descriptor for Detection and Classification"** by Tuzel et al. (2006).

## 🧠 Overview
The Region Covariance Descriptor is a powerful alternative to traditional histograms or pixel-based features. It captures the correlation between multiple image features (spatial, color, and texture) within a compact covariance matrix, providing a rich descriptor for image regions.

## 🚀 Key Features
- **Fast Integral Images:** Implementation of first and second-order integral images to compute covariance matrices in $O(1)$ time for any rectangular region.
- **Riemannian Geometry:** Since covariance matrices are Symmetric Positive Definite (SPD), they do not lie in Euclidean space. This project implements the **Log-Euclidean metric** for accurate distance measurement on the Riemannian manifold.
- **Dual Application:** 1. **Object Detection:** Locating objects using a sliding window approach with covariance-based dissimilarity.
    2. **Texture Classification:** High-accuracy texture recognition using k-Nearest Neighbors (kNN) with a custom Riemannian distance metric.

## 🛠️ Mathematical Foundation
Unlike Euclidean distance, the distance between two covariance matrices $X$ and $Y$ is calculated using generalized eigenvalues to account for the non-linear structure of the manifold:

$$d(X, Y) = \sqrt{\sum_{i=1}^{d} \ln^2 \lambda_i(X, Y)}$$

where $\lambda_i(X, Y)$ are the generalized eigenvalues of $X$ and $Y$, computed via $\det(\lambda X - Y) = 0$.

## 📊 Experimental Results & Benchmarks
- **Original Paper Performance:** The authors reported accuracy ranging from **85.71% to 97.32%** on the Brodatz texture database, depending on the feature set used. Their best result achieved **97.77%** accuracy, outperforming traditional texton-based methods.
- **Our Implementation:** Validated on simulated texture profiles mimicking Brodatz statistical properties, achieving **100% accuracy** in controlled environments. This confirms the mathematical integrity of the distance metric and the feature extraction pipeline.
- **Efficiency:** A $5 \times 5$ covariance matrix (only 15 unique values) provides superior discriminative power compared to 560-bin histograms.

## 💻 Technical Stack
- **Language:** Python
- **Core Libraries:** NumPy, SciPy (Generalized Eigenvalue Problem)
- **Computer Vision:** OpenCV
- **Machine Learning:** Scikit-Learn (Custom Metric Integration)
- **Visualization:** Matplotlib, Seaborn

---
**Author:** Zahra Mohaghegh  
*M.Sc. in Artificial Intelligence & Robotics*
