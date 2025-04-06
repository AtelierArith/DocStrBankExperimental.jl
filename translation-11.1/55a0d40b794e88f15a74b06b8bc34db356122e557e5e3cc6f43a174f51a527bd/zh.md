```
randcycle([rng=default_rng(),] n::Integer)
```

构造一个长度为 `n` 的随机循环排列。可选的 `rng` 参数指定一个随机数生成器，参见 [Random Numbers](@ref)。结果的元素类型与 `n` 的类型相同。

这里，“循环排列”意味着所有元素都位于一个单一的循环中。如果 `n > 0`，则有 $(n-1)!$ 种可能的循环排列，这些排列是均匀抽样的。如果 `n == 0`，`randcycle` 返回一个空向量。

[`randcycle!`](@ref) 是此函数的就地变体。

!!! compat "Julia 1.1"
    在 Julia 1.1 及以上版本中，`randcycle` 返回一个向量 `v`，其 `eltype(v) == typeof(n)`，而在 Julia 1.0 中 `eltype(v) == Int`。


# 示例

```jldoctest
julia> randcycle(Xoshiro(123), 6)
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
