# Assumptions of PCA
Principal Component Analysis (PCA) is fundamentally a linear technique. It is used for linear dimensionality reduction and linear analysis of data. Here’s a brief explanation of why PCA is considered linear:

1. **Linear Combinations**:
   - PCA identifies the directions (principal components) along which the variance of the data is maximized. These directions are linear combinations of the original features.
   - Mathematically, if $\mathbf{w}_i$ is a principal component (eigenvector), then the projection of the data onto this component is given by the linear combination $\mathbf{z}_i = X \mathbf{w}_i$.

2. **Covariance Matrix**:
   - PCA involves the computation of the covariance matrix of the data, which captures the linear relationships between features. The eigenvectors of this matrix are used to determine the principal components.
   - The covariance matrix $S$ is computed as $S = \frac{1}{n} \bar{X}^T \bar{X}$, where $\bar{X}$ is the mean-centered data.

3. **Eigenvalue Decomposition**:
   - The eigenvalue decomposition of the covariance matrix $S \mathbf{w}_i = \lambda_i \mathbf{w}_i$ is a linear operation, identifying the directions of maximum variance in the linear feature space.

## Limitations and Extensions
- **Nonlinear Relationships**: PCA cannot capture complex, nonlinear relationships in the data. It assumes that the principal components are linear combinations of the original features.
- **Kernel PCA**: To handle nonlinear relationships, Kernel PCA can be used. Kernel PCA extends PCA by first mapping the data into a higher-dimensional feature space using a nonlinear kernel function, and then performing linear PCA in that space.
- **Other Nonlinear Techniques**: For nonlinear dimensionality reduction, other techniques like t-SNE (t-Distributed Stochastic Neighbor Embedding), UMAP (Uniform Manifold Approximation and Projection), and autoencoders can be used.

---

# Assumptions in details
Principal Component Analysis (PCA) is a popular technique for dimensionality reduction and data analysis, but it relies on several key assumptions and conditions. Understanding these assumptions is crucial for applying PCA effectively. Here’s a detailed explanation of the main assumptions of PCA:

## 1. **Linearity**
**◎ Assumption:**
- PCA assumes that the principal components (directions of maximum variance) are linear combinations of the original features in the data matrix $X$.

**◎ Explanation:**
- PCA identifies linear combinations of the original features that capture the most variance in the data. It does not account for nonlinear relationships between features.
- If the data has a complex, nonlinear structure, PCA may not adequately capture the underlying patterns.

**◎ Mathematical Formulation**: 
$$X_{proj}=XW$$where $W$ is a matrix of principal components (eigenvectors) and $X_{proj}$​ is the projected data in the reduced space.

## 2. **Variance Maximization**
**◎ Assumption:**
- PCA assumes that the most important information in the data is the direction of maximum variance.
- Or, in other words, it assumes that the directions of maximum variance in the data correspond to the principal components. It seeks to maximize the variance captured by each principal component.

**◎ Explanation:**
- The principal components are the directions along which the data varies the most. This means that PCA aims to find the axes of maximum spread in the data.
- The principal components are ordered by the amount of variance they explain, with the first component explaining the most variance.

**◎ Mathematical Formulation**:
 $$
 \text{Var}(\mathbf{X} \mathbf{w}_i) = \mathbf{w}_i^T S \mathbf{w}_i
$$
 where $S$ is the covariance matrix of the data $\mathbf{X}$, and $\mathbf{w}_i$ is the $i$-th principal component.

## 3. **Gaussian Distribution (Optional but Beneficial)**
**◎ Assumption:**
- While not strictly necessary, PCA performs better when the data is approximately normally distributed.

**◎ Explanation:**
- PCA is often more interpretable and effective when the data follows a Gaussian distribution because the variance-covariance structure in Gaussian data is well-defined and interpretable.
- However, PCA can still be applied to non-Gaussian data; it just may not capture all meaningful patterns as effectively.

## 4. **Scale Sensitivity**
**◎ Assumption:**
- PCA assumes that the features are on a similar scale.

**◎ Explanation:**
- PCA is sensitive to the scale of the features because it is based on the covariance matrix, which is influenced by the scale of the data.
- Features with larger scales can dominate the principal components, leading to skewed results. Therefore, it’s important to standardize or normalize features before applying PCA.

## 5. **Mean Centering**
**◎ Assumption:**
- PCA assumes that the data has been mean-centered. This is necessary for correctly computing the covariance matrix and finding principal components.

**◎ Explanation:**
- PCA requires the data to be mean-centered (subtracting the mean of each feature) so that the covariance matrix is calculated relative to the mean of the data.
- If the data is not centered, the principal components may not properly reflect the directions of maximum variance.

**◎ Mathematical Formulation**:
$$ \bar{X} = X - \frac{1}{n} \mathbf{1} \mathbf{1}^T X$$

where $\bar{X}$ is the mean-centered data matrix, $\mathbf{1}$ is a vector of ones, and $n$ is the number of samples.

## 6. **Orthogonality of Principal Components**
**◎ Assumption:**
- PCA assumes that the principal components are orthogonal (uncorrelated).

**◎ Explanation:**
- The principal components are derived from the eigenvectors of the covariance matrix, and these eigenvectors are orthogonal by definition.
- Orthogonality ensures that each principal component captures a unique aspect of the data variance without redundancy.
- This orthogonality ensures that each principal component captures unique variance.

**◎ Mathematical Formulation**:
 $$\mathbf{w}_i^T \mathbf{w}_j = 0 \quad \text{for} \quad i \ne j$$
 where $\mathbf{w}_i$ and $\mathbf{w}_j$ are different principal components.


#### Summary of the assumptions
- **Linearity**: PCA assumes linear relationships among features.
- **Variance Maximization**: PCA focuses on directions of maximum variance.
- **Gaussian Distribution**: PCA works best with normally distributed data, but is not strictly required.
- **Scale Sensitivity**: Features should be on similar scales; otherwise, scaling issues can affect results.
- **Mean Centering**: Data should be mean-centered before applying PCA.
- **Orthogonality**: Principal components are orthogonal, ensuring that they capture independent variance.

---
## Consequences of Violating Assumptions
1. **Nonlinearity**:
   - **Issue**: If the data contains significant nonlinear relationships, PCA may not capture the underlying structure effectively. PCA will still find directions of maximum variance, but these directions may not correspond to meaningful patterns in the data.
   - **Impact**: Reduced effectiveness in capturing the true structure of the data and potential loss of important information.

2. **Variance Assumption**:
   - **Issue**: If the data does not exhibit variance that aligns with the directions PCA identifies, the principal components may not represent the most significant features.
   - **Impact**: The reduced data may not provide a meaningful representation of the original data, leading to poor performance in subsequent analyses.

3. **Mean Centering**:
   - **Issue**: If the data is not mean-centered, the covariance matrix will not be computed correctly. This affects the principal components obtained.
   - **Impact**: The principal components may be biased or incorrect, leading to inaccurate dimensionality reduction and representation.

4. **Orthogonality**:
   - **Issue**: If the principal components are not orthogonal, it indicates multicollinearity or redundant components.
   - **Impact**: The dimensionality reduction might not be as effective, and the components may not capture unique aspects of the variance, leading to potential overfitting or inefficient representation.

### Handling Violations
- **Nonlinearity**: Use nonlinear dimensionality reduction techniques such as Kernel PCA, t-SNE, or UMAP.
- **Variance Issues**: Consider other methods like Independent Component Analysis (ICA) if variance alone does not capture the structure.
- **Mean Centering**: Ensure proper preprocessing to center the data before applying PCA.
- **Orthogonality**: Regularization techniques or methods like Factor Analysis can help in dealing with correlated components.
