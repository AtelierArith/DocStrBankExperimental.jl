```
mod(x::Integer, r::AbstractUnitRange)
```

在范围 `r` 中找到 `y` 使得 $x ≡ y (mod n)$，其中 `n = length(r)`，即 `y = mod(x - first(r), n) + first(r)`。

另见 [`mod1`](@ref)。

# 示例

```jldoctest
julia> mod(0, Base.OneTo(3))  # mod1(0, 3)
3

julia> mod(3, 0:2)  # mod(3, 3)
0
```

!!! compat "Julia 1.3"
    此方法至少需要 Julia 1.3。

