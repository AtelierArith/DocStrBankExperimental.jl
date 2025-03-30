```
IdSet{T}([itr])
IdSet()
```

IdSet{T}() 使用 `===` 作为与类型 `T` 的值的相等性构造一个集合（参见 [`Set`](@ref)）。

在下面的示例中，所有值都是 `isequal`，因此它们在普通的 `Set` 中被覆盖。`IdSet` 通过 `===` 进行比较，因此保留了 3 个不同的值。

# 示例

```jldoctest; filter = r"\n\s*(1|1\.0|true)"
julia> Set(Any[true, 1, 1.0])
Set{Any} with 1 element:
  1.0

julia> IdSet{Any}(Any[true, 1, 1.0])
IdSet{Any} with 3 elements:
  1.0
  1
  true
```
