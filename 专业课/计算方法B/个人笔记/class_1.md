<script>
    function changeColor(){
        var x = document.getElementById("formula");
        x.style.color = "red";
        setTimeout(()=>{x.style.color="black"},2000);
    }
</script>

# 误差分析
---
## 误差来源
* chopping -- 舍入
* trunction --截断
    * 级数截断
    * 数值小数截断
* operation --运算
    * 希望尽可能减少运算的次数
    * 同时希望通过运算消除一些误差
    * => 权衡
* 模型本身
* 观测误差
## important formula
* 舎入误差
    x = $0.a_1a_2\ldots \times 10^m$ 为真值，x* 为估计值，x 有 t 位有效数字。
    * 绝对误差 
    $$ |x-x^*|< 0.5 \times 10^{m-t} \tag{1} $$
    * 相对误差 
    $$\frac{|x-x^*|}{|x|} < \frac{2}{a_1} \times 10^{-t} \tag{2}$$ 
## 稳定性
* 算法
    * 稳定：对初值条件的小扰动只有小影响
    * 条件稳定：对部分条件稳定
    * 不稳定：误差指数增长
* 问题本身（条件好坏）
    * 初值小的扰动带来结果大的变化
## 避免误差危害
* 避免相近数相减
* 避免极小数做除数
## 典型问题
* 为了使相对误差小于 $10^{-2}$, 应该取多少位有效数字？
    *解：直接带入公式 $(2)$