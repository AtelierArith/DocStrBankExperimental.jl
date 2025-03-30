```
map(f, c...) -> collection
```

通过对每个元素应用 `f` 来转换集合 `c`。对于多个集合参数，逐元素应用 `f`，并在任何一个集合耗尽时停止。

另见 [`map!`](@ref), [`foreach`](@ref), [`mapreduce`](@ref), [`mapslices`](@ref), [`zip`](@ref), [`Iterators.map`](@ref)。

# 示例

```jldoctest
julia> map(x -> x * 2, [1, 2, 3])
3-element Vector{Int64}:
 2
 4
 6

julia> map(+, [1, 2, 3], [10, 20, 30, 400, 5000])
3-element Vector{Int64}:
 11
 22
 33
```
