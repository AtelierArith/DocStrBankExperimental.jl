```
hypot(x, y)
```

计算斜边 $\sqrt{|x|^2+|y|^2}$，避免溢出和下溢。

此代码是对 Carlos F. Borges 所描述的算法的实现：改进的 `hypot(a,b)` 算法。该文章可在线访问，链接为 https://arxiv.org/abs/1904.09481

```
hypot(x...)
```

计算斜边 $\sqrt{\sum |x_i|^2}$，避免溢出和下溢。

另请参见标准库中的 `norm` [`LinearAlgebra`](@ref man-linalg)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> a = Int64(10)^10;

julia> hypot(a, a)
1.4142135623730951e10

julia> √(a^2 + a^2) # a^2 溢出
ERROR: DomainError with -2.914184810805068e18:
sqrt 被调用时使用了负实数参数，但仅在使用复数参数时才会返回复数结果。尝试使用 sqrt(Complex(x))。
Stacktrace:
[...]

julia> hypot(3, 4im)
5.0

julia> hypot(-5.7)
5.7

julia> hypot(3, 4im, 12.0)
13.0

julia> using LinearAlgebra

julia> norm([a, a, a, a]) == hypot(a, a, a, a)
true
```
