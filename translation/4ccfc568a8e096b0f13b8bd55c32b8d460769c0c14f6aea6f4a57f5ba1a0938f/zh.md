```
cumprod(itr)
```

迭代器的累积乘积。

另见 [`cumprod!`](@ref), [`accumulate`](@ref), [`cumsum`](@ref)。

!!! compat "Julia 1.5"
    在非数组迭代器上使用 `cumprod` 至少需要 Julia 1.5。


# 示例

```jldoctest
julia> cumprod(fill(1//2, 3))
3-element Vector{Rational{Int64}}:
 1//2
 1//4
 1//8

julia> cumprod((1, 2, 1, 3, 1))
(1, 2, 2, 6, 6)

julia> cumprod("julia")
5-element Vector{String}:
 "j"
 "ju"
 "jul"
 "juli"
 "julia"
```
