# 🔧📈 Exploring the Effects of Expressiveness and Regularization on Linear Regression Models
![Python](https://img.shields.io/badge/python-3.10%2B-blue?logo=python)
![Regression](https://img.shields.io/badge/Regression-linear-green)
![Regularization](https://img.shields.io/badge/Regularization-L1_and_L2-orange)

🔍 Investigating Bias-Variance Tradeoff and Regularization Strategies in Linear Regression 🔍

> **Authors**  
> Mingshu Liu, Kaibo Zhang, and Alek Bedard  
> **Affiliation**: McGill University, COMP551 - Applied Machine Learning  
> **Date**: October 22, 2024  

---

## Overview

This report investigates **linear regression models** with non-linear basis functions applied to synthetic data. Key areas of exploration include the impact of model complexity, regularization techniques, and their effects on bias-variance tradeoff. Additionally, we examine the loss landscapes of L1 and L2 regularization techniques and their influence on gradient descent optimization.

**Key Contributions:**
- Analysis of **Gaussian basis functions** and optimal complexity for generalization.
- Decomposition of the **bias-variance tradeoff** through multiple fits.
- Evaluation of **L1 and L2 regularization** strengths using 10-fold cross-validation.
- Visualization of **loss landscapes** for L1 and L2 and their impact on convergence.

---

## Dataset and Methodology

### Synthetic Dataset
- **Data Generation Function**:  
  \( y(x) = \sin(\sqrt{x}) + \cos(x) + \sin(x) + \epsilon \)
- **Size**: 100 data points generated with added noise.
- **Basis Functions**: Gaussian transformations with varying complexity \( D = [0, 100] \).  

**Preprocessing and Regularization:**
- L1 (Lasso) and L2 (Ridge) regularization techniques were employed.
- Models were evaluated through **10-fold cross-validation** for robust performance metrics.

---

### Key Experiments

1. <details>
    <summary>Gaussian Basis Functions and Overfitting</summary>

    - Varying the number of basis functions revealed a transition from underfitting to overfitting:
      - **Underfitting** at \( D < 20 \): High training and validation errors.
      - **Optimal Fit** at \( D = 20 \): Minimum validation error.
      - **Overfitting** at \( D > 50 \): Validation error increased due to noise capture.
   </details>

2. <details>
    <summary>Bias-Variance Tradeoff</summary>

    - Models trained on 10 datasets highlighted:
      - High bias and low variance for \( D = [0, 10] \).
      - Optimal bias-variance balance for \( D = [20, 40] \).
      - High variance for \( D > 40 \) due to overfitting.
   </details>

3. <details>
    <summary>L1 and L2 Regularization</summary>

    - 10-fold cross-validation determined:
      - **Optimal λ**: \( \lambda \approx 0.27 \) for L1, \( \lambda \approx 1.93 \) for L2.
      - L1 promoted sparsity, shrinking coefficients to zero.
      - L2 provided smoother weight shrinkage, enhancing generalization.
   </details>

4. <details>
    <summary>Loss Landscape Analysis</summary>

    - Visualized gradient descent paths under varying λ:
      - **L1 Regularization**: Induced sparsity with sharper, diamond-shaped contours.
      - **L2 Regularization**: Maintained smooth, circular contours for uniform shrinkage.
   </details>

5. <details>
    <summary>Gradient Descent Optimization</summary>

    - Compared vanilla gradient descent with ADAM optimizer:
      - ADAM achieved faster and smoother convergence for both regularization methods.
   </details>

---

## Results Summary

| Experiment                 | Metric              | Value/Effect    |
|----------------------------|---------------------|----------|
| Optimal Basis Functions    | Validation SSE      | Minimum at \( D = 20 \) |
| Bias-Variance Tradeoff     | Validation Error    | Balanced at \( D = 20 \) |
| L1 Regularization          | Optimal λ          | 0.27     |
| L2 Regularization          | Optimal λ          | 1.93     |
| Gradient Descent Efficiency| Convergence Speed  | Faster with ADAM |

---

## Insights and Future Work

- Increasing basis function complexity improves fit initially but risks overfitting at high values.
- **L1 regularization** effectively promotes sparsity, making it ideal for feature selection.
- **L2 regularization** provides smooth weight control, enhancing stability for dense datasets.
- Future explorations could combine L1 and L2 regularizations for fine-tuned complexity control or investigate alternative basis functions for broader applications.

---
