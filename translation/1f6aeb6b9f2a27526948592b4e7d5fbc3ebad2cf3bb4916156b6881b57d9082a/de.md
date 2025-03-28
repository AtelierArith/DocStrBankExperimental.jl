```
firstindex(collection) -> Integer
firstindex(collection, d) -> Integer
```

Gibt den ersten Index von `collection` zurück. Wenn `d` angegeben ist, gibt den ersten Index von `collection` entlang der Dimension `d` zurück.

Die Syntaxen `A[begin]` und `A[1, begin]` werden zu `A[firstindex(A)]` und `A[1, firstindex(A, 2)]` übersetzt.

Siehe auch: [`first`](@ref), [`axes`](@ref), [`lastindex`](@ref), [`nextind`](@ref).

# Beispiele

```jldoctest
julia> firstindex([1,2,4])
1

julia> firstindex(rand(3,4,5), 2)
1
```
