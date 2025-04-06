```
unique!(A::AbstractVector)
```

根据 [`isequal`](@ref) 和 [`hash`](@ref) 确定的标准移除重复项，然后返回修改后的 `A`。`unique!` 将按照元素出现的顺序返回 `A` 的元素。如果您不关心返回数据的顺序，那么调用 `(sort!(A); unique!(A))` 将会更高效，只要 `A` 的元素可以被排序。

# 示例

```jldoctest
julia> unique!([1, 1, 1])
1-element Vector{Int64}:
 1

julia> A = [7, 3, 2, 3, 7, 5];

julia> unique!(A)
4-element Vector{Int64}:
 7
 3
 2
 5

julia> B = [7, 6, 42, 6, 7, 42];

julia> sort!(B);  # unique! 能够更高效地处理已排序的数据。

julia> unique!(B)
3-element Vector{Int64}:
  6
  7
 42
```
