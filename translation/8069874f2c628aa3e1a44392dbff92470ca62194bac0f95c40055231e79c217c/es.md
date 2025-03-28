```
combine_axes(As...) -> Tuple
```

Determina los ejes resultantes para la difusión a través de todos los valores en `As`.

```jldoctest
julia> Broadcast.combine_axes([1], [1 2; 3 4; 5 6])
(Base.OneTo(3), Base.OneTo(2))

julia> Broadcast.combine_axes(1, 1, 1)
()
```
