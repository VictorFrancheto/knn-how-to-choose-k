# $k$-NN: How to choose $k$

In this repository, I will teach you how to choose the optimal value of $k$ in the $k$-NN algorithm. 
<p align="center">
  <img src="https://github.com/VictorFrancheto/K_means-How_to_choose_K/blob/main/k_nn.jpg">
</p>

# 🔍 k-Nearest Neighbors (k-NN): A Step-by-Step Guide

The **k-Nearest Neighbors (k-NN)** algorithm is a simple yet powerful non-parametric method for **classification** and **regression**. Instead of building a model during training, k-NN directly relies on the **training data** to make predictions, making it a **lazy learning algorithm**.

Let’s break it down step by step. 🚀

---

## 📌 How Does k-NN Work?

Given a dataset with labeled examples:

$$\{(x_i, y_i)\}_{i=1}^n,$$

the algorithm follows three main steps:

1️⃣ **Compute Distances**: For each training point \( x_i \), calculate its distance to the query point \( x_q \), using a chosen distance metric:

   $$d(x_q, x_i) = \|x_q - x_i\|.$$  
   
2️⃣ **Identify Nearest Neighbors**: Select the **k** closest points to \( x_q \) based on the computed distances.

3️⃣ **Predict the Output**:
   - **For Classification**: Assign the most common label among the **k** neighbors:
     
     $$\hat{y}(x_q) = \text{mode} \{y_{j_1}, y_{j_2}, \dots, y_{j_k}\}.$$
     
   - **For Regression**: Predict the **average** of the target values of the k-nearest neighbors:
     
     $$\hat{y}(x_q) = \frac{1}{k} \sum_{i=1}^k y_{j_i}.$$  
     
---

## 📏 Choosing the Right Distance Metric

The distance metric is **crucial** for determining the neighbors of \( x_q \). Here are some common options:

🔹 **Euclidean Distance** – The straight-line distance between two points:

   $$d_{\text{Euclidean}}(x_q, x_i) = \sqrt{\sum_{j=1}^d (x_{qj} - x_{ij})^2}.$$  

🔹 **Manhattan Distance** – The sum of absolute differences, useful in grid-like structures:

   $$d_{\text{Manhattan}}(x_q, x_i) = \sum_{j=1}^d |x_{qj} - x_{ij}|.$$  

🔹 **Chebyshev Distance** – The maximum absolute difference along any coordinate:

   $$d_{\text{Chebyshev}}(x_q, x_i) = \max_{j=1}^d |x_{qj} - x_{ij}|.$$  

🔹 **Minkowski Distance** – A generalization of Euclidean and Manhattan distances:

   $$d_{\text{Minkowski}}(x_q, x_i) = \left( \sum_{j=1}^d |x_{qj} - x_{ij}|^p \right)^{\frac{1}{p}}.$$  
   
   - \( p = 2 \) → Euclidean Distance
   - \( p = 1 \) → Manhattan Distance

🔹 **Hamming Distance** – Counts the number of differing features (useful for categorical data):

   $$d_{\text{Hamming}}(x_q, x_i) = \sum_{j=1}^d \mathbb{I}(x_{qj} \neq x_{ij}).$$

Each metric has its own strengths:
✔ **Euclidean** – Best for continuous and isotropic data.
✔ **Manhattan** – Useful for high-dimensional data.
✔ **Chebyshev** – Works well in grid-based problems.
✔ **Minkowski** – Allows fine-tuned distance calculations.
✔ **Hamming** – Ideal for binary and categorical data.

---

## 🔬 How to Choose \( k \)?

The choice of \( k \) impacts the algorithm’s performance:

✅ **Small \( k \)** → More sensitive to noise, risk of **overfitting**.
✅ **Large \( k \)** → Smoother predictions, but may lead to **underfitting**.

A common approach is to use **cross-validation** to find an optimal \( k \).

---

## ⏳ Computational Complexity

One major drawback of k-NN is its **high computational cost**. For each query, k-NN calculates distances to all **n** training points, leading to an overall complexity of:

   $$O(n \cdot d)$$ per query.

For large datasets, this can be **slow**, so techniques like **KD-Trees** or **Ball Trees** are used for optimization.

---

## ⚠️ Key Considerations

📌 **Scalability**: k-NN is memory-intensive and slow for large datasets.
📌 **Feature Scaling**: Since k-NN relies on distances, standardizing or normalizing features is **essential**.
📌 **Noise Sensitivity**: Outliers can heavily influence predictions, especially for small \( k \).

---

✅ Now you understand how k-NN works! Whether you’re using it for classification or regression, the key is to **choose the right \( k \) and distance metric** for your problem.

🚀 Ready to implement k-NN in Python? Let’s code! 🧑‍💻
   
2. **Feature Scaling**:  
   Features must be normalized or scaled, as $k$-NN is sensitive to the magnitude of features.

3. **Noise Sensitivity**:  
   $k$-NN is prone to being influenced by outliers or mislabeled data.
