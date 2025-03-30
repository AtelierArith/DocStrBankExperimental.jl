```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

在 `A` 中构造一个长度为 `length(A)` 的随机排列。可选的 `rng` 参数指定一个随机数生成器（参见 [Random Numbers](@ref)）。要随机排列任意向量，请参见 [`shuffle`](@ref) 或 [`shuffle!`](@ref)。

# 示例

```jldoctest
julia> randperm!(Xoshiro(123), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 1
 4
 2
 3
```
