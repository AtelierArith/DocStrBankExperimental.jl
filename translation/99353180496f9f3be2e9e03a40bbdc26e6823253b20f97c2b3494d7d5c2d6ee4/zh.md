```
tail(x::Tuple)::Tuple
```

返回一个 `Tuple`，包含 `x` 的所有组件，除了第一个。

另请参见: [`front`](@ref Base.front), [`rest`](@ref Base.rest), [`first`](@ref), [`Iterators.peel`](@ref).

# 示例

```jldoctest
julia> Base.tail((1,2,3))
(2, 3)

julia> Base.tail(())
ERROR: ArgumentError: 不能在空元组上调用 tail。
```
