```
combine_axes(As...) -> Tuple
```

Déterminez les axes de résultat pour le broadcasting à travers toutes les valeurs dans `As`.

```jldoctest
julia> Broadcast.combine_axes([1], [1 2; 3 4; 5 6])
(Base.OneTo(3), Base.OneTo(2))

julia> Broadcast.combine_axes(1, 1, 1)
()
```
