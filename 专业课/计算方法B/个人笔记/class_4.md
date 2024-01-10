# 多项式插值
---
## 多项式近似表示函数的存在性
* Weierstrass定理：设 $f(x)$ 为连续函数，则 $\forall \epsilon$ 存在多项式 $P(n)$ 使得 \[|P(n)-f|<\epsilon, \space x \in [a,b]\]
## 拉格朗日插值
* 基本思想：将函数写成一系列基函数的线性组合。已知 n+1 个节点，可以构造出至多 n 阶的多项式。
* n阶 Lagrange 插值多项式：\[P(n)=\sum_{k=0}^n(\prod_{i=0;i\ne k}^n\frac{(x-x_i)}{(x_k-x_i)})f(x_k)\]
* 阶数越高，在插值点附近的误差越小，但在边界点出会出现大幅度震荡，在阶数趋于无穷大时，边界的误差也趋于无穷。
    * 解决方式：改变取点方式。
* 问题：为保证计算结果在精度允许范围内，可能需要增加点，但在增加点后，系数无法复用。
    * 解决方式：取部分点，递归求出高阶多项式。
    \[P_n(x)=\frac{(x-x_i)P_{1,2,\dots,i-1,i+1,\dots,n}(x)-(x-x_j)P_{1,2,\dots,j-1,j+1,\dots,n}(x)}{x_j-x_i}\]
* 截断误差：\[R(n)=\frac{f^{n+1}(\eta)}{(n+1)!}\prod_{i=0}^n(x-x_i)\]
* nyquist-shannon

## 牛顿差分多项式
* 基本公式：\[P(n)=f[x_0]+\sum_{k=1}^n f[x_1,x_2,\dots,x_k]\prod_{i=0}^{k-1} (x-x_i)\]
* 当 $x_i$ 等距取点时牛顿差分多项式可写成更简单的形式：
    设 $x_i=x_0+i*h$
    * 前向差分多项式：
    设 $x=x_0+s*h$
    \[P_n(x)=f[x_0]+\sum_{k=1}^n\binom{s}{k}\Delta^kf[x_0]\]
    * 后向差分多项式：
    设 $x=x_n+s*h$
    \[P_n(x)=f[x_n]+\sum_{k={1}}^n(-1)^k\binom{-s}{k}\nabla^kf[x_n]\]
    * 中项差分多项式：只需要将各点按 $x_0,x_{-1},x_1,\dots$ 和 $x_0,x_1,x_{-1},\dots$ 分别写出一般的牛顿插值多项式然后取平均即得：
    \[P_{2m+1}(x)=f[x_0]+\frac{sh}{2}(f[x_{-1},x_0]+f[x_0,x_1])+s^2h^2f[x_{-1},x_0,x_1]+\cdots\newline +s^2(s^2-1)(s^2-4)\cdots (s^2-(m-1)^2)h^{2m}f[x_{-m},\dots,x_m] )\newline +\frac{s^2(s^2-1)\cdots(s^2-m^2)h^{2m+1}}{2}(f[x_{-m-1},\dots,x_m]+f[x_{-m},\dots,x_{m+1}])\]
    \[P_{2m}(x)=f[x_0]+\frac{sh}{2}(f[x_{-1},x_0]+f[x_0,x_1])+s^2h^2f[x_{-1},x_0,x_1]+\cdots\newline +s^2(s^2-1)(s^2-4)\cdots (s^2-(m-1)^2)h^{2m}f[x_{-m},\dots,x_m] )\]

## Hermite 插值多项式
* 基本思路：结合 Langrange 和 Taylor 多项式的特点，构造在给定点处不仅函数值相等，一阶导数也相等的多项式。
* 两种表述形式：
    * 利用 Langrange 插值多项式的系数：
    设 $ L_{n,j}(x) $ 为 n 阶 Langrange 多项式第 j 项的系数，满足约束 $ x_0,x_1, \ldots ,x_n$ 处函数值和导数均相等 则：
    \[P_{2n+1}(x)=\sum_{j=0}^n f(x_j)(1-2(x-x_j)L_{n,j}^{'}(x_j))L_{n,j}^2(x)+\sum_{j=0}^n f^{'}(x_j)(x-x_j)L_{n,j}^2(x)\]
    * 利用差商：
    设 $ z_0=z_1=x_0,z_2=z_3=x_1, \cdots $ 且 $ f[z_{2i},z_{2i+1}]=f^{'}(x_i)$, 则：
    \[P_{2n+1}(x)=f[z_0]+\sum_{k=1}^{2n+1} f[z_0,z_1, \ldots ,z_k] (x-z_0)(x-z_1)\cdots(x-z_{k-1})\]

## cubic spline interpolation
* 基本思想：Langrange 插值多项式在端点处震荡严重，为了解决这个问题，试图将曲线分成几个部分，每一部分分别用一条曲线近似。但是新问题是我们希望不同的曲线在连接处能表现为光滑可导。于是想到了在插值点上导数也相等的插值函数 -- Hermite 插值函数。是否可以在每一段上都用 Hermite 来近似呢？麻烦在于我们需要知道函数在每个点的导数信息，这并不容易。然后我们来到了 cubic spline -- 不需要知道导数信息也能让连接处光滑的插值函数。
* 基本公式：
设已知点 $x_0,x_1, \ldots ,x_n$ 处的函数值，在区间 $[x_i,x_{i+1}]$ 上，定义函数 $S_i=a_i+b_i(x-x_i)+c_i(x-x_i)^2+d_i(x-x_i)^3$ ，于是只需求解 $a_i,b_i,c_i,d_i, i=1,2\cdots, n$ 即可。并有约束条件：
    * $S_i(x_{i+1})=S_{i+1}(x_{i+1})=f(x_{i+1})\quad i= 0,1,\cdots,n-2$
    $ S_0(x_0)=f(x_0)\quad S_{n-1}(x_n)=f(x_n)$
    * $S_i^{'}(x_{i+1})=S_{i+1}^{'}(x_{i+1})\quad i=0,1, \ldots ,n-2$
    * $S_i^{''}(x_{i+1})=S_{i+1}^{''}(x_{i+1})\quad i=0,1, \ldots ,n-2$
    * $natural \;spline:\;S_0^{''}(x_0)=0\quad S_{n-1}^{''}(x_n)=0$
    $clamped \; spline:\;S_0{'}(x_0)=f^{'}(x_0)\quad S_{n-1}^{'}(x_n)=f^{'}(x_n)$

