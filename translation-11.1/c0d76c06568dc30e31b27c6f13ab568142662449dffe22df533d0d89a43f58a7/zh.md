```
binomial(n::Integer, k::Integer)
```

*二项式系数* $\binom{n}{k}$ 是多项式展开 $(1+x)^n$ 中第 $k$ 项的系数。

如果 $n$ 是非负的，那么它表示从 $n$ 个项目中选择 `k` 个的方式数：

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

其中 $n!$ 是 [`factorial`](@ref) 函数。

如果 $n$ 是负的，那么它根据以下恒等式定义：

$$
\binom{n}{k} = (-1)^k \binom{k-n-1}{k}
$$

另见 [`factorial`](@ref)。

# 示例

```jldoctest
julia> binomial(5, 3)
10

julia> factorial(5) ÷ (factorial(5-3) * factorial(3))
10

julia> binomial(-5, 3)
-35
```

# 外部链接

  * [二项式系数](https://en.wikipedia.org/wiki/Binomial_coefficient) 在维基百科上。
