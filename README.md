# Financial-Mathemathics
## Portfolio Risk Analysis

Assume four financial assets with values (per dollar) in 10 years as random variables $(X_1, X_2, X_3, X_4)$. Their **means** are \(200, 150, 80, 70\), **standard deviations** are \(30, 25, 10, 15\), and the **correlation matrix** is:

$$
R = \begin{pmatrix}
1.0 & 0.8 & -0.2 & 0.0 \\
0.8 & 1.0 & 0.0 & -0.5 \\
-0.2 & 0.0 & 1.0 & 0.3 \\
0.0 & -0.5 & 0.3 & 1.0
\end{pmatrix}
$$

**Portfolios** (investing \$1000 today):  
1. P1 = \(500, 200, 200, 100\)  
2. P2 = \(300, 300, 200, 200\)  
3. P3 = \(0, 700, 150, 150\)  
4. P4 = \(250, 250, 250, 250\)  

**Tasks**:  
1. Explain the mathematical background of computations and explain what rules of probability that can be applied and how (make sure to mention arguments for both the expected value as well as the standard deviations of the portfolios). 

2. Compute the expected values and standard deviations of each portfolio after 10 years using Python (with only imports from `numpy`) and give a recommendation in a markdown cell on what portfolio a conservative investor should choose. 

---

### **Financial Asset**

We have four financial assets, and their values (per dollar) in 10 years from today are the random variables $(X_1, X_2, X_3, X_4)$.

For computational convenience, we rearrange the asset value, the expected value, and standard deviation per dollar invested into matrix format as follows:

**Asset value:**

$$
X = \begin{pmatrix}
X_1 \\
X_2 \\
X_3 \\
X_4 \\
\end{pmatrix}
$$

**Expected value or mean $\mu$ vector:**

$$
\mu_{X} = \begin{pmatrix}
120 \\
150 \\
80 \\
70 \\
\end{pmatrix}
$$

**Standard deviation $\sigma_{X}$ matrix:**
The standard deviation is arranged into a diagonal matrix to facilitate the computation process in the later part.
$$
\sigma_{X} = 
\begin{pmatrix}
30 & 0.0 & 0.0 & 0.0 \\
0.0 & 25 & 0.0 & 0.0 \\
0.0 & 0.0 & 10 & 0.0 \\
0.0 & 0.0 & 0.0 & 15\\
\end{pmatrix}
$$

**Correlation matrix:**
The correlation matrix between the variables is given as:

$$
R = \begin{pmatrix}
1.0 & 0.8 & -0.2 & 0.0 \\
0.8 & 1.0 & 0.0 & -0.5 \\
-0.2 & 0.0 & 1.0 & 0.3 \\
0.0 & -0.5 & 0.3 & 1.0
\end{pmatrix}
$$

where the entry $(R_{i,j})$ corresponds to $\left(\rho(X_i,X_j) = \frac{Cov(X_i,X_j)}{Std(X_i)Std(X_j)}\right)$.

---

### **Portfolios' Scenario**

Now we consider the following four investment portfolios:

+ **P1**: Investing 500 into asset 1, 200 into asset 2, 200 into asset 3, and 100 into asset 4.
+ **P2**: 300, 300, 200, 200.
+ **P3**: 0, 700, 150, 150.
+ **P4**: 250, 250, 250, 250.

For simplicity, we arrange the four investment portfolios in a matrix format, where portfolios are rows and assets are columns:

$$
A =
\begin{pmatrix}
500 & 200 & 200 & 100 \\
300 & 300 & 200 & 200 \\
0 & 700 & 150 & 150 \\
250 & 250 & 250 & 250 \\
\end{pmatrix}
$$

---

To recommend the conservative option, we need to derive the **expected return** and **standard deviation** for each portfolio. This involves the following steps:


#### 1. **Expected Return of Each Portfolio**
The expected return of a portfolio is a measure of the average return we can expect from the portfolio based on the returns of its constituent assets.


#### 2. **Standard Deviation of Each Portfolio**
The standard deviation of a portfolio measures the volatility or risk associated with the portfolio's returns. A lower standard deviation indicates a more conservative (less risky) portfolio.


### **Mathematical Framework**

Before performing the computations, we need to define the following matrices in linear algebra terms:

#### **Portfolio Return Matrix ($P$)**
The return of the portfolio matrix $P$ can be derived as the dot product of the portfolio allocation matrix $A$ and the asset return matrix $X$:

$$
P = A \cdot X
$$

Here:
- $A$ is the portfolio allocation matrix, where each row represents a portfolio and each column represents the allocation to a specific asset.
- $X$ is the asset return matrix, where each row represents the returns of the assets.


##### **Expected Return Matrix ($\mu_{P}$)**
The expected return matrix $\mu_{P}$ contains the expected returns of each portfolio. It is a column vector where each entry $\mu_{p_{i}}$ represents the expected return of portfolio $i$:

$$
\mu_{P} = \begin{pmatrix}
\mu_{p_{1}} \\
\mu_{p_{2}} \\
\mu_{p_{3}} \\
\mu_{p_{4}} \\
\end{pmatrix}
$$


##### **Standard Deviation Matrix ($\sigma_{P}$)**
The standard deviation matrix $\sigma_{P}$ is a diagonal matrix where each diagonal entry $\sigma_{p_{i}}$ represents the standard deviation of the return of portfolio $i$. Off-diagonal entries are zero, as the standard deviation is specific to each portfolio and does not directly depend on other portfolios:

$$
\sigma_{P} = \begin{pmatrix}
\sigma_{p_{1}} & 0 & 0 & 0 \\
0 & \sigma_{p_{2}} & 0 & 0 \\
0 & 0 & \sigma_{p_{3}} & 0 \\
0 & 0 & 0 & \sigma_{p_{4}} \\
\end{pmatrix}
$$


### **Next Steps**
1. Compute the portfolio return matrix $P = A \cdot X$.
2. Derive the expected return matrix $\mu_{P}$ from $P$.
3. Calculate the standard deviation matrix $\sigma_{P}$ from $P$.

These computations will allow us to identify the most conservative portfolio based on the lowest standard deviation and an acceptable expected return.

**1. Expected Return of Each Portfolio**

Mathematically. it is simply a dot product of portfolios allocation matrix $(A)$ with expected value $(\mu)$  (per dollar) that each asset will yeild in the next 20 years. 

$$
\mu_{P} = A\cdot\mu_{X} = 
\begin{pmatrix}
500 & 200 & 200 & 100 \\
300 & 300 & 200 & 200 \\
0 & 700 & 150 & 150 \\
250 & 250 & 250 & 250 \\
\end{pmatrix}
\begin{pmatrix}
120 \\
150 \\
80 \\
70 \\
\end{pmatrix}
=\begin{pmatrix} 113000 \\ 111000 \\ 127500 \\ 105000 \end{pmatrix}
$$

**2. Standard Deviation of Each Portfolio**

In theory, we can derive $\sigma_P$ from the covariance matrix $Cov(P)$. The standard deviation matrix $\sigma_P$ is a diagonal matrix where each diagonal entry is the square root of the variance of portfolio $p_i$, given by:  

$$
Var(p_i) = Cov(p_i, p_i), \quad \text{for } i \in \{1, 2, 3, 4\}
$$

Thus, the covariance matrix of the portfolio is:  

$$
Cov(P) =
\begin{pmatrix}
Cov(p_1, p_1) & Cov(p_1, p_2) & Cov(p_1, p_3) & Cov(p_1, p_4) \\
Cov(p_2, p_1) & Cov(p_2, p_2) & Cov(p_2, p_3) & Cov(p_2, p_4) \\
Cov(p_3, p_1) & Cov(p_3, p_2) & Cov(p_3, p_3) & Cov(p_3, p_4) \\
Cov(p_4, p_1) & Cov(p_4, p_2) & Cov(p_4, p_3) & Cov(p_4, p_4) \\
\end{pmatrix}
$$

From this, we can construct the standard deviation matrix $\sigma_P$:  

$$
\sigma_P =
\begin{pmatrix}
\sqrt{Var(p_1)} & 0 & 0 & 0 \\
0 & \sqrt{Var(p_2)} & 0 & 0 \\
0 & 0 & \sqrt{Var(p_3)} & 0 \\
0 & 0 & 0 & \sqrt{Var(p_4)} \\
\end{pmatrix}
\quad (*)
$$

---

### Deriving $ Cov(P) $ 

We can compute $ Cov(P) $ using the following matrix transformation:  

$$
Cov(P) = Cov(A \cdot X)
$$

Expanding using expectation properties:  

$$
Cov(P) = \mathbb{E}[(AX - \mathbb{E}[AX])(AX - \mathbb{E}[AX])^T]
$$

$$
= \mathbb{E}[A (X - \mathbb{E}[X])(X - \mathbb{E}[X])^T A^T]
$$

$$
= A \cdot \mathbb{E}[(X - \mathbb{E}[X])(X - \mathbb{E}[X])^T] \cdot A^T
$$

Since the expectation term represents the covariance of $ X $, we substitute $ Cov(X) $:  

$$
Cov(P) = A \cdot Cov(X) \cdot A^T \quad (**)
$$

---

### Computing $Cov(X)$ from the Correlation Matrix  

To compute the covariance matrix of the assets $ Cov(X) $, we first use the correlation matrix $ R $. The relationship between correlation and covariance is given by:  

$$
\rho(X_i, X_j) = \frac{Cov(X_i, X_j)}{Std(X_i) Std(X_j)}
$$
Rearranging, we get:  

$$
Cov(X_i, X_j) = Std(X_i) \cdot Std(X_j) \cdot \rho(X_i, X_j)
$$

Thus, we can construct the covariance matrix \( Cov(X) \) as:  

$$
Cov(X) = \sigma_X \cdot R \cdot \sigma_X
$$

where $ \sigma_X $ is the diagonal matrix containing the standard deviations of the individual assets.

$$\Rightarrow Cov(X) = \begin{pmatrix}
30 & 0.0 & 0.0 & 0.0 \\
0.0 & 25 & 0.0 & 0.0 \\
0.0 & 0.0 & 10 & 0.0 \\
0.0 & 0.0 & 0.0 & 15\\
\end{pmatrix}
\cdot 
\begin{pmatrix}
1.0 & 0.8 & -0.2 & 0.0 \\
0.8 & 1.0 & 0.0 & -0.5 \\
-0.2 & 0.0 & 1.0 & 0.3 \\
0.0 & -0.5 & 0.3 & 1.0
\end{pmatrix}
\cdot 
\begin{pmatrix}
30 & 0.0 & 0.0 & 0.0 \\
0.0 & 25 & 0.0 & 0.0 \\
0.0 & 0.0 & 10 & 0.0 \\
0.0 & 0.0 & 0.0 & 15\\
\end{pmatrix} 
$$

Computing the result:

$$
Cov(X) =
\begin{pmatrix}
900 & 600 & -60 & 0 \\
600 & 625 & 0 & -187.5 \\
-60 & 0 & 100 & 45 \\
0 & -187.5 & 45 & 225
\end{pmatrix}
$$

We will now culculate $Cov(P)$, using relationship $(**)$ above:
