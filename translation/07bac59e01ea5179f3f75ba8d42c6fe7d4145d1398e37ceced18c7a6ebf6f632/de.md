```
first(coll)
```

Holen Sie sich das erste Element einer iterierbaren Sammlung. Gibt den Startpunkt eines [`AbstractRange`](@ref) zurück, auch wenn er leer ist.

Siehe auch: [`only`](@ref), [`firstindex`](@ref), [`last`](@ref).

# Beispiele

```jldoctest
julia> first(2:2:10)
2

julia> first([1; 2; 3; 4])
1
```
