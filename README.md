# Region Covariance Object Detection

This project is a Python implementation of the seminal paper **"Region Covariance: A Fast Descriptor for Detection and Classification"** by Tuzel, Porikli, and Meer.

## 🧠 Core Concept
Unlike traditional histograms or pixel-based features, this method uses the **Covariance Matrix** of image features (color, gradients, coordinates) as a region descriptor. 

### Key Advantages:
- **Fast Computation:** Uses **Integral Images** to calculate the covariance of any rectangular region in constant time.
- **Robustness:** Naturally resistant to illumination changes and rotations.
- **Riemannian Geometry:** Since covariance matrices do not lie in Euclidean space, we use a **Distance Metric** involving generalized eigenvalues.

## 🛠️ Implementation Details
- **Feature Extraction:** Integration of spatial (x, y), color (RGB/HSV), and first/second-order derivatives.
- **Fast Summing:** Implementation of first and second-order Integral Images.
- **Metric:** Log-Euclidean distance for Symmetric Positive Definite (SPD) matrices.

## 📈 Usage
```python
detector = RegionCovarianceDetector(kernels=my_kernels)
detector.fit(object_image)
top_left, bottom_right, score = detector.predict(target_image)
