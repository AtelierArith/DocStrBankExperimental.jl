```
Base.rest(collection[, itr_state])
```

通用函数，用于获取 `collection` 的尾部，从特定的迭代状态 `itr_state` 开始。如果 `collection` 本身是一个 `Tuple`，则返回一个 `Tuple`；如果 `collection` 是一个 `AbstractArray`，则返回一个 `AbstractVector` 的子类型；如果 `collection` 是一个 `AbstractString`，则返回一个 `AbstractString` 的子类型；否则返回一个任意迭代器，回退到 `Iterators.rest(collection[, itr_state])`。

可以为用户定义的集合类型重载，以自定义在最终位置的 [slurping in assignments](@ref destructuring-assignment) 的行为，例如 `a, b... = collection`。

!!! compat "Julia 1.6"
    `Base.rest` 至少需要 Julia 1.6。


另请参见: [`first`](@ref first), [`Iterators.rest`](@ref), [`Base.split_rest`](@ref)。

# 示例

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.rest(a, state)
(1, [3, 2, 4])
```
