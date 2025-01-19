# $k$-NN: How to choose K

In this repository, I will teach you how to choose the optimal value of K in the K-means algorithm to create concise clusters. **<span style="color:red;">(In progress)</span>**

<p align="center">
  <img src="https://github.com/VictorFrancheto/K_means-How_to_choose_K/blob/main/k_means.jpg">
</p>
Entendido! Aqui está o texto revisado para explicar o **k-Nearest Neighbors (k-NN)** em um formato mais técnico e conciso, com observações detalhadas e matematicamente estruturadas:

---

The **k-Nearest Neighbors (k-NN)** is a non-parametric algorithm used for classification and regression tasks. It predicts the label or value of a query point $x_q$ based on the $k$-closest points in the training set, measured using a distance metric (e.g., Euclidean, Manhattan etc).

Mathematically, given a dataset $\{(x_i, y_i)\}_{i=1}^n$, the algorithm proceeds as follows.

1. **Compute Distances**:  
   For each point $x_i$ in the training set, calculate its distance to the query point $x_q$,
   
   $$d(x_q, x_i) = \|x_q - x_i\|,$$
   
   where $\| \cdot \|$ is the chosen distance metric.

3. **Identify Nearest Neighbors**:  
   Select the $k$-points with the smallest distances to $x_q$.

4. **Predict the Output**:  
   - **For Classification**: Assign the most common label among the $k$-nearest neighbors
   - 
     $$\hat{y}(x_q) = \text{mode}\{y_{j_1}, y_{j_2}, \ldots, y_{j_k}\}.$$
     
   - **For Regression**: Predict the average of the $k$-nearest neighbors target values
   - 
     $$\hat{y}(x_q) = \frac{1}{k} \sum_{i=1}^k y_{j_i}.$$

### Observations

1. **Flexibility and Assumptions**:
   - $k$-NN is a **lazy learning algorithm**, as it does not build an explicit model during training. Instead, it relies on the stored data.
   - It assumes that similar data points are located near each other in the feature space.

2. **Distance Metrics**:  
   The choice of the distance metric significantly affects the performance of $k$-NN, as it determines how the **closeness** between points is measured. Common options include.

   - **Euclidean Distance**:  
     The straight-line distance between two points in space, calculated as:
     $$
     d_{\text{Euclidean}}(x_q, x_i) = \sqrt{\sum_{j=1}^d (x_{qj} - x_{ij})^2},
     $$
     where \( x_q = (x_{q1}, x_{q2}, \dots, x_{qd}) \) and \( x_i = (x_{i1}, x_{i2}, \dots, x_{id}) \).

   - **Manhattan Distance** (or Taxicab Distance):  
     The sum of the absolute differences of their coordinates, often used in grid-like structures:
     $$
     d_{\text{Manhattan}}(x_q, x_i) = \sum_{j=1}^d |x_{qj} - x_{ij}|.
     $$

   - **Chebyshev Distance**:  
     The maximum absolute difference across any dimension, capturing the idea of "one step in any direction":
     $$
     d_{\text{Chebyshev}}(x_q, x_i) = \max_{j=1}^d |x_{qj} - x_{ij}|.
     $$

   - **Minkowski Distance**:  
     A generalized form of distance, which includes both Euclidean and Manhattan distances as special cases:
     $$
     d_{\text{Minkowski}}(x_q, x_i) = \left( \sum_{j=1}^d |x_{qj} - x_{ij}|^p \right)^{\frac{1}{p}},
     $$
     where \( p \) is a parameter:
     - \( p = 2 \): Euclidean Distance.
     - \( p = 1 \): Manhattan Distance.

   - **Hamming Distance**:  
     Used for categorical variables or binary data, it measures the number of differing dimensions:
     $$
     d_{\text{Hamming}}(x_q, x_i) = \sum_{j=1}^d \mathbb{I}(x_{qj} \neq x_{ij}),
     $$
     where \( \mathbb{I} \) is an indicator function that is 1 if the values differ and 0 otherwise.

Each metric has specific applications:
- **Euclidean**: Suitable for continuous and isotropic data.
- **Manhattan**: Effective for high-dimensional data or grid-based movement.
- **Chebyshev**: Useful in chessboard-like systems.
- **Minkowski**: Offers flexibility with the \( p \)-parameter.
- **Hamming**: Ideal for text, binary, or categorical data.

3. **Effect of $k$**:
   - **Small $k$**: Sensitive to noise, prone to overfitting.
   - **Large $k$**: Provides smoother predictions but may underfit the data.

4. **Computational Complexity**:
   - For a query point, $k$-NN computes distances to all $n$ training points, leading to $O(n \cdot d)$ complexity per prediction, where $d$ is the number of dimensions. 

### Limitations and Considerations

1. **Scalability**:  
   $k$-NN struggles with large datasets, both in terms of memory and computational cost.
   
2. **Feature Scaling**:  
   Features must be normalized or scaled, as $k$-NN is sensitive to the magnitude of features.

3. **Noise Sensitivity**:  
   $k$-NN is prone to being influenced by outliers or mislabeled data.
