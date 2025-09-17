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
&= \theta - \alpha \cdot \frac{1}{2b} \nabla_{\theta} \sum_{i=1}^{b} \left( \hat{y}_i - y_i \right)^2
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
import os
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.ticker import MaxNLocator
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LinearRegression

# 分批数据生成器
def batch_generator(X, Y, batch_size, shuffle=True):
    batch_count = 0
    # 打乱数据
    if shuffle:
        index = np.random.permutation(X.shape[0])
        X = X[index]
        Y = Y[index]
    
    # 分批生成数据
    while True:
        start = batch_count * batch_size
        end = min(start + batch_size, X.shape[0]) # 防止索引越界
        if start >= end:
            break
        yield X[start:end], Y[start:end]
        batch_count += 1

def SGD(X_train, Y_train, X_test, Y_test, num_epochs, batch_size, learning_rate):
    # 数据预处理
    # 添加偏置项
    X_train = np.concatenate([X_train, np.ones((X_train.shape[0],1))],axis=-1)
    X_test = np.concatenate([X_test, np.ones((X_test.shape[0],1))],axis=-1)
    theta = np.random.normal(size=X_train.shape[1]) # 初始化回归系数
    test_losses = []
    
    # 迭代训练
    for epoch in range(num_epochs):
        # 生成分批数据
        batch_g = batch_generator(X_train, Y_train, batch_size)
        
        # 每批数据进行梯度下降
        for X_batch, Y_batch in batch_g:
            grad = (X_batch.T @ (X_batch @ theta - Y_batch)) / batch_size
            theta -= learning_rate * grad
        
        # 计算测试集损失（MSE）
        test_loss = (((X_test @ theta - Y_test).T @ (X_test @ theta - Y_test)) / 2) / X_test.shape[0]
        test_losses.append(test_loss)

    print('回归系数：', theta)
    return theta, test_losses
```
