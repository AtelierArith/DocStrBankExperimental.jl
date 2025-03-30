```
union(s, itrs...)
∪(s, itrs...)
```

构造一个包含所有参数中所有不同元素的对象。

第一个参数控制返回的容器类型。如果这是一个数组，它将保持元素首次出现的顺序。

Unicode `∪` 可以通过在 Julia REPL 中输入 `\cup` 然后按下 tab 键来输入，在许多编辑器中也是如此。这是一个中缀运算符，允许 `s ∪ itr`。

另请参见 [`unique`](@ref), [`intersect`](@ref), [`isdisjoint`](@ref), [`vcat`](@ref), [`Iterators.flatten`](@ref)。

# 示例

```jldoctest
julia> union([1, 2], [3])
3-element Vector{Int64}:
 1
 2
 3

julia> union([4 2 3 4 4], 1:3, 3.0)
4-element Vector{Float64}:
 4.0
 2.0
 3.0
 1.0

julia> (0, 0.0) ∪ (-0.0, NaN)
3-element Vector{Real}:
   0
  -0.0
 NaN

julia> union(Set([1, 2]), 2:3)
Set{Int64} with 3 elements:
  2
  3
  1
```
