
# 1. 类别概率

定义每个类别的得分 (logit)：

$$
z_i = \theta_i^\top x, \quad i = 1,2,\dots,K
$$

Softmax 定义为：

$$
\sigma(z)_i = \frac{e^{z_i}}{\sum_{j=1}^K e^{z_j}}, \quad i=1,2,\dots,K
$$

类别预测准确率为：

$$
P(y=i \mid x; \Theta) = \sigma(z)_i = \frac{e^{z_i}}{\sum_{j=1}^K e^{z_j}} 
= \frac{e^{\theta_i^\top x}}{\sum_{j=1}^K e^{\theta_j^\top x}}.
$$
指示函数形式的准确率：
$$
P(y \mid x; \Theta) = \prod_{k=1}^K \big( \sigma(z)_k \big)^{\mathbf{1}\{y = k\}}
$$
- 指示函数 ${\mathbf{1}\{y = k\}}$：当真实标签 $y_i = k$ 时，返回1
- 因此第k类概率指数为1，其他类概率指数为 0

---

# 2. 似然函数 (Likelihood)

给定训练数据 $\{(x^{(i)}, y^{(i)})\}_{i=1}^m$：

$$
L(\Theta) = \prod_{i=1}^m P(y^{(i)} \mid x^{(i)}; \Theta) 
= \prod_{i=1}^m \prod_{k=1}^K \Big(\sigma(z^{(i)})_k\Big)^{\mathbf{1}\{y^{(i)}=k\}}
$$

展开后：

$$
= \prod_{i=1}^m \prod_{k=1}^K 
\left(\frac{e^{\theta_k^\top x^{(i)}}}{\sum_{j=1}^K e^{\theta_j^\top x^{(i)}}}\right)^{\mathbf{1}\{y^{(i)}=k\}}.
$$

---

# 3. 对数似然 (Log-likelihood)

$$
\begin{align}
\ell(\Theta) 
&= \sum_{i=1}^m \sum_{k=1}^K \mathbf{1}\{y^{(i)}=k\} \, \log \sigma(z^{(i)})_k\\
&= \sum_{i=1}^m \sum_{k=1}^K \mathbf{1}\{y^{(i)}=k\} \, 
\log \left( \frac{e^{\theta_k^\top x^{(i)}}}{\sum_{j=1}^K e^{\theta_j^\top x^{(i)}}} \right)
\end{align}
$$

---

# 4. 损失函数（交叉熵）

负对数似然：

$$
\begin{align}
J(\Theta) 
&= - \ell(\Theta) \\
&= - \sum_{i=1}^m \sum_{k=1}^K \mathbf{1}\{y^{(i)}=k\} \, \log \sigma(z^{(i)})_k \\
&= - \sum_{i=1}^m \sum_{k=1}^K 
\mathbf{1}\{y^{(i)}=k\} \, 
\log \left( \frac{e^{\theta_k^\top x^{(i)}}}{\sum_{j=1}^K e^{\theta_j^\top x^{(i)}}} \right)
\end{align}
$$

---

# 5. 梯度

对每个 $\theta_k$：

$$
\begin{align}
\nabla_{\theta_k} J(\Theta) 
&= \sum_{i=1}^m \Big( \sigma(z^{(i)})_k - \mathbf{1}\{y^{(i)}=k\} \Big) x^{(i)} \\
&= \sum_{i=1}^m \Bigg( 
\frac{e^{\theta_k^\top x^{(i)}}}{\sum_{j=1}^K e^{\theta_j^\top x^{(i)}}}
- \mathbf{1}\{y^{(i)}=k\}
\Bigg) x^{(i)}
\end{align}
$$

