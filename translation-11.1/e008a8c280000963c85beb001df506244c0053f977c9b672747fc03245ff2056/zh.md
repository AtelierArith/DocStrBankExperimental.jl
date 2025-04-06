```
indexin(a, b)
```

返回一个数组，包含 `b` 中每个值在 `a` 中的第一个索引。输出数组在 `a` 不是 `b` 的成员的地方包含 `nothing`。

另请参见: [`sortperm`](@ref), [`findfirst`](@ref)。

# 示例

```jldoctest
julia> a = ['a', 'b', 'c', 'b', 'd', 'a'];

julia> b = ['a', 'b', 'c'];

julia> indexin(a, b)
6-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
 2
  nothing
 1

julia> indexin(b, a)
3-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
```
