```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

在 `A` 中构造一个长度为 `n = length(A)` 的随机循环排列。可选的 `rng` 参数指定一个随机数生成器，参见 [Random Numbers](@ref)。

这里，“循环排列”意味着所有元素都位于一个单一的循环中。如果 `A` 非空（`n > 0`），则有 $(n-1)!$ 种可能的循环排列，这些排列是均匀抽样的。如果 `A` 为空，`randcycle!` 将保持其不变。

[`randcycle`](@ref) 是此函数的一个变体，它分配一个新的向量。

# 示例

```jldoctest
julia> randcycle!(Xoshiro(123), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
