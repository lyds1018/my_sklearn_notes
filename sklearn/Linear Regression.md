# 线性回归解析算法

---

## 一、映射形式与算法目标
### 1. 映射形式
$$
\hat{y}_i = \boldsymbol{\theta}^\top \mathbf{x}_i = \mathbf{x}_i^\top\boldsymbol{\theta}
$$
- $\boldsymbol{\theta} = \begin{bmatrix} \mathbf{w} \\ b \end{bmatrix}$ , $\quad\mathbf{x}_i = \begin{bmatrix} \mathbf{x}_i \\ 1 \end{bmatrix}$ 
### 2. 损失函数(MSE)
$$
\begin{align}
J(\boldsymbol{\theta}) 
&= \frac{1}{2m} \sum_{i=1}^m \left( \hat{y}_i - y_i \right)^2\\
&= \frac{1}{2m} \, \lVert X \boldsymbol{\theta} - \mathbf{y} \rVert_2^2\\
&= \frac{1}{2m} \left( X\boldsymbol{\theta} - \mathbf{y} \right)^\top \left( X\boldsymbol{\theta} - \mathbf{y} \right)\\
\end{align}
$$
- $X = \begin{bmatrix}\mathbf{x}_1^\top \\\mathbf{x}_2^\top \\\vdots \\\mathbf{x}_m^\top\end{bmatrix}$, $\mathbf{y} = \begin{bmatrix}y_1 \\y_2 \\\vdots \\y_m\end{bmatrix}$
### 3. 解析方法推导
$$
\nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}) 
= \frac{1}{m} X^\top (X \boldsymbol{\theta} - \mathbf{y}) = 0
$$
$$
X^\top X \boldsymbol{\theta} = X^\top \mathbf{y}
$$
$$
\boldsymbol{\theta} = (X^\top X)^{-1} X^\top \mathbf{y}
$$
## 二、算法实现
```python
import numpy as np
```