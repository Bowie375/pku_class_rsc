# 格和布尔代数
---
## 格的定义
* 从集合性质出发的定义方式：
设 $\langle S,\preccurlyeq\rangle$ 是偏序集，如果 $\forall x,y\in S$ ，$\{x,y\}$ 都有最大上界和最小下界，那么称 $S$ 关于偏序 $\preccurlyeq$ 构成一个格。 

* 从代数所含运算的性质出发的定义方式：
设代数 $\langle S,\ast,\circ\rangle$ ，若该代数中的运算满足交换律，结合律，吸收律，（可推出满足交换律）则可适当定义 $S$ 中的偏序 $\preccurlyeq$ ，使得 $\langle S,\preccurlyeq\rangle$ 为格。

* 两种定义方式等价
    * 从集合性质出发的定义方式自然可以推出从代数运算性质出发的定义；
    * 从代数运算性质出发，可以定义集合 $S$ 上的关系 $\langle a,b\rangle\in R\Leftrightarrow a\circ b=b$ ，则可证明这个关系满足反对称性，传递性和反身性，故为偏序关系。

## 格的性质
* 格的对偶原理：设 $p$ 是含有格中元素以及符号 $=,\preccurlyeq,\succcurlyeq,\land,\lor$ 的命题。将 $p$ 中的 $\preccurlyeq$ 与 $\succcurlyeq$ 相互替换，$\land$ 和 $\lor$ 相互替换所得到的命题，称为 $p$ 的对偶命题，记作 $p^{*}$ 。若 $p$ 对一切格为真，则 $p^{*}$ 也对一切格为真。

* 运算性质
    * 若 $a\preccurlyeq b$ 且 $c\preccurlyeq d$ ，则\[a\land c\preccurlyeq b\land d\]\[a\lor c\preccurlyeq b\lor d\]

## 分配格的定义
* 满足分配率的格成为分配格，即设 $\langle L,\land,\lor\rangle$ 是格，若 $\forall a,b,c \in L$ 有\[a\land(b\lor c)=(a\land b)\lor(a\land c)\]\[a\lor(b\land c)=(a\lor b)\land(a\lor c)\]则称 $L$ 为分配格。

* 分配格的判定：设 $L$ 是格，则 $L$ 是分配格当且仅当 $L$ 中不含有与钻石格或五角格同构的自格。


## 有界格的定义
* 设 $L$ 是格，若 $L$ 存在全上界和全下界，则称 $L$ 为有界格，并将 $L$ 记作 $\langle L,\land,\lor,0,1\rangle$ 。
    其中全上界和全下界的定义为若 $\exist a\in L\;\;st\;\;\forall x\in L\;\;a\preccurlyeq x $ ，则称 $a$ 为全下界，类似的若$\exist a\in L\;\;st\;\;\forall x\in L\;\;a\succcurlyeq x $ ，则称 $a$ 为全上界。一般将全上界记作 1 ，全下界记作 0。

## 有界格中的补元
* 设 $\langle L,\land,\lor,0,1\rangle$ 是有界格，$a\in L$，若存在 $b\in L$ 使得：\[a\land b=0\;\;and\;\; a\lor b=1\]则称 $b$ 为 $a$ 的补元。

* 全上界一定有补元，即为全下界；
全下界一定有补元，即为全上界；
其他元素不一定有补元，也有可能有多个补元。

* 对于有界分配格来说，若 $a\in L$ ，且对于 $a$ 存在补元 $b$ ，则  $b$是 $a$ 的唯一补元。

## 布尔代数的定义
* 定义一：若一个有界格中所有元素都存在补元，则称这个有界格为有补格。一个有补分配格称为布尔代数。

* 定义二：对一个代数系统 $\langle B,\ast,\circ\rangle$ ，$\ast$ 和 $\circ$ 是二元运算，若这两个运算满足：
    * 交换律
    * 分配律
    * 同一律\[\exist \;0,1\in B\;\;st\;\; a\ast 1=a\;,\;a\circ 0=a\]
    * 补元律\[\exist a^{'}\in B\;\;st\;\; a\ast a^{'}=0\;,\;a\circ a^{'}=1\]

    则称这个代数系统是一个布尔代数。事实上可以从这四条性质中推出结合律和吸收律。

## 布尔代数的性质
* 设 $0\in L\;,\;0\ne a\in L$，若 $\forall b\in L$ 当 $0\prec b\preccurlyeq a$ 时，总有 $b=a$ ，则称 $a$ 是 $L$ 中的原子。
* 设 $B$ 是有限布尔代数，$A$ 是 $B$ 的全体原子构成的集合，则 $B$ 同构于 $A$ 的幂集代数 $P(A)$
* 任何有限布尔代数的基数是 $2^n$。
* 任何等势的布尔代数都是同构的。