```
unique(itr)
```

返回一个数组，仅包含集合 `itr` 的唯一元素，这些元素是通过 [`isequal`](@ref) 和 [`hash`](@ref) 确定的，并按照每组等效元素最初出现的顺序排列。输入的元素类型得以保留。

另请参见：[`unique!`](@ref), [`allunique`](@ref), [`allequal`](@ref)。

# 示例

```jldoctest
julia> unique([1, 2, 6, 2])
3-element Vector{Int64}:
 1
 2
 6

julia> unique(Real[1, 1.0, 2])
2-element Vector{Real}:
 1
 2
```
