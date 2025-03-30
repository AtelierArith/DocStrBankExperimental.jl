```
Base.split_rest(collection, n::Int[, itr_state]) -> (rest_but_n, last_n)
```

用于拆分 `collection` 尾部的通用函数，从特定的迭代状态 `itr_state` 开始。返回一个包含两个新集合的元组。第一个集合包含尾部的所有元素，但不包括最后 `n` 个元素，这些元素构成第二个集合。

第一个集合的类型通常遵循 [`Base.rest`](@ref) 的类型，除了回退情况不是惰性求值，而是急切地收集到一个向量中。

可以为用户定义的集合类型重载，以自定义在非最终位置的 [赋值中的吸取](@ref destructuring-assignment) 行为，例如 `a, b..., c = collection`。

!!! compat "Julia 1.9"
    `Base.split_rest` 至少需要 Julia 1.9。


另请参见: [`Base.rest`](@ref)。

# 示例

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.split_rest(a, 1, state)
(1, ([3, 2], [4]))
```
