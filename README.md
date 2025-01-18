# K_means: How_to_choose_K

In this repository, I will teach you how to choose the optimal value of K in the K-means algorithm to create concise clusters. **<span style="color:red;">(In progress)</span>**

<p align="center">
  <img src="https://github.com/VictorFrancheto/K_means-How_to_choose_K/blob/main/k_means.jpg">
</p>

The **k-means** is an iterative partitioning algorithm that minimizes the sum of squared distances between data points and their respective centroids, aiming to solve the clustering problem in a metric space. It implicitly assumes that the clusters have an approximately spherical shape and that the number $k$ of clusters is known a priori.

Mathematically, the goal of $k$-means is to minimize the following cost function:

$$
J = \sum_{i=1}^k \sum_{x \in C_i} \| x - \mu_i \|^2,
$$

where $C_i$ is the set of points in cluster $i$ and $\mu_i$ is the corresponding centroid.

### Observations

1. **Convergence**:  
   - The algorithm always converges to a local minimum of the objective function but does not guarantee finding the global minimum. The quality of the solution can strongly depend on the initialization of the centroids, making the algorithm sensitive to this choice.

2. **Computational Complexity**:  
   - The $k$-means has a complexity of $O(n \cdot k \cdot t \cdot d)$, where $n$ is the number of points, $k$ the number of clusters, $t$ the number of iterations, and $d$ the dimensionality of the data.

3. **Limitations and Extensions**:  
   - The algorithm assumes that clusters are convex and isotropic, which may not be suitable for datasets with non-linear distributions or complex shapes.  

The main goal here is to implement the algorithm and determine the best choice for $k$. 
