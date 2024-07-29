

```mehrmaid
graph TD
    A[Data Matrix X] --> B[Mean Centering]
    B[Mean Centering] --> C["Centered Data <br> $$\bar{X} = X - \frac{1}{n} \mathbf{1} \mathbf{1}^T X$$"]
    C --> D[Covariance Matrix S]
    D["Covariance Matrix <br> $$S = \frac{1}{n} \bar{X}^T \bar{X}$$"] --> E[Eigenvalue Decomposition]
    E["Eigenvalue Decomposition <br> $$S \mathbf{w}_i = \lambda_i \mathbf{w}_i$$"] --> F[Principal Components]
    F["Select top $k$ eigenvectors $$W = [\mathbf{w}_1, \mathbf{w}_2, \ldots, \mathbf{w}_k]$$"] --> G[Projection onto Principal Components]
    G["Projected Data $$Z = \bar{X} W$$"]
```

```ad-important
Mermaid *does not* natively support mathematical equations. However, it can be arranged. For Mathematical equations to show up in the Mermaid plot, do install ==`mehrmaid`== extension along with ==`mermaid`==.

Ref: [Forum discussion link](https://forum.obsidian.md/t/mermaid-diagrams-why-isnt-simple-math-rendering/85605)
```


This diagram sequentially illustrates the key steps in PCA:
1. **Data Matrix $X$**: Start with the original data matrix $X$ of dimensions $n \times p$. 
2. **Mean Centering**: Subtract the mean of each feature to center the data.
3. **Centered Data $\bar{X}$**: Resulting centered data matrix.
4. **Covariance Matrix $S$**: Compute the covariance matrix $S$ of the centered data.
5. **Eigenvalue Decomposition**: Perform eigenvalue decomposition on the covariance matrix $S$ to find the eigenvalues $\lambda_i$​ and eigenvectors $\mathbf{w}_i$.
6. **Principal Components**: Select the top $k$ eigenvectors corresponding to the largest eigenvalues to form the projection matrix $W$.
7. **Projection onto Principal Components**: Project the centered data $\bar{X}$ onto the principal components to obtain the transformed data $Z$.


## Steps in detail

1. **Data Matrix**:
   Given a data matrix $X \in \mathbb{R}^{n \times p}$, where $n$ is the number of samples and $p$ is the number of features.

2. **Mean Centering**:
   Center the data by subtracting the mean of each feature:       
   $$\bar{X} = X - \frac{1}{n} \mathbf{1} \mathbf{1}^T X$$   
   where $\mathbf{1} \in \mathbb{R}^n$ is a vector of ones.

3. **Covariance Matrix**:
   Compute the covariance matrix $S \in \mathbb{R}^{p \times p}$ of the centered data:
   $$
   S = \frac{1}{n} \bar{X}^T \bar{X}
   $$

4. **Eigenvalue Decomposition**:
   Perform eigenvalue decomposition of the covariance matrix $S$:
   $$S \mathbf{w}_i = \lambda_i \mathbf{w}_i \quad \text{for} \quad i = 1, 2, \ldots, p$$
   
   where $\mathbf{w}_i \in \mathbb{R}^p$ are the eigenvectors and $\lambda_i \in \mathbb{R}$ are the corresponding eigenvalues.

5. **Principal Components**:
   The principal components are the eigenvectors $\mathbf{w}_i$ corresponding to the largest eigenvalues $\lambda_i$. Arrange the eigenvalues in descending order:
   $$
   \lambda_1 \ge \lambda_2 \ge \cdots \ge \lambda_p
   $$
   Select the top $k$ eigenvectors $\mathbf{w}_1, \mathbf{w}_2, \ldots, \mathbf{w}_k$ to form the projection matrix $W$:
   $$
   W = [\mathbf{w}_1 \; \mathbf{w}_2 \; \ldots \; \mathbf{w}_k]
   $$

6. **Projection onto Principal Components**:
   Project the centered data $\bar{X}$ onto the principal components:
   $$
   Z = \bar{X} W
   $$
   where $Z \in \mathbb{R}^{n \times k}$ is the transformed data in the new $k$-dimensional space.

These mathematical equations outline the steps involved in PCA, from centering the data and computing the covariance matrix to performing eigenvalue decomposition and projecting the data onto the principal components.


---

## Mean centering

$$\bar{X} = X - \mathbf{1} \mu^T$$

Where:
- $\bar{X}$ is the centered data matrix.
- $X$ is the original data matrix of size $n \times p$.
- $\mathbf{1}$ is a column vector of ones of length $n$.
- $\mu$ is the mean vector of each feature (of length $p$).
- $\mu^T$ is the transpose of the mean vector, making it a row vector.

In detailed steps:
1. Compute the mean vector $\mu$:
   $$\mu = \frac{1}{n} \sum_{i=1}^{n} X_i$$
   
   where $X_i$ is the $i$-th row of the matrix $X$.

2. Center the data by subtracting the mean vector from each row of $X$:
   $$\bar{X} = X - \mathbf{1} \mu^T$$

   where $\mathbf{1} \mu^T$ replicates the mean vector $\mu$ across all $n$ rows of $X$.

In summary, the correct mean centering formula is:
$$\bar{X} = X - \mathbf{1} \mu^T$$

where $\mu^T$ ensures that the mean vector is subtracted from each row of the data matrix.



#### Miscellaneous
![Principal Component Analysis second principal](https://builtin.com/sites/www.builtin.com/files/inline-images/national/Principal%2520Component%2520Analysis%2520second%2520principal.gif)
