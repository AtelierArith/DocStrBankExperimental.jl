```
findlast(A)
```

Gibt den Index oder Schlüssel des letzten `true` Wertes in `A` zurück. Gibt `nothing` zurück, wenn es keinen `true` Wert in `A` gibt.

Indizes oder Schlüssel sind vom gleichen Typ wie die, die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegeben werden.

Siehe auch: [`findfirst`](@ref), [`findprev`](@ref), [`findall`](@ref).

# Beispiele

```jldoctest
julia> A = [true, false, true, false]
4-element Vector{Bool}:
 1
 0
 1
 0

julia> findlast(A)
3

julia> A = falses(2,2);

julia> findlast(A) # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> findlast(A)
CartesianIndex(2, 1)
```
