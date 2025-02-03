# 分治算法的设计与分析
## 分治算法的构成
- **分解(Divide)** 步骤将问题划分为一些子问题，子问题的形式与原问题一样，只是规模更小。
- **解决(Conquer)** 步骤递归地求解出子问题。如果子问题的规模足够小，则停止递归，直接求解。
- **合井(Combine)** 步骤将子问题的解组合成原问题的解

## 使用递归式描述分治算法的运行时间
一个 **递归式(recurrence)** 就是一个等式或不等式，它通过更小的输入上的函数值来描述一个函数。例如
```math
\begin{align}
    T(n) = a T(n / b) + f(n)
\end{align}
```
上式描述的是这样一种算法的运行时间：它将规模为 $n$ 的问题分解为 $a$ 个子问题，
每个子问题规模为 $n / b$ ，其中 $a$ 和 $b$ 都是正常数。 $a$ 个子问题递归地进行求解，每个花费时间
 $T(n/b)$ 。函数 $f(n)$ 包含了问题分解和子间题解合并的代价。

> [!NOTE]
> 当声明、求解递归式时，我们常常忽略向下取整、向上取整及边界条件。

## 使用主方法求解上述递归式的界
1. 若对某个常数 $\varepsilon > 0$ 有 $f(n) = O\left(n^{\log_b a - \varepsilon}\right)$ ，
则 $T(n) = \Theta\left(n^{\log_b a}\right)$ 。
2. 若 $f(n) = \Theta\left(n^{\log_b a}\right)$ ，则 $T(n) = \Theta\left(n^{\log_b a} \lg n\right)$ 。
3. 若对某个常数 $\varepsilon > 0$ 有 $f(n) = \Omega\left(n^{\log_b a + \varepsilon}\right)$ ，
且对某个常数 $c < 1$ 和所有足够大的 $n$ 有 $a f(n / b) \leqslant c f(n)$ ，
则 $T(n) = \Theta(f(n))$ 。

## 实例
