```
popfirst!(collection) -> item
```

Entfernt das erste `item` aus `collection`.

Diese Funktion wird in vielen anderen Programmiersprachen `shift` genannt.

Siehe auch: [`pop!`](@ref), [`popat!`](@ref), [`delete!`](@ref).

# Beispiele

```jldoctest
julia> A = [1, 2, 3, 4, 5, 6]
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> popfirst!(A)
1

julia> A
5-element Vector{Int64}:
 2
 3
 4
 5
 6
```
