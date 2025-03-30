```
combine_axes(As...) -> Tuple
```

`As` içindeki tüm değerler için yayılma (broadcasting) üzerinde sonuç eksenlerini belirleyin.

```jldoctest
julia> Broadcast.combine_axes([1], [1 2; 3 4; 5 6])
(Base.OneTo(3), Base.OneTo(2))

julia> Broadcast.combine_axes(1, 1, 1)
()
```
