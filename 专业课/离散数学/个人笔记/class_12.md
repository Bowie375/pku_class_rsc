# 代数系统
---
## 运算
* 二元运算：函数 $f:S\times S\rightarrow S$ 称为二元运算
* 一元运算：函数 $f:S\rightarrow S$ 称为一元运算
## 性质
1. 运算的性质
    * 一种运算
        * 交换律: $a\circ b=b\circ a$
        * 结合律: $a\circ(b\circ c)=(a\circ b)\circ c $
        * 幂等律: $a\circ a=a$
        * 消去律: $a\circ b=a\circ c$ 且 $a$ 不是零元，则 $b=c$
    * 两种运算
        * 分配率: $(a\circ b)\ast c=(a\ast c)\circ(b\ast c) $ 且 $c\ast(a\circ b)=(c\ast a)\circ(c\ast b) $ ，称 $\ast$ 对 $\circ$ 是可分配的。
        * 吸收率：$a\ast(a\circ b)=a $ 且 $a\circ(a\ast b)=a$ ，称 $\ast$ 和 $\circ$ 满足吸收律。
2. 元素的性质
    * 单位元: $e\circ b = b\circ e =b$ ，称 $e$ 为单位元。
        * 单位元若存在，则唯一
    * 零元: $\theta \circ b = b\circ\theta = \theta$ ，称 $\theta$ 为零元。
        * 零元若存在，则唯一
    * 逆元: $a\circ b= e = b\circ a$ ，其中$e$ 为单位元，称 $a$ 和 $b$ 互为逆元。
        * 逆元是否存在与具体元素有关，即使存在，不同元素的逆元也不一定相等。
## 代数系统
* 定义：非空集合 $S$ 和 $S$ 上 $k$ 个一元或二元运算 $f_1,f_2, \ldots ,f_k$ 组成的系统称为一个代数系统，记作 $\langle S,f_1,f_2, \ldots ,f_k\rangle$ , 为了强调系统中代数常数（如单位元，零元等）的存在，可以将代数常数也加入到系统的表达式中。有时也直接用元素集合的名字标记代数系统。
* 同类型的代数结构、同种的代数结构
    * 同类型指两个代数结构中运算的数目及其元数和代数常数的数目都相同。
    * 同种指两个代数结构不仅同类型，而且每个运算满足的性质都相同。
* 子代数
    设 $V=\langle S,f_1,f_2, \ldots ,f_k\rangle$ 是代数系统，$B\subseteq S $ ，如果 $B$ 对所有 $V$ 中的运算都封闭，且代数常数和 $V$ 中的相同，则称 $\langle B,f_1,f_2, \ldots ,f_k\rangle$ 是 $V$ 的子代数系统。
    * 由 $V$ 本身组成的 $V$ 的子代数和只由 $V$ 中的代数常数组成的子代数都称为平凡子代数。
* 积代数
    * 设 $V_1=\langle A,\circ\rangle$ 和 $V_2=\langle B,\ast\rangle$ 是两个同类型的代数系统，则取\[\cdot \
    \;: (A\times B)\times(A\times B)\rightarrow A\times B\newline \langle a_1,b_1\rangle\cdot\langle a_2,b_2\rangle=\langle a_1\circ a_2,b_1\ast b_2\rangle\]定义的运算得到的代数结构 $V=\langle A\times B,\cdot\rangle $ 称为 $V_1$ 与 $V_2$ 的积代数。
    * 性质
        * 若 $V_1$ 和 $V_2$ 都满足交换律（结合律，幂等律），则 $V$ 也满足交换律（结合律，幂等律）。__消去律不满足此规律。如 $x_1=\langle \theta_1,b_1\rangle$ , $x_2=\langle a_2, \theta_2\rangle$ , $x_3=\langle a_3,\theta_2\rangle$ 满足 $x_1\cdot x_2=x_1\cdot x_3=\langle \theta_1,\theta_2\rangle$ , 但 $x_2$ 不等于 $x_3$ 。其中$\theta_1$ 、$\theta_2$ 分别为$V_1$ 、$V_2$ 的零元。__
        * 设 $V_1$ 和 $V_2$ 的单位元（零元，逆元）分别为 $a_0$ , $b_0$ ， 则 $V$ 中的单位元（零元，逆元）为 $\langle a_0,b_0\rangle$ 。 
## 同态（映射）和同构（映射）
* 设 $V_1=\langle A,\circ\rangle$ 和 $V_2=\langle B,\ast\rangle$ 为两个代数系统，函数 $f:V_1\rightarrow V_2$ 满足：\[f(a_1\circ a_2)=f(a_1)\ast f(a_2)\]则 $f$ 称为同态映射。简称同态。
* 若同态映射为单射（满射），称为单同态（满同态）；若同态映射是双射，称为同构。
* 若 $V_1=V_2$ 则类似的有自同态，单自同态，满自同态，自同构的概念。
* 性质：
    * 若 $V_1$ 中 $\circ$ 满足交换律（结合律，幂等律），则同态像 $f(V_1)$ 中 $\ast$ 满交换律（结合律，幂等律）。__消去律不满足此规律。如 $\circ$ 和 $\ast$ 都是取两个元素最大值的函数，$f$ 是简单递增函数就是一个反例。__
    * 同态映射将单位元（零元，逆元）映射到单位元（零元，逆元）。