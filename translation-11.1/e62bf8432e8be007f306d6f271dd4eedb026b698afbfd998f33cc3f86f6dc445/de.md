```
findfirst(predicate::Function, A)
```

Gibt den Index oder Schlüssel des ersten Elements von `A` zurück, für das `predicate` `true` zurückgibt. Gibt `nothing` zurück, wenn es kein solches Element gibt.

Indizes oder Schlüssel sind vom gleichen Typ wie die, die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegeben werden.

# Beispiele

```jldoctest
julia> A = [1, 4, 2, 2]
4-element Vector{Int64}:
 1
 4
 2
 2

julia> findfirst(iseven, A)
2

julia> findfirst(x -> x>10, A) # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> findfirst(isequal(4), A)
2

julia> A = [1 4; 2 2]
2×2 Matrix{Int64}:
 1  4
 2  2

julia> findfirst(iseven, A)
CartesianIndex(2, 1)
```
