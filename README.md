# Laptop Price Prediction – Regression from Scratch

> End-to-end regression system built **from scratch using NumPy** to explore and compare different formulations of linear regression, including optimization, closed-form solutions, and statistical inference.

---

##  Project Overview

This project implements **linear regression without using high-level ML regression libraries** (e.g., `sklearn.linear_model`), focusing on understanding the mathematical foundations of:

- Optimization-based learning (Gradient Descent)
- Analytical solutions (Normal Equation)
- Statistical inference (t-tests, confidence intervals, p-values)

The models are applied to a **laptop price prediction dataset**, and evaluated under different feature selection strategies.

---

##  Implemented Models

### 1. Gradient Descent Regression (Multivariate)
- Custom implementation of linear regression using iterative optimization
- Supports:
  - L2 Regularization (Ridge)
  - L1 Regularization (Lasso)
- Handles multi-feature learning and convergence tracking

---

### 2. Closed-Form Regression (Normal Equation)
- Direct matrix-based solution for optimal coefficients
- Extended to include Ridge/Lasso regularization
- Used for comparison with iterative optimization

---

### 3. Statistical Regression Inference Model
- Implements regression from a statistical perspective
- Computes:
  - Coefficients
  - Standard Errors
  - t-statistics
  - p-values
  - Confidence Intervals
- Provides interpretability beyond prediction accuracy

---

## ⚙️ Features

- Pure NumPy implementation of regression algorithms
- Feature preprocessing:
  - MinMax Scaling
  - Ordinal Encoding (via scikit-learn preprocessing only)
- Regularization implemented manually (L1 / L2)
- Multiple feature selection strategies:
  - Best single feature (RAM)
  - Full feature set
  - Domain-knowledge feature subset
- Full evaluation pipeline:
  - R²
  - Adjusted R²
  - MSE / SSE
- Visualization suite:
  - Correlation heatmap
  - Regression fit plots
  - Residual analysis
  - Gradient descent convergence curves
  - Coefficient comparison plots

---

##  Experimental Results

| Model Type            | Regularization | R² Score | Adj. R² | Features |
|----------------------|----------------|----------|---------|----------|
| Full Model           | OLS            | 0.568    | 0.552   | 9        |
| Full Model           | Lasso (λ=0.001)| 0.563    | 0.547   | 9        |
| Domain Knowledge     | OLS            | 0.539    | 0.525   | 7        |
| Single Feature (RAM) | OLS            | 0.310    | 0.307   | 1        |

### Key Insights
- Full model achieves highest predictive performance
- Domain-knowledge model achieves competitive performance with fewer features (bias-variance tradeoff)
- Lasso regularization improves sparsity without major loss in accuracy
- RAM is the strongest single predictor of laptop price

---##  Project Structure

```bash
regression_project/
├── regression_project.ipynb   # Full implementation & analysis
├── laptopData.csv             # Dataset (excluded from repo)
└── README.md                  # Project documentation
 How to Run
1. Clone Repository
git clone https://github.com/hamo229/regression-project.git
cd regression-project
2. Install Dependencies
pip install numpy pandas matplotlib plotly scikit-learn scipy
3. Run Notebook
jupyter notebook regression_project.ipynb

Or open it using:

VS Code
Google Colab
 Example Usage
from regression_project import LinearRegressionGD

model = LinearRegressionGD()

# Train with Lasso regularization
model.fit(X_train, y_train, alpha_lasso=0.001)

# Predict
y_pred = model.predict(X_test)

# Evaluate
print(model.metrics())
