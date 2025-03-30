```
skipmissing(itr)
```

返回一个迭代器，遍历 `itr` 中的元素，跳过 [`missing`](@ref) 值。返回的对象可以使用 `itr` 的索引进行索引，如果后者是可索引的。对应于缺失值的索引是无效的：它们被 [`keys`](@ref) 和 [`eachindex`](@ref) 跳过，并且在尝试使用它们时会抛出 `MissingException`。

使用 [`collect`](@ref) 来获取一个包含 `itr` 中非 `missing` 值的 `Array`。请注意，即使 `itr` 是一个多维数组，结果始终是一个 `Vector`，因为在保留输入的维度的同时无法删除缺失值。

另见 [`coalesce`](@ref)，[`ismissing`](@ref)，[`something`](@ref)。

# 示例

```jldoctest
julia> x = skipmissing([1, missing, 2])
skipmissing(Union{Missing, Int64}[1, missing, 2])

julia> sum(x)
3

julia> x[1]
1

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]

julia> argmax(x)
3

julia> collect(keys(x))
2-element Vector{Int64}:
 1
 3

julia> collect(skipmissing([1, missing, 2]))
2-element Vector{Int64}:
 1
 2

julia> collect(skipmissing([1 missing; 2 missing]))
2-element Vector{Int64}:
 1
 2
```
