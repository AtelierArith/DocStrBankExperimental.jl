```
binomial(x::Number, k::Integer)
```

广义二项式系数，对于 `k ≥ 0` 由多项式定义

$$
\frac{1}{k!} \prod_{j=0}^{k-1} (x - j)
$$

当 `k < 0` 时返回零。

对于整数 `x` 的情况，这等同于普通的整数二项式系数

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

对非整数 `k` 的进一步推广在数学上是可能的，但涉及伽马函数和/或贝塔函数，这些在Julia标准库中没有提供，但在外部包如 [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl) 中可用。

# 外部链接

  * [二项式系数](https://en.wikipedia.org/wiki/Binomial_coefficient) 在维基百科上。
