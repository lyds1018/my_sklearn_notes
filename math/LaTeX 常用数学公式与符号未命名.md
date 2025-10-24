
---

## 一、数学模式基础

| 用法    | 代码                                         | 效果                        |
| :---- | :----------------------------------------- | :------------------------ |
| 行内公式  | `$\alpha + \beta = \gamma$`                | $\alpha + \beta = \gamma$ |
| 独立公式  | `$$E = mc^2$$`                             | $$E = mc^2$$              |
| 带编号公式 | `\begin{equation} E = mc^2 \end{equation}` | （自动编号）                    |

---

## 二、常用符号

| 含义     | 代码                            | 显示                            |
| :----- | :---------------------------- | :---------------------------- |
| 加减乘除   | `+ \ - \times \div`           | $+ \ - \times \div$           |
| 等式与不等式 | `= \neq \approx \sim \le \ge` | $= \neq \approx \sim \le \ge$ |
| 分数     | `\frac{a}{b}`                 | $\frac{a}{b}$                 |
| 根式     | `\sqrt{x} \quad \sqrt[n]{x}`  | $\sqrt{x} \quad \sqrt[n]{x}$  |
| 上下标    | `x_i^2`                       | $x_i^2$                       |
| 括号自动调整 | `\left( \frac{a}{b} \right)`  | $\left( \frac{a}{b} \right)$  |
| 绝对值    | `\|x\|`                       | $\|x\|$                       |
| 范数     | `\quad \|x\|_2`               | $\quad\|x\|_2$                |


---

## 三、希腊字母

| 小写                      |           代码            | 大写        |    代码     |
| :---------------------- | :---------------------: | :-------- | :-------: |
| $\alpha$                |        `\alpha`         | $A$       |    `A`    |
| $\beta$                 |         `\beta`         | $B$       |    `B`    |
| $\gamma$                |        `\gamma`         | $\Gamma$  | `\Gamma`  |
| $\delta$                |        `\delta`         | $\Delta$  | `\Delta`  |
| $\epsilon, \varepsilon$ | `\epsilon, \varepsilon` | $E$       |    `E`    |
| $\theta$                |        `\theta`         | $\Theta$  | `\Theta`  |
| $\lambda$               |        `\lambda`        | $\Lambda$ | `\Lambda` |
| $\mu$                   |          `\mu`          | $M$       |    `M`    |
| $\pi$                   |          `\pi`          | $\Pi$     |   `\Pi`   |
| $\sigma$                |        `\sigma`         | $\Sigma$  | `\Sigma`  |
| $\phi$                  |         `\phi`          | $\Phi$    |  `\Phi`   |
| $\psi$                  |         `\psi`          | $\Psi`    |  `\Psi`   |
| $\omega$                |        `\omega`         | $\Omega$  | `\Omega`  |

---

## 四、集合与逻辑符号

| 含义 | 代码 | 显示 |
|:--|:--|:--|
| 属于 / 不属于 | `\in \notin` | $\in \notin$ |
| 子集 / 真子集 | `\subseteq \subset \supseteq` | $\subseteq \subset \supseteq$ |
| 空集 | `\emptyset` | $\emptyset$ |
| 全集 | `\mathbb{U}` | $\mathbb{U}$ |
| 并 / 交 | `\cup \cap` | $\cup \cap$ |
| 存在 / 对任意 | `\exists \forall` | $\exists \forall$ |
| 且 / 或 / 非 | `\land \lor \neg` | $\land \lor \neg$ |

---

## 五、向量与矩阵

| 含义 | 代码 | 显示 |
|:--|:--|:--|
| 向量 | `\mathbf{x} \quad \vec{x}` | $\mathbf{x} \quad \vec{x}$ |
| 矩阵 | `A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}` | $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$ |
| 单位矩阵 | `I_n` | $I_n$ |
| 零向量 / 零矩阵 | `\mathbf{0}` | $\mathbf{0}$ |
| 转置 | `A^\top` | $A^\top$ |
| 逆矩阵 | `A^{-1}` | $A^{-1}$ |
| 行列式 | `\det(A)` | $\det(A)$ |

---

## 六、微积分符号

| 含义 | 代码 | 显示 |
|:--|:--|:--|
| 导数 | `\frac{dy}{dx}` | $\frac{dy}{dx}$ |
| 偏导 | `\frac{\partial f}{\partial x}` | $\frac{\partial f}{\partial x}$ |
| 梯度 | `\nabla f` | $\nabla f$ |
| 散度 / 旋度 | `\nabla \cdot \mathbf{F}, \ \nabla \times \mathbf{F}` | $\nabla \cdot \mathbf{F}, \ \nabla \times \mathbf{F}$ |
| 积分 | `\int_a^b f(x)\,dx` | $\int_a^b f(x)\,dx$ |
| 二重 / 三重积分 | `\iint, \iiint` | $\iint, \iiint$ |
| 求和 | `\sum_{i=1}^n i^2` | $\sum_{i=1}^n i^2$ |
| 连乘 | `\prod_{i=1}^n a_i` | $\prod_{i=1}^n a_i$ |
| 极限 | `\lim_{x \to 0}` | $\lim_{x \to 0}$ |

---

## 七、概率与统计

| 含义 | 代码 | 显示 |
|:--|:--|:--|
| 概率 | `\Pr(A)` | $\Pr(A)$ |
| 期望 | `\mathbb{E}[X]` | $\mathbb{E}[X]$ |
| 方差 | `\mathrm{Var}(X)` | $\mathrm{Var}(X)$ |
| 协方差 | `\mathrm{Cov}(X,Y)` | $\mathrm{Cov}(X,Y)$ |
| 条件概率 | `P(A \mid B)` | $P(A \mid B)$ |
| 独立 | `A \perp B` | $A \perp B$ |
| 正态分布 | `X \sim \mathcal{N}(\mu, \sigma^2)` | $X \sim \mathcal{N}(\mu, \sigma^2)$ |

---

## 八、常用函数与符号

| 含义 | 代码 | 显示 |
|:--|:--|:--|
| 指数函数 | `e^x` | $e^x$ |
| 对数函数 | `\ln x, \log_a x` | $\ln x, \log_a x$ |
| 三角函数 | `\sin x, \cos x, \tan x` | $\sin x, \cos x, \tan x$ |
| 取整 | `\lfloor x \rfloor, \lceil x \rceil` | $\lfloor x \rfloor, \lceil x \rceil$ |
| 向量范数 | `\|x\|_2` | $\|x\|_2$ |
| Kronecker delta | `\delta_{ij}` | $\delta_{ij}$ |
| Dirac delta | `\delta(x)` | $\delta(x)$ |

---

## 九、排版技巧

| 用法 | 代码 | 示例 |
|:--|:--|:--|
| 省略号 | `\ldots, \cdots` | $a_1, a_2, \ldots, a_n$ |
| 对齐公式 | `\begin{align} ... \end{align}` | 多行公式对齐 |
| 分段函数 | `\begin{cases} ... \end{cases}` | $\begin{cases} x, & x>0 \\ 0, & x\le0 \end{cases}$ |
| 注释 | `\text{...}` | $\text{说明文字}$ |
| 粗体符号 | `\boldsymbol{x}` | $\boldsymbol{x}$ |
