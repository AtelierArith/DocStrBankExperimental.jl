```
randperm([rng=default_rng(),] n::Integer)
```

构造一个长度为 `n` 的随机排列。可选的 `rng` 参数指定一个随机数生成器（参见 [随机数](@ref)）。结果的元素类型与 `n` 的类型相同。

要随机打乱任意向量，请参见 [`shuffle`](@ref) 或 [`shuffle!`](@ref)。

!!! compat "Julia 1.1"
    在 Julia 1.1 中，`randperm` 返回一个向量 `v`，其 `eltype(v) == typeof(n)`，而在 Julia 1.0 中，`eltype(v) == Int`。


# 示例

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
