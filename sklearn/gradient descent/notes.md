# 梯度下降算法

---

## 一、数学原理
### 1. 一般形式（MSE）
$$
\theta = \theta - \alpha \cdot \nabla_{\theta} J\bigl(\theta\bigr)
$$
- 均方误差（MSE）：$\frac{1}{m} \sum_{i=1}^m \left( \hat{y}_i - y_i \right)^2$
- 均方误差（梯度下降）：$J(\boldsymbol{\theta}) = \frac{1}{2m} \sum_{i=1}^m \left( \hat{y}_i - y_i \right)^2$
- $\nabla_{\theta} J\bigl(\theta\bigr)$是损失函数对参数的梯度
- α 是学习率 (learning rate)，控制每一步更新的步长
### 2. 批量、随机、小批量形式
- **批量梯度下降 (BGD)：** 每次用整个训练集计算梯度
$$
\begin{align}
\theta 
&= \theta - \alpha \cdot \frac{1}{2m} \nabla_{\theta} \sum_{i=1}^{m} \left( \hat{y}_i - y_i \right)^2
\end{align}
$$
- **随机梯度下降 (SGD)：** 每次只用一个随机样本
$$
\begin{align}
\theta 
&= \theta - \alpha \cdot \frac{1}{2} \nabla_{\theta} \left( \hat{y}_i - y_i \right)^2
\end{align}
$$
- **小批量梯度下降 (Mini-batch GD)：** 每次用一个小批量样本（大小为 b）
$$
\begin{align}
\theta 
&= \theta - \alpha \cdot \frac{1}{2b} \nabla_{\theta} (\sum_{i=1}^{b} \left( \hat{y}_i - y_i \right)^2)
\end{align}
$$
### 3. 线性回归形式(BGD)
$$
\begin{align}
\theta 
&= \theta - \alpha \cdot \nabla_{\theta} J\bigl(\theta\bigr)\\
&= \theta - \alpha \cdot \frac{1}{2m} \nabla_{\theta} \sum_{i=1}^{m} \left( \hat{y}_i - y_i \right)^2\\
&= \theta - \alpha \cdot \frac{1}{2m} \nabla_{\theta} (\left( X\boldsymbol{\theta} - \mathbf{y} \right)^\top \left( X\boldsymbol{\theta} - \mathbf{y} \right))\\
&= \theta - \alpha \cdot \frac{1}{m} X^\top (X \boldsymbol{\theta} - \mathbf{y})
\end{align}
$$

---

## 二、SGD算法实现
```Python

```
