# 递推方程与生成函数
---
## 常系数线性递推方程
* 解法：齐次通解 + 非齐次特解
* 齐次通解：
    * 先求特征方程的根，对于方程 \[T_n+a_1T_{n-1}+ \cdots + a_{k}T_{n-k}=f(n)\]特征方程即为\[x^k+a_1x^{k-1}+ \cdots a_k=0\]
    * 设根为\[\alpha_0,\alpha_1, \ldots ,\alpha_k\]
        * 若无重根，则解为\[c_0\alpha_0^n+c_1\alpha_1^n+ \cdots +c_k\alpha_k^n\]
        * 若有重根，设 $\alpha_i$ 为 $r_i$ 重根，则将 $r_i$ 个 $\alpha_i$ 替换为 $\alpha_i,n\alpha_i, \ldots ,n^{r_i-1}\alpha_i$ ，重新利用上一个公式即可

## 非常系数线性递推方程
* 换元法：用于系数是常数，但迭代方程的变量不是常数差值的情形，如 $T(n)+cT(n/2)=f(n)$
* 迭代法，用于各种情形，有时要化简后迭代。
* 作差法，用于递推公式表现为与前面多项（所有项）相关的情形，如 $T(n)= \sum_{i=0}^{n-1} c_iT(i)$

## （一般）生成函数
* 基本思想：设所求序列为 $\{a_n\}$，构造多项式 $a_0+a_1x+ a_2x^2+\cdots $ ，记作原序列的生成函数。将该多项式化为简单的表达形式（通常为 $(x+y)^\alpha$ ），再将其展开（一般利用牛顿二项式系数）可以求出各项的系数。

* 具体操作步骤
    * 根据实际问题写出生成函数，使 $\{a_n\}$ 恰好对应到各项的系数，这一步需要自己构造，没有一般的方法。
    * 用某种公式将生成函数化成简单的形式。（如等比数列求和公式）
    * 利用牛顿二项式系数展开
    \[ \binom{\alpha}{n}=\frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!} \]
    __Note:__ 有用的公式：\[ \binom{-\alpha}{n}=\frac{-\alpha(-\alpha-1)\cdots(-\alpha-n+1)}{n!}=(-1)^n\binom{\alpha+n-1}{n}\]
    得到：\[(x+y)^\alpha=\sum_{n=0}^{\infty} \binom{\alpha}{n} x^ny^{\alpha-n}\]注意求和号的上下限。
    * 对应项的系数就是要的结果。

* 可以解决哪些问题
    * __Catalan 数的通项__
        * 迭代方程
        \[
        \begin{equation}
            \left\{
                \begin{array}{l}
                    h_n=\sum_{k=1}^{n-1} h_kh_{n-k}\;\;(n\ge 2) \\
                    h_1=1
                \end{array}
            \right.
        \end{equation}
        \]
        * 求解过程：设生成函数为 $T_n(x)$，则 $T_n^2(x)=T_n(x)-x$ ，求解该一元二次方程的根后再展开即可。
    * __求多重集 $\{k_1*a_1,k_2*a_2, \ldots ,k_n*a_n\}$ 的 r 组合数（实际上就是将 r 个相同的球分到 n 个不同的盒子里面）__
        * 求解过程：生成函数为：\[(1+y+y^2+ \cdots +y^{k_1})(1+y+ \cdots +y^{k_2})\cdots(1+y+ \cdots +y^{k_n})\]可以化简为：\[\frac{(1-y^{k_1+1})\cdots(1-y^{k_n+1})}{(1-y)^n}\]再求出其中各项的系数即可（事实上，实际操作中可以不用化简直接从最初的式子暴力看出要求的系数，在没有 $k_i$ 的限制或限制条件很少时，可以得到简单的化简形式 $1/(1-y)^n$ 这个时候考虑化简后展开。）
    * __求不定方程的解的个数__
        * 求解过程：与求多重集的 r 组合数思路完全一致，考虑到变量取值范围的约束可以写出对应的方程。如设不定方程为 $a_0x_0 + a_1x_1 + a_2x_2 + \cdots +a_nx_n = r$ ，其中 $b_i\le x_i \le c_i$ ，则生成函数为：\[(y^{a_0b_0}+y^{a_0(b_0+1)}+ \cdots y^{a_0c_0})\cdots(y^{a_nb_n}+ \cdots +y^{a_nc_n})\]
    * __正整数拆分__
        设待拆分的正整数为 m 
        * 无序可重复拆分
            * 考虑拆分结果中 1 有多少个， 2 有多少个，···， m 有多少个，于是转换为求解不定方程 $1*x_1+2*x_2+ \cdots m*x_m = m$ 的解的个数。
            * 求解过程：直接利用求不定方程解的个数的方法
        * 无序不重复拆分
            * 对于不定方程的变量取值范围作出限制，只能为 0 或 1 
            * 求解过程：利用求带限制的不定方程的解的个数的方法。
        * 有序可重复拆分
            * 求解思路：直接考虑组合方式求解，若只分成一份，则个数为 1 ，若分成两份，则个数为 $C_{m-1}^1$, 类似的，若分成 n 份，则个数为 $C_{m-1}^{n-1}$ ,对各种情况求和可得总情况数为 $2^{m-1}$ 。
        * 有序不重复拆分
            * 求解思路：先求无序不重复拆分的数目，对于拆分成 n 组的情况，考虑其全排列情形，将所有 n 值对应的情形总数相加。
## 指数生成函数
* 定义：对于序列 $\{a_n\}$ ，其指数生成函数是：\[\sum_{n=0}^{\infty}a_n\frac{x^n}{n!}\]如 $P(m,n)$ 的指数生成函数是 $(1+x)^m$
* 可以解决哪些问题
    * __多重集的 r 排列问题__
        设多重集为 $\{k_1*a_1,k_2*a_2, \ldots ,k_n*a_n\}$
        * 求解过程：生成函数为\[(1+x+\frac{x^2}{2!}+ \cdots +\frac{x^{k_1} }{k_1!})\cdots(1+x+\frac{x^2}{2!}+ \cdots +\frac{x^{n_k} }{n_k!})\]
## Stirling 数
* 第一类 Stirling 数
    * 来源：$x(x-1)\cdots(x-n+1)$ 的第 r 项的系数记作$
        \left[
            \begin{array}{c}
                n\\r
            \end{array}
        \right]
        $ ，称为第一类 Stirling 数
    * 递推公式\[
        \left\{
            \begin{array}{l}
                \left[
                \begin{array}{c}
                    n\\r    
                \end{array}
                \right]=
                \left[
                    \begin{array}{c}
                        n-1\\r-1
                    \end{array}
                \right]+(n-1)
                \left[
                \begin{array}{c}
                    n-1\\r    
                \end{array}
                \right] \;\;(n>r\ge 1)\\
                \left[
                \begin{array}{c}
                    n\\0    
                \end{array}
                \right]=0\;\;\;\;
                \left[
                \begin{array}{c}
                    n\\1    
                \end{array}
                \right]=(n-1)！                
            \end{array}
        \right.
        \]
    * 性质
        * \[
            \left[
                \begin{array}{c}
                    n\\n    
                \end{array}
            \right]= 1
        \]
        * \[
            \left[
                \begin{array}{c}
                    n\\n-1    
                \end{array}
            \right]=\frac{n(n-1)}{2}
            \]
        * \[
            \sum_{r=1}^n
            \left[
                \begin{array}{c}
                    n\\r    
                \end{array}
            \right]=n!
            \]
* 第二类 Stirling 数
    * 来源：将 n 个不同的球恰好放到 r 个相同的盒子里面的方法数。记作$
    \left\{
    \begin{array}{c}
        n\\r
    \end{array}
    \right\}$
    * 递推公式\[
        \left\{
            \begin{array}{l}
                \left\{
                \begin{array}{c}
                    n\\r    
                \end{array}
                \right\}=
                \left\{
                    \begin{array}{c}
                        n-1\\r-1
                    \end{array}
                \right\}+r
                \left\{
                \begin{array}{c}
                    n-1\\r    
                \end{array}
                \right\}\\
                \left\{
                \begin{array}{c}
                    n\\0    
                \end{array}
                \right\}=0\;\;\;\;
                \left\{
                \begin{array}{c}
                    n\\1    
                \end{array}
                \right\}=1                
            \end{array}
        \right.
    \]
## 放球问题总结
设有 n 个球，m 个盒子；
|球是否有区别|盒子是否有区别|是否有空盒|模型|方案计数|
|:--:|:--:|:--:|:--:|:--:|
|有|有|有|选取|$m^n$|
|有|有|无|第二类<br/>Stirling数| $m!\left\{\begin{array}{c}n\\m\end{array}\right\}$ |
|有|无|有|第二类<br/>Stirling数|\[\sum_{r=1}^n\left\{\begin{array}{c}n\\r\end{array}\right\}\]|
|有|无|无|第二类<br/>Stirling数|$\left\{\begin{array}{c}n\\m\end{array}\right\}$|
|无|有|有|直接组合计数|$C_{n+m-1}^{m-1}$|
|无|有|无|直接组合计数|$C_{n-1}^{m-1}$|
|无|无|有|不定方程|生成函数 $\frac{1}{(1-y)\cdots(1-y^m)}$|
|无|无|无|不定方程|生成函数 $\frac{y^m}{(1-y)\cdots(1-y^m)}$|
