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