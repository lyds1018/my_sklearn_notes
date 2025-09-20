# 逻辑斯蒂二分类

## 一、数学原理
### 1. 逻辑斯蒂函数（logistic function）
$$
\begin{aligned}
\sigma(z) &= \frac{1}{1+e^{-z}} \\[6pt]
\frac{d\sigma}{dz}
&= \frac{1}{1+e^{-z}} \left(1-\frac{1}{1+e^{-z}}\right)\\
&= \sigma(z)\big(1-\sigma(z)\big).
\end{aligned}
$$
![logistic function](img.PNG)
### 2. 模型预测正确率

- 似然函数：
$$
\begin{aligned}
L(\theta) 
& = 
\begin{cases}
f_\theta(x_i), & \text{if } y_i = 1 \\[6pt]
1 - f_\theta(x_i), & \text{if } y_i = 0
\end{cases}\\
&= \prod_{i=1}^m \big[f_\theta(x_i)\big]^{y_i} \, \big[1 - f_\theta(x_i)\big]^{\,1-y_i}
\end{aligned}
$$
- 对数似然函数：
$$
\ell(\theta) = \sum_{i=1}^m \Big( y_i \log f_\theta(x_i) + (1-y_i)\log\big(1 - f_\theta(x_i)\big) \Big)
$$
- 梯度计算：
$$
\begin{aligned}
\frac{\partial \ell(\theta)}{\partial \theta}
&= \sum_{i=1}^m \left[ y_i \frac{1}{f_\theta(x_i)} \frac{\partial f_\theta(x_i)}{\partial \theta}
+ (1-y_i)\frac{1}{1-f_\theta(x_i)} \left(-\frac{\partial f_\theta(x_i)}{\partial \theta}\right) \right] \\
&= \sum_{i=1}^m \left[ \left(\frac{y_i}{f_\theta(x_i)} - \frac{1-y_i}{1-f_\theta(x_i)}\right)
\frac{\partial f_\theta(x_i)}{\partial \theta} \right]
\end{aligned}
$$
### 3. 线性回归形式
- 映射形式：
$$
\begin{aligned}
f_\theta(x_i) 
&= \sigma(\theta^\top x_i)\\
&= \frac{1}{1 + e^{-\theta^\top x_i}}
\end{aligned}
$$
- 梯度计算：
$$
\begin{aligned}
\frac{\partial f_\theta(x_i)}{\partial \theta}
&= \frac{\partial}{\partial \theta}\,\sigma(\theta^\top x_i)\\
&= \sigma(\theta^\top x_i)\,\big(1-\sigma(\theta^\top x_i)\big)\,x_i
\end{aligned}
$$
$$
\begin{aligned}
\frac{\partial \ell(\theta)}{\partial \theta}
&= \sum_{i=1}^m \big(y_i - \sigma(\theta^\top x_i)\big)\, x_i\\
&= X^\top \big(y - \sigma(X\theta)\big)
\end{aligned}
$$
- 损失函数：
$$
J(\theta) = -\ell(\theta)
$$
$$
\nabla_\theta J(\theta) = - \nabla_\theta \ell(\theta)\\
$$
- 梯度下降：
$$
\begin{aligned}
\theta 
&= \theta - \alpha \, \nabla_\theta J(\theta)\\
&= \theta + \alpha \, \nabla_\theta \ell(\theta)\\
&= \theta + \alpha \, \sum_{i=1}^m \big(y_i - \sigma(\theta^\top x_i)\big)\, x_i\\
&= \theta + \alpha \, X^\top \big(y - \sigma(X\theta)\big)
\end{aligned}
$$
- L2正则化约束
$$
J(\theta) = -\ell(\theta) + \frac{\lambda}{2} \|\theta\|_2^2\\
$$
$$
\nabla_{\theta} J(\theta) = - X^\top (y - \sigma(X\theta)\big) + \lambda \theta
$$
$$
\begin{aligned}
\theta 
&= \theta - \alpha \, \nabla_\theta J(\theta)\\
&= (1- \lambda \alpha) \theta + \alpha X^\top (y - \sigma(X\theta)\big)
\end{aligned}
$$
## 二、