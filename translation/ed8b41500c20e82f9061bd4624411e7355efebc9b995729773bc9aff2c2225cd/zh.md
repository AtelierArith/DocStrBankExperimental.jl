```
front(x::Tuple)::Tuple
```

返回一个 `Tuple`，包含 `x` 的所有组件，除了最后一个。

另请参见: [`first`](@ref), [`tail`](@ref Base.tail).

# 示例

```jldoctest
julia> Base.front((1,2,3))
(1, 2)

julia> Base.front(())
ERROR: ArgumentError: 不能在空元组上调用 front。
```
