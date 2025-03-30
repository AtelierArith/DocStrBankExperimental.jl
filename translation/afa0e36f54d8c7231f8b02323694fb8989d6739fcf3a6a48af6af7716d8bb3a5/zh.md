```
intersect(s, itrs...)
∩(s, itrs...)
```

构造一个包含所有参数中出现的元素的集合。

第一个参数控制返回的容器类型。如果这是一个数组，它将保持元素首次出现的顺序。

Unicode `∩` 可以通过在 Julia REPL 中输入 `\cap` 然后按下 tab 键来输入，在许多编辑器中也是如此。这是一个中缀运算符，允许 `s ∩ itr`。

另请参见 [`setdiff`](@ref), [`isdisjoint`](@ref), [`issubset`](@ref Base.issubset), [`issetequal`](@ref)。

!!! compat "Julia 1.8"
    从 Julia 1.8 开始，intersect 返回的结果具有两个输入的类型提升后的 eltype 的 eltype


# 示例

```jldoctest
julia> intersect([1, 2, 3], [3, 4, 5])
1-element Vector{Int64}:
 3

julia> intersect([1, 4, 4, 5, 6], [6, 4, 6, 7, 8])
2-element Vector{Int64}:
 4
 6

julia> intersect(1:16, 7:99)
7:16

julia> (0, 0.0) ∩ (-0.0, 0)
1-element Vector{Real}:
 0

julia> intersect(Set([1, 2]), BitSet([2, 3]), 1.0:10.0)
Set{Float64} with 1 element:
  2.0
```
