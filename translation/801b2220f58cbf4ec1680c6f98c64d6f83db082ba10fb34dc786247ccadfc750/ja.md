```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

与えられた整数型のコンポーネントを持つ [`Rational`](@ref) 数として浮動小数点数 `x` を近似します。結果は `x` から `tol` 以上の差はありません。

# 例

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
