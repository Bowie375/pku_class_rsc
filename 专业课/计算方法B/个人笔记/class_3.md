# 非线性方程组
---
## 迭代法
* 基本思路：
    * 考虑迭代函数:\[G: \mathbb{R^n} \to \mathbb{R^n} \newline \vec{x}=(x_1,x_2,\dots,x_n) \to (g_1(\vec{x}),g_2(\vec{x}),\dots,g_n(\vec{x}))\]    
    * 满足自身映射、连续函数，则可保证存在不动点；
    * 满足对每个自变量的偏导数小于 $k/n\space (k
    <1)$ ,即有不动点唯一且可以区间内任意一点为起始点进行迭代。
* 重要结论：n 次迭代后，有：\[\Vert \vec{x}_n-p\Vert< \frac{k^n}{1-k}\|\vec{x}_1-\vec{x}_0  \|\]
## 牛顿法
* 基本思路：
    * 试图找出矩阵 $A$ 使得:\[G(\vec{x})=\vec{x} -A(f_1(\vec{x}),\dots,f_n(\vec{x}))^T\]对 $\vec{x}$ 的一阶偏导数为0。
    * 直接暴力计算得知: \[A=J^{-1}(x)\]
* 是否可以避免求解 $A^{-1}$ 以减少计算量？（类似非线性方程的割线法）
    * Broyden 方法：
    \[A_i=A_{i-1}+\frac{y_i-A_{i-1}s_{i} }{||s_i||_2^2}s_i^t\] 其中：\[y_i=F(\vec x^{(i)})-F(\vec x^{(i-1)}),\;\;s_i=\vec{x}^{(i)}-\vec{x}^{(i-1)},\;\;A_i=A(\vec x^{(i)}) \]
    * Shermon-Morrison 公式：\[(A+xy^t)^{-1}=A^{-1}-\frac{A^{-1}xy^tA^{-1} }{1+y^tA^{-1}x} \] 于是：\[A_i^{-1}=A_{i-1}^{-1}+\frac{(s_i-A^{-1}_{i-1}y_i)s^t_iA^{-1}_{i-1} }{s_i^tA^{-1}_{i-1}y_i } \]
## 梯度下降法
* 基本思路：将求解的过程转换为求解多元函数极值的问题。
* 重要过程：
令：
\[G(\vec{x})=\sum_{i=1}^{n}f_i^{2}(\vec{x})\]
求该函数的极小值：
\[\vec{x}_{n+1}=\vec{x}_n-\alpha\nabla G(\vec{x}_n)\]
如何选择合适的步长 $\alpha$ ?
    * 牛顿插值法: 选取 $\alpha_1<\alpha_2<\alpha_3$ , 其中 $\alpha_2=\frac{\alpha_1+\alpha_3}{2}$ , $G(\vec{x}_n,\alpha_3)<G(\vec{x}_n,\alpha_1)$ , 构造二阶插值多项式，并求导求出最佳的 $\alpha$ 。
    * 泰勒展开：将函数在 $\vec{x}_n$处展开：
\[G(\vec{x}_n+\Delta \vec{x})-G(\vec{x}_n)=\nabla G(\vec{x}_n)^T\cdot \Delta \vec{x}+ \frac{1}{2}\Delta \vec{x}^T\cdot H(\vec{x}_n)\cdot \Delta \vec{x}\]
对 $\Delta \vec{x}$ 求导求出最佳变化量：
\[\Delta \vec{x}=-H^{-1}(\vec{x}_n)\nabla G(\vec{x}_n)\]
__Note__ ：当 $H(\vec{x}_n)$ 近似为奇异矩阵时，会出现步长很大的情况，这时可以考虑加上抑制因子：\[\Delta \vec{x}=-\gamma H^{-1}(\vec{x}_n)\nabla G(\vec{x}_n)\] 其中 $\gamma$ 的选取方式和之前在最速下降法中求 $\alpha$ 的方式基本一致。


## 同伦延拓法
* 基本思想：\[G:[0,1]\times \mathbb{R^n}\to \mathbb{R^n}
\newline G(\lambda,X)=\lambda F(X)+(1-\lambda)(F(X)-F(X(0))) \]当 $\lambda$ 为 0 时，零点为初值，当 $\lambda$ 为 1 时，零点为所求向量。将解 $X$ 的过程转换为求解函数 $X(\lambda)$ 的过程。
* 重要过程：
对 $\lambda$ 求导：
\[\frac{dF}{dX}\cdot X^{'}(\lambda)+F(X(0))=0\]
即：
\[X^{'}(\lambda)=-J^{-1}(X)F(X(0))\]
剩下只需求解这个微分方程即可。（Runge-Kutta）