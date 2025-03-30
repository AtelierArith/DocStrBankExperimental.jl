```
nextpow(a, x)
```

最小的 `a^n` 不小于 `x`，其中 `n` 是非负整数。`a` 必须大于 1，`x` 必须大于 0。

另见 [`prevpow`](@ref)。

# 示例

```jldoctest
julia> nextpow(2, 7)
8

julia> nextpow(2, 9)
16

julia> nextpow(5, 20)
25

julia> nextpow(4, 16)
16
```
