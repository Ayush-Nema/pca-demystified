The objective function for Principal Component Analysis (PCA) can be expressed using mathematical equations. PCA aims to find the directions (principal components) that maximize the variance of the data while minimizing the reconstruction error. Here is a mathematical representation of the PCA objective function:

1. **Maximizing Variance**:
   Given a data matrix  $X \in \mathbb{R}^{n \times p}$  where $n$ is the number of observations and $p$ is the number of features, we seek a set of orthonormal vectors $\{ \mathbf{w}_1, \mathbf{w}_2, \ldots, \mathbf{w}_k \}$ (principal components) such that the variance of the projections of $X$ onto these vectors is maximized.

   The first principal component $\mathbf{w}_1$ is found by solving:   $$\mathbf{w}_1 = \arg\max_{\mathbf{w} \in \mathbb{R}^p, \|\mathbf{w}\| = 1} \mathbf{w}^T S \mathbf{w}$$
   where $S = \frac{1}{n} X^T X$ is the sample covariance matrix of $X$.

</br>

2. **Subsequent Principal Components**:
   For each subsequent principal component $\mathbf{w}_i$ (where $i = 2, 3, \ldots, k$), we need to ensure orthogonality to the previously found components and maximize the variance:
   $$\mathbf{w}_i = \arg\max_{\mathbf{w} \in \mathbb{R}^p, \|\mathbf{w}\| = 1, \mathbf{w} \perp \mathbf{w}_j \, \forall \, j < i} \mathbf{w}^T S \mathbf{w}$$
</br>

3. **Minimizing Reconstruction Error**:
   Alternatively, PCA can be viewed as finding a low-dimensional subspace that minimizes the reconstruction error. The reconstruction error for projecting $X$ onto the subspace spanned by $\{ \mathbf{w}_1, \mathbf{w}_2, \ldots, \mathbf{w}_k \}$ is:
   $$\min_{W \in \mathbb{R}^{p \times k}} \| X - X W W^T \|_F^2$$

   where $W = [\mathbf{w}_1 \; \mathbf{w}_2 \; \ldots \; \mathbf{w}_k]$ is a matrix whose columns are the principal components, and $\| \cdot \|_F$ denotes the Frobenius norm.

</br>

4. **Eigenvalue Decomposition**:
   The principal components are the eigenvectors corresponding to the largest eigenvalues of the covariance matrix $S$. Mathematically, we solve the eigenvalue problem:   
   $$
   S \mathbf{w}_i = \lambda_i \mathbf{w}_i
   $$
   
   where $\lambda_i$ are the eigenvalues and $\mathbf{w}_i$ are the eigenvectors.

Combining these formulations, the *objective function of PCA* can be summarized as _finding the orthonormal vectors that either maximize the variance of the data projections or minimize the reconstruction error_, typically solved via eigenvalue decomposition of the data covariance matrix.

