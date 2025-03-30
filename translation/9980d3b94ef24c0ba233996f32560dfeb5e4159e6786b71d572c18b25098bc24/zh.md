```
axes(A, d)
```

返回数组 `A` 在维度 `d` 上的有效索引范围。

另见 [`size`](@ref)，以及关于 [具有自定义索引的数组](@ref man-custom-indices) 的手册章节。

# 示例

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A, 2)
Base.OneTo(6)

julia> axes(A, 4) == 1:1  # 所有维度 d > ndims(A) 的大小为 1
true
```

# 使用说明

每个索引必须是 `AbstractUnitRange{<:Integer}`，但同时可以是使用自定义索引的类型。因此，例如，如果您需要一个子集，请使用诸如 `begin`/`end` 或 [`firstindex`](@ref)/[`lastindex`](@ref) 的广义索引构造：

```julia
ix = axes(v, 1)
ix[2:end]          # 对于例如 Vector 会有效，但在一般情况下可能会失败
ix[(begin+1):end]  # 对于广义索引有效
```
