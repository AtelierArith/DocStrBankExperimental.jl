```
combine_axes(As...) -> Tuple
```

Bestimmen Sie die Ergebnisachsen für das Broadcasting über alle Werte in `As`.

```jldoctest
julia> Broadcast.combine_axes([1], [1 2; 3 4; 5 6])
(Base.OneTo(3), Base.OneTo(2))

julia> Broadcast.combine_axes(1, 1, 1)
()
```
