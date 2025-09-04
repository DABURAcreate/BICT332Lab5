# BICT332 Lab 5 – Dimensionality Reduction

This repository explores **dimensionality reduction techniques** including PCA, LDA, and Kernel PCA, and evaluates their effectiveness on datasets such as Wine and the half-moon dataset.

---

## Questions & Answers

### 1. Explained Variance
- **Explained variance** in PCA shows how much of the dataset’s total variance is captured by each principal component.  
- As the number of components increases, the explained variance increases but with diminishing returns (the first few components usually explain most of the variance).  
- To capture **95% of the variance** in the Wine dataset, typically **about 13–15 components** are required (depending on preprocessing and scaling).

---

### 2. PCA vs. LDA
- **PCA** is unsupervised: it maximizes variance without considering class labels. Its components may not necessarily separate classes well.  
- **LDA** is supervised: it explicitly maximizes class separability by projecting data onto axes that best separate class means while minimizing within-class variance.  
- **Result:** LDA projections of the Wine dataset usually show **much better class separation** compared to PCA, which makes LDA more effective for **classification tasks** as a preprocessing step.

---

### 3. KPCA Gamma Parameter
- The **γ (gamma)** parameter in RBF Kernel PCA controls the influence of each training example.  
  - **Too small (e.g., 0.01):** The decision boundary becomes overly smooth, classes overlap, and data is not well separated.  
  - **Too large (e.g., 100):** The kernel becomes too sensitive to individual points, leading to overfitting and noisy decision boundaries.  
- A **moderate γ** value results in a good balance, transforming the half-moon dataset into a linearly separable form.

---

### 4. Classifier Performance
- **Original Wine Data:** Classifiers like Logistic Regression or SVM perform reasonably well but may take longer due to high dimensionality.  
- **PCA-Transformed Data:**  
  - Reduces computation time.  
  - Accuracy remains high if enough components are used (e.g., 95% explained variance).  
- **LDA-Transformed Data:**  
  - Best performance for classification tasks because LDA explicitly maximizes class separability.  
  - Typically achieves higher accuracy than PCA while also reducing dimensionality.  

**Observation:**  
- PCA is better for unsupervised dimensionality reduction and visualization.  
- LDA is superior when classification is the goal.  
- Both improve efficiency compared to raw data.

---

### 5. Limitations
- **When PCA might fail:**  
  - PCA assumes linear relationships.  
  - It fails with **nonlinear structures**, e.g., the “two moons” dataset, where linear projections cannot separate the classes.  

- **How KPCA addresses this:**  
  - KPCA uses the **kernel trick** to map data into a higher-dimensional feature space where nonlinear structures can be separated linearly.  
  - For example, KPCA with RBF kernel can transform the “two moons” dataset into a linearly separable form.

---

## Summary
- **PCA** reduces dimensionality by capturing variance.  
- **LDA** optimizes for class separation and generally outperforms PCA for classification.  
- **KPCA** extends PCA to nonlinear datasets via kernel methods.  
- Choice of method depends on whether the task is **unsupervised exploration** (PCA) or **supervised classification** (LDA/KPCA).

---
