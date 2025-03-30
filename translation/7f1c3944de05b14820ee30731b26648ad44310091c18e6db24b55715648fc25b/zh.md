```
filter(f, itr::SkipMissing{<:AbstractArray})
```

返回一个与给定 `SkipMissing` 迭代器包装的数组类似的向量，但所有缺失元素以及 `f` 返回 `false` 的元素都被移除。

!!! compat "Julia 1.2"
    此方法需要 Julia 1.2 或更高版本。


# 示例

```jldoctest
julia> x = [1 2; missing 4]
2×2 Matrix{Union{Missing, Int64}}:
 1         2
  missing  4

julia> filter(isodd, skipmissing(x))
1-element Vector{Int64}:
 1
```
