```
length(collection) -> Ganzzahl
```

Gibt die Anzahl der Elemente in der Sammlung zurück.

Verwenden Sie [`lastindex`](@ref), um den letzten gültigen Index einer indexierbaren Sammlung zu erhalten.

Siehe auch: [`size`](@ref), [`ndims`](@ref), [`eachindex`](@ref).

# Beispiele

```jldoctest
julia> length(1:5)
5

julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
