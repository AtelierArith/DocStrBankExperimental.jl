```
cispi(x)
```

`cis(pi*x)` 的更精确方法（特别是对于较大的 `x`）。

另请参见 [`cis`](@ref), [`sincospi`](@ref), [`exp`](@ref), [`angle`](@ref)。

# 示例

```jldoctest
julia> cispi(10000)
1.0 + 0.0im

julia> cispi(0.25 + 1im)
0.030556854645954562 + 0.03055685464595456im
```

!!! compat "Julia 1.6"
    此函数需要 Julia 1.6 或更高版本。

