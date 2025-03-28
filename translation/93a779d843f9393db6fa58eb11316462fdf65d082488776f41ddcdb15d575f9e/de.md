```
lastindex(collection) -> Ganzzahl
lastindex(collection, d) -> Ganzzahl
```

Gibt den letzten Index von `collection` zurück. Wenn `d` angegeben ist, gibt den letzten Index von `collection` entlang der Dimension `d` zurück.

Die Syntaxen `A[end]` und `A[end, end]` werden zu `A[lastindex(A)]` und `A[lastindex(A, 1), lastindex(A, 2)]` umgewandelt.

Siehe auch: [`axes`](@ref), [`firstindex`](@ref), [`eachindex`](@ref), [`prevind`](@ref).

# Beispiele

```jldoctest
julia> lastindex([1,2,4])
3

julia> lastindex(rand(3,4,5), 2)
4
```
