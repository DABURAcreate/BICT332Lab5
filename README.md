# BICT332 Lab 5 – Dimensionality Reduction

This repo is for **Lab 5**, where we explored PCA, LDA, and Kernel PCA.  
I tried out these dimensionality reduction methods on the Wine dataset and the half-moon dataset, and then compared how classifiers perform on the transformed data.  

---

## Questions & My Answers

### 1. Explained Variance
When you do PCA, each new component explains some part of the variance in the data. The first few components usually explain most of it, then after a while the extra ones don’t add much.  
For the Wine dataset, I noticed you need around **13–15 components** to explain about **95% of the variance**. So instead of keeping all features, you can actually work with way fewer and still not lose much info.

---

### 2. PCA vs. LDA
- **PCA**: just looks at variance, doesn’t care about class labels. Good for general dimensionality reduction but not perfect for separating classes.  
- **LDA**: uses class labels and tries to maximize the separation between them. That makes it way better for classification problems.  

On the Wine dataset, the LDA projection showed clear separation between classes, while PCA was more about spreading data by variance. That’s why LDA usually wins if your goal is **classification**.

---

### 3. KPCA Gamma Parameter
In Kernel PCA with the RBF kernel, the **gamma (γ)** value is super important:  
- **Too small (e.g. 0.01):** The boundary is too smooth, so classes don’t really separate well.  
- **Too big (e.g. 100):** It overfits and gets too sensitive to noise, like drawing weird wiggly boundaries.  
- A **medium gamma** worked best for the half-moon dataset, because it made the moons nicely separable without overfitting.

---

### 4. Classifier Performance
I tested classifiers (like Logistic Regression and SVM) on three versions of the Wine dataset:  
- **Original data:** Works okay but a bit heavy since the data is high-dimensional.  
- **PCA data:** Runs faster, accuracy is still decent if you keep enough components (like the 95% variance rule).  
- **LDA data:** Actually gave the best accuracy because LDA is literally built to separate classes.  

So yeah, PCA is nice for speed and general dimensionality reduction, but if you’re doing classification, LDA gives you that extra edge.

---

### 5. Limitations
- **Where PCA fails:** PCA struggles with nonlinear datasets. Example: the “two moons” dataset. PCA just flattens it and the classes overlap badly.  
- **How KPCA fixes this:** KPCA uses kernels (like the RBF kernel) to project the data into a higher dimension where the classes become separable. That’s how the moons dataset can be untangled with KPCA.

---

## Wrap Up
Here’s what I learned:  
- PCA is good for reducing dimensions and keeping most of the variance.  
- LDA is better when labels matter and you want the best class separation.  
- KPCA is like the nonlinear version of PCA and works well when normal PCA can’t capture the structure.  

Overall, this lab showed me why you wouldn’t just blindly use PCA all the time — it depends on what you’re trying to achieve.

---
