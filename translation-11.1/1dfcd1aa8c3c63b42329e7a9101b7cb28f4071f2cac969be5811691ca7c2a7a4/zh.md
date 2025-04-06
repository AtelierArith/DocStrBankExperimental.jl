```
popfirst!(collection) -> item
```

从 `collection` 中移除第一个 `item`。

在许多其他编程语言中，这个函数被称为 `shift`。

另请参见: [`pop!`](@ref), [`popat!`](@ref), [`delete!`](@ref)。

# 示例

```jldoctest
julia> A = [1, 2, 3, 4, 5, 6]
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> popfirst!(A)
1

julia> A
5-element Vector{Int64}:
 2
 3
 4
 5
 6
```
