```
prevpow(a, x)
```

不大于 `x` 的最大 `a^n`，其中 `n` 是非负整数。`a` 必须大于 1，`x` 必须不小于 1。

另请参见 [`nextpow`](@ref)，[`isqrt`](@ref)。

# 示例

```jldoctest
julia> prevpow(2, 7)
4

julia> prevpow(2, 9)
8

julia> prevpow(5, 20)
5

julia> prevpow(4, 16)
16
```
