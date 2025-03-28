```
findlast(predicate::Function, A)
```

Gibt den Index oder Schlüssel des letzten Elements von `A` zurück, für das `predicate` `true` zurückgibt. Gibt `nothing` zurück, wenn es kein solches Element gibt.

Indizes oder Schlüssel sind vom gleichen Typ wie die, die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegeben werden.

# Beispiele

```jldoctest
julia> A = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> findlast(isodd, A)
3

julia> findlast(x -> x > 5, A) # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> findlast(isodd, A)
CartesianIndex(2, 1)
```
