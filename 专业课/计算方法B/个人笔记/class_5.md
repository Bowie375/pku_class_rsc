# 多项式近似
---
## 离散最小二乘近似
* 基本思想：
最小化 \[S=\sum_{i=0}^n (y_i-\sum_{k=0}^m (a_k x_i^k))^2\] 只需让 ${\partial S}/{\partial a_i}=0,\quad i=0,1, \ldots ,m$ 其中 $m<n-1$，于是：\[\sum_{k=0}^m a_k \sum_{i=0}^n x_i^{k+j}=\sum_{i=0}^n y_i x_i^{j}\] 其中 $j=0,1, \ldots ,m$ 写成矩阵形式即为：
\[
    \begin{equation} \notag
        \left[
            \begin{array}{cccc}
               \sum_{i=0}^n x_i^0 & \sum_{i=0}^n x_i^1 & \cdots & \sum_{i=0}^n x_i^m\\
               \sum_{i=0}^n x_i^1 & \sum_{i=0}^n x_i^2 & \cdots & \sum_{i=0}^n x_i^{m+1}\\
               \vdots \\
               \sum_{i= 0}^n x_i^m & \sum_{i=0}^n x_i^{m+1} & \cdots & \sum_{i=0}^{n} x_i^{2m}
            \end{array}
        \right]
        \left[
            \begin{array}{c}
                a_0 \\ a_1 \\ \vdots \\a_m
            \end{array}
        \right]
        =
        \left[
            \begin{array}{c}
                \sum_{i=0}^n y_ix_i^0 \\ 
                \sum_{i=0}^n y_ix_i^1 \\ 
                \vdots \\
                \sum_{i=0}^n y_ix_i^m
            \end{array}
        \right]
    \end{equation}
\]
## 连续最小二乘近似
* 基本思想：
最小化 \[S=\int_a^b (f(x)-\sum_{k=0}^m (a_k x^k))^2 dx\] 只需让 ${\partial S}/{\partial a_i}=0,\quad i=0,1, \ldots ,m$ 其中 $m<n-1$，于是：\[\sum_{k=0}^m a_k \int_a ^bx_i^{k+j}=\int_a^b f(x) x^{j}\] 其中 $j=0,1, \ldots ,n$ 写成矩阵形式即为：
\[
    \begin{equation} \notag
        \left[
            \begin{array}{cccc}
               \int_a^b x_i^0 & \int_a^b x_i^1 & \cdots & \int_a^b x_i^m\\
               \int_a^b x_i^1 & \int_a^b x_i^2 & \cdots & \int_a^b x_i^{m+1}\\
               \vdots \\
               \int_a^b x_i^m & \int_a^b x_i^{m+1} & \cdots & \int_a^b x_i^{2m}
            \end{array}
        \right]
        \left[
            \begin{array}{c}
                a_0 \\ a_1 \\ \vdots \\a_m
            \end{array}
        \right]
        =
        \left[
            \begin{array}{c}
                \int_a^b y_ix_i^0 \\ 
                \int_a^b y_ix_i^1 \\ 
                \vdots \\
                \int_a^b y_ix_i^m
            \end{array}
        \right]
    \end{equation}
\]
* 问题：方程条件差，难以求解
## 正交多项式基线性组合拟合函数
* 基本思想：考虑一组 n 阶多项式基 $\{\phi_0,\phi_1, \ldots ,\phi_n\}$ 其中 $\phi_i$ 为 i 阶多项式，则任何一个阶数小于等于 n 的多项式均可由这组多项式线性表出。 于是我们要求的多项式可以写成 $P_n(x)=\sum_0^n a_i\phi_i$ ，设权重函数为 $w(x)$，问题转换为求解\[S=\int_a^b w(x)(f(x)-\sum a_i\phi_i)^2 dx\] 的最小值。同样对 $a_i$ 求导可知:\[\sum_{i=1}^m a_i\int_a^b w(x)\phi_i\phi_j dx=\int_a^b w(x)f(x)\phi_j dx\quad \forall j\in \{0,1, \ldots ,m\}\] 如果 $\phi_i$ 满足：
\[\int_a^b w(x)\phi_i\phi_j=
    \left\{
        \begin{array}{l}    
            \int_a^b w(x)\phi_i^2 \quad i=j\\
            0\quad i\neq j
        \end{array}
    \right.
\] 则 $a_i$ 可表达为：
\[\frac{\int_a^b w(x)f(x)\phi_i dx}{\int_a^b w(x)\phi_i^2 dx}\]
* Note: \[w(x)\ge0,\;\forall x\in D\;\text{but}\;w(x) \not\equiv 0\]
## 如何获取一组正交基函数
* 基本思想：Gram-Schmidt 正交化：确定 $\phi_0$ 后，在所有阶数小于等于 n 的多项式组成的线性空间中，定义 $\phi_i,\phi_j$ 的内积为：\[\langle\phi_i,\phi_j\rangle =\int_a^b w(x)\phi_i\phi_j dx\] 有递归方程：\[\phi_n=x\phi_{n-1}-\frac{\langle x\phi_{n-1},\phi_{n-1}\rangle}{\langle \phi_{n-1},\phi_{n-1}\rangle}\phi_{n-1}-\frac{\langle x\phi_{n-1},\phi_{n-2}\rangle }{\langle\phi_{n-2},\phi_{n-2}\rangle}\phi_{n-2}\]则 $\phi_0,\phi_1, \ldots ,\phi_n $ 为一组正交基函数。
## 几组特殊的基函数
* Legendre polynomials
    * 权函数:\[w(x)=1\]
    * $\phi_0=1$
    * 性质：
        * 所有高于 0 阶的多项式在 $[-1,1]$ 上的积分恒等于 0 。
* Chebyshev Polynomials
    * 权函数:\[w(x)=\frac{1}{\sqrt{1-x^2}}\]
    * 表达式:\[T_n(x) = \cos[n \arccos x] ,\;\;\; \widetilde{T}_n(x) = \frac{T_n(x)}{2^{n-1}}\]
    * 满足递推关系：
        \[T(n+1) = 2xT(n) - T(n-1)\]
    * 具有性质:
        \[max(\widetilde{T}_n(x)) \le max(P_n(x)),\;\;\forall P_n(x)\;\text{whose factor of}\;x^n\;\text{is 1}\]
    * 应用：
        * 求出让 lagrange 插值多项式余项的最坏估计最小的插值点。（就是 $T_n(x)$ 的根）
        * 在引入的误差限最小的情况下，降低多项式的阶数。（不断减去与最高阶项相符的 $T_n(x)$ ）
## 最小二乘法三角多项式逼近
* 连续情形：
    * 用\[S_n(x)=\frac{1}{2}a_0+a_n\cos(nx)+\sum_{k=1}^{n-1}(a_k\cos(kx)+b_k\sin(kx))\]逼近所求的函数
    * 和前面讨论的基函数的情形一致，直接对各项系数求偏导数：
    \[a_i=\frac{\int_{-\pi}^\pi f(x)\cos(ix)dx}{\int_{-\pi}^\pi \cos(ix)\cos(ix)dx}=\frac{1}{\pi}\int_{-\pi}^\pi f(x)\cos(ix)dx\]
    \[b_i=\frac{\int_{-\pi}^\pi f(x)\sin(ix)dx}{\int_{-\pi}^\pi \sin(ix)\sin(ix)dx}=\frac{1}{\pi}\int_{-\pi}^\pi f(x)\sin(ix)dx\]
* 离散情形：
    * 此时需要规定等间距取点:\[x_j=-\pi+\frac{j}{m}\pi,\;j=0,1, \ldots ,2m-1\] 
    此时需要利用一些性质：
    \[
        \sum_{i=0}^{2m-1} \cos(nx_i) = 
            \left\{
                \begin{array}{l}
                0, \; \text{n is not multiply of 2m}\\
                2m,\; \text{otherwise}
                \end{array}
            \right.
    \]
    \[\sum_{i=0}^{2m-1}\sin(nx_i)=0\]
    \[\sum_{i=0}^{2m-1}\cos^2(nx_i)=
        \left\{
            \begin{array}{l}
                m,\;\text{n is not multiply of m}\\
                2m,\;\text{otherwise}
            \end{array}
        \right.
    \]
    \[\sum_{i=0}^{2m-1}\sin^2(nx_i)=
        \left\{
            \begin{array}{l}
                m,\;\text{n is not multiply of m}\\
                0,\;\text{otherwise}
            \end{array}
        \right.
    \]
    * 与前面求离散情形的最小二乘法一致：
    \[a_i=\frac{1}{m}\sum_{j=0}^{2m-1}f(x_j)\cos(ix_j)\]
    \[b_i=\frac{1}{m}\sum_{j=0}^{2m-1}f(x_j)\sin(ix_j)\]
* 快速傅里叶变化
    * 应用情形：考虑用三角多项式构造插值函数，实则为阶数 $n = m$ 的最小二乘三角近似多项式。（考虑 sin 和  cos  的系数个数可知 n = m 时共有 2m 个未知数，对应 2m 个插值点。）
    * 表达式：依然采用前面离散形式时求出的系数表达式，对公式进行调整：
    \[S_n(x)=\frac{a_0+a_n\cos(nx)}{2}+\sum_{k=1}^{n-1}(a_k\cos(kx)+b_k\sin(kx))\]
    * 采用递归的思想，在 $m$ 等于 $2^n$时，每次跨越 $m$ 对系数进行相加减。实际上，要求出 $a_i$ 和 $b_i$, 直接用公式
    \[a_i=\frac{1}{m}\sum_{j=0}^{2m-1}f(x_j)\cos(ix_j)\]
    \[b_i=\frac{1}{m}\sum_{j=0}^{2m-1}f(x_j)\sin(ix_j)\]
    即可，但计算量较大，考虑新的变量
    \[\tilde{c}_k= \frac{1}{m}\sum_{j=0}^{2m-1}f(x_j)e^{ik(-\pi+\frac{j}{m}\pi)}=\frac{1}{m}e^{-ik\pi}\sum_{0}^{2m-1}f(x_j)e^{ik\frac{j}{m}\pi}\]
    去掉前面的累加常数，得到
    \[c_k=\sum_{j=0}^{2m-1}f(x_j)e^{ik\frac{j}{m}\pi}\]
    这个数是直接可算的，只要算出了这个数，添上累加常数后得到的实部和虚部就是我们要的 $a_n$ 和 $b_n$ 了。这里只是用欧拉公式获得更简单的表达形式，并没有减少计算量。但是进一步观察可知：
    \[c_k+c_{k+m}=\sum_{j=0}^{2m-1}f(x_j)e^{ik\frac{j}{m}\pi}(1+e^{ij\pi})\]
    \[c_k-c_{k+m}=\sum_{j=0}^{2m-1}f(x_j)e^{ik\frac{j}{m}\pi}(1-e^{ij\pi})\]
    因此前一个公式中其实只有偶数项有贡献，而后一个公式中只有奇数项有贡献，两个式子足以解出 $c_k$ 和 $c_{k+m}$ 。于是计算这两个系数所用的计算量件减半了。而式子的形式并不会发生变化：
    \[c_k+c_{k+m}=\sum_{j=0}^{m-1}f(x_j)e^{ik\frac{j}{m/2 }\pi}=\sum_{j=0}^{2\widetilde{m}-1}f(x_j)e^{ik(j/{\widetilde{m} })\pi}\] , 其中 $\widetilde{m} = \frac{m}{2}$ ，只要 $\widetilde{m}$ 仍然为 $2^p$ ，上述过程可不断进行，由此来达到减少计算量的目的。
