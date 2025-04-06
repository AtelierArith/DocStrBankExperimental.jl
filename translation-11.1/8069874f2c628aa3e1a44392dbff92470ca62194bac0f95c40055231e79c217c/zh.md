```
combine_axes(As...) -> Tuple
```

确定在 `As` 中所有值的广播结果轴。

```jldoctest
julia> Broadcast.combine_axes([1], [1 2; 3 4; 5 6])
(Base.OneTo(3), Base.OneTo(2))

julia> Broadcast.combine_axes(1, 1, 1)
()
```
