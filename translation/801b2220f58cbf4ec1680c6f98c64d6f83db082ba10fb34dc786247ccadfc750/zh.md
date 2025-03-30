```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

将浮点数 `x` 近似为给定整数类型的 [`Rational`](@ref) 数字。结果与 `x` 的差异不超过 `tol`。

# 示例

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
