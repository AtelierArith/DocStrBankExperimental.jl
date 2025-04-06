```
merge!(d::AbstractDict, others::AbstractDict...)
```

使用其他集合中的键值对更新集合。另见 [`merge`](@ref)。

# 示例

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> merge!(d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 4
```
