# Linear-Algebra Review
---
## 概念
* 酉性质：保二范数，即\[||A\vec{x}||_2=||\vec{x}||_2\]

* 矩阵的零度：使得 $A\vec{x}=0$ 成立的向量 x 构成的空间的维数。

## 矩阵的秩
* 矩阵的行秩等于列秩。
    - 高斯消去法<br/><br/>

* 矩阵 $A^tA$ 的秩等于矩阵 $A$ 的秩
    - 证明思路：转化为证明矩阵 $A^tA$ 的零度和矩阵 $A$ 的零度相等。事实上，若 $A\vec{x}=0$ ，则 $A^tA\vec{x}=A^t(A\vec{x})=0$ ，因此矩阵 $A$ 的零度小于等于矩阵 $A^tA$ 的零度；同时若 $A^tA\vec{x}=0$ 则 $\vec{x}^tA^tA\vec{x}=(A\vec{x})^t(A\vec{x})=0 $ 则 $A\vec{x}=0$ 故矩阵 $A$ 和矩阵 $A^tA$ 的零度相等。<br/><br/>

* 矩阵 $A^2$ 的秩小于等于矩阵 $A$ 的秩
    - 证明思路：和上一条性质的证明思路一样，不难证明矩阵 $A^2$ 的零度大于等于矩阵 $A$ 的零度。

## 特征值和特征向量
* 对应于 n 个不同特征值的 n 个特征向量必然是线性无关的。

* 一个对称矩阵的属于不同特征值的特征向量必然正交，因而属于某一个特征值的特征向量会张出一个子空间。
    - 证明思路：
    \[\langle \alpha_1,A\alpha_2\rangle = \lambda_2\langle \alpha_1,\alpha_2\rangle = \alpha_1^tA\alpha_2=(A\alpha_1)^t\alpha2=\langle A\alpha_1,\alpha_2\rangle =\lambda_1\langle \alpha_1,\alpha_2\rangle \] $\implies(\lambda_1-\lambda_2)\langle\alpha_1,\alpha_2\rangle = 0 $<br/><br/>

* 对称矩阵的特征值一定为实数。（实对称和复对称都成立）
    - 证明思路：
    \[\bar{\alpha}^t{\bar{A}}^t\alpha=\bar{\alpha}^t\bar{\lambda}\alpha = \bar{\alpha}^tA\alpha = \bar{\alpha}^t\lambda\alpha\]

* 矩阵 $A^tA$ 和矩阵 $AA^t$ 有相同的特征值
    - 证明思路：设 $\vec{v}$ 是矩阵 $A^tA$ 的属于特征值 $\lambda $ 的特征向量，则: 
    \[A(A^tA\vec{v})=A(\lambda\vec{v})=\lambda(A\vec{v})=(AA^t)(A\vec{v}) \]所以 $\lambda$ 也是矩阵 $AA^t$ 的特征值。反之同理，事实上 $A^tA = A^t(A^t)^t $ 于是可以用同样的过程证明。<br/><br/>

* 矩阵 $A^tA$ 的特征值一定为非负实数。
    - 证明思路：特征值为实数已经在前面的性质中证明，设 $\vec{v}$ 是矩阵 $A^tA$ 的属于特征值 $\lambda $ 的特征向量，则:
    \[(A\vec{v})^t(A\vec{v})=\vec{v}^tA^tA\vec{v}=\lambda \vec{v}^t\vec{v} \]因为 $(A\vec{v})^t(A\vec{v})\ge 0 $ 且 $\vec{v}^t\vec{v}\ge 0 $ 故结论成立。

## 矩阵相似
* 性质
    * 相似矩阵有相同的特征值；<br/><br/>

* $n\times n$ 矩阵可对角化当且仅当矩阵有 n 个线性无关的特征向量。
    - 证明思路：矩阵可对角化时，满足 $A=P^{-1}DP $ 的 $P$ 的列向量就是特征向量，因为 $P$ 是非奇异阵，所以特征向量线性无关。反之，以线性无关的特征向量作为列向量的矩阵 $P$ 必然满足 $A=P^{-1}DP $, 其中 $D$ 是由与特征向量对应的特征值作为对角线元素形成的矩阵。<br/><br/>

* 具有 n 个不同的特征值的矩阵相似于对角线矩阵。<br/><br/>

* 复数域上，任何矩阵都正交相似于上三角矩阵。
    - 证明思路：[数学归纳法](https://blog.csdn.net/dc12499574/article/details/126090395)<br/><br/>

* $n\times n$ 矩阵是对称的当且仅当存在正交矩阵 $Q$ 和对角矩阵 $D$ 满足 $A = QDQ^t$<br/><br/>

* 复数域上，所有矩阵都相似于一个约当标准型。

## 正定矩阵
* 对称矩阵是正定矩阵当且仅当该矩阵所有的特征值都是正数。
    - 证明思路：对称矩阵一定正交相似于对角线矩阵，且对角线上的元素都是实数。